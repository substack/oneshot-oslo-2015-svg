# some fun things to do with svg

![wizard](images/wizard.svg)

---
# about:me

substack

Oakland, California

working on:
[omega projects](https://github.com/substack/omega-projects/issues)

---
# how I survived murphy's law

"Anything that can go wrong, will go wrong."

---
# how I survived murphy's law

It's the law.

---
# how I survived murphy's law

* I'm very sick right now.

---
# how I survived murphy's law

* I'm very sick right now.
* My linux system completely broke yesterday.

---
# how I survived murphy's law

* I'm very sick right now.
* My linux system completely broke yesterday.
* I'm in a strange country where everything is
  expensive and I don't speak the language.

---
# how I survived murphy's law

* I'm very sick right now.
* My linux system completely broke yesterday.
* I'm in a strange country where everything is
  expensive and I don't speak the language.
* I wrote my own slide viewer software right
  before my talk.

---
# how I survived murphy's law

* I'm very sick right now.
* My linux system completely broke yesterday.
* I'm in a strange country where everything is
  expensive and I don't speak the language.
* I wrote my own slide viewer software right
  before my talk.
* I'm about to do some live coding

---
# how I survived murphy's law

* I'm very sick right now.
* My linux system completely broke yesterday.
* I'm in a strange country where everything is
  expensive and I don't speak the language.
* I wrote my own slide viewer software right
  before my talk.
* I'm about to do some live coding
  inside the presentation software I just wrote.

---
# how I survived murphy's law

WHAT COULD POSSIBLY GO WRONG

![pony](images/pony.svg)

---
# circuit boards

[tech report](http://substack.net/doc/rov-2010-tech-report.pdf)

![circuit](images/topside.svg)

---
# meet inkscape

* free and open source vector graphics tool

---
# svg crash course

``` svg
<svg xmlns="http://www.w3.org/2000/svg">...</svg>
```

---
# svg

``` svg
<svg width="800" height="500" xmlns="http://www.w3.org/2000/svg">
  <circle cx="300" cy="200" r="100" fill="purple" />
</svg>
```

<script>
function hue2rgb(p, q, t){
    if(t < 0) t += 1;
    if(t > 1) t -= 1;
    if(t < 1/6) return p + (q - p) * 6 * t;
    if(t < 1/2) return q;
    if(t < 2/3) return p + (q - p) * (2/3 - t) * 6;
    return p;
}
function hsl2rgb(h, s, l) {
    var r,g,b;
    h = parseInt(h,10)/360;
    s = parseInt(s,10)/100;
    l = parseInt(l,10)/100;
    if ( s === 0 ) {
        r = g = b = l;
    } else {
        var q = l < 0.5 ?  l * (1 + s) : l+s - l*s;
        var p = 2*l - q;
        r = hue2rgb(p,q,h+1/3);
        g = hue2rgb(p,q,h);
        b = hue2rgb(p,q,h - 1/3);
    }
    r = Math.round(r*255);
    g = Math.round(g*255);
    b = Math.round(b*255);
    return 'rgb('+r+','+g+','+b+')';
}
</script>

![circle](images/circle.svg)

---
# attributes

* `fill`
* `stroke`
* `stroke-width

---
``` svg
<circle cx="300" cy="200" r="5" fill="purple" />
```

* `cx` - center x coordinate
* `cy` - center y coordinate
* `r` - radius

![circle](images/circle.svg)

---
# `<rect>`

``` svg
<rect x="1" y="1" width="998" height="298"
  fill="orange" stroke-width="2" />
```

![rect](images/rect.svg)

---
# if you don't put the `/>`

``` svg
<rect x="1" y="1" width="998" height="298"
  fill="orange" stroke-width="2">
```

aaaaaaaaaaaaaaaaaaaaaaaaa

![rect](images/rect_fucked.svg)

---
# other things that will waste your time

* if you don't put `xmlns` in the `<svg>` tag
* blank image because your image is clipped
* xml extremism

---
# `<text>`

``` svg
<text x="250" y="150" font-family="Verdana" font-size="55">
  whatever
</text>
```

<script>
function hue2rgb(p, q, t){
    if(t < 0) t += 1;
    if(t > 1) t -= 1;
    if(t < 1/6) return p + (q - p) * 6 * t;
    if(t < 1/2) return q;
    if(t < 2/3) return p + (q - p) * (2/3 - t) * 6;
    return p;
}
function hsl2rgb(h, s, l) {
    var r,g,b;
    h = parseInt(h,10)/360;
    s = parseInt(s,10)/100;
    l = parseInt(l,10)/100;
    if ( s === 0 ) {
        r = g = b = l;
    } else {
        var q = l < 0.5 ?  l * (1 + s) : l+s - l*s;
        var p = 2*l - q;
        r = hue2rgb(p,q,h+1/3);
        g = hue2rgb(p,q,h);
        b = hue2rgb(p,q,h - 1/3);
    }
    r = Math.round(r*255);
    g = Math.round(g*255);
    b = Math.round(b*255);
    return 'rgb('+r+','+g+','+b+')';
}
</script>

![text](images/text.svg)

---
# transforms

Set the "transform" attribute to any of these:

* transform
* scale
* rotate
* scaleX
* scaleY
* matrix

---
# translate

``` svg
<svg xmlns="http://www.w3.org/2000/svg" width="800" height="500">
  <circle cx="300" cy="200" r="200" fill="cyan" />
  <circle transform="translate(30,20)" cx="300" cy="200" r="200" fill="purple" />
</svg>
```

![translate](images/translate.svg)

---
# scale

``` svg
<svg xmlns="http://www.w3.org/2000/svg" width="800" height="700">
  <circle transform="scale(0.5,2)" cx="100" cy="200" r="100" fill="red" />
</svg>
```

![scale](images/scale.svg)

---
# rotate

``` svg
<svg xmlns="http://www.w3.org/2000/svg" width="800" height="500">
<rect x="200" y="1" width="400" height="200"
  fill="orange" stroke-width="2" transform="rotate(30)" />
</svg>
```

![rotate](images/rotate.svg)

---
# `<g>`

Create a group of elements.

You can transform all the child nodes of a g by setting a
transform on a `<g>` element.

---
# `<path>`

create a shape from a path string

``` svg
<path d="M 100 100 L 300 100 L 200 300 z"
  fill="orange" stroke="black" stroke-width="3" />
```

![path](images/path.svg)

---
# path string syntax

* `M x,y` - move to (absolute)
* `m dx,dy` - move to (relative)

* `L x,y` - line to (absolute)
* `l dx,dy` - line to (relative)

* `C c1x,c1y c2x,c2y x,y` - curve to (absolute)
* `c dc1x,dc1y dc2x,dc2y dx,dy` - curve to (relative)

* `z` / `Z` - close path

Some others:

* A/a - elliptical arc
* T/t - quadratic bezier curve
* S/s - cubic bezier curve

---
# `<polygon>`

create a closed shape from line segments

``` svg
<polygon points="60,20 100,40 100,80 60,100 20,80 20,40" fill="lime" />
```

![polygon](images/polygon.svg)

---
# `<polyline>`

create an open shape from line segments

``` svg
<polyline points="60,20 100,40 100,80 60,100 20,80 20,40"
  stroke="purple" fill="transparent" stroke-width="8px" />
```

![polyline](images/polyline.svg)

---

paths, polylines, and polygons are great for interactive
graphs and visualizations

---

You can also dynamically construct elements with javascript!

---
# document.createElementNS()

Constructing elements is a bit weird:

``` js
var svg = document.createElementNS('svg', 'http://www.w3.org/2000/svg');
var circle = document.createElementNS('circle', 'http://www.w3.org/2000/svg');
```

---
# svg dom methods

All of the usual dom methods work on svg:

``` js
var circle = document.createElementNS('circle', 'http://www.w3.org/2000/svg');
circle.setAttribute('fill', 'cyan');

var circle2 = elem.cloneNode(true);
circle2.style.backgroundColor = 'orange';
```

---
# svg dom methods

some useful methods:

* `elem.cloneNode(true)` - copy a node and its children
* `elem.setAttribute(name, value)` - set an attribute

---
# svg-create-element

with the `svg-create-element` module, we can create svg
attributes more tersely with less remembering w3 urls:

``` js
var createElement = require('svg-create-element');
var svg = createElement('svg');
var circle = createElement('circle');
```

---
# inserting svgs into the page

Inlining svg into your html is annoying if you create the
svgs in an image program.

This works to display an image:

``` svg
<img src="cats.svg">
```

but you won't be able to manipulate the svg with javascript.

---
# loading an svg

Instead, we can use xhr to load an svg image, putting the
contents into a constructed `<div>` to pull out the `<svg>`
element:

``` js
var xhr = require('xhr');

xhr('cats.svg', function (err, res, body) {
    if (err) return console.error(err);
    if (/^2/.test(res.statusCode)) {
        return console.error(res.statusCode + ': ' + body);
    }
    var div = document.createElement('div');
    div.innerHTML = body;
    var svg = div.querySelector('svg');
    if (!svg) return console.error('no svg found');
    document.body.appendChild(svg);
});
```

---
# load-svg

or just use the `load-svg` package instead:

``` js
var loadsvg = require('load-svg');

loadsvg('cool.svg', function (err, svg) {
    document.body.appendChild(svg);
});
```

---
# window.requestAnimationFrame()

We can make animations using
`window.requestAnimationFrame()`:

``` js
window.requestAnimationFrame(loop);

function loop () {
    // update the scene here
}
```

---
# time delta

Not all computers are capable of running a simulation at 60
fps. By computing a time delta, you can make your simulation
work even on systems that can't keep up at 60 fps.

---
# time delta

``` js
var last = Date.now();
window.requestAnimationFrame(loop);

function loop () {
    var now = Date.now();
    var dt = last - now;
    last = now;
    
    // update the scene here based on dt
}
```

---
# frame-loop

Use frame-loop to automatically set up the request animation
frame loop with the time difference `dt`:

```
var loop = require('frame-loop');
var engine = loop(function (dt) {
    // ...
});
engine.run();
```
---
# frame-loop

You can also set timers and intervals based on game time:

``` js
var loop = require('frame-loop');
var engine = loop(function (dt) {
    // ...
});

engine.setInterval(function () {
    console.log('beep');
}, 1000);

engine.setTimeout(function () {
    engine.pause();
}, 5000);

engine.run();
```

These timers can be paused with `engine.pause()`.

---
# 2d physics

``` js
position.x += velocity.x * dt;
position.y += velocity.y * dt;

velocity.x += acceleration.x * dt;
velocity.y += acceleration.y * dt;
```

---
# box-sprite-svg

Wrap an svg element with physics!

``` js
var sprite = require('box-sprite-svg');
var player = sprite(document.querySelector('svg #player'));

var loop = require('frame-loop');
var engine = loop(function (dt) {
    player.tick(dt);
});
engine.run();

window.addEventListener('keydown', function (ev) {
    if (ev.keyCode === 37) {
        player.velocity.x = -400;
    }
    else if (ev.keyCode === 39) {
        player.velocity.x = 400;
    }
});
window.addEventListener('keyup', function (ev) {
    if (ev.keyCode === 37 || ev.keyCode === 39) {
        player.velocity.x = 0;
    }
});
```

---
# .getBoundingClientRect()

You can get a bounding box on any svg element:

``` js
document.querySelector('#player').getBoundingClientRect()
```

prints:

```
ClientRect {height: 100, width: 100, left: 250, bottom: 350, right: 350…}
```

---
# box-sprite-svg bbox()

Handily, box-sprite-svg exposes a `.bbox()` method that
calls `.getBoundingClientRect()`:

``` js
var sprite = require('box-sprite-svg');
var player = sprite(document.querySelector('svg #player'));
console.log(player.bbox());
```

prints:

```
{ bottom: 350, height: 100, left: 250, right: 350, top: 250, width: 100 }
```

---
# box-collide

Given two bounding boxes, the box-collide module will tell
you if they collide:

``` js
var collide = require('box-collide');
var a = document.querySelector('#a');
var b = document.querySelector('#b');
console.log(collide(a, b));
```

---
# an idea

What if you could just draw your game?

* You don't need to write a level editor, just use inkscape!
---
# wall street panic

[wall st panic](http://localhost:43545)

![wallst](images/wallst.svg)

---
# what about robots

what IF

---
# some modules

first, some modules:

* svg-linearize
* svg-line-segments
* svg-create-element
* abs-svg-path
* parse-svg-path
* simplify-geometry

---
# robot dinosaur

[svg 2 inform](http://substack.neocities.org/svg2inform.html)

![apatosaur](images/apatosaur.svg)

---

![robot drawing a dinosaur](https://www.youtube.com/watch?v=pY9v50FBd5E)

---

EOF
