---
title: "camera files (even raw) with 72dbi when uploaded"
date: 2013-10-10
forum: Ubuntu Studio
---

### Post by ninja-pri on 2013-10-10
I use ubuntu studio 13.04 and everytime I upload a file from my camera, it comes in 72dpi, in every software(darktable, gimp), I don't know how to change that, help!

---

### Post by jejeman on 2013-10-10
dbi? I assume dpi.

Make new image in GIMP with size you need, open image from camera as layer.

What's wrong with 72dpi? Why do you espect different?

---

### Post by ninja-pri on 2013-10-10
Sorry, I meant dpi. I sometimes need to print the pictures, so I need to be able to change it. I'll try that and come back, thanks.

---

### Post by coldraven on 2013-10-11
I Googled "screen resolution vs print resolution". 
Here are a couple of the results:
[http://www.gototheboard.com/articles/article_7/Resolution.pdf](http://www.gototheboard.com/articles/article_7/Resolution.pdf)
[http://www.vsellis.com/understanding-dpi-resolution-and-print-vs-web-images/](http://www.vsellis.com/understanding-dpi-resolution-and-print-vs-web-images/)

---

### Post by jejeman on 2013-10-11
ninja-pri,

Look, you have finite amount of pixels, so DPI does not matter. When you print, just set the size of the print and you will have maximum DPI automatically for that size. If you want to know for 300dpi which is the size for that amount of pixels you have, then just calculate it.
I don't see the point in setting 300dpi for jpegs. It all depends on program you use to print. Will it see the setting?

For example, my camera sets 300dpi to jpegs, and in that resolutions it is ~A3 format. Do I need A3 print, no I just want picture 10x15cm so what good it gave me setting 300dpi - none. So I just set the print size and let DPI be as much it has to be. In this case ~770dpi.

---

### Post by ninja-pri on 2013-10-11
It's not jpeg, it's raw camera files, and I want them in their original resolution, it seems that the os is changing the resolution, not the softwares, I even tried windows, and there, the images come in their original dpi. Why does that happen?

---

### Post by jejeman on 2013-10-11
Form my camera raw is, like the jpegs, in 300dpi, but that is not important at all. I'm still printing at ~770dpi 10x15cm photo.
I don't see why would OS change internal properties of a file. Maybe it just reads different info tags.
If, by any chance, you are losing pixel count then that is a problem, other wise DPI value is no issue at all.

Anyway, to cut the story short, you can use Imagemagick to change the DPI values with -density option.

---

