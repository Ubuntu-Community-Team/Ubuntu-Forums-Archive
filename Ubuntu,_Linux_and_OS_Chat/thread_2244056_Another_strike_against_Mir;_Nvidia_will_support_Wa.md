---
title: "Another strike against Mir; Nvidia will support Wayland"
date: 2014-09-13
forum: Ubuntu, Linux and OS Chat
---

### Post by etna2 on 2014-09-13
Nvidia has thrown its weight behind Wayland:

[http://lists.x.org/archives/xorg-devel/2014-March/041534.html](http://lists.x.org/archives/xorg-devel/2014-March/041534.html)

And Phoronix's report: [http://www.phoronix.com/scan.php?page=news_item&px=MTY0Njc](http://www.phoronix.com/scan.php?page=news_item&px=MTY0Njc)

---

### Post by buzzingrobot on 2014-09-13
You noticed those reports are from March?

Not supporting Wayland would mean abandoning most of Linux in the near future.

Supporting Wayland does not mean ignoring Mir.

Nvidia and AMD will also need to support X for the foreseeable future, unless they wash their hands of Linux (which would not entirely surprise me).

---

### Post by etna2 on 2014-09-13
> **buzzingrobot said:**
> You noticed those reports are from March?

Not supporting Wayland would mean abandoning most of Linux in the near future.

Supporting Wayland does not mean ignoring Mir.

Nvidia and AMD will also need to support X for the foreseeable future, unless they wash their hands of Linux (which would not entirely surprise me).

Well they definitely have to support X until the so-called replacements actually start gaining more traction, fair enough. But the likelihood of them pulling out of Linux entirely? Much lower; Nvidia for one has investments in Linux-powered workstations and embedded devices. 

I won't know about AMD; i **think** chances of them abandoning Linux do appear higher since they  have a greater stake in BSD considering how the PS4 has really injected cash into their pockets and uses a BSD variant for its base system. But at least the open drivers have official support from them...

---

### Post by buzzingrobot on 2014-09-13
Right, but it's always seemed to me video driver support for Linux hangs on by a narrow thread. When it isn't something necessary to support profitable lines of business, it will end.

---

### Post by etna2 on 2014-09-13
> **buzzingrobot said:**
> Right, but it's always seemed to me video driver support for Linux hangs on by a narrow thread. When it isn't something necessary to support profitable lines of business, it will end.

The good thing is that the open drivers and Mesa have really progressed far enough to the point where KMS works and native resolutions are supported right out of the box. Sure, radeon, radeonSI and nouveau are **** compared to the binary drivers, but they are at least able to provided an accelerated DE. 

So even if AMD and Nvidia pulled all proprietary driver support for their hardware tomorrow, Linux will continue to work with the open drivers. Last I heard, nouveau now has Maxwell support as well, and radeonSI has managed to enable hardware acceleration for Hawaii cards in the previous month. That basically means at every single video card released by AMD and Nvidia to date are, in theory, compatible and functioning with 2D and 3D acceleration with the open drivers

---

### Post by grahammechanical on 2014-09-13
How long did it take Nvidia to start working on a Linux driver for its Optimus technology? Far too long for me to be convinced that the Nvidia bosses care about Linux.

---

### Post by etna2 on 2014-09-13
> **grahammechanical said:**
> How long did it take Nvidia to start working on a Linux driver for its Optimus technology? Far too long for me to be convinced that the Nvidia bosses care about Linux.

Nvidia wanted to use the kernel's DMA-BUF mechanism to bring Optimus to Linux. And then they ran into the first problem: DMA-BUF only allowed GPL symbols. So Nvidia asked the kernel developers if DMA-BUF could be made more permissive. The devs essentially told Nvidia to sod off because they will not do so. And thus Nvidia had to write their own special mechanism within the driver to do so.

And you complain about how long it took Nvidia to bring Optimus to Linux? Why not blame the developers that refused to make DMA-BUF more permissive?

---

### Post by mastablasta on 2014-09-16
> **etna2 said:**
> 
I won't know about AMD; i **think** chances of them abandoning Linux do appear higher since they  have a greater stake in BSD considering how the PS4 has really injected cash into their pockets and uses a BSD variant for its base system. But at least the open drivers have official support from them...

what they are trying to do (as it would seem form some of their statements) is to move all drivers slowly into opensource. and then help with opensource development.

---

### Post by NGRhodes on 2014-09-18
> **etna2 said:**
> Nvidia wanted to use the kernel's DMA-BUF mechanism to bring Optimus to Linux. And then they ran into the first problem: DMA-BUF only allowed GPL symbols. So Nvidia asked the kernel developers if DMA-BUF could be made more permissive. The devs essentially told Nvidia to sod off because they will not do so. And thus Nvidia had to write their own special mechanism within the driver to do so.

And you complain about how long it took Nvidia to bring Optimus to Linux? Why not blame the developers that refused to make DMA-BUF more permissive?

You could equally blame Nvidia for refusing to use GPL.

---

