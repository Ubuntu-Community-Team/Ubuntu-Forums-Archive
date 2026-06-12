---
title: "Why do I get warnings about cryptsetup-initramfs?"
date: 2019-01-14
forum: Ubuntu Development Version
---

### Post by SeijiSensei on 2019-01-14
I've been testing out Kubuntu 19.04 for a couple of weeks now.  Lately when I run a package upgrade, I get this warning:

> update-initramfs: Generating /boot/initrd.img-4.18.0-11-generic
cryptsetup: WARNING: The initramfs image may not contain cryptsetup binaries 
    nor crypto modules. If that's on purpose, you may want to uninstall the 
    'cryptsetup-initramfs' package in order to disable the cryptsetup initramfs 


I never saw anything like that in 18.04 or earlier versions.  I have never had an encrypted filesystem and do not want one in the future.

I had uninstalled both those packages, but they were apparently reinstalled by "apt upgrade".  So I've now removed them again, then used "apt-mark hold" to block cryptsetup and cryptsetup-initramfs from being installed in the future.  But why are these warnings appearing now?

---

### Post by VMC on 2019-01-15
I get the warning also. It mentioned about remove the package if your sure its not needed. I removed the package. Not sure why/when it started.

---

### Post by SeijiSensei on 2019-01-15
I removed the packages, but they were restored at the next update.  That's why I had to mark them with "apt-mark hold".

---

### Post by #&amp;thj^% on 2019-01-15
It's been around since about kernel 4.17 
> This warning is intentional if you have devices that need to be unlocked
at initramfs stage (for instance devices required to unlock the root FS).

And you did not need that so you were ok in uninstalling.
First Bug Reported: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=901830](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=901830)

---

### Post by SeijiSensei on 2019-01-16
According to that bug report, this was "fixed" last June in Debian.

I suppose most ordinary users never update from the command prompt.  Does that mean they won't see this warning?  Otherwise it will confuse the hell out of a lot of people.

I'd be curious how many people have installations with encrypted filesystems.  Are they even a quarter of installations?  Can the installer determine if there are any encrypted filesystems in use and only install cryptsetup-initramfs in those situations?  I realize at some level all filesystems are just a bunch of binary bits, but perhaps looking for a plain-text directory structure or something similar could help.

---

### Post by #&amp;thj^% on 2019-01-17
> **SeijiSensei said:**
> According to that bug report, this was "fixed" last June in Debian.

.
And with a lot of older bugs "They're Back" :)
I think the packagers are having a rough time keeping up with the changes.
> **SeijiSensei said:**
> 
I suppose most ordinary users never update from the command prompt.  Does that mean they won't see this warning?  Otherwise it will confuse the hell out of a lot of people.

Great Thought, I'm just a terminal guy myself so I'm no good for this question.:(
Maybe someone else can add their experience with that question.
> **SeijiSensei said:**
> 
I'd be curious how many people have installations with encrypted filesystems.  Are they even a quarter of installations?  Can the installer determine if there are any encrypted filesystems in use and only install cryptsetup-initramfs in those situations?  I realize at some level all filesystems are just a bunch of binary bits, but perhaps looking for a plain-text directory structure or something similar could help.

As a test I used encrypted partitions but seen the same warning, so again my thoughts return to the packagers having a tough time keeping up with the changes.
Cutting Edge at it's finest. ;)

---

