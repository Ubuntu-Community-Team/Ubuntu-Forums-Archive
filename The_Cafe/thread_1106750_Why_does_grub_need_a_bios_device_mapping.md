---
title: "Why does grub need a bios device mapping?"
date: 2009-03-26
forum: The Cafe
---

### Post by mrsteveman1 on 2009-03-26
When you install grub manually, it appears to require a mapping of bios device numbers to actually write anything to the device in question. Syslinux and extlinux don't seem to require any such mapping, they are able to be installed simply by giving them a device name in /dev/.

I ask because i was making a custom ubuntu usb stick earlier, and grub refused to install to the stick because it didn't know the bios number for it, extlinux happily installed and worked just fine. This has happened to me hundreds of times in the past. I've also seen grub incorrectly write over the wrong disk because it guessed the bios device wrong, so it is a huge problem even if that particular problem doesn't affect people often.

So why exactly is grub so difficult to work with? It can't be because it needs to know the bios number, i've moved drives around and moved USB drives to entirely different systems and the grub installation worked just fine, so whats the problem?

---

### Post by gn2 on 2009-03-26
It could be inconsistencies in how different BIOS and drive controllers identify the drives.

---

### Post by mrsteveman1 on 2009-03-26
> **gn2 said:**
> It could be inconsistencies in how different BIOS and drive controllers identify the drives.

Yea, but syslinux works just fine without this drive mapping crap, that or it is simply better at doing the mapping.

There are plenty of bootloaders from other operating systems that don't cause nearly as much trouble as grub, i just don't get it.

---

### Post by smartboyathome on 2009-03-26
Well, Grub legacy was made a while ago, and has been around for *years*. Grub2 has been in development for a long time, and it seems stable to me, but I only used it a bit because I had to reinstall to get an encrypted drive, and haven't bothered to reinstall grub2.

---

### Post by Npl on 2009-03-26
Syslinux is restricted to boot from the same hdd(/cd/floppy) its started from AFAIK.

Grub can boot (and read configuration files) from any HDD, thats why it needs the correct mapping,

---

### Post by mrsteveman1 on 2009-03-26
> **Npl said:**
> Syslinux is restricted to boot from the same hdd(/cd/floppy) its started from AFAIK.

Grub can boot (and read configuration files) from any HDD, thats why it needs the correct mapping,

So you're saying it needs to know what its bios number is to distinguish things? What about when i move a drive to a different SATA or USB port, or a different machine? Grub keeps working, the numbers all change. Heck they change even in one machine depending on what order things were plugged in.

---

### Post by Npl on 2009-03-26
> **mrsteveman1 said:**
> So you're saying it needs to know what its bios number is to distinguish things? What about when i move a drive to a different SATA or USB port, or a different machine? Grub keeps working, the numbers all change. Heck they change even in one machine depending on what order things were plugged in.Bios number is a enumeration of the attached drives, so if you change the port for a single drive it wont matter at all.

Say you have 3 drives, in this Bios order:
1: Grub-Bootblock, says load menu.lst from drive 2
2: menu.lst
3: other stuff

Now you change the Bios order (swapping connectors from 2 and 3 should work in most cases - its not reliable though):
1: Grub-Bootblock, says load menu.lst from drive 2
2: other stuff
3: menu.lst

Now Grub will fail to load its configuration file, until you fix the device-mapping and reinstall the bootblock on drive 1

---

### Post by mrsteveman1 on 2009-03-26
Once grub is installed to a single drive (point of distinction maybe), it seems to work fine regardless of where you put that drive, but during installation it seems quite concerned with what its actual bios number is.

And the mapping is sometimes wrong, i'm not sure what the answer here is though :(

---

