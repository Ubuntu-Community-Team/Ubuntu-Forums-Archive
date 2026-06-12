---
title: "problem reverting after testing kernel"
date: 2012-08-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by unibroker on 2012-08-04
After installing the version 3.5x kernel (actually wanted the 3.6 but that's another story), I get the following error when I try to go back to my precise kernel.

```
E: Unable to locate package linux-image-3.5.0-7.7-generic
E: Couldn't find any package by regex 'linux-image-3.5.0-7.7-generic'
E: Unable to locate package linux-headers-3.5.0-7.7
E: Couldn't find any package by regex 'linux-headers-3.5.0-7.7'
E: Unable to locate package linux-headers-3.5.0-7.7-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-7.7-generic'
```

When I reboot the kernel is still the first option in grub and I have to go to previous linux versions in order to boot to the proper one.  I did the testing before and had no problems reverting.

Any ideas?

---

### Post by jfernyhough on 2012-08-04
$ sudo update-grub

should sort it.

---

### Post by unibroker on 2012-08-04
> **jfernyhough said:**
> $ sudo update-grub

should sort it.
Thanks for the response.

Seemed to update ```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-7-generic
Found initrd image: /boot/initrd.img-3.5.0-7-generic
```

but get same error message when I try to execute this ```
sudo apt-get remove --purge linux-image-generic-lts-quantal linux-headers-generic-lts-quantal linux-image-3.5.0-7.7-generic linux-headers-3.5.0-7.7 linux-headers-3.5.0-7.7-generic 
```

---

### Post by jfernyhough on 2012-08-04
Oh, check you have another kernel installed before you remove this one...

You don't need the .7 at the end:

sudo apt-get remove --purge linux-image-generic-lts-quantal linux-headers-generic-lts-quantal linux-image-3.5.0-7-generic linux-headers-3.5.0-7 linux-headers-3.5.0-7-generic

---

### Post by unibroker on 2012-08-04
> **jfernyhough said:**
> Oh, check you have another kernel installed before you remove this one...

You don't need the .7 at the end:

sudo apt-get remove --purge linux-image-generic-lts-quantal linux-headers-generic-lts-quantal linux-image-3.5.0-7-generic linux-headers-3.5.0-7 linux-headers-3.5.0-7-generic

Bingo!  Thank you.  I wonder how we tell this site the error [http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads]("http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads")

---

### Post by cariboo on 2012-08-04
> **unibroker said:**
> Bingo!  Thank you.  I wonder how we tell this site the error [http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads]("http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads")

When you add your test results, there is a comment box, where you can add your experience.

---

### Post by unibroker on 2012-08-06
> **jfernyhough said:**
> Oh, check you have another kernel installed before you remove this one...

You don't need the .7 at the end:

sudo apt-get remove --purge linux-image-generic-lts-quantal linux-headers-generic-lts-quantal linux-image-3.5.0-7-generic linux-headers-3.5.0-7 linux-headers-3.5.0-7-generic

Well apparently it is not an error because now that site [http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads]("http://packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads") has updated to [HTML]sudo apt-get remove --purge linux-image-generic-lts-quantal linux-headers-generic-lts-quantal linux-image-3.5.0-8.8-generic linux-headers-3.5.0-8.8 linux-headers-3.5.0-8.8-generic [/HTML] as part of the uninstall procedure.  I followed install and uninstall from this site so could I be the only one having the uninstall problem?

---

### Post by balloons on 2012-08-06
Unibroker, you hit the timing window I think for when the ppa updated. It went to the .8 series this morning. However, I still goofed on the package names.. sorry about that mate! Let me go fix the site now since I did the same for the .8 series, adding the extra .8..

---

### Post by unibroker on 2012-08-06
No worries.  I'm such a novice at this I expected to be the problem!

---

