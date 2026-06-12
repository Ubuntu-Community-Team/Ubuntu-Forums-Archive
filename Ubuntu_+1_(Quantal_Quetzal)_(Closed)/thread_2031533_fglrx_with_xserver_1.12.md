---
title: "fglrx with xserver 1.12"
date: 2012-07-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by jfernyhough on 2012-07-22
I've been keeping an eye on this bug report for a while: [http://http://ati.cchtml.com/show_bug.cgi?id=522](http://http://ati.cchtml.com/show_bug.cgi?id=522) 

It details the reasons why on 64-bit systems (possibly only Debian-based, looking at the Arch forums) xserver 1.12 crashes when loading fglrx.

There is a workaround, and it's nasty. There's been nothing added for a while so I thought I'd give it a go myself (and it works). :)

Huge props to Pawe&#322; Chmielowski for the patch and Paul Menzel for step-by-step instructions.

**In summary**:
0) Ensure you have a working build environment.
1) Download source for libpciaccess0
2) Download and adapt patch
3) Apply patch and build deb
4) Install and troubleshoot
5) Reboot

**The process**:
0) Make sure you have a working build environment. Normally all you should need is:
```
$ sudo apt-get install build-essential
```but there may be other things missing. If you can't fix that, don't do any more.

1) These instructions credit to Paul Menzel ([http://ati.cchtml.com/show_bug.cgi?id=522#c12](http://ati.cchtml.com/show_bug.cgi?id=522#c12))
```

$ cd ~/src
$ sudo apt-get build-dep libpciaccess0
$ debcheckout libpciaccess0
$ cd libpciaccess0
```2) Download Pawe&#322; Chmielowski's patch from here: [http://pastebin.com/swpDj4FD](http://pastebin.com/swpDj4FD) (tip: use the raw paste data)
```

COPY
$ nano amd.patch
PASTE
```You need to edit the patch to match your system (thanks again, Paul). First you need to find which ID your AMD card has:

```

$ lspci
...
02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series]
...

```Note the ID code: 02:00. This is for the card, not the HDMI audio. Watch out.

```
$ nano amd.patch
```Edit the **two** instances of the line pci_device_find_by_slot(0, 1, 0, 0) so it matches your ID. For mine it changes to pci_device_find_by_slot(0, 2, 0, 0). If your ID is 00:10 then it should be pci_device_find_by_slot(0, 0, 1, 0)

**Change both instances. There are two lines you need to edit.** If you don't it won't work.

3) Apply the patch and add some details to the .deb. And why not?
```

$ patch -p1 < amd.patch
$ dch
$ git commit -a
$ dpkg-buildpackage -us -uc -B
```4) Install the deb
```
$ cd ..
$ sudo dpkg -i libpciaccess0_0.13.1-2ubuntu1_amd64.deb

```This is the package it built for me. If you copy the line and it doesn't work, good.

You may find it complains that libpciaccess0:i386 needs to be the same version. This is a multiarch thing. Rather than download and increment the deb number (which I should have done) I forced the installation of the amd64 version.

I'm leaving that up to you. If you don't know how, don't do it.

Finally, a
```
$ sudo apt-get install -f
``` removed libpciaccess0:i386 so I presumed it wasn't needed. YMMV. I upgraded xorg etc., rebooted, and now have a working X.

Good luck if you try it yourself. :D

---

### Post by jfernyhough on 2012-08-16
This should be fixed with Catalyst 12.8 (fglrx 8.982).

Yay!

[http://www2.ati.com/drivers/linux/amd-driver-installer-12.8-x86.x86_64.zip](http://www2.ati.com/drivers/linux/amd-driver-installer-12.8-x86.x86_64.zip)

---

### Post by tokertok on 2012-08-25
"You may find it complains that libpciaccess0:i386 needs to be the same version. This is a multiarch thing. Rather than download and increment the deb number (which I should have done) I forced the installation of the amd64 version."

I am still having this problem with catalyst 12.8. I tried the libpciaccess0 solution and had this complaint but just removing libpciaccess0:i386 did not work for me. I am on 12.04. you suggest downloading and incrementing the deb number, but it turns out i do not know how to do it. I also apparently cannot build so easily the libpciaccess0:i386 package. Can you elaborate on these right steps to properly do it if you have time?

---

