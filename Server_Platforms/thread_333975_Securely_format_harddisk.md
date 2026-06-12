---
title: "Securely format harddisk"
date: 2007-01-08
forum: Server Platforms
---

### Post by el3ktro on 2007-01-08
Hi,
I have a question for you. I have an old harddisk that I want to sell, and I want to securely format it first. I don't need enterprise-grade security, and there's no sensitive data on the harddisk, but I want to do more than just a simple format. I though that something like dd if=/dev/random of=/dev/hdb would do the job, perhaps 2 or 3 times? Or would that destroy my harddisk? I'm not sure how the blocksize argument of dd affects this procedure (regarding speed).

I've read about some LiveCDs or floppy images that do this job, but I don't want to reboot my computer and leave it unusable for hours to do this. Is there a program in the repository that I could use for that?

Thanks a lot,
Tom

---

### Post by kj1h234lkj1234 on 2007-01-08
You can use **shred** to do this.

shred -vzn 30 /dev/hda

That command will fill /dev/hda with random data 30 times, then zero-fill it.

30 times might be a *tad* excessive, but you get the idea. ;) 

I believe shred is in the coreutils package, so you should have it already. (I actually boot off an old Gentoo livecd that has shred on it when I'm destroying disks)

And no, overwriting it with random data (even 100 times) will not "destroy" the disk. When the disk is partitioned and filesystems are applied, the disk is basically a clean slate once again.

---

### Post by az on 2007-01-08
I would check for bad blocks before I sold it.  I would use the badblocks write-mode to do a read-write check of your entire hard drive.

Actually, I think that mkfs can do that as it creates an ext3 filesystem.  So, with one command, you test your hard disk and erase your data at the same time.

---

### Post by spd106 on 2007-01-08
Thanks for the tip about shred. Although the dd method works doesn't give much feedback of progress.

I also found that making sure DMA was enabled for the drive through hdparm sped up the process, particularly on older systems/drives. It's still one of those "set off and then go read a book" activities, just like a kernel recompile.

---

