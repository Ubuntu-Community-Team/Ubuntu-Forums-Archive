---
title: "Making an OS image bootable"
date: 2010-03-29
forum: Virtualisation
---

### Post by korvirlol on 2010-03-29
Hi There,

Im not sure if this is the right forum, so if not please move.

I have an image of an OS on an IDE harddrive that i need to do some work on, but the problem is, it isnt bootable. I am not even sure if it is possible, but is there a way to make this hard drive bootable? If the OS matters it is ubuntu 9.04.

Thanks for any help!

---

### Post by lykwydchykyn on 2010-03-29
Well, that depends on why it's not bootable in the first place.  How did Ubuntu get installed on the drive?  Did it come from another machine with a dual-boot setup?

To boot an OS, you basically need:
 - The BIOS set to boot to the hard drive
 - A partition marked "boot" (A.K.A. "active")
 - A bootloader installed (e.g. GRUB) to the MBR
 - An operating system installed that can be booted.

If any of these is missing, it won't boot.  So which is it here?

---

### Post by oldfred on 2010-03-29
You can always chroot into the system and run commands from that to repair if it is repairable.

Similar chroot commands I just posted #7, not sure what commands you may need to run.
[http://ubuntuforums.org/showthread.php?t=1441525](http://ubuntuforums.org/showthread.php?t=1441525)

---

### Post by korvirlol on 2010-03-29
> **lykwydchykyn said:**
> Well, that depends on why it's not bootable in the first place.  How did Ubuntu get installed on the drive?  Did it come from another machine with a dual-boot setup?

To boot an OS, you basically need:
 - The BIOS set to boot to the hard drive
 - A partition marked "boot" (A.K.A. "active")
 - A bootloader installed (e.g. GRUB) to the MBR
 - An operating system installed that can be booted.

If any of these is missing, it won't boot.  So which is it here?


Thanks for replying - this isnt my area of expertise so i apologize for not providing the correct details. Anyways, here it is:

The hard drive i received (actually its red hat even though for some reason in my OP i said it was ubuntu) is something i have to get some data off of. This harddrive is just an image of an OS that is running on a machine somewhere, and this imaged copy was given to me to work with. It has an OS, and according to the partitioner, this is what the drive is mapped out as:

/dev/sdb1   linux native   /boot    ext2
/dev/sdb2   extended
/dev/sdb5   linux native   /usr      ext2
/dev/sdb6   linux native   /home   ext2
/dev/sdb7   linux native   /var       ext2
/dev/sdb8   linux native   /          ext2
/dev/sdb9   linux native   swap


so it seems like it has all of the requirements you specified except grub. What i think i'd like to do is modify my current grub setup to also be able to boot to this as an additional option, and this is something i dont know how to do. Also, depending on how difficult/easy it is, is this something that could be virtualized? 

thanks for any help.

---

### Post by lykwydchykyn on 2010-03-29
If you just need to get data off of it, the simplest thing is to mount the partitions and copy off the data.  

But if for some reason you need to make this boot, I'd recommend not messing with your own grub config and just booting it in a virtual machine.

Do you have experience working with a particular virtualization product?

---

### Post by korvirlol on 2010-03-29
Thank you for helping me!

The problem is i need to use some software installed on image to get the data off (the data being stored by the software is obfuscated), so it seemed to me, the simplest way to do this would be to boot into it.

I like the idea of virtualzing it, but i dont know how to do it. I have some (limited) experience with hypervisor, but i am a fast learner. If you wouldnt mind giving me a quick description about how i can virtualize it, i would be REALLY greatful (grateful?)

---

### Post by lykwydchykyn on 2010-03-30
Simplest way IMHO is to install qemu

Then run:
```

sudo qemu -hda /dev/sdb -m 512

```

The "sudo" is necessary because you'll be directly accessing that drive.
The "-m 512" gives the vm 512 MB of RAM, but that of course assumes you have 512 MB of RAM to spare.  If you machine has less RAM, lower that amount (default is 128).

See if that boots up for you.

---

### Post by korvirlol on 2010-03-30
It ALMOST worked - thanks for the tip. It infact tries to boot up using qemu but...

of course the next obscure error: 
```

Kernel panic: VFS: unable to mount root fs on 08:08
```not sure what that means, so back to gooling. Thanks again for the help, and any advice on an error like this is appreciated!

---

### Post by lykwydchykyn on 2010-03-30
> **korvirlol said:**
> It ALMOST worked - thanks for the tip. It infact tries to boot up using qemu but...

of course the next obscure error: 
```

Kernel panic: VFS: unable to mount root fs on 08:08
```not sure what that means, so back to gooling. Thanks again for the help, and any advice on an error like this is appreciated!

What this tells me is that we have a boot loader of some kind, and the partition is marked bootable.

However, the partition has changed location; since we're telling qemu it's hda, the disk is hd0 to grub.  But originally it was apparently not the first hard drive.  So now when the kernel goes looking for the root parition at hd08, partition 08, it's not finding a disk there.  Make sense?

Do you get a grub menu or LILO prompt when it starts, before the error?
what probably needs to happen is the boot loader entry needs to be edited to point to the first hard drive.

---

### Post by korvirlol on 2010-03-31
Yea, that explanation does make sense, and it is lilo. So this emulator actually runs the bootloader on the disk?


After doing some reading about lilo, i found that the lilo.conf file is stored normally in /etc/lilo.conf ... which in this case happens to be in the root directory hd08 or sdb8. In fact like you pointed out, it was trying to boot /dev/sda8, so i changed this to what it should be in this case, saved the file and tried to qemu it again, but it failed with the same error.

How could it be loading that lilo.conf file if it is on the root partition which it cant mount?? So then i looked into the /boot directory for this particular OS, and there isnt a lilo.conf file, but a bunch of binary files that might hold the answer - i dont know.

Do i have to change the lilo.conf file and then re-create the items in the /boot directory somehow, or is it loading a different lilo.conf file somewhere else that I cant seem to find?

---

### Post by lykwydchykyn on 2010-03-31
> **korvirlol said:**
> Yea, that explanation does make sense, and it is lilo. So this emulator actually runs the bootloader on the disk?


After doing some reading about lilo, i found that the lilo.conf file is stored normally in /etc/lilo.conf ... which in this case happens to be in the root directory hd08 or sdb8. In fact like you pointed out, it was trying to boot /dev/sda8, so i changed this to what it should be in this case, saved the file and tried to qemu it again, but it failed with the same error.

How could it be loading that lilo.conf file if it is on the root partition which it cant mount?? So then i looked into the /boot directory for this particular OS, and there isnt a lilo.conf file, but a bunch of binary files that might hold the answer - i dont know.

Do i have to change the lilo.conf file and then re-create the items in the /boot directory somehow, or is it loading a different lilo.conf file somewhere else that I cant seem to find?

Ok, this is a little confusing because there are multiple things going on here.

To your machine, the disk is /dev/sdb
To the virtualized machine, the disk is either going to be /dev/sda or /dev/hda, depending on how old the redhat install is.

Qemu only emulates IDE, IIRC, so if this disk image was originally on SATA or SCSI, it's going to be set up to boot to /dev/sda.

This may affect the fstab as well.

So my advice going forward is to try telling lilo to boot to /dev/hda8, and edit the fstab to change all /dev/sda to /dev/hda.

Your workstation will still see the disk as /dev/sdb, but the emulated machine will see it as /dev/hda.

---

