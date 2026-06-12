---
title: "Problems installing VirtualBox"
date: 2009-03-26
forum: Virtualisation
---

### Post by PicoDeRyo on 2009-03-26
I am a serious Noob when it comes to Linux and I am trying to get VirtualBox up and running, I installed the one from the repositories through add/remove applications, but I kept having problems with the mouse capture. So I tried installing it from Sun's website by using the package installer, but I get this error when I try to install.

dpkg: error processing /tmp/virtualbox-2.1_2.1.4-42893_Ubuntu_hardy_i386.deb (--install):
trying to overwrite '/lib/modules/2.6.24-23-generic/misc/vboxdrv.ko',which is also in package virtualbox-ose-modules-2.6.24-23-generic
dpkg-deb: subprocess paste killed by signal (Broken pipe)

I think something went wrong having the one installed and then installing the newer version. But I have since uninstalled the version from the repositories, and the newer version still doesn't get installed. Any help would be greatly appreciated.

I looked in the misc folder and there are no files in there at all to overwrite.

---

### Post by PicoDeRyo on 2009-03-26
Anyone have some advice for me? I am considering reinstalling ubuntu if I can't get this fixed. Any help would be greatly appreciated

---

### Post by KCG102282 on 2009-03-26
From what I heard the OSE edition is a pain to get installed I would try the rugular edition. I installed in with no issues :)

---

### Post by PicoDeRyo on 2009-03-26
That is the problem, I installed the OSE version first, and then when I tried installing a the 2.1 version from the Sun website I get the error I listed above

---

### Post by PicoDeRyo on 2009-03-26
I was able to get this installed from the Sun website by going into synaptic and completely removing the old ose version. But now that I have it installed I can't find the link to open the application. Any idea where to find it?

---

### Post by PicoDeRyo on 2009-03-26
I restarted and got it setup this is resolved

---

