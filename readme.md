A simple layout utility for photos based on Flexbox. Its purpose is to allow building a simple one page photo portfolio with only basic HTML knowledge.

All `photo` element are grouped in `photos` within a `layout`, like here:

```html
<div class="layout">
  <div class="photos">
    <div class="photo width-4"><img src="photo-01.jpg"></div>
    <div class="photo width-4"><img src="photo-02.jpg"></div>
    <div class="photo width-4"><img src="photo-03.jpg"></div>
  </div>
</div>
```

Each photo has a width assigned, starting from `width-1` (being one twelfth of the layout's width: 8.33%) to `width-12` (the full width of the layout: 100%). The width of the layout itself also takes the viewport height into account (read this [article on vertical media queries](https://markus.is/designing/fluid-images/) for further details). In the example above all widths sum up to 12. If we've added another element or the last items would have `width-5` it would wrap into the next line.

There is a space between each element. I am using `box-sizing: border-box` – that way the padding will be included in the width). If two elements are next to each other the space will be summed up, that's why there's another space added to the surrounding `layout`.

Within each line the elements are vertically and horizontally centered, but this can be changed of course: vertically `top` and `bottom`, horizontally `left`, `right`, `space-between` and `space-around` (check out [this guide to the Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), this is how it works).

So each `photos` block has it own vertical and horizontal alignment, if you want to change this just add another `photos` block. The vertical alignment of elements within a block can be changed individually as well, the options are `top`, `center` and `bottom`. Here's an advanced example:

```html
<div class="layout">
  <div class="photos left bottom">
    <div class="photo width-4"><img src="photo-01.jpg"></div>
    <div class="photo width-6"><img src="photo-02.jpg"></div>
  </div>
  <div class="photos right top">
    <div class="photo width-2"><img src="photo-03.jpg"></div>
    <div class="photo width-5"><img src="photo-04.jpg"></div>
    <div class="photo width-3 bottom"><img src="photo-05.jpg"></div>
  </div>
</div>
```

In this example the elements of the first block have the widths 33.33% and 50% and the ones in the second block 16.66%, 41.66% and 25%. Each element has a different height (assuming all have the same ratio). The elements in the first block are vertically aligned to the bottom and the ones in the second block to to the top (besides the last element, this one's aligned to the bottom as well).

The height of each `element` depends on the photo ratio. In my example all photos are 3:2, but it of course works fine for different aspect ratios as well. I am using the [padding-bottom hack](https://www.smashingmagazine.com/2013/09/responsive-images-performance-problem-case-study/) for displaying the images (to avoid layout shifting while the images load).

See a demo page with different layouts here: [recurving.github.io/photo-layout](https://recurving.github.io/photo-layout/).

---

**Sidenote:** As said above the whole CSS is just meant to be simple enough for people without much knowledge to work with - otherwise I'd recommend building the same component with functional CSS libraries. Here is a quick example how I would solve it with [Tachyons](http://tachyons.io) (please note: the widths are in percent and not fractions):

```html
<div class="mw8 pa1 center">
  <div class="flex-ns flex-wrap-ns justify-end-ns items-end-ns">
    <div class="pa1 w-20-ns">
      <div class="aspect-ratio aspect-ratio--6x4">
        <img src="building.jpg" alt="Building" class="aspect-ratio--object">
      </div>
    </div>
    <div class="pa1 w-50-ns">
      <div class="aspect-ratio aspect-ratio--6x4">
        <img src="ocean.jpg" alt="Ocean" class="aspect-ratio--object">
      </div>
    </div>
    <div class="pa1 w-20-ns self-start-ns">
      <div class="aspect-ratio aspect-ratio--6x4">
        <img src="beach.jpg" alt="Beach" class="aspect-ratio--object">
      </div>
    </div>
  </div>
  <div class="flex-ns flex-wrap-ns justify-start-ns items-center-ns">
    <div class="pa1 w-70-ns">
      <div class="aspect-ratio aspect-ratio--6x4">
        <img src="window.jpg" alt="Window" class="aspect-ratio--object">
      </div>
    </div>
  </div>
  <div class="flex-ns flex-wrap-ns justify-center-ns items-start-ns">
    <div class="pa1 w-30-ns">
      <div class="aspect-ratio aspect-ratio--6x4">
        <img src="pier.jpg" alt="Pier" class="aspect-ratio--object">
      </div>
    </div>
    <div class="pa1 w-40-ns">
      <div class="aspect-ratio aspect-ratio--6x4">
        <img src="street.jpg" alt="Street" class="aspect-ratio--object">
      </div>
    </div>
  </div>
</div>
```
