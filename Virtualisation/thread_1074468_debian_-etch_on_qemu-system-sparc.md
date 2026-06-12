---
title: "debian -etch on qemu-system-sparc"
date: 2009-02-19
forum: Virtualisation
---

### Post by tigga on 2009-02-19
Hi!

i have a x86 linux(ubuntu8.04) and want to run debian etch 5.0.0 for sparc as a qemu image in the qemu-system-sparc emulator.
here's what i'm doing:

i followed this toturial:
[www.aurel32.net/info/debian_sparc_qemu.php]("www.aurel32.net/info/debian_sparc_qemu.php")

i created an image test.img with qemu-img. this image is /dev/hda, the ubuntu-iso is the cdrom drive, which is booted:

#qemu-system-sparc -hda test.img -cdrom debian-500-sparc-netinst.iso -boot d

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

 Welcome to Debian GNU/Linux lenny!

This is a Debian installation CDROM, built on 20090214-16:12.
Keep it once you have installed your system, as you can boot from it
to repair the system on your hard disk if that ever becomes necessary.

WARNING: You should completely back up all of your hard disks before
  proceeding. The installation procedure can completely and irreversibly
  erase them! If you haven't made backups yet, remove the rescue CD from
  the drive and press L1-A to get back to the OpenBoot prompt.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent permitted
by applicable law.

[ ENTER - Boot install ]   [ Type "expert" - Boot into expert mode ]
                           [ Type "rescue" - Boot into rescue mode ]

boot:
Your imagename `install' and arguments `' have either wrong syntax,
or describe a label which is not present in silo.conf
Type `help' at the boot: prompt if you need it and then try again.
boot: rescue
Your imagename `rescue' and arguments `' have either wrong syntax,
or describe a label which is not present in silo.conf
Type `help' at the boot: prompt if you need it and then try again.

Can you please help me.

---

