---
title: "32b Ubuntu server 10.04 and 3TB Drive"
date: 2010-12-15
forum: Server Platforms
---

### Post by RadiusXE on 2010-12-15
Hi,
is accesible 3TB drive (ext4) at Ubuntu server 10.04 32b?
Or must I reinstall whole system to 64b (btw. must I do clean install or is possible some kind of upgrade?)?
My board (D510MO) supports EFI -> hopefully I am able to boot from this drive.

Thanks Radius

---

### Post by CharlesA on 2010-12-15
If you have a machine that can see a 3TB drive, use 64-bit.

I'm not sure if the 32-bit version would see it or not.

---

### Post by RadiusXE on 2010-12-15
Actually I plan to buy 3TB drive and I wish to know, while I need (or not) to upgrade (or only clear install?) to 64b version.

Server is running like a charm and I don't wanna to touch him, unless it is absolutely necessary. ;)

---

### Post by CharlesA on 2010-12-15
Ah I see. I don't know, tbh. The best thing would probably be to do some research on the chipset your mobo uses to see it it supports booting from drives that big.

Since you are running EFI (which supports booting from GPT drives IIRC) you should be fine.

As I haven't tried it personally, I think the best thing you can do is to get the drive and see if it'll boot up, and if not, just hook it up as a secondary drive with the current one as primary.

---

### Post by srs5694 on 2010-12-16
I've just tested using a 32-bit version of Ubuntu 9.04 in a virtual machine, and it had no problems accessing a 4 TiB virtual disk, so I think you'll be fine.

I'd be more concerned about EFI, if your board doesn't have a standard BIOS. The reason is that Ubuntu's EFI support is pretty weak. OTOH, if Ubuntu is already booting on this system, you should be fine just adding a new bigger drive, whether the motherboard uses EFI or BIOS.

---

### Post by RadiusXE on 2010-12-16
Thanks for answers.

My chipset is Intel® NM10 Express and tech. spec. is huge (over 600 pages) and after quick reading I don't find max drive capacity (or boot capacity).

The goal is to have low power consumption server -> I wish to have only one drive.

srs5694:
Good job, I have try it at home too :).


I have found, at linux core specification, that 2.6.3x 32b core can handle 5TB drive (ext4) -> probably there is no problem for me. :popcorn:

---

