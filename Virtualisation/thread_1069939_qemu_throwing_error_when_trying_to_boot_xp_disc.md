---
title: "qemu throwing error when trying to boot xp disc"
date: 2009-02-14
forum: Virtualisation
---

### Post by beastrace91 on 2009-02-14
I am following [this walk through](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) and at step 12 I am getting the following error thrown when I enter the command it says to use:

```
jeff@jeff-ubuntu:~$ qemu -localtime -cdrom /dev/cdrom -m 384 -boot d xpPro.imgCould not initialize SDL - exiting
```

Any ideas?
~Jeff

---

### Post by the_unforgiven on 2009-02-17
> **beastrace91 said:**
> I am following [this walk through](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo) and at step 12 I am getting the following error thrown when I enter the command it says to use:

```
jeff@jeff-ubuntu:~$ qemu -localtime -cdrom /dev/cdrom -m 384 -boot d xpPro.imgCould not initialize SDL - exiting
```

Any ideas?
~Jeff
The message clearly says that you don't have SDL installed.
Try installing the libsdl1.2 package:
```

sudo apt-get install libsdl1.2

```
As an aside, you can run the VM and use VNC to connect to it as well:
```
jeff@jeff-ubuntu:~$ qemu -localtime -cdrom /dev/cdrom -m 384 -boot d xpPro.img **-vnc :1**

```
And then, use the rdesktop client (Internet -> Terminal Service Client or something like that in Ubuntu - I use Kubuntu :p) to connect to vnc:/localhost:1

HTH ;)

---

