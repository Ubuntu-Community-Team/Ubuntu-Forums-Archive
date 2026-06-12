---
title: "Darktable on Ubuntu Studio"
date: 2012-05-11
forum: Ubuntu Studio
---

### Post by LinuxDanish on 2012-05-11
HI I recently installed Ubuntu studio (lucid) on an older compaq presario sr1053wm. I then installed Darktable. the install said it worked fine yet it wouldn't open. when i gave the command to run in the terminal it gives me this response:  
    pippin@pippin:~$ darktable
[defaults] found a 32-bit system with 961772 kb ram and 1 cores
[defaults] setting very conservative defaults
Illegal instruction

It starts to open but then just stops. any help would be greatly appreciated! 
   -Thanks in advance :)

---

### Post by sgx on 2012-05-12
Hi, did you check synaptic package manager for the dependencies?
Or newer versions of them? (Click the 'reload' button in synaptic)

libsqlite3, libjpeg, libpng, libraw (supplied), rawspeed (supplied), gtk+-2, cairo, lcms2, exiv2, tiff, curl, gphoto2, dbus-glib, gnome-keyring, fop, openexr

from the webpage,

"You might need to get lcms2 from Pascal's ppa (see Ubuntu below)
Optional: gcc >= 4.4 (OpenMP, earlier versions could not handle OpenMP statements in non-main threads)"

go here for the lcms2  

[https://launchpad.net/~pmjdebruijn/+archive/darktable-release/+packages](https://launchpad.net/~pmjdebruijn/+archive/darktable-release/+packages)

Cheers

---

### Post by LinuxDanish on 2012-05-12
Hmm.. I checked all the dependencies and it appears that I have them all, but it still doesn't start :(

---

### Post by sgx on 2012-05-13
If started from a terminal, is there any message in the window?

Try running it as sudo from a terminal, in case of a weird
permission somewhere.

Do other graphics and photo apps work okay?

gimp, xara, aaphoto, rawstudio, inkscape etc?

On my non-ubuntu setup, it won't install do to

libcurl-gnutls.so.4 is needed by darktable-1.0.3-1.i386
libexiv2.so.6 is needed by darktable-1.0.3-1.i386
libtiff.so.4 is needed by darktable-1.0.3-1.i386

That first one might be worth googling, as it is
a nuisance in some cases, where libcurl is already
installed. I also had libtiff.so.3, so you might
double check versions in /usr/lib.

---

### Post by LinuxDanish on 2012-05-13
the message I get in the terminal is:
     [defaults] found a 32-bit system with 961772 kb ram and 1 cores
     [defaults] setting very conservative defaults
     Illegal instruction

the other graphics apps work fine as far as I can tell (gimp, inkscape, UFRaw, shotwell).

I do have libcurl3 installed, however I can't find anything other than the dev documentation for libcurl4 do I need a special repo for it?

---

### Post by sgx on 2012-05-14
[http://askubuntu.com/questions/31724/broken-package-error-while-installing-development-headers-for-libcurl](http://askubuntu.com/questions/31724/broken-package-error-while-installing-development-headers-for-libcurl)
this helped someone.



[http://packages.debian.org/sid/libcurl4-openssl-dev](http://packages.debian.org/sid/libcurl4-openssl-dev)

from reading here, it appears libcurl4 is part of this package.
So go to the list at the bottom, and choose your computers
architecture, 1386, amd64 etc which takes you to the list of
download mirrors. to install it,

sudo dpkg -i nameOF.deb

If it needs other parts, the download will fail, and tell you
the first/next one you need to get. If it is not available in synaptic, try getting it from the dependency list at the same link.
There could be several needed, or none. I know I've done such
installs needing 8 or 10, type in google
libcurl "dependency hell" for a hoot

Jot down each item you install, in case it leads to trouble,
and you have to uninstall later.
Cheers

---

### Post by LinuxDanish on 2012-05-16
I started following the dependencies. every dependency I have is roughly .5 or so of a version of from what is needed for libcurl. Finally when I got down to needing to update libc6 itsays I will break the libc6 already installed, but it won't let me remove libc6 unless I remove almost all my other programs like Ardour, agave, apt-utils, etc.  do I have a hope of getting darktable of working or should I just stop before I break something ? :p

---

### Post by jejeman on 2012-05-16
Don't mess around with libc.
Beter compile darktable yourself, than to touch libc.

---

### Post by sgx on 2012-05-16
> **LinuxDanish said:**
> should I just stop before I break something ? :p

At this point, I would install Bodhi linux on a usb stick,
it's based on ubuntu 12.04, but unbloated, do the experiments on that, so you can reinstall easily after any failed attempts.
Cheers

also, compiling is something you can safely learn in a safe
repeatedly expendable Bodhi setup, and the knowledge is
transferable.

---

### Post by LinuxDanish on 2012-05-16
Thanks Guys!
 I will be sure to check that Distro out and do that! I have been meaning to learn how to compile anyways so nows a good time :)

---

### Post by dinamic78 on 2012-05-18
> **LinuxDanish said:**
> HI I recently installed Ubuntu studio (lucid) on an older compaq presario sr1053wm. I then installed Darktable. the install said it worked fine yet it wouldn't open. when i gave the command to run in the terminal it gives me this response:  
    pippin@pippin:~$ darktable
[defaults] found a 32-bit system with 961772 kb ram and 1 cores
[defaults] setting very conservative defaults
Illegal instruction

It starts to open but then just stops. any help would be greatly appreciated! 
   -Thanks in advance :)

Hi, darktable is highly dependent on SSE2 instructions set, and "Illegal instruction" indicates this might be the problem, check the file /proc/cpuinfo and verify that your processor is SSE2 capable.

/Henrik

---

