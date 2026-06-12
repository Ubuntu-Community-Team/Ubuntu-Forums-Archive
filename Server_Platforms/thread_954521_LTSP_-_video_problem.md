---
title: "LTSP - video problem"
date: 2008-10-21
forum: Server Platforms
---

### Post by Zurbriggen on 2008-10-21
Hi! I have a LTSP Server with Ubuntu 8.04, I've been trying unsuccessfully to set up 3d features in thin clients, dual monitors, etc. But I can't install the drivers in the thin client environment. For example, trying to install nvidia drivers in the the thin client environment fails due to the lack of the /proc folder. In the web several people have succeeded in installing 3d drivers with the K12LTSP, but it relays in the proc folder. I am new to Linux, so please forgive if my question is to obvious.
Can anyone help me?

Best Regards,

---

### Post by lykwydchykyn on 2008-10-21
Before you chroot, try this:
```

sudo mount --bind /proc /path/to/chroot/proc

```
Then chroot and try the install.  That's how you do it when working with a LiveCD chroot, and I think LTSP client environments are the same basic concept.

---

### Post by Zurbriggen on 2008-12-04
Thank you lykwydchykyn, for your response. I am sorry that I took so long to response.
After I tried what you suggested I was able to install the glx driver for nvidia. But still does not work.

Here is what I did from the beginning:

1) I updated my chroot with the intructions in the folowing link:
[https://help.ubuntu.com/community/UbuntuLTSP/UpdatingChroot?](https://help.ubuntu.com/community/UbuntuLTSP/UpdatingChroot?)

2) Once my sources and system were updated under my chroot (following the previus link), I did the following:
$ sudo mount --bind /proc /opt/ltsp/i386/proc
$ sudo chroot /opt/ltsp/i386
$ apt-get install nvidia-glx-new

The installation run without erros, but still does not load the drivers, I can't use the two monitors neither the 3d in the thin clients.

There is a link in the web that I am trying to follow, but it is intended for k12ltsp:
[http://www.k12ltsp.org/mediawiki/index.php/FC9-LTSP5_walk-through](http://www.k12ltsp.org/mediawiki/index.php/FC9-LTSP5_walk-through)

Apperantly, it is not reading my lts.conf. I then placed in the lts.conf:
[DEFAULT]###without this it doesn't read anything###
X_CONF=/etc/X11/xorg.conf.nvidia

And then after updating the images and rebooting the thin clients, the ubuntu progress bar appears at boot time in the two monitors, but the screens go blank in the next moment.

I don't know what else to try. Does anyone else successfully install dual monitors and 3d for thin clients in Ubuntu LTSP 8.04?

---

### Post by Zurbriggen on 2008-12-04
There is also this pdf, that someone claims trough other drivers that it works in ubuntu 8.04. It is similar to the post in k12ltsp:

[www.disklessworkstations.com/web/documentation/dualMonitorLTSP.pdf](www.disklessworkstations.com/web/documentation/dualMonitorLTSP.pdf)

---

