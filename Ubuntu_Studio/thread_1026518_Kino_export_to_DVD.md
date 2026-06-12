---
title: "Kino export to DVD"
date: 2008-12-31
forum: Ubuntu Studio
---

### Post by matth1j on 2008-12-31
Hi- I've managed to capture some DAT home videos off my DV camcorder using Kino, and now want to transfer them to DVD. The Kino help says I need mjpeg-tools to create the appropriate files, but that seems to be non-trivial to install to a relatively new Ubuntu user like myself. That is, I downloaded the mjpeg-tools .rpm file, then found out the rpm utility wasn't installed so installed it, then found out I can't use rpm on Ubuntu :confused:

Should I persevere with mjpeg-tools, or would it be better to use some other application to convert the raw DV files into something I can burn to DVD?

Cheers
John

---

### Post by cotcot on 2009-01-01
Mjpegtools is easy to install with synaptic (see --> System --> Administration --> Synaptic package manager).

(You cannot install rpm directly. You need to convert is to .deb with a package called Alien. But again there is no need for it)

Have a look to [COLOR="Blue"]Devede[/COLOR].

---

### Post by artsci2 on 2009-04-07
Ah! the exact thread needed on the first term of the first search.
Thanks guys.

How does one tell if mjpeg tools are compatible with 64bit Ubuntu? There is a -64bit version of the mjpegtools out there. 

Does synaptic package manager automatically screen programs according to the operating system?

Re-installing 32 bit Ubuntu is ok but this is a purpose-built video editing machine and it already has 4Gb of RAM. It will be upgraded to 8Gb as soon as It can import/edit/save H.264 and also export DVD compatible (mpeg-2 ?) files.

---

### Post by artsci2 on 2009-04-07
OK I just installed the mjpegtools on My Ubuntu 9.04 64bit system using Synaptic Package Manager. It seems to export to MJPEg just fine. I'll edit this post after trying to burn and play a DVD.

Kino seems to only use one processor.

System:
Athlon 7750 BE running 3.0Ghz (x15 multiplier in BIOS)
Gigabyte GA-MA78GM-US2H, 4Gig memory, sata 250Gig system and sata 250G data.
Saphire HD4550 video card. 430watt 

Camera Aiptek HD, 8Gb SD card

---

### Post by cariboo on 2009-04-08
I am doing the same thing, Kino just finish creating the mpeg file, and now I'm using devede to add menus and convert to an iso, which can be burned to a dvd.

Devede is in the repositories and you can use Synapitc Package Manager to install it. BTW if you are running 64-bit all the packages in the repositories are 64-bit. There are some 32-bit libs for compatability.

Jim

---

