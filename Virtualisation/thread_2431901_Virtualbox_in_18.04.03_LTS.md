---
title: "Virtualbox in 18.04.03 LTS"
date: 2019-11-23
forum: Virtualisation
---

### Post by gardnermarquis43 on 2019-11-23
Please somebody help. Lol, never used ubuntu before but am trying to use windows 10 in a virtual machine inside of ubuntu. I have installed latest version of virtualbox and added extension. However, i now want to install windows 10 iso file to run in virtual machine and had issue saying kernel driver not loading or available???

---

### Post by QIII on 2019-11-23
Moved to virtualization as a more appropriate sub-forum.

I'm sure there are those who would be quite willing to help, but you have not articulated a question.

---

### Post by gardnermarquis43 on 2019-11-23
thank you i was just editing my thread. i will move its my first day here bear with me lol

---

### Post by QIII on 2019-11-23
You can't move it.  I already did.

---

### Post by gardnermarquis43 on 2019-11-23
thx. any suggestions?

---

### Post by QIII on 2019-11-23
It has been many years since I used Virtualbox (I use the built-in KVM (Kernel Virtual Machine) in the kernel itself), but I think you need to install build-essential and dkms at the very least.  Add linux-headers for good measure.  Probably already have it, but you will be told if you do.

Did you install via the instructions [here]("https://www.virtualbox.org/wiki/Linux_Downloads") or from the Ubuntu repositories?  Because of Oracle's licensing, certain parts of Virtualbox cannot be made available through any distribution's repositories.  You have to add them from Oracle's site anyway, so might as well get it clean from the start.

I would suggest installing the following via the command line:

```

sudo apt install linux-headers-generic build-essential dkms

```

and then downloading and installing from Oracle's site.

---

### Post by gardnermarquis43 on 2019-11-23
thank you it also said to run root /sbin/vboxconfix

---

### Post by gardnermarquis43 on 2019-11-23
should i also disable secure boot?

---

### Post by wildmanne39 on 2019-11-23
You have to disable secure boot or sign a security key before you can install build-essential dkms, it is much easier to disable it.

---

### Post by gardnermarquis43 on 2019-11-23
thx yall i was able to do the QIII and it did a bunch of stuff lol. And yes wildmanne39 i was able to disable secureboot. Now once the headers are installed should i try again or should i delete virtualbox and then download again?

---

### Post by gardnermarquis43 on 2019-11-23
and yea i downloaded from the link you gave QIII

---

