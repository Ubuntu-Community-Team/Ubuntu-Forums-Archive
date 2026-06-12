---
title: "Start Up Disk Creator in 13.04 is Crashing!"
date: 2013-02-11
forum: Ubuntu Development Version
---

### Post by kevpan815 on 2013-02-11
It won't let me File a Bug Report either saying that I have Obsolete Packages Installed.

---

### Post by balloons on 2013-02-11
You should update your packages :-)

however, is is one of these?

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1120756](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1120756)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1121980](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1121980)

What do you mean by not working?

---

### Post by kevpan815 on 2013-02-11
> **guitara said:**
> You should update your packages :-)

however, is is one of these?

[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1120756](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1120756)
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1121980](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1121980)

What do you mean by not working?

It crashes at the end either while trying to create the EFI Bootloader or just after that, Only setting that I changed was to Discard On Shut Down, this is NOT a Mac Computer so I am surprised that it thinks that I have an EFI Boot Loader?

---

### Post by BhimaPandava on 2013-04-14
Has anyone else experienced this?  I've been running Ubuntu 13.04 in a Parallels VM on my Mac, and this app is terribly unreliable.  Using a variety of 13.04 server daily images, sometimes it crashes (silently), other times it appears like it finishes but doesn't yield a usable USB boot drive.  The VM is completely updated before I start and I use the current daily when I attempt to make the usb boot disk.

---

### Post by Gyokuro on 2013-04-14
> **BhimaPandava said:**
> Has anyone else experienced this?  I've been running Ubuntu 13.04 in a Parallels VM on my Mac, and this app is terribly unreliable.  Using a variety of 13.04 server daily images, sometimes it crashes (silently), other times it appears like it finishes but doesn't yield a usable USB boot drive.  The VM is completely updated before I start and I use the current daily when I attempt to make the usb boot disk.

I can confirm that's an unreliable application and not only on RR - I had the some problems on 12.04 LTS (up to date)  too and therefore I was dd'ing daily ISOs (since yesterday it is working again). I will look what's the problem but due to lack of time I was unable to digg deeper - it seems there is a problem in generating working boot support/code.

---

### Post by fooman on 2013-04-14
i have had issues with the start-up disc creator for at least the last couple of releases.  i have switched to using "unetbootin" and have had no problems whatsoever. 

"unetbootin" is available in the repos.

---

### Post by jasidog on 2013-04-25
Thank you for the unetbootin recommendation. Much apreciated. :)

---

