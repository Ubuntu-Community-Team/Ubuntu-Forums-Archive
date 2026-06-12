---
title: "Live USB security &amp; root mode"
date: 2013-03-04
forum: Security
---

### Post by bipbipman on 2013-03-04
Hi 

I am using Linux on Live USB in a daily manner since I find this meets my flexibility needs. Given that I understand Live USB are in permanent root mode with no password, is doing so reasonably secure for e.g. online banking or protecting data on my PC? Is there anything I could do to restrict permissions & strengthen the security level while staying Live USB? Thanks in advance for you help!

bipbipman

---

### Post by sudodus on 2013-03-04
Welcome to the Ubuntu Forums :-)

I have installed Lubuntu as a regular installation, but to a USB 3 pendrive. The USB 3 hardware makes it as fast as can be, because the flash hardware is not limiting the speed (so it is running at full USB 2 speed in USB 2 ports). And I have encrypted home. This makes it much safer than a persistent live system.

When doing this installation, it is important to choose 'Something else' at the partitioning screen, and remember to install grub to the MBR of the pendrive (not to the internal drive, which is the default, and not to any partition).

*Edit*: Do *not* install any proprietary drivers, if you want portability.

---

### Post by bipbipman on 2013-03-04
Thanks for your help Sudodus! This looks better to me than what I currently run. I am going to try and get there, starting with my first dual-boot! ;-). Thanks for your advice.

---

### Post by C.S.Cameron on 2013-03-04
A persistent USB install is not secure even if you are setup as a user with password.
All changes are saved in the casper-rw file which can be mounted and all data can be extracted.

Better to use a Live USB, (without persistence), for banking as nothing is saved on the drive.

A Full install to USB is as secure as a desktop install, except a flash drive is much easier to loose than a desktop.

---

### Post by tubbygweilo on 2013-03-05
I have at times installed truecrypt upon a persistent USB install (10.04 lts) + 12.04 and placed data inside the truecrypt container and considered it safe unless the truecrypt pass phrase has been compromised or I no longer have physical access / control over the USB memory stick.

I think this method to be safe but am always open to advice and further thoughts on the subject.

---

### Post by bipbipman on 2013-03-05
Thanks C.S. Cameron for the detailed explanation, now this is much clearer in my mind. And thanks tubbygweilo for the tip about encryption. Further to Sudodus comments, I just made today a full install on USB and... so far so good! :) Beyond the security concern (main driver though), I am happy to have moved to full install! Thanks everyone.

---

### Post by sudodus on 2013-03-06
You are welcome :-)

---

