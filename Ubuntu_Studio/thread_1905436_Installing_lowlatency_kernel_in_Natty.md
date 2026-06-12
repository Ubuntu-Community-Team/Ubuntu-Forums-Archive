---
title: "Installing lowlatency kernel in Natty"
date: 2012-01-06
forum: Ubuntu Studio
---

### Post by Robert Finley on 2012-01-06
Can someone please detail how to install the “interim -lowlatency kernel” available in Allesio Bogani's PPA?
I read about it on the Ubuntu Studio home page and I have already added Allesio's PPA.

---

### Post by Sylos on 2012-01-07
I've never actually done this but I would think you should be able to just open synaptic - update the list - then search for 'linux-lowlatency' and then install the package once you have found it. After that I would expect it to appear as an option in Grub when you boot and you should be able to select booting into it.

Hope that works.

Cheers

---

### Post by jejeman on 2012-01-07
```
$ dpkg -l | grep -i lowlatency
ii  linux-headers-2.6.38-8-lowlatency    2.6.38-8.42~ppa2                                 Linux kernel headers for version 2.6.38 on x86/x86_64
ii  linux-headers-3.0.0-10-lowlatency    3.0.0-10.16ppa1~natty1                           Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-3.0.0-11-lowlatency    3.0.0-11.18ppa1~natty1                           Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-3.0.0-13-lowlatency    3.0.0-13.21ppa1~natty1                           Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-3.0.0-9-lowlatency     3.0.0-9.14ppa1~natty1                            Linux kernel headers for version 3.0.0 on x86/x86_64
ii  linux-headers-lowlatency             3.0.0.13.15ppa1~natty1                           lowlatency Linux kernel headers
ii  linux-image-2.6.38-8-lowlatency      2.6.38-8.42~ppa2                                 Linux kernel image for version 2.6.38 on x86/x86_64
ii  linux-image-3.0.0-10-lowlatency      3.0.0-10.16ppa1~natty1                           Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-11-lowlatency      3.0.0-11.18ppa1~natty1                           Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-13-lowlatency      3.0.0-13.21ppa1~natty1                           Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-3.0.0-9-lowlatency       3.0.0-9.14ppa1~natty1                            Linux kernel image for version 3.0.0 on x86/x86_64
ii  linux-image-lowlatency               3.0.0.13.15ppa1~natty1                           lowlatency Linux kernel image
ii  linux-lowlatency                     3.0.0.13.15ppa1~natty1                           Complete lowlatency Linux kernel
```This is the list of what I have installed from Abogani's PPA. Just find in synaptic and install
linux-lowlatency, linux-headers-lowlatency, linux-image-lowlatency
that will install the latest version.

---

### Post by Robert Finley on 2012-01-07
Thank you for the quick responses guys.  I am anxious to try it out.  The PPA seems to be broken now though :(.  I got a "404 not found" when I updated my apt cache.  I had to remove the following repositories to get a clean update.

[http://ppa.launchpad.net/abogani/lowlatency/ubuntu](http://ppa.launchpad.net/abogani/lowlatency/ubuntu) natty main
[http://ppa.launchpad.net/abogani/lowlatency/ubuntu](http://ppa.launchpad.net/abogani/lowlatency/ubuntu) natty main (Source Code)
[http://ppa.launchpad.net/ubuntustudio-dev/ubuntu](http://ppa.launchpad.net/ubuntustudio-dev/ubuntu) natty main
[http://ppa.launchpad.net/ubuntustudio-dev/ubuntu](http://ppa.launchpad.net/ubuntustudio-dev/ubuntu) natty main (Source Code)

---

### Post by jejeman on 2012-01-07
Natty version has been moved few months ago to old versions
[https://launchpad.net/~abogani/+archive/ppa](https://launchpad.net/~abogani/+archive/ppa)

---

### Post by Robert Finley on 2012-01-07
Outstanding.  That fixed me right up.  I now have the Linux 3.0.0-13-lowlatency installed.  Thank you for your help.

---

