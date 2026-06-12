---
title: "Ultra-lightweight Linux Distro"
date: 2015-07-20
forum: Ubuntu, Linux and OS Chat
---

### Post by Mk32 on 2015-07-20
So I procured a thin client for free recently. 

[http://www.supertronic.it/include/files/prod_files/TK3750.pdf](http://www.supertronic.it/include/files/prod_files/TK3750.pdf)

Datasheet. 

It has a CompactFlash card slot inside. Max it takes is 4GB apparently. 

What Linux distro, Debian I would prefer, would fit on roughly 2GB of space and still have a perfectly normal GUI? 

The CPU is pretty feeble, as you might expect. It's apparently nearly equivalent to a Pentium 4 Mobile, or perhaps a higher end Pentium III. It takes 512MB of RAM tops. I've already trialed Puppy Linux and didn't care for it much. 

Ideas? I'd rather avoid obscure distros like Mandrake/Fedora/some far off distro. Lubuntu 7.10 maybe?

---

### Post by kerry_s on 2015-07-21
800mhz & 512mb ram you could try lubuntu 14.04

does that thing even boot from usb ?

you could also try a debian net install. [http://ftp.debian.org/debian/dists/jessie/main/installer-i386/current/images/netboot/mini.iso](http://ftp.debian.org/debian/dists/jessie/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by mastablasta on 2015-07-21
Debian net install, or Ubuntu mini.iso and then add icewm or jwm. you can try ToriOS.

You can also try AntiX

---

### Post by buzzingrobot on 2015-07-21
Don't run X or any GUI.  Pretty much the "lightest" Linux you can get.  And it's available on all distributions.  Fanatics might start configuring and compiling their own kernels and drivers.

---

### Post by mastablasta on 2015-07-21
only they stated in specs: "would fit on roughly 2GB of space and still have a perfectly normal GUI" - so they need and want a GUi for whatever reason.

which is why the bets way might be to build something form basic install up or to use one of the light distros.

---

### Post by Mk32 on 2015-07-21
Hmmm. Lubuntu 14.04 says it wants 3GB of disk space. 

What about Lubuntu 10.04 or something older? 8.10, 9.04? Someone hinted to me that the newer Linux kernels probably won't have support for the VIA IDE controller.

---

### Post by v3.xx on 2015-07-21
> **Mk32 said:**
> Hmmm. Lubuntu 14.04 says it wants 3GB of disk space. 

What about Lubuntu 10.04 or something older? 8.10, 9.04? Someone hinted to me that the newer Linux kernels probably won't have support for the VIA IDE controller.
Using old unsupported releases will be a pain.  They won't even update anymore.

What about LXDE?  It uses openbox and is bare bone.  No display manager, use startx.  I'm thinking that will fit in 2G of space.
```
sudo apt-get install xinit && sudo apt-get install --no-install-recommends lxde
```
[URL="http://packages.ubuntu.com/trusty/lxde"]http://packages.ubuntu.com/trusty/lxde

EDIT
Forgot startx in the command
[/URL]

---

### Post by mastablasta on 2015-07-21
yeah just install from minimal and add LXDE or better yet just Windows manager: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by sudodus on 2015-07-21
[This link](https://help.ubuntu.com/community/9w/RAM_%26_disk_usage) illustrates how much disk space is needed for some basic linux systems based on Ubuntu mini.iso 14.04 LTS.

---

### Post by kerry_s on 2015-07-21
> **Mk32 said:**
> Hmmm. Lubuntu 14.04 says it wants 3GB of disk space. 

What about Lubuntu 10.04 or something older? 8.10, 9.04? Someone hinted to me that the newer Linux kernels probably won't have support for the VIA IDE controller.

that's just to install, once installed it's far less.
i currently have debian testing xfce installed via the net installer & i'm only at 1.9gb, it's the full desktop with office & all.
after the base install task select will ask what you want, use the space bar to unselect everything & just select lxde, then tab & continue.

---

### Post by anakai on 2015-07-21
Debian base install with fluxbox or openbox

---

