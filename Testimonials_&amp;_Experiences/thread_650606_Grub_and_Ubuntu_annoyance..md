---
title: "Grub and Ubuntu annoyance."
date: 2007-12-26
forum: Testimonials &amp; Experiences
---

### Post by dbcalo on 2007-12-26
Alright i've been using ubuntu with a dual boot of xp for a while now. All as been well until i received an external enclosure for xmas. The external enclosure isn't the problem itself as it has esata and when properly arranged on the sata connectors all is well.

My annoyance is that grub and ubuntu use two different ways of identifying the first hard disk. Grub looks for hd0 while ubuntu will look for and find the first drive chosen as the boot drive. This single issue gave me hours of unwanted heart burn when i started receiving grub errors.

My complaint is simply that i feel both should be using the same method for identifying the first hdd so it will in fact install the boot loader to the location that you intended. perhaps it was too much to assume that sda was hd0 but i do know that i'm probably not the only one who will make this mistake.

thanks for reading.

---

### Post by psusi on 2007-12-26
This is a result of the way that the PC BIOS evolved and the fact that grub must use the bios to boot, then the kernel takes over control of all hardware itself.  Two different systems, two different ways of accessing disks.

Honestly, I'm surprised that the general PC market has not yet moved away from bios to EFI like Apple and the Intel Itanium platform did.

---

### Post by dbcalo on 2007-12-26
what i notice is that during the install it gives you the option to type in what drive you would like the boot loader installed on. would it not be an option to allow us to type in sda/sdb/sdc or something of the like?

also why is is that grub cannot pull the boot order from the bios and use that instead?

---

### Post by psusi on 2007-12-26
No, because grub does not have any concept of /dev/sda.  It has to speak to the bios, and the bios only understands hd0.

---

### Post by jpkotta on 2007-12-26
GRUB stands for Grand Unified Bootloader.  It is meant to boot more than Linux - any OS really.  But yes, that makes things more confusing.  See [https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668](https://help.ubuntu.com/community/GrubHowto#head-62dd4ea50c42fb3113752a272d7100469d733668) for how GRUB finds which partition it installs to.

---

### Post by dbcalo on 2007-12-27
i understand now how grub works but i don't think anyone has addressed specifically why the ubuntu installer could not use sdx and then translate that into the proper hdx for grub. would somewhat simplify things. i just feel that the area of the boot loader is the last area that has been ignored in making linux more robust.

---

### Post by psusi on 2007-12-27
Because there is no way to know how the bios will map the drives.

---

### Post by meierfra on 2007-12-27
I don't understand the discussion:

In the advanced tab  during installation of Ubuntu with the Live CD you **can** use /dev/sda (and so on)

You need to use "dev/sda" not "sda" and not "(sda)"

---

### Post by psusi on 2007-12-27
> **meierfra said:**
> I don't understand the discussion:

In the advanced tab  during grub install you **can** use /dev/sda (and so on)

You need to use "dev/sda" not "sda" and not "(sda)"

Not sure which screen you are talking about, but grub uses (hd0) in /boot/grub/menu.lst to refer to the first hard disk in the system.  It does not understand sd* or /dev* because those do not exist to the system bios.

---

### Post by meierfra on 2007-12-27
I'm talking about installing Ubuntu with the Live CD. The last screen  during the installation process has an "advanced" button. Clicking on the advanced  button one can choose where to install grub. The default  option is "(hd0)". This can be replaced by "/dev/sda" or "dev/sdb2"   etc.

(Sorry I should have said "Ubuntu Install" in place of "grub install" in my previous post)

---

### Post by meierfra on 2007-12-27
You can also use 

> sudo grub-install /dev/sda

if you  want to install grub to /dev/sda.

---

### Post by psusi on 2007-12-28
When you are installing it from within Linux, the kernel provides /dev/sda, but when it's booting it has to talk to the bios, which is why menu.lst specifies (hd0).

---

### Post by meierfra on 2007-12-28
psusi: I agree with everything you said in this thread. I just wanted to point out methods to install grub using  sda instead of (hd0).

But I have to admit there are often situation where one has to understand what (hd0,0)   means.

---

