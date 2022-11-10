# CSS Cheat Sheet
So it begins. My cheat sheet for CSS By SHIBAM NATH ❤❤

### HTML elements
* block elements - always starts on a new line and takes up the whole block (div, fieldset, form, footer, h1-h6, header, li, nav, ol, p, table, ul, video)
* inline elements - do not start on a new line and only take up as much width as necessary (a, button, i, img, input, label, span, strong, textarea). Margin top and botton won't be applied to them because the box model isn't working for inline elements. If we want them to be treated as block elements, we have to give them the ```display: block``` profull width availableperty. If we want them to be treated like blocked AND inline element, we should give the m ```display: inline-block```

### Terminology 
* descendants - children + grandchildren + ... of
* children - only first level
* inheritance - inherits the style from the parent element (the ```inherit``` value)

### Important tips
* the browser is "reading" the CSS from top to bottom (cascade) - two identical selectors with different properties, the bottom one will win
* if some font families have 2 words, we need to put them in quote marks

### Selectors
* ```#container``` - ID selector
* ```.container``` - class selector
* ```span``` - element selector
* ```span, div, p``` - multiple elements selector
* ```#container p``` - select ```p``` that is the descendant of ```#container```
* ```#container > p``` - select ```p``` that is the child od ```#container```
* ```h2 + p``` - adjacent selector, the one that comes directly after the ```h2```
* ```input[type="text"]``` - attribute selector
* ```span:hover``` - dynamic pseudo selector (behavior) - hover, presses, checked etc
* ```ul:nth-child(5)``` - structural pseudo selector (parent-child relationship) - 5th li tag, element without children etc.
* ```*``` - universal selector (mostly used to override default styles)

### Selector specificity points

CSS Specificity is the set of the rules applied to CSS selectors in order to determine which style is applied to an element. The more specific a CSS style is, the higher point value it accrues, and the likelier it is to be present on the element's style.

* inline style - 1000 points
* ID - 100 points
* classes, pseudo class, attribute - 10 points
* elements - 1 point
* !important - overrides everything (try not to use this, rather write nice and clean code!)

