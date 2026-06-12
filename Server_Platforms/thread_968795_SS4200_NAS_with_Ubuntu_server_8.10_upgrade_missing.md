---
title: "SS4200 NAS with Ubuntu server 8.10 upgrade missing ide_generic module"
date: 2008-11-02
forum: Server Platforms
---

### Post by Brian Lee on 2008-11-02
Hi,

I build a Ubuntu server on Intel SS4200 NAS from Ubuntu 8.04 server and manually patch the kernel to load ide_generic and ata_piix module (see [http://ubuntuforums.org/archive/index.php/t-501353.html](http://ubuntuforums.org/archive/index.php/t-501353.html)) and the NAS operates without problem.

However, when I update to 8.10 by using apt-get, the new kernel does not load the ide_generic and ata_piix module by default and then it fails to locate the IDE drive.

How can I chroot to the new kernel and patch the /etc/initramfs-tools/modules? I do not want to do it in new installation. I manage to change the grub to load the previous kernel and can boot up the SS4200.

---

### Post by dlong on 2008-11-25
I don't suppose you have written instructions on 'how-to' for putting ubuntu on the SS4200?

Thanks,

-d

---

### Post by dlong on 2008-11-28
> **dlong said:**
> I don't suppose you have written instructions on 'how-to' for putting ubuntu on the SS4200?

Thanks,

-d

Or perhaps an image (ie: clonezilla)?

-d

---

### Post by peroksid on 2009-01-08
I'd also appriceate a howto or an image, if possible.
Thank you.

LpP

---

### Post by dlong on 2009-01-08
> **peroksid said:**
> I'd also appriceate a howto or an image, if possible.
Thank you.

LpP

I haven't been able to find either!  Let us know if you find one.

-d

---

### Post by McLogic on 2009-03-03
> **Brian Lee said:**
> 
I build a Ubuntu server on Intel SS4200 NAS from Ubuntu 8.04 server and manually patch the kernel to load ide_generic and ata_piix module (see [http://ubuntuforums.org/archive/index.php/t-501353.html](http://ubuntuforums.org/archive/index.php/t-501353.html)) and the NAS operates without problem.

Do the lights on the front of the device still show drive status?

> **Brian Lee said:**
> 
However, when I update to 8.10 by using apt-get, the new kernel does not load the ide_generic and ata_piix module by default and then it fails to locate the IDE drive.

How can I chroot to the new kernel and patch the /etc/initramfs-tools/modules? I do not want to do it in new installation. I manage to change the grub to load the previous kernel and can boot up the SS4200.

Nobody has even found a guide to get this working, so I think you are ahead of the pack. If we had more people using Ubuntu on the SS4200, then we would be able to experiment.

---

### Post by Teleken on 2009-11-22
Sorry to resurrect an old thread but was there ever any resolution to this?

I've gotten the latest 9.1 server to work on my SS4200 but the IDE drives won't work in UDMA mode which is a pain.

I too had to recompile the kernel with classic IDE drivers enabled and PATA support disabled to get it to detect them.

---

### Post by CrazyDave on 2010-02-08
Hello,

I figured out when you boot the system with pressed "reset" button (you can release it when grub is loaded OR when the InstallerCD menu appears) than the IDE and the SATA will get recognized at the same time.

I installed now 9.10 on this way and the system works very nice...

Cheers,
David

---

### Post by Magneto on 2010-02-15
thanks for this info
did u guys go headless or use a video adapter?

---

### Post by CrazyDave on 2010-02-16
I connected via RS232. It's bit tricky to start the Installer but then it's ok.

Because of this IDE Problem I decide to kick out the DOM and install Ubuntu on the 4Raid Drives.

---

### Post by Magneto on 2011-03-10
I did a blind boot and initial prompts using a usb dvd drive, Putty and a usb serial adapter. The adapter was like $2 on ebay. Cheapest option and no video card or other mods required.

---

