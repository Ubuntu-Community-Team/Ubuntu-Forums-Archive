---
title: "Best app for bulk resizing of images for uploading?"
date: 2009-05-25
forum: The Cafe
---

### Post by blue carrot on 2009-05-25
Hi guys,
Just a quick question...I know how to resize images one by one in GIMP etc. but is there a good app that makes it easy to resize a whole selection of images from within a folder for bulk resizing? 

Any tips much appreciated!
Cheers

---

### Post by Paqman on 2009-05-25
Yep, just get the nautilus-image-converter plugin. You can select as many pics as you like in Nautilus and resize them all in one go.

---

### Post by monsterstack on 2009-05-25
There's a terminal app that does all that called convert. You could do this:

```
for x in *.jpg; do convert -resize 50% "$x" size/thumb-"$x"; done
```

which would take all of the jpegs in the current folder, reduce them to 50% of the original size, and put them into the subfolder "size/". The originals will not be changed.

---

### Post by artir on 2009-05-25
Phatch

---

### Post by blue carrot on 2009-05-25
Hi paqman, I downloaded the nautilus-image-converter plugin, but to be honest I am a complete noob and im not actually too sure where to find nautilus itself? it doesnt appear in my 'applications' drop down menu anywhere. sorry for the noobness!

---

### Post by mxboy15u on 2009-05-25
There may be an easier way but I just use the export feature of Google Picasa, it allows for batch quality changes and resize.

---

### Post by Paqman on 2009-05-25
> **blue carrot said:**
> Hi paqman, I downloaded the nautilus-image-converter plugin, but to be honest I am a complete noob and im not actually too sure where to find nautilus itself? it doesnt appear in my 'applications' drop down menu anywhere. sorry for the noobness!

Nautilus is the default Gnome file browser. Open any folder and "viola", you're using Nautilus. You should now be able to converter images from a right-click.

Sorry, should have mentioned that one.

---

### Post by 0per4t0r on 2009-05-25
I use gimp for resizing. Works good enough for me. Anyway, if you're just uploading images, tinypic can resize them for you when you upload them.

---

### Post by n2dabloo on 2009-05-25
> **Paqman said:**
> Nautilus is the default Gnome file browser. Open any folder and "viola", you're using Nautilus. You should now be able to converter images from a right-click.

Sorry, should have mentioned that one.

I downloaded the image converter from Synaptics, opened a photo, right clicked and, there is no option for resizing.  I looked in Applications/Grahpics as well, no image converter.  Do I have to start this in Terminal for it to work?

---

### Post by binbash on 2009-05-25
Phatch

---

### Post by ftabor on 2009-05-25
> **Paqman said:**
> Yep, just get the nautilus-image-converter plugin. You can select as many pics as you like in Nautilus and resize them all in one go.

I installed the plugin, but I don't seem to be able to find the dialog to resize under right-click or any of the menus.  What am I doing wrong?

---

### Post by lovinglinux on 2009-05-25
+1 for Phatch

---

### Post by hessiess on 2009-05-25
Image magic.

---

### Post by Paqman on 2009-05-26
> **n2dabloo said:**
> I downloaded the image converter from Synaptics, opened a photo, right clicked and, there is no option for resizing.  I looked in Applications/Grahpics as well, no image converter.  Do I have to start this in Terminal for it to work?

> **ftabor said:**
> I installed the plugin, but I don't seem to be able to find the dialog to resize under right-click or any of the menus.  What am I doing wrong?

Not sure. Try logging out and back in. You might just need to restart Nautilus.

hessiess: nautilus-image-converter actually uses imagemagick.

---

### Post by ftabor on 2009-05-26
Logging out and logging back in did it.  Restarting Nautilus didn't work.

---

### Post by rax_m on 2009-05-26
Another +1 for Phatch if you want to use a gui. 
ImageMagik works well too if you don't mind the cli.

---

