---
title: "backup to external hdd via rsync"
date: 2009-02-12
forum: Server Platforms
---

### Post by mjfroggy on 2009-02-12
Hey all,

I have a ubuntu server 8.10 setup and just bout a 1tb hdd I plan to plug the external hard into the server and I want to just setup rsynce so that the server will automatically be backed up to the enternal hdd.

Is their any good tutorials anyone can point me to inorder to hookup/setup the hdd and also then setup rsync to work via a cron to backup to the external hdd that will be plugged into the server?

Thanks

---

### Post by tubezninja on 2009-02-12
Mounting the external drive is pretty straightforward once you have all the info you need to do it.  Once you have the drive connected, you'll want to make a directory somewhere on your server to mount it to.  Then, run 'sudo fidsk -lu' to find out what device designation is for this new drive:

```
scaredpoet@capacity1:~$ sudo fdisk -lu

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00003518

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1441448189   720724063+  83  Linux
/dev/sda2      1441448190  1465144064    11847937+   5  Extended
/dev/sda5      1441448253  1465144064    11847906   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c2908

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  2930272064  1465136001   83  Linux

[B]Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc011b73b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976751999   488375968+   c  W95 FAT32 (LBA)[/B]
```

In this example, my server already has 2 internal filesystems, and  I've just attached a 500GB external drive via firewire to my server, and it shows up as the last device on the list (which I've put in bold here).  The volume has been designated /dev/sc1, and it's a FAT32 filesystem.

So, now I'll mount this drive.  I've created a directory called /media/backups, and this will be my mount point for this drive:

```
sudo mount -t vfat /dev/sdc1 /media/backups 
```

This tells the server that I'm mounting a FAT filesystem ("-t vfat"), the device I'm mounting is /dev/sdc1 (as listed in fdisk) and that I'm mounting it to /media/backups.

Once executed, everything on that drive will be readable in /media/backups and anything I write to that location will end up on this drive.

If I formatted the volume as ext3, then I would replace 'vfat' with 'ext3'.  For NTFS, use 'ntfs-3g'.  If this were a real-world case, I'd probably format this drive to the same filesystem as the drive I'm backing up (ext3 in my case).

That's the hard part. :)  Once you have the drive mounted, this tutorial explains rsync:

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)


Oh, I forgot to add: When you're done and would like to disconnect this drive from your server, issue the command:

```
 sudo umount /media/backups
```
 
Of course, replace '/media/backups' with whatever mount point you've used.  Make sure no users are sitting on that directory or doing any read/write operations there, or else the unmount will fail.

---

### Post by mjfroggy on 2009-02-12
thanks scaredpoet for the information :-)
I am going to try this out tomarrow and am sure I may have some bumps in the roud or additional questions :-)

but thanks

---

### Post by unixeducation on 2009-02-12
You may also wish to investigate using rdiff-backup: [http://www.nongnu.org/rdiff-backup/](http://www.nongnu.org/rdiff-backup/)

It lets you do incremental backups from and to any combination of local and remote host locations. I use it for backing up several VPS systems to a central backup server, along with backing up my laptop daily.

---

### Post by falconed7 on 2009-02-12
> **mjfroggy said:**
> Is their any good tutorials anyone can point me to inorder to hookup/setup the hdd and also then setup rsync to work via a cron to backup to the external hdd that will be plugged into the server?

Thanks

I do this myself I just run this command every night at 12am:
```
rsync -av --delete /media/store /media/usbdrive/serverbackup
```

This guide is the best I've come across:
[http://www.marksanborn.net/howto/use-rsync-for-daily-weekly-and-full-monthly-backups/](http://www.marksanborn.net/howto/use-rsync-for-daily-weekly-and-full-monthly-backups/)

---

