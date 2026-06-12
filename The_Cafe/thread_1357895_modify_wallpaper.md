---
title: "modify wallpaper"
date: 2009-12-17
forum: The Cafe
---

### Post by rkakkar on 2009-12-17
hey can someone please remove all text from this image? i'd really appreciate it.

[http://images2.fanpop.com/images/photos/2900000/True-Blood-true-blood-2965909-1024-768.jpg](http://images2.fanpop.com/images/photos/2900000/True-Blood-true-blood-2965909-1024-768.jpg)

---

### Post by John Bean on 2009-12-17
Why not ask instead how to do it yourself?

Clue: a few seconds with a clone tool in GIMP can work wonders :-)

---

### Post by MaxIBoy on 2009-12-18
That gradient appears to be almost up-and-down but not quite, with some minor error dithering and jpeg compression artefacts. For a straight horizontal gradient or for a smooth gradient in a lossless format like png, this is a bit easier, but its still quite easy to do.

A good way to figure out the approximate angle of the gradient is to use the magic wand tool (see attachment 1.) You can see roughly the direction at which the gradient is angled, and you can use the fuzzy looking outlines as guidelines.

You can then draw path along that approximate band of color and convert it to a selection (see attachment 2.) 

Take a cross section of that selection (see attachment 3.) Be sure to set the rectangular selection tool to "intersect with current selection."

Copy the selection and paste it over and over, moving it slightly up each time, and it will match up with the gradient! (see attachment 4.) I recommend doing this in another layer on top of the main one, so you can see where to match it. As you can see, I set the main layer mostly transparent. When you're done, set the main layer as fully opaque, merge the layers, and export the file!

Not really that hard to do. If you don't know how to add a new layer, use the magic wand tool or anything like that, you can easily find it in the GIMP manuals.

Have fun, and I hope people find this mini-tutorial helpful!

---

### Post by rkakkar on 2009-12-21
> **MaxIBoy said:**
> That gradient appears to be almost up-and-down but not quite, with some minor error dithering and jpeg compression artefacts. For a straight horizontal gradient or for a smooth gradient in a lossless format like png, this is a bit easier, but its still quite easy to do.

A good way to figure out the approximate angle of the gradient is to use the magic wand tool (see attachment 1.) You can see roughly the direction at which the gradient is angled, and you can use the fuzzy looking outlines as guidelines.

You can then draw path along that approximate band of color and convert it to a selection (see attachment 2.) 

Take a cross section of that selection (see attachment 3.) Be sure to set the rectangular selection tool to "intersect with current selection."

Copy the selection and paste it over and over, moving it slightly up each time, and it will match up with the gradient! (see attachment 4.) I recommend doing this in another layer on top of the main one, so you can see where to match it. As you can see, I set the main layer mostly transparent. When you're done, set the main layer as fully opaque, merge the layers, and export the file!

Not really that hard to do. If you don't know how to add a new layer, use the magic wand tool or anything like that, you can easily find it in the GIMP manuals.

Have fun, and I hope people find this mini-tutorial helpful!



this is GREAT! thanks!

---

