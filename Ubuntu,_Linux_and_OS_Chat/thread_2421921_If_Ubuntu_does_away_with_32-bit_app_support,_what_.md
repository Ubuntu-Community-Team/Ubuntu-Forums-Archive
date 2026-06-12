---
title: "If Ubuntu does away with 32-bit app support, what options do I have with my printer?"
date: 2019-06-29
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2019-06-29
I do realize that [Canonical has backtracked on their decision to not support 32-bit applications]("https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts"), but I want to be prepared for the future if they ever do change their minds.

I have a printer that I bought 2 years ago, a Canon PIXMA iP2700, while there is a driver for it available in CUPS, the local  driver is very limited in features, like printing in Fast Mode isn't  available, I ended up wasting lots of ink when I used the local driver.

The Linux driver that Canon provides has a print in Fast Mode feature, however, their driver is only available in 32-bit and in order to install and run my printer with their driver, I  had to enable  32-bit support by running these  commands in the  Terminal:

```
sudo dpkg --add-architecture i386
sudo apt-get update
```

If Canonical does eventually do away with supporting 32-bit, what options do I have to continue using my printer into the future?

---

### Post by Artim on 2019-06-29
Manufacturers are likely to write 64-bit drivers for their products, now that 64-bit is the norm.

---

### Post by kc1di on 2019-06-29
Debian still supports 32 bit and so does MX linux There are other options also.  Good luck.

---

### Post by Artim on 2019-06-29
Yup!  Any Debian-based distro (except Ubuntu and it's derivatives) still has all that 32-bit support.  MX-Linux is awesome for newbies, by the way, so don't let the fact that it's Debian scare you off.

---

### Post by deadflowr on 2019-06-29
32-bit libraries for printer drivers are some of the few 32-bit packages they are currently working toward figuring out a fix for.
[https://community.ubuntu.com/t/32bits-printer-drivers-on-amd64-systems/11342]("https://community.ubuntu.com/t/32bits-printer-drivers-on-amd64-systems/11342")

---

### Post by ardouronerous on 2019-06-29
> **deadflowr said:**
> 32-bit libraries for printer drivers are some of the few 32-bit packages they are currently working toward figuring out a fix for.
[https://community.ubuntu.com/t/32bits-printer-drivers-on-amd64-systems/11342](https://community.ubuntu.com/t/32bits-printer-drivers-on-amd64-systems/11342)

Thanks for the heads up! :)

---

### Post by charlieg on 2019-07-01
Nobody is forcing you to use the bleeding edge version of Ubuntu. What reasons cause you to need to move to 19.10 or later? Just stick with 18.04 or whatever version you are on now.

---

### Post by mastablasta on 2019-07-01
> **charlieg said:**
> Nobody is forcing you to use the bleeding edge version of Ubuntu. What reasons cause you to need to move to 19.10 or later? Just stick with 18.04 or whatever version you are on now.

well ubuntu derivatives support for 18.04 ends in 2021, so time to plan for when that date comes.

---

### Post by CatKiller on 2019-07-01
> **mastablasta said:**
> well ubuntu derivatives support for 18.04 ends in 2021, so time to plan for when that date comes.

The flavours only maintain their configurations and packages that aren't provided by the Ubuntu flavour. All of the system libraries are going to be supported till 2023. Things like graphics drivers and new versions of Mesa, where people might want the newest stuff, come through PPAs anyway.

---

