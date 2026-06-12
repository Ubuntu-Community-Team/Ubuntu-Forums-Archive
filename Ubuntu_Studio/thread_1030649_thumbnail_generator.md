---
title: "thumbnail generator"
date: 2009-01-04
forum: Ubuntu Studio
---

### Post by mckelly46 on 2009-01-04
Hello all,

I'm looking for a good, linux-based thumbnail generator app. Any recommendations or preferences?

Cheers,

Michael

---

### Post by shecky on 2009-01-04
ImageMagick is pretty decent for thumbnail generating.
```
sudo apt-get install imagemagick
```
To make thumbnails of all the JPGs in a directory with a width of 100 pixels:
```
cd /path/to/image_directory
for i in $(ls *.jpg); do convert -scale 100 $i th-$i; done
```

---

### Post by brucewestfall on 2009-01-05
I am playing with Album Shaper right now.  Real nice for making html albums. I like the way you can easily add captions also.

sudo apt-get install albumshaper

should work

Even if you don't want an html album, it will make thumbnails of all the images you add to it.  ImageMagick is the best choice for making thumbnails - albumshaper is just a nice easy to use gui version.  I think it does drag-and-drop also. (not sure, sorry.)

---

### Post by Jabz.biz on 2009-01-07
You can also use the Gimp for that matter. Similar to Photoshop, Gimp has Actions for mass-handling. You can write these yourself or download them on the net. Simply check [Google for Gimp Actions]("http://www.google.com/search?q=Gimp+Actions").

---