```css
body #content .data img(:hover) /* 1 + 100 + 10 + 1 + 10 = 122 */
```
### The box model
How (block level) elements represent themselves in terms of space.
![The box model](https://s3.amazonaws.com/viking_education/web_development/web_app_eng/css_box_model_chrome.png)
```css
.box {
  margin: 30px 20px 15px 5px; /* top-right-bottom-left */
  padding: 30px;
  border: 1px solid black;
  width: 400px; /* width of the blue box */ 
  height: 200px;
  /* 
    total width will be 522px = 400px + 2*margin + 2*padding + 2*border 
    that means that if we set the width to 100%, it can break through and produce unwanted behavior
    pay attention to collapsing margins - 30px + 30px =/= 60px.
  */ 
}
```

# HTML variables
```css
# definition
:root {
  --primary: blue;
}
# usage
background: var(--primary);
```

# CSS properties
### Font size
* absolute - px
* relative - em, percentages - used when making responsive design

```css
.container {
  font-size: 12px;
}
article {
  font-size: 14px;
}
article h2 {
  font-size: 2em; /* inherit font size from article and miltiple it by 2 */
}
article p {
  font-size: 50%; /* inherit font size from article and take 50% of size */
}
```

### Font family
Note: some families already exist on user's computer. Remember to use the font family stack for fallbacks.
```css
.container {
  font-family: arial, helvetica, sans-serif; /* if arial is not available, use helvetica etc. */
}
```

### Text decoration
Possible values: ```inerhit|line-through|none|underline|overline|inherit```
```css
.container {
  text-decoration: underline;
}
```

### Font weight
Possible values: ```normal|bold|bolder|lighter|number|initial|inherit```

Note: Bold is same as 700, normal is same as 400. Most font families won't have every possible number value.

Note: some font families don't have certain weights as their options!
```css
.container {
  font-weight: bolder;
}
```

### Text transform
Changing the letter casing.

Possible values: ```none|capitalize|uppercase|lowercase|initial|inherit```
```css
.container {
  text-transform: uppercase;
}
```

### Text color
Changing the color of the text.
```css
 .container {
  color: blue;
  color: #FEFEFE;
 }
```

### Letter spacing and word spacing
Spacing between letters: e.g. s p a c i n g

Spacing between words: e.g. space   between   words

Values mostly in pixels;
```css
.container {
  letter-spacing: 3px;
  word-spacing: 5px;
  letter-spacing: 2em; /* the case with em's is font-size times number of em's */
}
```

### Line height
Vertical space between lines in a paragraph. Not the gap, just the height of the line.

The font size itself is not included, meaning,if you put ```line-height``` to be 12px and the ```font-size``` itself is 12px, nothig will happen.

Possible values: normal|number|length|initial|inherit
```css
.container {
  line-height: 24px;
  line-height: 2em; /* the case with em's is font-size times number of em's */
}
```

### Border style
Mostly used values: solid|none|hidden
```css
.container {
  border: 1px solid black; /* width, style, color */
  border-radius: 10px; /* for rounded corners; it has 4 corners */
  border-radius: 5px 10px 30px 20px; /* different corenrs */
}
```

### Width and height
They Can be static (in pixels) and dynamic (in percentages).
```css
.container {
  height: 100px; /* static height */
  width: 300px; /* static width, no matter how big the browser is */
  width: 70%; /* dynamic, width is 70% of the parent element */
}
.container{
  width: 40%;
  display: inline-block; /* display inline but keep respecting the box model (block elements) */
}
```

### Background
It can be colored or used an image background.
```css
.container {
  width: 500px;
  height: 500px;
  background-color: #606060;
  background-image: url(https:url);
  background-repeat: no-repeat; /* if the image is smaller than the container and we don't want it to repeat */
  background-position: center; /* or we can specify in pixels */
  background-size: 100px; /* if we have an background image, we can resize it */
}
```

### Gradient
Smooth transitions between colors.
Useful links:
* https://uigradients.com
* http://www.gradients.io/
Important: add prefixes like ```-moz-``` and ```-webkit-``` for Mozilla Firefox and other supports.
```css
/* syntax */
background: linear-gradient(direction, color-stop1, color-stop2, ...);
.container {
  background: yellow; /* fallback, if gradient isn't supported in the browser */
  background: linear-gradient(to bottom right, red, yellow);
}
```

### Box shadow
Possible values: none|h-offset v-offset blur spread color |inset|initial|inherit

```css
.container {
  width: 100px;
  height: 100px;
  border: 1px solid #3d56b9;
  position: relative;
  box-shadow: 0 0 10px #3d56b9;
}
```

# CSS variables
Also known as "custom properties" (same thing). They are just like regular properties, just with ```--``` before them.

E.g. ```--my-property: value;```
```css
/*
the easiest way to declare them and use them anywhere,
because they are scoped to the element where they are defined 
*/
:root {
  --my-color: #aabbcc;
}
.box {
  color: var(--my-color);
  width: 500px;
  height: 500px;
}

.outro-text {
  color: var(--my-color);
}
```

# CSS positioning

### Floating elements
Possible values: left|right|inherit|none

Important: removes the element from the real document flow and floats it somewhere.

Example: floating columns
```css
/* both are block level elements */
.left, .right {
  float: left;
  width: 46%; /* not 50% because of padding + margin */
  padding: 1%;. Often used in combination with relative positioning. 
  margin 1%;
  background: yellow;
}

/*
wrapper of .left and .right (always the parent element!)
this css makes sure that anything after the .columns is cleared, meaning, it respects the normal document flow again
(because float will break it)
*/
.columns {
  display: block;
  content: "";
  clear: both;
}
```

### Position
Possible values: static|relative|absolute|fixed|inherit

* relative - the element is positioned relative to its normal position. It does NOT remove content from the normal document flow, it is still occuping it's expected position, but it's mostly just "offseted" from it's original position with top|bottom|right|left (without them nothing will happen). When relative element move, no other element on the layout are affected.
* absolute - allows you to place your element precisely where you want it. Often used in combination with relative positioning. The positioning is done relative to the first relatively (or absolutely) positioned parent element. The element is removed from the normal document flow.
* fixed - mostly used to fix the nav bar to the top, so when we scroll down, it stays "sticky". It also removes the element from the normal document flow.

### Stack order and z-index
Stack order - the further down in the HTML you are, the higher the stacking order is (LIFO).

E.g. for semantic rasons, the navigation should be at the top od the page, but visualy above all elements.

With it```z-index```, we are controling the stacking order.
```css
.nav {
  z-index: 1;
  position: relative; /*when using z-index, we have to include the position value*/
}
```

# Flexbox
A parent element gets a ```display: flex``` property, and his direct desendants become flex items. We can control how they shrink and how they grow. Flex items stack left to right.
Playground: https://codepen.io/collection/AWOkYM/
```css
.container {
  display: flex;
}
```

### flex-grow
If there is room left in the container, items will grow and fill that space.
```css
.box {
  flex-grow: 1; /* grow rate. every box will have the same rate */
}
```

### flex-shrink
Same as ```flex-grow```, just for shrinking items. When we start shrinking the browser window beneath the parent width, the items will shrink in the given rate.

### flex-wrap
If flex-items have a min width, when shrinking the browser, the last element will eventually exit the screen and a scrollbar will appear. If we want to move that item to the next row, we can use ```flex-wrap: wrap```. If we want that item to move above other flex items, we can use ```flex-wrap: wrap-reverse```. Check the codepen url.

### flex-basis
Similar to ```min-width``` but instead of showing the scrollbar when shrinked beneath the defined value, they will shrink as normal flex items.

### justify-content
Aligns the flexible container's items when the items do not use all available space on the main-axis (horizontally).

In other hand, on the cross-axis, the same thing does the ```align-items``` property.

__Important!__ The elements __always__ follow the direction of the main-axis!

Possible values: flex-start|flex-end|center|space-between|space-around|initial|inherit

### flex-flow
Make the flexible items display in reverse order, or vertically.

```css
.container {
  display: -webkit-flex; /* Safari */
  -webkit-flex-flow: row-reverse wrap; /* Safari 6.1+ */
  display: flex;
  flex-flow: row-reverse wrap;
}
```
# Grid

When you put a ```display: grid``` on a container, you make its direct children grid items. Just putting ```display: grid``` doesn't do much because we have to "slice and dice" columns and rows, so we have to say how big they have to be.

```css
.container {
  display: grid;
  grid-template-columns: 100px 100px 100px; /* 3 columns */
  grid-gap: 20px;
}

```
### grid-template-columns
With ```grid-template-columns``` we are defining how many columns does our grid have and what width should they be.
Whatever the full width of the grid is, each column is going to be 1 fraction in width.
The fr unit allows you to set the size of a track as a fraction of the free space of the grid container. For example, this will set each item to one third the width of the grid container:
```css
.container {
  grid-template-columns: 1fr 1fr 1fr; /* shorthand: repeat(3, 1f3) */
}
```

### grid-column
Check the css grid generator by [sdras](https://github.com/sdras)
```css
.one {
  grid-column: 1/5; /* start from line one all the way to line 5 (first 4 columns) */
}
.two {
  grid-column: 6/9; /* start from line 6 all the way to line 9 */
}
.three {
  grid-column: 10/12; /* start from line 12 all the way to line 12 */
  grid-row: 2; /* start at 2nd row */
}
```

# Responsive design and media queries

Viewport meta tags tell the browser what width the viewport of the browser should be. Example of how a webpage can look like if the viewport meta tag is not used can be found [here](https://www.w3schools.com/tags/tag_meta.asp).
Media queries tell the browser how to style an element at particular viewport dimensions. They allow us to style elements differently on different widths.

```css
/* media query example */

@media screen and (max-width: 1400px) {
/*
on devices with screen width less than 1400 pixels, I want to apply these styles
or: when it reaches this width or below, apply these styles
we are adding just the styles that we want to override
*/
  .test {
    font-size: 14px;
  }
}
@media screen and (min-width: 620px) {
/*
on devices with screen width at least 620 pixels, I want to apply these styles
*/
  .test {
    font-size: 14px;
  }
}
```

