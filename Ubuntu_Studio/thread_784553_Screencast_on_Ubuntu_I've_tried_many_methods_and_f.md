---
title: "Screencast on Ubuntu? I've tried many methods and failed."
date: 2008-05-06
forum: Ubuntu Studio
---

### Post by softtower on 2008-05-06
I have tried to make screencasts using Ubuntu Hardy (8.04) and nothing seem to work just right. Here is what I've been doing (and failing). How do you do it?  I've seen plenty of nice Ubuntu screencasts online with sound.

Here is what I've been trying:

**Option 1: xvidcap**

Installed with apt-get, it segfaulted on first run. I got it to work by 
specifying "--audio no" option, thus no sound. Besides, files produced by xvidcap play too fast: FPS problem?

**Option 2: ffmpeg**

ffmpeg that comes with Ubuntu is compiled without screen-grabbing module. And I don't want to compile my own - I try not to have a custom-compiled software on my system because it's hard to keep track (and uninstall) it later.

**Option 3: gtk-recordmydesktop**

This one actually got very close: I got the video and sound working, but the sound was skipping and getting out of sync with video. It appears to be a common problem based on a few google searches I've done. Morever, it records in only OGG which is, of course, useless outside of Linux world. (but I managed it convert it to MPEG4, losing some quality and boosting file size by 30% in proces of doing so)

**Option 4: pyvnc2swf**
Works only via VNC. Too sluggish for most practical purposes.

At this point I'm pretty frustrated. How do I make a screen cast on Ubuntu?

---

### Post by Gustavo Narea on 2008-05-22
*bump*

I'm glad to know I'm not alone.

Also, xvidcap *always* crashes on my computer, even when running it from the command line as "xvidcap --audio no --gui yes".

---

### Post by FakeOutdoorsman on 2008-05-22
> **softtower said:**
> 
**Option 2: ffmpeg**

ffmpeg that comes with Ubuntu is compiled without screen-grabbing module. And I don't want to compile my own - I try not to have a custom-compiled software on my system because it's hard to keep track (and uninstall) it later.

You might want to try ffmpeg.  Yesterday I just went through the effort of getting a compiled ffmpeg with x11grab enabled on Ubuntu: [ffmpeg recording + hardy not working (worked in feisty)]("http://ubuntuforums.org/showthread.php?t=801174")

As for keeping track of custom-compiled software, that's what checkinstall is for.  It will make a nice and clean deb package and add your custom install to Synaptic, etc.

Once you get it running you can use something like:
```
ffmpeg -f oss -i /dev/audio -f x11grab -s 800x600 -r 15 -i :0.0 outputvid.avi
```

[ffmpeg documentation: 2.2 X11 grabbing]("http://ffmpeg.mplayerhq.hu/ffmpeg-doc.html#SEC4")
[How to Create a Screencast in Ubuntu]("http://ubuntu.wordpress.com/2006/06/08/how-to-create-a-screencast-in-ubuntu/") (old, but has some useful commands)

---

### Post by EuclidsElements on 2008-08-13
Bump!  I have a big project I'd like to do and the free software that comes with Ubuntu is perfect for it, but I can't get recordmydesktop to work (or any other screen capture software for that matter).

Is there any other software out there?

---

### Post by suniyo on 2009-12-19
I am also searching for this kind of software for screencasting. Are there any better softwares for linux out there>?

---

