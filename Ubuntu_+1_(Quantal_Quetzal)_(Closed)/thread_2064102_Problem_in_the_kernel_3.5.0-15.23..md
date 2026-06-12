---
title: "Problem in the kernel 3.5.0-15.23."
date: 2012-09-28
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by irv on 2012-09-28
Anyone using the ATI RS690M graphics card is out of luck with the release of 12.10 Until the release of 3.5.0-15.24 or -16.24 kernel because the graphics are corrupt in 3.5.0-15.23. The only way to get this release to work is to compile your own kernel.
Now I have never compiled my own kernel and I am sure there are many out here that have not. I have been trying every few days to download and test there release and have finial made the dissension to to stick with 12.04 seeing it is LTR.
I am not a programmer but I would think in kernel design it would be a good idea to try to stay backward compatible with older hardware.
I file a bug report along with other if you are interested in looking at it. The fix is there waiting for the kernel to be compiled.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1029582]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1029582")

---

### Post by jfernyhough on 2012-09-28
You could always try the 3.6-rc7 mainline kernel as they appear to have fixed the problem. No need to compile your own then.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/)

---

### Post by dino99 on 2012-09-28
3.5.0-16 is out

---

### Post by irv on 2012-09-28
> **jfernyhough said:**
> You could always try the 3.6-rc7 mainline kernel as they appear to have fixed the problem. No need to compile your own then.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.6-rc7-quantal/)

What would I do? Would I install the kernel and then do an upgrade to 12.10 using the 
```
update-manager -d
```?

---

### Post by irv on 2012-09-28
> **dino99 said:**
> 3.5.0-16 is out

The 3.5.0-16 is not packaged with the daily built. I just tried it this morning.

---

### Post by mc4man on 2012-09-28
> **irv said:**
> The 3.5.0-16 is not packaged with the daily built. I just tried it this morning.

The .24 are now in quantal-proposed. If the nature of your issue is installing then figure it will show in the live images the day after it leaves proposed
(on the current live web page ck. the manifest of the image for linux-* version included

---

### Post by irv on 2012-09-28
I just found this at Softpedia @ [http://news.softpedia.com/news/Ubuntu-12-10-Alpha-2-Has-Linux-Kernel-3-5-278132.shtml]("http://news.softpedia.com/news/Ubuntu-12-10-Alpha-2-Has-Linux-Kernel-3-5-278132.shtml")
> The following important filesystem utilities have been updated in Ubuntu 12.10 Alpha 2: e2fsprogs 1.42.4, mdadm 3.2.5, autofs 2012-06-01, and btrfs-tools 2012-03-28. [COLOR="Red"]Also, there's now a new version of the ATI video driver.[/COLOR]


EDIT: I am just going to wait until the finial release of 12.10 seeing it is getting so close to the release date anyway. But thanks for your input on this.

---

