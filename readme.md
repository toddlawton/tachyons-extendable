# TACHYONS EXTENDABLE

Extendable functional css for humans.

Quickly build and design new UI without writing css.

This is a fork of [tachyons-custom](https://github.com/tachyons-css/tachyons-custom) which makes use of PostCSS placeholders. When used in conjunction with [postcss-extend](https://github.com/travco/postcss-extend) it is possible to take full advantage of Tachyons without bloating your markup with classnames. Since placeholders act as virtual classes, only those which are `@extend`ed will be included in the final output CSS.



##### src/_position.css
```
/*

   POSITIONING
   Docs: http://tachyons.io/docs/layout/position/

   Media Query Extensions:
     -ns = not-small
     -m  = medium
     -l  = large

*/

%static { position: static; }
%relative  { position: relative; }
%absolute  { position: absolute; }
%fixed  { position: fixed; }

@each $bkpt, $nmsp in (--breakpoint-not-small, --breakpoint-medium, --breakpoint-large), (ns, m, l) {
  @media ($bkpt) {
    %static-$(nmsp) {
      @extend %static;
    }
    %relative-$(nmsp) {
      @extend %relative;
    }
    %absolute-$(nmsp) {
      @extend %absolute;
    }
    %fixed-$(nmsp) {
      @extend %fixed;
    }
  }
}
```

## Requirements

* [postcss](https://github.com/postcss/postcss)
* [postcss-extend](https://github.com/travco/postcss-extend)
* [postcss-each](https://github.com/outpunk/postcss-each)


## Getting started

With `tachyons-extendable` and the deps above installed and configured, it is then simply a matter of composing CSS files in your application using the provided placeholders.

```
.big-title {
  @extend %pa1;
  @extend %bg-black-90;
  @extend %white;
  @extend %lh-copy;
  @extend %tracked-tight;
}
```


### Local Setup

Clone the repo from github and install dependencies through npm.

```
git clone https://github.com/toddlawton/tachyons-extendable.git
cd tachyons-extendable
npm install
```

## License

MIT
