---
title: "[SOLVED] ffmpeg-php"
date: 2008-08-07
forum: Server Platforms
---

### Post by CrusaderAD on 2008-08-07
I installed a package with the following method:

[http://packages.ubuntu.com/hardy/source/ffmpeg-php](http://packages.ubuntu.com/hardy/source/ffmpeg-php)

Is this the correct way to install ffmpeg-php? I also install ffmpeg with:

sudo apt-get install ffmpeg

Is that all I need to do? I tried these directions:

[http://ffmpeg-php.sourceforge.net/](http://ffmpeg-php.sourceforge.net/)

but was unsuccessful. I get this error:

checking for ffmpeg libavcodec.so... configure: error: ffmpeg share libraries not found. Make sure you've built ffmpeg as shared libs using the --enable-shared option

---

### Post by CrusaderAD on 2008-08-07
It looks like just installing these two:

sudo apt-get install php-ffmpeg

sudo apt-get install ffmpeg

did the trick.

---

### Post by StickyStyle on 2008-08-07
Looks like that was a just now fixed bug [https://bugs.launchpad.net/ubuntu/+source/ffmpeg-php/+bug/245566](https://bugs.launchpad.net/ubuntu/+source/ffmpeg-php/+bug/245566)

---

