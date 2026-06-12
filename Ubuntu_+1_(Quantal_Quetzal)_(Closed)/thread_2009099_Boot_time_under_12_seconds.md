---
title: "Boot time under 12 seconds"
date: 2012-06-23
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by kansasnoob on 2012-06-23
Lots of changes recently in Xorg but also the new 3.5.0-1 kernel and I'm blown away by how fast this Intel Atom test box boots :D

I'm used to about 25 to 30 seconds and this is awesome.

---

### Post by cecilpierce on 2012-06-24
Still no glory here, 45 sec to the mouse pointer, 55 sec to login sound, 85 sec to full desktop screen, bummer !

p.s.
wonder why it says 12.04?

---

### Post by sudodus on 2012-06-24
> **kansasnoob said:**
> Lots of changes recently in Xorg but also the new 3.5.0-1 kernel and I'm blown away by how fast this Intel Atom test box boots :D

I'm used to about 25 to 30 seconds and this is awesome.
Is this quantal as it is from the iso file, or did you make those changes in Xorg? I guess you didn't change the kernel ;-)

---

### Post by firekage on 2012-06-24
> **cecilpierce said:**
> Still no glory here, 45 sec to the mouse pointer, 55 sec to login sound, 85 sec to full desktop screen, bummer !

p.s.
wonder why it says 12.04?

How did you measured this boot time?

---

### Post by kansasnoob on 2012-06-24
> **firekage said:**
> How did you measured this boot time?

With my digital wrist watch. Since this is a multi-boot I just counted from the moment I selected the entry in grub and hit enter to the moment the DE finished loading.

---

### Post by kansasnoob on 2012-06-24
> **cecilpierce said:**
> Still no glory here, 45 sec to the mouse pointer, 55 sec to login sound, 85 sec to full desktop screen, bummer !

p.s.
**wonder why it says 12.04?**

It's alpha and not all the artwork is done, try running:

```
lsb_release -a
```

eg;

> lance@lance-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu quantal (development branch)
Release:	12.10
Codename:	quantal


---

### Post by kansasnoob on 2012-06-24
> **sudodus said:**
> Is this quantal as it is from the iso file, or did you make those changes in Xorg? I guess you didn't change the kernel ;-)

I had held off updating for several days because of the "removal" list:

> Removed the following packages:
libebook-1.2-12
libedata-book-1.2-11
libupnp3
xserver-xorg-video-all
xserver-xorg-video-ati
xserver-xorg-video-qxl
xserver-xorg-video-radeon
xz-lzma

Then yesterday I read some of the changelogs and decided to take the plunge. The relevant Xorg packages updated were:

> xinit (1.3.1-1) to 1.3.2-1
xserver-common (2:1.11.4-0ubuntu11) to 2:1.12.1.902-1ubuntu1
xserver-xorg-core (2:1.11.4-0ubuntu11) to 2:1.12.1.902-1ubuntu1
xserver-xorg-video-cirrus (1:1.4.0-1) to 1:1.4.0-1build1
xserver-xorg-video-fbdev (1:0.4.2-4ubuntu2) to 1:0.4.2-4ubuntu3
xserver-xorg-video-geode (2.11.13-3) to 2.11.13-3build1
xserver-xorg-video-intel (2:2.19.0-1ubuntu1) to 2:2.19.0-1ubuntu2
xserver-xorg-video-mach64 (6.9.1-2) to 6.9.1-2build1
xserver-xorg-video-mga (1:1.5.0-1) to 1:1.5.0-1build1
xserver-xorg-video-neomagic (1:1.2.6-1) to 1:1.2.6-1build1
xserver-xorg-video-nouveau (1:0.0.16+git20120322+ab7291d-1) to 1:1.0.1-1build1
xserver-xorg-video-openchrome (1:0.2.906-1) to 1:0.2.906-1build1
xserver-xorg-video-r128 (6.8.2-1) to 6.8.2-1build1
xserver-xorg-video-s3 (1:0.6.3-4build2) to 1:0.6.3-4build3
xserver-xorg-video-savage (1:2.3.3-1ubuntu1) to 1:2.3.4-1ubuntu1
xserver-xorg-video-siliconmotion (1:1.7.6-1) to 1:1.7.6-1build1
xserver-xorg-video-sis (1:0.10.4-1) to 1:0.10.4-1build1
xserver-xorg-video-sisusb (1:0.9.4-3) to 1:0.9.4-3build1
xserver-xorg-video-tdfx (1:1.4.4-1) to 1:1.4.4-1build1
xserver-xorg-video-trident (1:1.3.5-1) to 1:1.3.5-1build1
xserver-xorg-video-vesa (1:2.3.1-1) to 1:2.3.1-1build1
xserver-xorg-video-vmware (1:12.0.1-1ubuntu2) to 1:12.0.1-1ubuntu3
xz-utils (5.1.1alpha+20110809-3) to 5.1.1alpha+20120614-1

Could be bad news for ati/radeon :confused:

---

### Post by QIII on 2012-06-24
Just installed today's build and I'm pretty sure I got the Radeon package...

fglrx still doesn't work out of the box with the 3.5 kernel.

---

### Post by jerrylamos on 2012-06-24
Boot up to me is all the way to wireless WPA connect. That part can easily take longer than 12 seconds, sometimes recently 5 minutes trying to get Quantal to "enable wireless" and "connect automatically".  Sometimes it will connect sometimes it's a pitched battle to even get the menu bars to respond to a mouse or keyboard selection.

Jerry

---

### Post by gacb on 2012-08-30
I have two partitions both running Quantal. One boots much faster than the other, and I suspect it may be related to VirtualBox.

I have BUM installed on both, and that's the only difference I can see.

---

### Post by sammiev on 2012-08-30
I boot in about 30 seconds from the time I select my boot option and shut down in 3 seconds. With 12.04 my shut down time is higher than 1 min most of the times. My next fresh install of QQ will be when Beta1 comes out next week. :)

---

