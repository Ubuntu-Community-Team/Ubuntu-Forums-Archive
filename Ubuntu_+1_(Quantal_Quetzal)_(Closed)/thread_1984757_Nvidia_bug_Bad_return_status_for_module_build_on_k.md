---
title: "Nvidia bug Bad return status for module build on kernel: 3.4.0-2-"
date: 2012-05-22
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-05-22
Error! Bad return status for module build on kernel: 3.4.0-2-generic (x86_64)

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506)

I've not booted into QQ as I just did the update via chroot.

---

### Post by Harry33 on 2012-05-22
Just to remind people using xorg-edgers PPA,
the nvidia-current_302.11 in that PPA works fine and builds the correct kernel module OK.
However, xorg-edgers version can only be installed on a system with xserver 1.12.
Well, Quantal is going to move to xserver 1.12 later anyway.

---

### Post by philinux on 2012-05-22
Nice catch Harry.

Also fix released with 295.53-0ubuntu1. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506/comments/9](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/993506/comments/9)

Although it hasn't hit the repos yet.

---

### Post by ventrical on 2012-05-22
I just updated on one install. No way that kernel will match up with nVidia driver. It is the same problem as with 3.4.0-1 and no ppas here.

---

### Post by philinux on 2012-05-22
```
apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.53-0ubuntu1

```

All up to date and fine. New kernel too 3.4.0-3

---

### Post by ventrical on 2012-05-22
wow . that was fast ... thanks philinux ! :)

---

### Post by ventrical on 2012-06-02
> **philinux said:**
> ```
apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.53-0ubuntu1

```All up to date and fine. New kernel too 3.4.0-3


I posted in another forum about the nVidia Big Screen comming back and now I get this:

dale@dale-desktop:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: 295.53-0ubuntu1
  Candidate: 295.53-0ubuntu1
  Version table:
 *** 295.53-0ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/restricted i386 Packages
        100 /var/lib/dpkg/status
dale@dale-desktop:~$

---

