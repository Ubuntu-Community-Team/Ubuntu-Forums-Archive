---
title: "Cant play DVD with media player"
date: 2007-11-12
forum: Ubuntu Customization Guide
---

### Post by ejonestexas on 2007-11-12
Im finding that I cant play a movie DVD.  The movie player opens and the image and sound is jumpy.  I feel this is because the DVD is copy protected.  I can play a public domain DVD or a DVD I recorded from TV just fine.

The player sometimes says I dont the the plugins.  Do you have a way to do this?  Or another DVD player which is better?

---

### Post by por100pre1 on 2007-11-13
First, add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and then copy, paste and ENTER this command in Terminal (**Applications> Accesories> Terminal**):

```
sudo apt-get install libdvdcss2
```

If this is not enough check [this]("https://help.ubuntu.com/community/RestrictedFormats#head-ade7b6cc5a280ee943fd7884cf7dc49ebe7e22ca").

---

### Post by ubuntu-freak on 2008-03-18
Just incase you are missing anything necessary, follow at least Part 1 and 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=661833). 
 
Nathan

---

