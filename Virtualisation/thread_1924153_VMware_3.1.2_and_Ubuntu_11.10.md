---
title: "VMware 3.1.2 and Ubuntu 11.10"
date: 2012-02-12
forum: Virtualisation
---

### Post by birdofbeauty12 on 2012-02-12
Hello,

I am trying to install Ubuntu 11.10 on VMWare 3.1.2.

When I try to mount the drive, I am getting "block drive /dev/sr0 is write-protected, mounting read-only"

I have screenshots  below, showing my /etc/fstab file, and what the mounting message. I am new to Linux, and I have a feeling that something is wrong with my fstab file.

A little background, I am trying to install the VMTools so I can have the option to use the GUI option.

Thanks in advance.

---

### Post by k999 on 2012-02-12
This is not an error, but an informational message. CD-ROMs are read only, but you didn't specify "-o ro" on the command line, so mount is friendly enough to tell you that this file system has been mounted read only even though you didn't explicitly tell it to do that. :) All should be fine, and you can continue as you had intended.

---

### Post by nothingspecial on 2012-02-12
*Thread moved to **Virtualization**.*

---

### Post by birdofbeauty12 on 2012-02-12
> **k999 said:**
> This is not an error, but an informational message. CD-ROMs are read only, but you didn't specify "-o ro" on the command line, so mount is friendly enough to tell you that this file system has been mounted read only even though you didn't explicitly tell it to do that. :) All should be fine, and you can continue as you had intended.

k999, 

Thanks, I restarted the virtual machine, and all is working now!

---

