---
title: "Daru2, gutsy upgrade - Lost everything"
date: 2007-10-20
forum: System76 Support
---

### Post by imhavoc on 2007-10-20
I did an upgrade on my Daru2. Everything seemed fine, then suddenly, it refused to boot.

When I pull up the drive in fdisk, I get:
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          29      232911   83  Linux
/dev/sda2              30       19458   156056528+   5  Extended
/dev/sda5              30       19458   156056528   8e  Linux LVM

When I pull it up with QtParted, it reports sda5 is "unknown."

I haven't been able to mount the partition to copy my files off.

I'm stumped. I've been working on this all day.

---

### Post by thomasaaron on 2007-10-22
What happens, exactly, when you try to boot?

Does it hang for a long time and then give you a busybox prompt?
Do you get any error messages?

Your partitioning looks OK.

---

### Post by digitalbenji on 2007-10-22
If you boot off a livecd, are you able to mount the drive?  How have you been trying to mount the drive?

---

