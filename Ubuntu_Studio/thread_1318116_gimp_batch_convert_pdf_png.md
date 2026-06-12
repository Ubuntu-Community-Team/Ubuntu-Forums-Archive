---
title: "gimp batch convert pdf png"
date: 2009-11-07
forum: Ubuntu Studio
---

### Post by rick71 on 2009-11-07
Can anyone tell me how get gimp to batch convert a directory of pdf files to pngs? I can convert them one by one from the UI, and I like the default output, so I'd like to use whatever settings GIMP uses when converting from the UI.

Any and all help appreciated.

---

### Post by cotcot on 2009-11-07
Have you installed ImageMagick ?

If so open terminal, go to the folder with the pdf's (cd) and do
```
mogrify -format png *.pdf
```

---

### Post by rick71 on 2009-11-07
> **cotcot said:**
> Have you installed ImageMagick ?

If so open terminal, go to the folder with the pdf's (cd) and do
```
mogrify -format png *.pdf
```

I do have ImageMagick installed. I have tried:

```
convert 002.pdf -density 200 -resize 843x1099 -quality 90 002.png
```

But the resulting PNGs are of much lower quality than what GIMP produces. I'll give the mogrify command a shot. Thanks.

---

### Post by rick71 on 2009-11-07
It seems mogrify also results in a degraded image.

---

### Post by kaibob on 2009-11-07
I ran your command on a pdf file and got a degraded png file. I then eliminated the options one at a time and found that the resize option was responsible for the degradation. I don't know if this is the case with your pdf file, but I think you simply have to experiment to see what is causing the problem. The first step, of course, is to eliminate all options and see if the resulting png file is degraded.

If you can't get imagemagick to work, ghostscript is an alternative, but I would try to get things resolved with imagemagick first. 

BTW, as far as I know, convert and mogrify differ as to file handling not image conversion.

As to your original issue, I don't use gimp and can't be of help there. Hopefully, with this bump, someone will be able to answer your question as to gimp settings.

---

### Post by rick71 on 2009-11-08
I have found using 
```
convert -units pixelsperinch -density 200x200 file.pdf file.png
```
works. Thanks for the help and pointers.

---

### Post by Inaimathi on 2011-03-27
I'll throw in my two cents, since I recently had the same problem; ```
-resize
``` has nothing to do with it, you need to put the ```
-density
``` directive before the filename you convert. You also don't need to specify both dimensions (geometry does that for you, maintaining aspect ratio by default). So

```
convert -density 200 foo.pdf -resize 843 foo.png
```

should do what you initially wanted to. Ive found that a density lower than ```
300
``` doesn't produce very crisp images though, and you may want to bump it up further if you need really high-quality pics. Obviously, the higher it is, the longer image processing will take, so balance the need for quality with the need for speed.

---

