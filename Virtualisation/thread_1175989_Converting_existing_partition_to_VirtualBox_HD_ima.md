---
title: "Converting existing partition to VirtualBox HD image"
date: 2009-06-01
forum: Virtualisation
---

### Post by Zeikcied on 2009-06-01
Is there a way to convert an existing Windows XP partition to a VirtualBox hard drive image?

I recently upgraded to Jaunty, and installed the newest version of the closed-source edition of VirtualBox.  But for some reason I can't get my WinXP NTFS partition to mount so that I can have read/write access.  The mount point is set to root permissions, and "sudo chown" isn't changing the owner like it did with my newer ext4 partitions.

So the only way I can get my VirtualBox drive images to open in VirtualBox is by using the app as root, and I know that's not very wise.  So I figure that if I can convert it to a disk image, not only can I get rid of that partition once and for all (I do have space to put the disk image), but I can hopefully be rid of the NTFS mounting nightmare.

---

### Post by Zeikcied on 2009-06-03
Ok, I figured out how to get write permissions to the NTFS partition, so I was able to boot my WinXP VM again.

But I would still like to convert it to a disk image instead of booting from the physical partition.

I found out that I can use the VMWare Converter.  I ran it in my WinXP VM (I can't exactly boot to WinXP normally anymore) and set one of my ext4 partitions to the Shared Folders.  But when I try to tell the converter to put the VM on my ext4 partition, it forces me to split up the disk image into 2 Gig parts, because it doesn't realize that the file system can handle large files.  (I guess VirtualBox sets non-Windows file systems to identify as FAT32 or something in order to allow Windows to read it.)

So, is there any way to either combine the 2 Gig parts, or to use a native Linux program or command to convert the Windows partition to a virtual disk image?  Or am I stuck?

---

### Post by Zeikcied on 2009-06-11
Does anyone know if I can do this?

---

### Post by flamacue on 2009-07-28
Will this do?

[http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

See also [http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

---

