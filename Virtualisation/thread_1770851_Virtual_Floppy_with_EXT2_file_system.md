---
title: "Virtual Floppy with EXT2 file system"
date: 2011-05-29
forum: Virtualisation
---

### Post by nik.liepins on 2011-05-29
I need to create a virtual floppy device with ext2 file system, I am using latest ubuntu and vmware player.
I tried to create a virtual floppy using vmware but for some reasons Ubuntu does not recognize it after I do connect from the vmware player menu. 
I tried to create a virtual floppy file using winimage software but it creates floppies only with FAT12 and I can not reformat it under linux. The problem is that once this virtual floppy is mounted mkfs.ext2 does not want to create a file system on it - because it is mounted. But once I do not mount it I have no idea how I can ask mkfs.ext2 to use this file because it uses (as far as I understand) only /dev/fd... devices.
I would like to have a command similiar to this but for ext2 - 
sudo mkfs.msdos -C floppy.img 1440.

I would apprecitata any help on this issue.  A lot of thanks.

---

### Post by insane_alien on 2011-06-01
could you not format it to ext2 in the virtual machine?

---

### Post by nik.liepins on 2011-06-01
I have no reason to format it inside VM but I *HAVE* to have an option to create EXT2 floppy diskette.
Do you have any ideas where else can I format the diskette to EXT2?
 
Thanks a lot,

---

