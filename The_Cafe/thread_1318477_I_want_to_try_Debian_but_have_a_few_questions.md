---
title: "I want to try Debian but have a few questions"
date: 2009-11-07
forum: The Cafe
---

### Post by Ewingo401 on 2009-11-07
Hey guys.  I've been wanting to give Debian a try lately.  Mainly out of curiosity.  But I have a few questions that I was hoping some of you could help me with.  First of all I would be installing the latest stable version (Lenny I think).  I'm wondering if it will be as easy to get my wireless up and running as it is in Ubuntu.  In Ubuntu all I have to do is download and install the b43fwcutter and extract the firmware when it asks me.  I was also wondering how easy it is to get mp3 playback support as well as flash capabilities.  I know Debian is much more focused on the free aspects of things, thats why I was wondering how easy it would be to get these things to work.  Any input is appreciated!

---

### Post by coldReactive on 2009-11-07
debian isn't as easy as ubuntu, that's all you really need to know.

But, if you want to try debian:

[http://lmgtfy.com/?q=debian+codecs](http://lmgtfy.com/?q=debian+codecs)

---

### Post by SunnyRabbiera on 2009-11-07
It might be a little harder getting your wireless to work, but as for Mp3 and media playback there is a place like medibuntu for debian.

---

### Post by kavon89 on 2009-11-07
From what I remember when installing the PPC version of Lenny on my iBook, there are no wireless utilities like iwconfig included. Nor is there a GUI if you're not comfortable installing wireless tools, a window manager, xorg, and video drivers from command line.

Maybe it was because I just downloaded CD 1, and those other packages were on CD 2. Debian is great once you've got it going. :D

---

### Post by SunnyRabbiera on 2009-11-07
> **kavon89 said:**
> From what I remember when installing the PPC version of Lenny on my iBook, there are no wireless utilities like iwconfig included. Nor is there a GUI if you're not comfortable installing wireless tools, a window manager, xorg, and video drivers from command line.

Maybe it was because I just downloaded CD 1, and those other packages were on CD 2. Debian is great once you've got it going. :D

Well the PPC version might not bee so good, but for me when I tried lenny out it was fairly easy.
I use x86

---

### Post by cariboo on 2009-11-07
Debian now has a graphical installer, that makes installing it just about as easy as installing Ubuntu.

---

### Post by perce on 2009-11-07
Disclaimer: I used to run Debian before switching to Ubuntu, and my information about it may be outdated. 

I've installed Debian Lenny on a desktop a couple of years ago when it was still testing and, and I found it disappointingly easy to install. However if you your wireless card is a problematic one, then Debian stable might not be the best choice, since it provides older software. I suggest you to try Debian testing, which in my experience has always been already very stable (sometimes more stable than Ubuntu in fact).

For multimedia there was (once upon a time) a specific repository based in France in order to avoid all annoyance inhabitants of the Land of Free enjoy thank to DMCA and software patents. Something like that should still exist.

---

### Post by snowpine on 2009-11-07
Hi Ewing, I suggest Googling the following phrases: "debian wiki b43fwcutter", "debian wiki codecs", and "debian wiki flashplugin".

I think you will find the answers are well-documented and involve adding some combination of the "contrib", "non-free", and "multimedia" repos to your software sources.

Ubuntu IS Debian; the main difference you will notice is that Debian is stricter about segregating free vs. non-free software, so that users who choose to use only free software can do so easily.

While it is not part of (or endorsed by) the Debian project, I find the smxi script (from smxi.org) is a wonderful tool for tweaking a new Debian install. Good luck!

---

### Post by kerry_s on 2009-11-07
will you be connected to do the install?
if so, i recommend the net installer:
[http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-businesscard.iso)

i recommend you select the expert mode, so you can select not to use root & have a sudo system instead, you can also choose to use non-free packages, it will also give you the option for targeted kernel, with only the drivers for your system, you will also be able to pick which grub you want as long as you don't use ext4, i don't recommend ext4.

b43-fwcutter is only a apt-get away, it's in the repo.

as with ubuntu you add the media repos to get the restricted stuff.
```
deb http://www.debian-multimedia.org lenny main
```

i'm using debian lenny gnome, so i can help if you get stuck.

---

### Post by Ewingo401 on 2009-11-07
> **kerry_s said:**
> will you be connected to do the install?
if so, i recommend the net installer:
[http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-businesscard.iso)

i recommend you select the expert mode, so you can select not to use root & have a sudo system instead, you can also choose to use non-free packages, it will also give you the option for targeted kernel, with only the drivers for your system, you will also be able to pick which grub you want as long as you don't use ext4, i don't recommend ext4.

b43-fwcutter is only a apt-get away, it's in the repo.

as with ubuntu you add the media repos to get the restricted stuff.
```
deb http://www.debian-multimedia.org lenny main
```

i'm using debian lenny gnome, so i can help if you get stuck.


Thank you.  I think this covers everything that I need to know!

---

