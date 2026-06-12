---
title: "Server Dead"
date: 2009-12-08
forum: Server Platforms
---

### Post by Vegan on 2009-12-08
Well after attempting to run fsck at reboot, I noticed then I used touch that the system compplained my file system was read-only.

Rebooting saw the file system as corrupt, so I ran fsck and fixed all the errors. But the OS still does not want to mount the disk.

Thoughts? Time for a new disk again? Or is there some way to repair the mess.

---

### Post by munky99999 on 2009-12-08
What filesystem is the volume set to?

Or what is the underlying reason you want to run fsck?

Seems you wanted to run fsck before you discovered it to be read-only and/or corrupt.

You can try booting up a livecd of karmic ubuntu to run disk utilities on it.

---

### Post by Vegan on 2009-12-08
Default was ext2 I think, for all disks. I used the defaults. Thought it was supposed to be ext3 though.

no errors, fsck or badblocks.

machine now starts in single user mode.

mount point /var/run does not exit etc

mount of root file system failed.

I wonder if /var is history, its not here, anymore.

---

### Post by Vegan on 2009-12-08
I tried mounting the disk, seems to be nominally there but /var is missing which is a critical folder. So where is it hiding?

my fstab seems to be damaged, text is a bit misaligned.

I used

mount -v -a

which tells me everything in fstab is mounted yet no /home or /var so I am now looking where the true locations are?

---

