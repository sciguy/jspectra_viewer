## JSpectraViewer (JSV) ##

A Javascript library for viewing spectra. While designed primarily for NMR spectra, it can be used for any XY plot.

### Documentation and Demos ###

For the latest documentation, download the repository and open the following file:
_docs/index.html_

A demo of JSV can be found in the _demo_ directory.

### Dependencies ###
* D3 - http://d3js.org
* x2js - https://github.com/abdmob/x2js (Optional. Required to read nmrML data)

### Setup ###

* Copy the dependencies (d3.v3.min.js) and jspectra_viewer.js to your javascript folder.
* Add script tags pointing to the files in your html:

```html
<script src='javascript/d3.v3.min.js'></script>
<script src='javascript/jspectra_viewer.js'></script>
```

* Copy jspectra_viewer.css to your stylesheets folder and add a link to the file in your html:

```html
<link rel="stylesheet" href="stylesheets/jspectra_viewer.css" />
```

### Create new viewer ###

Create a container for the viewer in HTML:

```html
<div id='my-spectra'></div>
```

Create viewer:
```js
sv = new JSV.SpectraViewer('#my-spectra', {
  height: 450,
  width: 850,
  axis_y_lock: true,
  axis_y_show: true,
  axis_x_label: 'ppm'
});
sv.flash('Loading...')
```

See [SpectraViewer](SpectraViewer.js.html) for details about additional options.

Add an XY plot:
```js
sv.add_spectrum(
  {
    id:'spectrum',
    name: 'Spectrum',
    xy_line: xy_data
  },
  {color: '#00F'}
);
```

### XY data format ###
The XY data is an object with x and y arrays:
```js
xy_data = { x: [0, 1, 2], y: [0, 2, 4] };
```
Additional data formats are described in [SpectraViewer.add_spectrum](SpectraViewer.js.html#add_spectrum).


### JSV Namespace ###
All JSV classes and utility functions are accessed through the JSV namespace:
```js
merged = JSV.merge({a:1, b:1}, {b:2, c:3}); // => {a:1, b:2, c:3}
```

If a JSV object already exists, you can use the full name of JSpectraViewer instead:
```js
merged = JSpectraViewer.merge({a:1, b:1}, {b:2, c:3}); // => {a:1, b:2, c:3}
```

### Spectra Viewer Controls ###

Action              | Command
--------------------|-------------
Zoom In/Out X Axis  | Scroll wheel
Zoom In/Out Y Axis  | Alt/Option Key + Scroll wheel
Zoom In on Area     | Alt/Option Key + Click and Drag around area
Zoom Out Completely | Alt/Option Key + Click once anywhere on viewer.
Move Around         | Click and Drag

### Zoombox Controls (box in upper left corner) ###

Action              | Command
--------------------|-------------
Move Around         | Click and Drag grey selection box
Zoom In on Area     | Click on unselected region and drag around new selection
Zoom Out Completely | Click once anywhere in unselected region
Alter Zoomed Area   | Click and Drag on sides of grey selection box
