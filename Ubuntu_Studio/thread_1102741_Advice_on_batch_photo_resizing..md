---
title: "Advice on batch photo resizing."
date: 2009-03-22
forum: Ubuntu Studio
---

### Post by kulturloseramerikaner on 2009-03-22
I need a photo archiving or manipulation program that can take all the jpg's from in a folder and downsize them as a group; does anyone know of a program for 'nix that can do this, or if there are several, what are your favorites?  I recently got back from a trip in which I took at least 700 shots with a pair of Canon DSLRs that I need to post on an image-hosting site.  I set the camera to record both the RAW files (which on the Canon have a .cr2 extension) and high-quality jpegs of each frame.  Ideally I'd like to be able to resize the jpg's as copies while keeping the original high-res jpg's and RAWs.  Obviously, resizing one-at-a-time in GIMP will be *extremely* time consuming so I need another option that hopefully won't involve ThatOtherOS.
Also, on a similar note, is there a plugin that will enable GIMP to read the .cr2's, or a better program for editing RAW files?

Thank you in advance.

---

### Post by lovinglinux on 2009-03-22
I recommend Phatch for batch processing and digikam for editing raw images and organizing your collection. DigiKam also has batch processing features.

---

### Post by FakeOutdoorsman on 2009-03-22
You can use ImageMagick.  It contains the ever useful "convert" tool and can easily do batch style converting:
```
convert *.jpg -resize 120x120 newimage.jpg
```
The above example will convert all jpg files in the current directory and resize the largest dimension of the original to 120 pixels.  You can also use a percentage:
```
convert *.jpg -resize 40% newimage.jpg
```

---

### Post by cotcot on 2009-03-22
And with ufraw you can manipulate the .cr2 and gimp-ufraw is the plugin for gimp to read them. The difference is that with gimp-ufraw you loose the high color depth. Gimp is limited to 8bit; ufraw can take 16 bit.

---

### Post by kulturloseramerikaner on 2009-03-24
Perfect thanks everyone.

---

### Post by binbash on 2009-03-26
+1 for phatch

---

### Post by ubigT on 2009-03-28
If you want another option you can have re-size and rotate extensions in your right click menu in Nautilus 

sudo apt-get install nautilus-image-converter

I find it quite handy :)

---

### Post by jo4hnc on 2009-03-28
Here's a link to the Gimp plugin registry.

[http://registry.gimp.org/](http://registry.gimp.org/)

Lotsa stuff here.

John

---

