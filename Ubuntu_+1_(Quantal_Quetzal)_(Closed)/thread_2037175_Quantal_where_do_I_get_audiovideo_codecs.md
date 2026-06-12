---
title: "Quantal where do I get audio/video codecs"
date: 2012-08-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Cavsfan on 2012-08-03
Everything is going fairly smooth. Just thought I would try out some music with Rhythmbox and mp3s and wmas do not play.
Where can I get the codecs for Quantal for these?

BTW the link to install Java 7.5 in my sig worked for me. 

Thanks :)

---

### Post by mc4man on 2012-08-03
```
sudo apt-get install gstreamer0.10-ffmpeg \
gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```
should cover your decoding needs
(the ffmpeg plugin handles most gstreamer decoding that's not default suppied

---

### Post by QIII on 2012-08-04
> **Cavsfan said:**
> Everything is going fairly smooth. Just thought I would try out some music with Rhythmbox and mp3s and wmas do not play.
Where can I get the codecs for Quantal for these?

BTW the link to install Java 7.5 in my sig worked for me. 

Thanks :)

The link entitled "Using webupd8.org's strikingly easy method" in the Java 7 section of the Community Wiki Java link in my signature installs Java without the need to reinstall if a new version comes out
;)

---

### Post by Cavsfan on 2012-08-04
> **mc4man said:**
> ```
sudo apt-get install gstreamer0.10-ffmpeg \
gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly
```should cover your decoding needs
(the ffmpeg plugin handles most gstreamer decoding that's not default suppied

Thank you mc4man! Playing some Alice in Chains - Jar of Flies and it sounds good! :) I B Jammin!

> **QIII said:**
> The link entitled "Using webupd8.org's strikingly easy method" in the Java 7 section of the Community Wiki Java link in my signature installs Java without the need to reinstall if a new version comes out
;)

Thanks QIII! I'm pretty used to doing the java thing the hard way but, I bookmarked your site.
I should adopt your method as I could free up a lot of signature room. 

Funny thing: I have this transparent conky on the right side of my 28" monitor telling me the GPU, CPU temps and such. 
With Quantal,  I boot up and after a few minutes open Firefox and the conky gets this sort of white background to it.
I have cairo dock, compiz and the whole cube thing going on and resetting the window manager does not even fix it.
It just stays white behind it. But, if I open the home folder and start to show hidden files it fixes itself back to transparent.
It is like it knows I am going to edit the file and usually by making a small change and saving it fixed it at first.
Now, all I have to do is appear that I am going to edit it and it reverts back to transparent for the entire session!
There is some irony in there somewhere. ;)

---

### Post by Cavsfan on 2012-08-04
I should have made the title to this thread a lot more broad.

It appears I have both 64 bit and 32 bit sources. Check this short part of the output of sudo apt-get update:

```
Get:23 http://us.archive.ubuntu.com quantal-backports/main amd64 Packages [14 B]
Get:24 http://us.archive.ubuntu.com quantal-backports/restricted amd64 Packages [14 B]
Get:25 http://us.archive.ubuntu.com quantal-backports/universe amd64 Packages [14 B]
Get:26 http://us.archive.ubuntu.com quantal-backports/multiverse amd64 Packages [14 B]
Get:27 http://us.archive.ubuntu.com quantal-backports/main i386 Packages [14 B]
Get:28 http://us.archive.ubuntu.com quantal-backports/restricted i386 Packages [14 B]
Get:29 http://us.archive.ubuntu.com quantal-backports/universe i386 Packages [14 B]
Get:30 http://us.archive.ubuntu.com quantal-backports/multiverse i386 Packages [14 B]

```Am I right and should I try to fix it?
It is the same all through the output. Looking like I have both 32 and 64 bit sources.

Thanks! :)

---

### Post by Cavsfan on 2012-08-04
I just looked at my sources - **cat /etc/apt/sources.list** and there is no mention of either 32 or 64 bit. 
My /etc/apt/sources.list.d folder has one file in it - medibuntu.list but, it is blank.

---

