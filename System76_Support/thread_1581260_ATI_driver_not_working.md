---
title: "ATI driver not working"
date: 2010-09-24
forum: System76 Support
---

### Post by flucoe on 2010-09-24
Hi.

Yesterday I used the Update Manager in my PanP7 and, no idea why, the package FGLRX did something weird and is not longer working. I went to "Harware Drivers" and the ATI driver is not activated (even though it was a couple of days ago). I tried to activate it and it doesn't work, and the message says it has something to do with not being able to install fglrx. Any ideas???

Thanks,

Fernando

---

### Post by thomasaaron on 2010-09-28
flucoe, I'm sorry you didn't get a response on the forums to this. Are you still having this problem?

(We've had a couple of customers we've been helping via email support with similar issues, and I'm wondering if you are one of them?)

---

### Post by flucoe on 2010-09-28
Yes! I was one of those. Yesterday Ian helped me to solve the problem. Thanks.

---

### Post by excalq on 2010-09-29
I've been having a hell of a time ever since upgrading to the "10-9-x86.x86_64" ATI drivers. They seem to be quite unstable, especially with an external monitor involved. I've now gotten X running again with glx related functionality broken, moving windows being laggy, etc. I'm going to attempt using the open source drivers or an older version of ATIs. Otherwise, I too will be taking advantage of System76's awesome support tomorrow.

Also, I noticed the ATI installer gave me these errors:
[Error] Kernel Module : Failed to build fglrx-8.771 with DKMS
[Error] Kernel Module : Removing fglrx-8.771 from DKMS

---

### Post by isantop on 2010-09-29
Typically, the drivers directly from ATI are fairly unstable with Ubuntu. I'd use the ones available from (System > Administration > Hardware Drivers/Additional Drivers).

---

### Post by excalq on 2010-09-30
OK, I was able to get it working (had to use recovery mode and console), by installing "fglrx" from the standard repos (after uninstalling the driver downloaded from ATI 
```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```
```
sudo aptitude install fglrx
```

I also did various things listed here: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD), but the Open Source drivers never did seem to work for me.

---

### Post by Haymakers9th on 2010-10-09
Sorry, I'm still having problems on my PANP7, installing the proprietary driver through jockey or synaptic results in either a loss of compiz with moving windows acting very laggy, freezing on login screen, or most recently/commonly, just a blank screen after the plymouth loading animation.

The error report I submitted through Ubuntu's system was marked as duplicate of [this bug]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518"), which tells me it's some kind of compiling error when dpkg installs it?

Also to note is any time I run fglrxinfo after installing it I get a segmentation fault, lending evidence to the "not properly compiling" thing.  It's happened on a fresh Ubuntu install more than once.

One thing that confuses me is that it was [marked as "fix released"]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/642518/+editstatus") yet I still get the issue on 10.04 and 10.10 RC, so is it supposed to be fixed or am I doing something wrong?

---

