---
title: "GIMP Hue-Saturation Tool in ImageMagick"
date: 2009-11-17
forum: Ubuntu Studio
---

### Post by pores_n on 2009-11-17
GIMP's Hue-Saturation tool has options "Select Primary Color to Adjust".
So we can change Hue, Lightness and Saturation of the specific color range.
It seems to divide colors to 6 Hue range (60 degrees), and operate HSV in only one range.

ImageMagick has "modulate" option to change HSV.
[http://www.imagemagick.org/Usage/color/#modulate](http://www.imagemagick.org/Usage/color/#modulate)
But it doesn't seem to have specific color range operations.

I have 200+ pictures to change HSV.
I'd like to know how to change the specific color range's HSV with ImageMagick.
Any other script tool is also welcome.

---

### Post by pores_n on 2009-11-22
This is self reply.

GIMP's Hue-Saturation tool seems to use HSL, not HSV.
I divided to HSL channel and changed saturation channel with cosine function, due to non-linear transformation is needed.

Here is code.
```
ls *.JPG | xargs -I "FILENAME" \
convert "FILENAME" -colorspace HSL -channel G -fx ${function} \
-colorspace RGB converted_"FILENAME"
```

Note: In HSL colorspace, channel G of ImageMagick means saturation channel.

${function} is like below.
```
function="g*(${R_base}*0.5*((${R_extra}+1)+(${R_extra}-1)*cos(2*pi*(r-${H_rot}))))"
```

r is hue value of pixel.
g is saturation value of pixel.

R_base is base saturation ratio. (ex. 1.2)
R_extra is extra saturation ratio. (ex. 1.4)
Maximum ratio is R_base * R_extra.

H_rot is hue angle of maximum saturation ratio. (ex. 0.5, this means cyan)

But this way is very slow.
100 second per one picture with 6M pixels.

It had better calculate constant value before execute ImageMagick.
So, ${function} is like below.
```
function="g*(${C_a}+(${C_b}*cos(${C_c}*(r-${H_rot}))))"
```
It compresses time to 30 seconds per one picture.
However it is a bit slow.

---

