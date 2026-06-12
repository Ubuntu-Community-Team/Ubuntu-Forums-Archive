---
title: "A new version of Ubuntu MATE Welcome"
date: 2015-07-28
forum: Ubuntu Development Version
---

### Post by QDR06VV9 on 2015-07-28
Whimpy([Martin Wimpress]("https://plus.google.com/103917631499285627130"))has been busy.
I am very impressed with his works.
[https://plus.google.com/+MartinWimpress/posts/PgoQi9G8Vk8](https://plus.google.com/+MartinWimpress/posts/PgoQi9G8Vk8)
> A new version of Ubuntu MATE Welcome is ready for testing, including for 14.04

I've published a new version of Ubuntu MATE Welcome in the PPAs for 14.04, 15.04 and 15.10. Please come and test, particularly the Software Install feature :-) Ubuntu MATE Welcome won't pop up by default when installed outside of Ubiquity, so you'll find it in Applications -> System -> Ubuntu MATE Welcome.

This version adds a few more applications to the Software section and now reflects the installation status immediately after performing an install or remove operation. I've also added setup for complex input methods for Chinese, Japanese and Korean. 

Ubuntu MATE 15.10

    sudo apt-add-repository ppa:ubuntu-mate-dev/wily-mate
    sudo apt-get update
    sudo apt-get install ubuntu-mate-welcome

Ubuntu MATE 15.04

    sudo apt-add-repository ppa:ubuntu-mate-dev/vivid-mate
    sudo apt-get update
    sudo apt-get install ubuntu-mate-welcome

Ubuntu MATE 14.04

    sudo apt-add-repository ppa:ubuntu-mate-dev/trusty-mate
    sudo apt-get update
    sudo apt-get install ubuntu-mate-welcome&#65279; 
Probably more suited for new users. But worth noting.
Looking forward to his version Mate 1.10
Kind Regards

---

### Post by euphoria42 on 2015-07-29
Very neat! I'll have to see if we can get something similar into Ubuntu GNOME.

---

### Post by ventrical on 2015-09-05
Just  Dl/ed the ubuntu-mate daily-iso , hard installed it to hdd and when it boots it comes up with a rolling welcome window with all sorts of link buttons.  It is good to see  some of the ubuntu distros being proactive with instructional development. I presume that Canonical finally figured out that new users are trying ubuntu each day in much larger numbers.

Regards..

---

### Post by Bucky Ball on 2015-09-05
I like it but suspect it is down to the Mate team rather than Canonical, at least in Mate. :-k

---

### Post by ventrical on 2015-09-05
After reading some of the content I can see that mate is fiercely trying to distinguish itself from other distros. Interesting..  I hope we can all reach  somehow.

Regards..

---

### Post by QDR06VV9 on 2015-09-05
> **ventrical said:**
> Just  Dl/ed the ubuntu-mate daily-iso , hard installed it to hdd and when it boots it comes up with a rolling welcome window with all sorts of link buttons.  It is good to see  some of the ubuntu distros being proactive with instructional development. I presume that Canonical finally figured out that new users are trying ubuntu each day in much larger numbers.

Regards..
I see you think along the same Thoughts.:D
[http://ubuntuforums.org/showthread.php?t=2288608](http://ubuntuforums.org/showthread.php?t=2288608)

---

### Post by flocculant on 2015-09-05
> I presume that Canonical finally figured out that new users are trying ubuntu each day in much larger numbers. Would be nothing to do with Canonical unless it appears on the Ubuntu image and install.

If it *was* Canonical it would show on their distro - for sure we're not been made aware of anything available in normal repo's of this at Xubuntu. 

Not that we'd not take it into consideration of course.

This is an Ubuntu Mate effort only currently.

---

### Post by Frogs Hair on 2015-09-05
Threads Merged

---

### Post by ventrical on 2015-09-06
> **Frogs Hair said:**
> Threads Merged

??

 And I created a thread about mate background themes. Why did that get removed?.

Regards..

---

### Post by ventrical on 2015-09-06
> **runrickus said:**
> I see you think along the same Thoughts.:D
[http://ubuntuforums.org/showthread.php?t=2288608](http://ubuntuforums.org/showthread.php?t=2288608)

It is a beginning to help new users get a handle on the workings of the ubuntus distros. They have had it with ubuntu-desktop for a while and it's been a good starting point for noobs and unity-desktop.

---

### Post by tgalati4 on 2015-09-07
Can someone briefly summarize the differences between MATE 1.8.1 and 1.10?  Is it worth upgrading?

---

### Post by QDR06VV9 on 2015-09-07
Just a version upgrade.
In the Caja file browser, you can now enable/disable extensions at run-time.
Thanks to a new audio library, libmatemixer, MATE can now take full advantage of mixer functionality and it is able to automatically detect and support PulseAudio, ALSA and OSS.
Under the hood, static code analysis was performed on the MATE source code and many memory leaks were fixed. Atril now supports the ePub format.
Caja is a little snappier with folders containing a large amount of files.
Better memory allocation, Outside of those not a lot of difference.
I installed 1.10 on trusty about a month ago and all is well.
Regards

---

