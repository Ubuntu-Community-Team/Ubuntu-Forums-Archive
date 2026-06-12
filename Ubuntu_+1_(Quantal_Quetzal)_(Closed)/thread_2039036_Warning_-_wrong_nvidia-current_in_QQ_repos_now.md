---
title: "Warning - wrong nvidia-current in QQ repos now"
date: 2012-08-07
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-08-07
There is a wrong update of nvidia-current in QQ repos now.
This will remove your xserver and drivers even whether you have xserver 1.12 or xserver 1.13 installed.
This wrong version has an old ABI (xserver-video-abi-11), which is for xserver 1.11. QQ does not have that old xserver.

The wrong versions are:
nvidia-current 304.32-0ubuntu2
nvidia-current-updates-0ubuntu4

Here:
[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu2](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu2)

[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers-updates/304.32-0ubuntu4](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers-updates/304.32-0ubuntu4)

---

### Post by cariboo on 2012-08-08
Thanks, Harry33 for the warning, I just wish there was a way that the forum software would make this stand-out more than the rest of the threads.

---

### Post by Harry33 on 2012-08-08
Here is a bit more info on this one.

The Canonical developer, Alberto Milone, has uploaded these drivers.
Version 304.32-0ubuntu3 is a correction to the erraneous version 304.32-0ubuntu2.

For nvidia-current_304.32-0ubuntu3 he wrotes:

> 
* debian/rules:
- Add ABIs 12 and 13.


This suggests that this driver could support (in addition to xserver-video-abi-11) also video-abi-12 and video-abi-13.
So it could work on all three xservers (1.11 and 1.12 and 1.13).

I will check this later on, and will post the results here.
It is safe to test it with synaptic by only selecting (but not applying) this package to be upgraded. Synaptic will then show if something is going to be removed.

Anyway, the safe version for xserver 1.12 is this older one here (v. 304.32-0ubuntu1):

[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu1)

---

### Post by ventrical on 2012-08-08
> **Harry33 said:**
> Here is a bit more info on this one.

The Canonical developer, Alberto Milone, has uploaded these drivers.
Version 304.32-0ubuntu3 is a correction to the erraneous version 304.32-0ubuntu2.

For nvidia-current_304.32-0ubuntu3 he wrotes:



This suggests that this driver could support (in addition to xserver-video-abi-11) also video-abi-12 and video-abi-13.
So it could work on all three xservers (1.11 and 1.12 and 1.13).

I will check this later on, and will post the results here.
It is safe to test it with synaptic by only selecting (but not applying) this package to be upgraded. Synaptic will then show if something is going to be removed.

Anyway, the safe version for xserver 1.12 is this older one here (v. 304.32-0ubuntu1):

[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu1](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu1)

Good eye Harry33!

---

### Post by ventrical on 2012-08-08
> **cariboo907 said:**
> Thanks, Harry33 for the warning, I just wish there was a way that the forum software would make this stand-out more than the rest of the threads.


Can't you add something to the 'prefix' directory like they do with [kubuntu] ect?? ie; if  they edit in *warning* in bright red .. it may catch our attention so warnings like these may  get more notice.

---

### Post by VinDSL on 2012-08-08
> **Harry33 said:**
> There is a wrong update of nvidia-current in QQ repos now.
This will remove your xserver and drivers even whether you have xserver 1.12 or xserver 1.13 installed.
This wrong version has an old ABI (xserver-video-abi-11), which is for xserver 1.11. QQ does not have that old xserver.

The wrong versions are:
nvidia-current 304.32-0ubuntu2
nvidia-current-updates-0ubuntu4

Here:
[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu2](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers/304.32-0ubuntu2)

[https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers-updates/304.32-0ubuntu4](https://launchpad.net/ubuntu/quantal/+source/nvidia-graphics-drivers-updates/304.32-0ubuntu4)
Thanks for making the correction, in the initial warning, Harry!

When you first posted about 0ubuntu 3 & 5, I thought I was missing something.  They were working fine for me.

Another mystery solved.  ;)

---

### Post by Harry33 on 2012-08-08
Yes the corrected versions work OK with all the three xservers branches (1.11 and 1.12 and 1.13). So this is solved now.

---

### Post by philinux on 2012-08-08
> **cariboo907 said:**
> Thanks, Harry33 for the warning, I just wish there was a way that the forum software would make this stand-out more than the rest of the threads.

Could have use an icon like the warning triangle maybe.

[http://ubuntuforums.org/images/icons/icon4.gif](http://ubuntuforums.org/images/icons/icon4.gif)

---

