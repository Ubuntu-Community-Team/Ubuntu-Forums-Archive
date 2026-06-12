---
title: "Ubuntu boot issues with rr2220 RAID card"
date: 2008-04-26
forum: Server Platforms
---

### Post by Vadir on 2008-04-26
I am having an issue with ubuntu booting up successfully when I have my array hooked up to my raid card.  With just the card in and no drives hooked up to it boots fine. (I use a separate drive for my OS)

I am running 2.6.24-16-server (64 bit) and it is hanging after I select the kernel to boot from in grub.  It simply hangs at "Starting up..."

I have compiled the drivers for my card and lsmod shows that they have been loaded.

Any suggestions on how to fix this?

---

### Post by GregM15 on 2008-05-07
I have the same issue with an ST Labs raid card

---

### Post by windependence on 2008-05-07
In my experience, 3Ware cards are better supported by more distros than most other cards. Some cards won't work at all without a lot of tweaking, even with the proper drivers. Many raid cards are just software raid on a chip.

-Tim

---

