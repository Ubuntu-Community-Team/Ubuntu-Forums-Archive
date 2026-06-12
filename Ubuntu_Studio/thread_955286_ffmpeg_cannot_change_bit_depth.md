---
title: "ffmpeg cannot change bit depth"
date: 2008-10-22
forum: Ubuntu Studio
---

### Post by susiriss on 2008-10-22
Hi all,
I have installed ffmpeg from source in my Hardy. I want clips converted to have a color depth of 12bpp ( bits per pixel).

I tried with the option -pix_fmt like this,


```
ffmpeg -i myclip.wmv -vcodec mpeg4 -acodec libfaac -pix_fmt yuyv422 -f avi test.avi
```

But the encoded clip always has color depth 24bpp.

Isn't this the way I should use to convert the color depth. What I am doing wrong.

Thanks
-susiriss

---

### Post by zenith001 on 2008-10-23
[Crusher](http://www.crusher.south.am)[Jaw Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Jaw-Crusher/Jaw-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Cone-Crusher/Cone-Crusher.html)[Cone Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/HPC-Cone-Crusher/HPC-Cone-Crusher.html)[Impact Crusher](http://www.crusher.south.am/Crushing-Equipment/Crusher/Impact-Crusher/Impact-Crusher.html)

---

