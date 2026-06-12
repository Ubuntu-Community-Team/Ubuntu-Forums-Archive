---
title: "Struggling to make bootable CF card"
date: 2009-02-10
forum: Server Platforms
---

### Post by Lumpy3 on 2009-02-10
I'm pretty new to Linux/Ubuntu, I've only installed it on a couple machines to play around with.

My goal is to make a Intel Atom based Ubuntu NAS box.  I've got a MSI Wind and a 1T drive to make it with.  I chose the Wind for it's  bootable CF card on the motherboard.

I've burned a ISO of the install and run it on my WinXP machine to load the OS onto the CF card.  Everything seems to go smoothly until I get to the GRUB boot installer.  I don't know what to select, I've tried it a couple ways and skipped the GRUB and tried the LILO as well.  Each time i put the CF into the Wind pc and each time I get the same error message "..Select proper boot device or Insert Boot Media...."

The BIOS recognizes the CF card as a bootable device and it's selected as the 1st boot device.

Does anybody know what I'm doing wrong?

Thanks

---

### Post by netztier on 2009-02-10
> **Lumpy3 said:**
> I've burned a ISO of the install and run it on my WinXP machine to load the OS onto the CF card. 

How exactly are you doing that? Normally, you would run the installer from CD (i.e. boot from CD) and it would write the OS to the destination drive. How do you do that from within XP? Can that be done with WUBI?

> **Lumpy3 said:**
> The BIOS recognizes the CF card as a bootable device and it's selected as the 1st boot device.

Is the partition you want to boot from marked as "bootable"? You'd have to run some form of fdisk to give it the bootable flag. The partitioning section in the installer normally takes care of this.

regards

Marc

---

### Post by Adina on 2009-02-10
maybe you can try to boot from a cd rom with the cd you burned the ubuntu image on and then install it on the cf card from the cdrom.

I installed ubuntu server 8.10 on an old pentium 3 machine this way. I connected the cf card reader with ide cable to the ide/hdd connector on the motherboard and installed ubuntu from the cd image just like on a regular hdd. The cf card was 4GB and I didn't encounter any problems booting or anything else.

I hope this was any helpful.

---

### Post by Lumpy3 on 2009-02-10
Thanks all.  I was trying to creat the bootable CF on my XP machine 'cause i don't have a USB or SATA cd drive and those are the only headers available on this new MSI Wind Atom based machine.  I just went out and bought a USB external cd drive so I can do it all on the new Wind machine.  It's loading now, hopefully witout incident.

Thanks.

---

