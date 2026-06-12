---
title: "ubuntu-7.10.sparc in qemu on x86"
date: 2007-10-21
forum: Sun Sparc Users
---

### Post by cruppstahl on 2007-10-21
Hi!

i have a x86 64bit host linux and want to run ubuntu 7.10 for sparc as a qemu image in the sparc emulator. (I'm author of an open source library and i want to test my library on a sparc architecture, that's why.)

but i haven't managed to get ubuntu running. here's what i'm doing:

i created an image test.img with qemu-img. this image is /dev/hda, the ubuntu-iso is the cdrom drive, which is booted:

qemu-system-sparc -hda test.img -cdrom ubuntu-7.10-server-sparc.iso -boot d

i get the following output:

Nvram id QEMU_BIOS, version 1
CPUs: 1
nvram error detected, zapping pram
Welcome to OpenBIOS v1.0RC1 built on Sep 21 2006 18:03
  Type 'help' for detailed information

[sparc] Booting file 'cdrom' without parameters.
Not a bootable ELF image
Not a Linux kernel image
Loading a.out image...
Loaded 7680 bytes
entry point is 0x4000
Jumping to entry point...
SILO Version 1.4.13

                       Welcome to Ubuntu gutsy!

This is an Ubuntu installation CDROM, built on 20071016.
Keep it once you have installed your system, as you can boot from it
to repair the system on your hard disk if that ever becomes necessary.

WARNING: You should completely back up all of your hard disks before
  proceeding. The installation procedure can completely and irreversibly
  erase them! If you haven't made backups yet, remove the rescue CD from
  the drive and press L1-A to get back to the OpenBoot prompt.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

[ ENTER - Boot install ]   [ Type "rescue" - Boot into rescue mode ]
boot: 
Your imagename `install' and arguments `' have either wrong syntax,
or describe a label which is not present in silo.conf
Type `help' at the boot: prompt if you need it and then try again.
boot: rescue
Your imagename `rescue' and arguments `' have either wrong syntax,
or describe a label which is not present in silo.conf
Type `help' at the boot: prompt if you need it and then try again.

as you can see, neither the default boot mode nor "rescue" work. Can anybody help me?

Thanks
Chris

---

### Post by jcastill on 2007-10-22
have u tried typing "install" I really don't know if it helps but you never know.

---

### Post by cruppstahl on 2007-10-23
Hi,

thanks for your reply, but it does not have any different effect:

boot: install
Your imagename `install' and arguments `' have either wrong syntax,
or describe a label which is not present in silo.conf
Type `help' at the boot: prompt if you need it and then try again.

---

