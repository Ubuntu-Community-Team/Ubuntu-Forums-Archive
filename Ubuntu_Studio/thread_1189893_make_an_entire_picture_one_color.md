---
title: "make an entire picture one color"
date: 2009-06-17
forum: Ubuntu Studio
---

### Post by ZeldaFan on 2009-06-17
How do I make a picture entirely one color (that is not black or white) in GIMP? I have it primarily that color but there are random dots here and there in different colors.

---

### Post by unutbu on 2009-06-17
If you are using GIMP 2.6, click Colors>Colorize...
I forget if there is this menu item in older versions of GIMP.
It probably is there. But if it is not, then you could also
do it the long way:
```

Color>Desaturate
In the Layers window, Make new layer
Fill the new layer with the color you want
In the Layers window, change the layer mode to "Multiply".
```

---

### Post by kayosiii on 2009-06-17
edit->fill there are two options foreground and background

---

### Post by sedawk on 2009-06-17
You mean something like a greyscale picture, but only in 
"redscale", "greenscale", "bluescale", or a "greyscale"
in an arbitrary color (E.g. like putting a colored "filter"
on top of a greyscale photography)?

---

### Post by ZeldaFan on 2009-06-17
The colorize function worked fine, because I could just make everything white and then fill with the specific color I wanted. But I was wondering, if I had the specific color I wanted (with the HTML code b/c its the only surefire way to use that specific color), if there's a way to colorize to that color.

---

### Post by raboofje on 2009-06-17
> **ZeldaFan said:**
> The colorize function worked fine, because I could just make everything white and then fill with the specific color I wanted. But I was wondering, if I had the specific color I wanted (with the HTML code b/c its the only surefire way to use that specific color), if there's a way to colorize to that color.

You can use [http://arnout.engelen.eu/files/dev/hsvrgb.html](http://arnout.engelen.eu/files/dev/hsvrgb.html) to convert between RGB (decimal, not hex) and HSV. Then use those values for colorize.

Edit: just noticed: that script does HSV, not HSL, while gimp uses the latter. The 'hue' value will still be useful though :).

---

### Post by kayosiii on 2009-06-18
With regards to colourising to a specific colour the following should work
1) Create a new layer
2) fill it with the colour you want
3) select the layer you want to colourise and desaturate it.
4) place it above the colour layer
5) set it's merge mode to "multiply"

---

### Post by mcduck on 2009-06-18
> **kayosiii said:**
> With regards to colourising to a specific colour the following should work
1) Create a new layer
2) fill it with the colour you want
3) select the layer you want to colourise and desaturate it.
4) place it above the colour layer
5) set it's merge mode to "multiply"

Or even simpler:

1. Create a new layer above the one you wish to colorize
2. Fill with the color you want
3. Set the layer's blending mode to "Color" (or "Hue").

---

### Post by MINHAJUL ISLAM on 2009-06-26
Bro I can not Make A Forum Image Plz Make a New Image

---

