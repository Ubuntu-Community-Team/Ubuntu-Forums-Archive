---
title: "Create Disk Image for 12.04 Server"
date: 2012-06-25
forum: Server Platforms
---

### Post by dbrooke on 2012-06-25
O.K., I did a thorough search for this on this forum and on google and could not come up with anything that fits regarding Ubuntu's latest server characteristics (mostly ext4 fs type).

I also scanned the official [12.04 server documentation]("http://help.ubuntu.com/12.04/serverguide/") and couldn't find much there.

So, here is the simple question:
**What is the best practice for creating a full disk image for a Ubuntu 12.04 Server?**

*More Verbose:*

I tried following:
[https://help.ubuntu.com/community/DriveImaging]("https://help.ubuntu.com/community/DriveImaging")

However, the problem is that the recommended partimage does not support the default fs type (ext4) which appears to be the default fs type installed for Ubuntu 12.04. So, though partimage does have some great features, like not including free space when copying, it does not appear to be the best option.

**Other Options:**
'dd' is also mentioned, but I am more used to the vmware methods of making a snapshot, and dd appears complicated. If dd *is* the recommended method, I'd sure like to get some help, and even maybe we can come up with a community HowTo to use it.

[Clonezilla]("http://www.clonezilla.org/") is another resource, but its limitations are not that enticing in my opinion. In other words, you are required to have a drive of equal or greater size of the partition you are making an image of (to store your image). I don't actually have that resource at the moment. 

At the end of the 12.04 [docs]("https://help.ubuntu.com/12.04/serverguide/backup-shellscripts.html") regarding backups, it mentions:
[I]
"rsnapshot: a file system snapshot utility used to create copies of an entire file system."[/I]

This looks to be a perl based rsync solution, so I'm not sure it actually creates a bit by bit snapshot as defined. The project website is [here]("http://www.rsnapshot.org/"). It would be interesting for those who know more about this to comment.

**Summary:**
Ideally, I'd like to find a solution that is spelled out clearly, as I'm sure many of us Ubuntu Server operators would as well. Maybe it's already out there, and I am over-thinking this. Hopefully someone can point that out if that is the case. However, using VMWare on my mac, I just press a 'Create Snapshot' button and it just works. I don't expect that, but it would be nice to have something clear to work with for creating snapshots.

Donovan

---

### Post by Gompa on 2012-06-25
i don't know but  you could try [clonezilla]("http://clonezilla.org/")

---

### Post by PCNetSpec on 2012-06-25
You might want to look into rsync

---

### Post by darkod on 2012-06-25
If you are looking for offline backup, you can also consider FS Archiver.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

If I am not mistaken clonezilla is also offline, you need to boot with the clonezilla cd. But with clonezilla the restore partition has to be same or greater than the source partition regardless of the amount of data actually on it.

FS Archiver can restore on a smaller partition than the original as long as the data fits.

It is included on the System Rescue CD, so you can boot the server with it and run it.

After the restore I think you will need to edit /etc/fstab to change the UUID of the new partition, and reinstall grub2 on the MBR of the disk.

---

### Post by dbrooke on 2012-06-25
> **Gompa said:**
> i don't know but  you could try [clonezilla]("http://clonezilla.org/")

Gompa, please read my original through.

Thx,
Donovan

---

### Post by dbrooke on 2012-06-25
> **PCNetSpec said:**
> You might want to look into rsync

I love rsync, but I don't believe it's suited for snapshot creation. It's better at backups and backing up 'differences'.

Donovan

---

### Post by dbrooke on 2012-06-25
> **darkod said:**
> If you are looking for offline backup, you can also consider FS Archiver.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

If I am not mistaken clonezilla is also offline, you need to boot with the clonezilla cd. But with clonezilla the restore partition has to be same or greater than the source partition regardless of the amount of data actually on it.

FS Archiver can restore on a smaller partition than the original as long as the data fits.

It is included on the System Rescue CD, so you can boot the server with it and run it.

After the restore I think you will need to edit /etc/fstab to change the UUID of the new partition, and reinstall grub2 on the MBR of the disk.

Darkod, thanks for pointing out FS Archiver. It's not what I had in mind (It doesn't create an 'image' in the traditional sense), but it looks like a possible solution for my needs anyway.

Anyway, ..would like to hear more comments/ideas if they are out there.

Thx all!,

Donovan

---

### Post by CharlesA on 2012-06-25
> **dbrooke said:**
> Gompa, please read my original through.

Thx,
Donovan

I used to use PING (PartImage is not Ghost), but hit a brick wall with it when I wanted to clone an ext4 partition. I've used Clonezilla every since.

They have very good documentation too.

However, if you are looking to take snapshots of the drive, why not just use LVM snapshots?

[http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html)

---

### Post by Gompa on 2012-06-25
oh srry i some how totally missed that

---

### Post by dbrooke on 2012-06-25
> **CharlesA said:**
> -snip-I've used Clonezilla every since.

I'd try it out, but I just don't have the backup space right now to utilize for this particular backup.

> **CharlesA said:**
> 

However, if you are looking to take snapshots of the drive, why not just use LVM snapshots?

[http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html](http://tldp.org/HOWTO/LVM-HOWTO/snapshotintro.html)

I ran into this just before I saw your post.. was looking at:
[http://www.sysresccd.org/Sysresccd-LVM-EN-Making-consistent-backups-with-LVM#Creation_of_an_LVM_snapshot]("http://www.sysresccd.org/Sysresccd-LVM-EN-Making-consistent-backups-with-LVM#Creation_of_an_LVM_snapshot")

Alright, I'm going to try this but I'm not happy about it. ;-)

It appears I have to do a few things to make this work.

First, here is a look at my drives:
```
root@edc-webhost1:/var/www# fsarchiver probe simple
[======DISK======] [=============NAME==============] [====SIZE====] [MAJ] [MIN]
[sda             ] [ST3500630AS                    ] [   465.76 GB] [  8] [  0]
[sr0             ] [DVD-RW GSA-H60L                ] [   378.96 MB] [ 11] [  0]

[=====DEVICE=====] [==FILESYS==] [======LABEL======] [====SIZE====] [MAJ] [MIN] 
[sda1            ] [ext2       ] [<unknown>        ] [   243.00 MB] [  8] [  1] 
[sda5            ] [LVM2_member] [<unknown>        ] [   465.52 GB] [  8] [  5] 
[dm-0            ] [ext4       ] [<unknown>        ] [   463.04 GB] [252] [  0] 
[dm-1            ] [swap       ] [<unknown>        ] [     2.43 GB] [252] [  1]
```

As shown, I chose the LVM option when setting up Server 12.04 and told it to make 1 partition that spanned the entire drive.

Of what I'm reading, this is probably not the best thing to do when utilizing LVM, because it's easier to size up, than size down.

So, why do I have to size down? Well, If I'm going to make an LVM snapshot, I will need enough room in my Volume Group to create the snapshot "logical-volume". 

For those that care to understand.. ;-).. some of the benefits of creating an LVM snapshot are:
1. You are creating a frozen data set that can easily be reverted back to. (this may be pertinent for pre-upgrade integrity or pre-application install integrity, especially in a production situation).

2. Once a snapshot is created, you don't have to stop the server to get an uninterrupted backup of the snapshot volume (using rsync, fsarchiver, etc..)


So, to elaborate further, I guess the basic steps are:
1. size down my single logical volume to make room for the new "snapshot" volume.

2. Create the LVM snapshot.. below contains some info that I guess I'll have to use to create it... looks like I could create the swap partition snapshot as well???

```
  --- Logical volume ---
  LV Name                /dev/edc-webhost1/root
  VG Name                edc-webhost1
  LV UUID                1RvKOS-f3rw-8nw8-eU6H-zOPn-tEeb-CKa6pH
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                463.04 GiB
  Current LE             118538
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/edc-webhost1/swap_1
  VG Name                edc-webhost1
  LV UUID                sTV2j4-1ScO-2eFY-rKlA-U94j-vTg4-JXeHMe
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                2.43 GiB
  Current LE             623
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

```

3. Mount the new snapshot, in order to attain a clean backup.

4. Make a backup using fsarchiver or rsync to my mounted external firewire drive.

Ultimately, I may just use the script they have listed at:[http://www.sysresccd.org/Sysresccd-LVM-EN-Making-consistent-backups-with-LVM#Creation_of_an_LVM_snapshot]("http://www.sysresccd.org/Sysresccd-LVM-EN-Making-consistent-backups-with-LVM#Creation_of_an_LVM_snapshot") ;-)

Wish me luck!

Donovan

---

### Post by CharlesA on 2012-06-25
Wow that is a lot of stuff to do. Hope it works out for you!

---

### Post by dbrooke on 2012-06-26
O.K., this actually went over pretty well.

I have both a successful LVM snapshot running of my root Logical-Volume and a successful dated backup of that snapshot to my external fw drive, using fsarchiver. More so, I have a bash script now, saved in root, that I just need to run to make all this happen automagically... (could easily run this through crontab for a nightly backup of my root drive I guess).

I will work on a "best practices" howto when I have a chance.

I still have at least one question...

1.) I've opted to keep my unmounted snapshot logical volume alive.. at least until I run the next script. I have heard there is a performance overhead to this idea.. but does anyone know to what extent? Is it not a good idea to keep a snapshot alive for a long period of time?

Thanks.
Donovan

---

### Post by CharlesA on 2012-06-26
I am not sure what you mean by leaving an unmounted drive "active." I've got my backup drive attached to my server but unmounted and haven't noticed any problems with performance.

However, the drive I am using isn't hosting LVM snapshots, so I don't know if that would cause issues or not.

---

### Post by LHammonds on 2012-06-26
I believe he is asking about "always" having a snapshot sitting around.

I would recommend against it.  If you have made a backup and it is safely stored elsewhere, there is no need to keep the snapshot there.  I would include in your backup script to delete the snapshot immediately after fsarchiver finished (with a verified success...meaning fsarchiver did not give any error message and the file you were creating actually exists and is greater than 0 in size)

If you leave a snapshot in place throughout the day, the I/O takes a double-hit each time a change is made to the system.  However, if it is the root LV only and does not contain variable data such as /var, /home, /srv and /usr, it might be OK if there are no or very few writes to the volume.  But I would still prefer to stick to a standard of 1) take snapshot, 2) perform backup, 3) remove snapshot...no matter which LV you are working with.

That's my 2 cents.

I plan to include a backup and restore script in the server "how-to" thread I created today.  I always roll my eyes when I see people showing how to backup a system without the all important and usually VERY TIME-SENSITIVE restore procedure.  Typically, you can take your time setting up a backup process and when to do the backups and what not...but when you face an event where you need to restore, there is usually a fire under your chair to get it done asap...and this is most-definitely NOT the time to figure out how a restore is supposed to work...in theory.  Your restore process needs to be completed, documented and TESTED before you can claim that you have a backup process in place.

LHammonds

---

### Post by CharlesA on 2012-06-26
> **LHammonds said:**
> 
I plan to include a backup and restore script in the server "how-to" thread I created today.  I always roll my eyes when I see people showing how to backup a system without the all important and usually VERY TIME-SENSITIVE restore procedure.  Typically, you can take your time setting up a backup process and when to do the backups and what not...but when you face an event where you need to restore, there is usually a fire under your chair to get it done asap...and this is most-definitely NOT the time to figure out how a restore is supposed to work...in theory.  Your restore process needs to be completed, documented and TESTED before you can claim that you have a backup process in place.

Oh yeah.. that's a good idea tbh. I test my backups every so often, but it does take a long while to verify everything is able to be copied ok, depending on how much data needs to be verified, of course. Of course, I use rsync to do my backups, so I can be sure the backup is the same as the source.

I wonder if doing a dry-run from backup --> source would be an easier way to verify everything is ok. Probably not, but I'm not sure..

---

### Post by LHammonds on 2012-06-27
> **CharlesA said:**
> I test my backups every so often, but it does take a long while to verify everything is able to be copied ok, depending on how much data needs to be verified, of course
There is a difference between a verified backup, a verified restore process and a verified restore.

Most archiving programs include the ability (like rsync and fsarchive) to verify that what it backed up is the same as the source or by using checksums (e.g. verified backup).  They also tend to do this with each and EVERY backup.

A verified restore process requires a document that shows how to take a backup and restore it.  This document must be kept up-to-date with current backup procedures and verified to work correctly any time there is a change in the backup process.

A verified restore is the done manually by an administrator every once in a while (hopefully) to make sure that the backups are actually good backups and that the documented restore process works.  This is basically a test of the restore process and the backup process as a whole.  It should be the only thing that gives end-users / managers / administrative types a warm fuzzy feeling that the servers are in good hands.

> **CharlesA said:**
> I wonder if doing a dry-run from backup --> source would be an easier way to verify everything is ok. Probably not, but I'm not sure..
It completely depends on your environment and backup process.

If you are wanting to test the restore of individual files, you could do so directly to the original by renaming an unimportant / unused file and see if you can restore it.

If you need to test the restore of the entire operating system, it typically is never a good idea to test it by restoring to your production server!  Imagine the chaos if it fails.  Also, if the source is a virtual machine, the test restore could simply be to a new virtual machine (with the NIC disabled for obvious reasons).

If you have a bare-metal server, you could try the restore on a similar physical machine (I always budget for test servers for critical systems in the event the primary server fails, I could always restore to the test server and hop along until the primary was fixed/replaced).  You might even be able to restore a bare-metal server into a virtual machine...but I have not done this so it might not be a wise idea due to device drivers or absence of physical parts like a fax board.

LHammonds

---

### Post by CharlesA on 2012-06-27
Thanks for that. That really helps! The only thing I have backed up is my data cuz the OS can be reinstalled easily. ;-)

I've cut a ton of stuff out of the backup by excluding the steam folder from the daily backup, so it should be fairly easy to just restore the backup to a different directory via rsync in order to test it.

In my case, restoring from backups is easy - I just need mount the backup drive, then run rsync with the source and destination swapped.

---

### Post by LHammonds on 2012-06-27
> **CharlesA said:**
> Thanks for that.You're welcome.

> **CharlesA said:**
> In my case, restoring from backups is easy - I just need mount the backup drive, then run rsync with the source and destination swapped.
It is only easy if you are familiar with the process and know it works.

It can be a real nightmare if your server fails to boot and you are caught wondering:
1) How can I restore a backup?
2) How can I access the backup files to restore them on a server that won't boot?
3) How do I restore to the right locations if booted from a LiveCD?
4) Are my backup files even accessible when I boot from a LiveCD?
5) etc.

---

### Post by CharlesA on 2012-06-27
> **LHammonds said:**
> 
It can be a real nightmare if your server fails to boot and you are caught wondering:
1) How can I restore a backup?
2) How can I access the backup files to restore them on a server that won't boot?
3) How do I restore to the right locations if booted from a LiveCD?
4) Are my backup files even accessible when I boot from a LiveCD?
5) etc.

I can see how that can be a royal pain. In my case, I'd be "ok" as long as I could mount the backup drive. The only problem I would run into would be that the RAID driver needs to be compiled and installed for it to see the RAID array, but that can be done from a livecd. ;)

What's the saying, plan for the worst, but expect the best?

Good documentation goes a long, long way. :)

---

### Post by dbrooke on 2012-06-27
> **LHammonds said:**
> I believe he is asking about "always" having a snapshot sitting around.

I would recommend against it.  If you have made a backup and it is safely stored elsewhere, there is no need to keep the snapshot there.  I would include in your backup script to delete the snapshot immediately after fsarchiver finished (with a verified success...meaning fsarchiver did not give any error message and the file you were creating actually exists and is greater than 0 in size)

If you leave a snapshot in place throughout the day, the I/O takes a double-hit each time a change is made to the system.  However, if it is the root LV only and does not contain variable data such as /var, /home, /srv and /usr, it might be OK if there are no or very few writes to the volume.  But I would still prefer to stick to a standard of 1) take snapshot, 2) perform backup, 3) remove snapshot...no matter which LV you are working with.

That's my 2 cents.

I plan to include a backup and restore script in the server "how-to" thread I created today.  I always roll my eyes when I see people showing how to backup a system without the all important and usually VERY TIME-SENSITIVE restore procedure.  Typically, you can take your time setting up a backup process and when to do the backups and what not...but when you face an event where you need to restore, there is usually a fire under your chair to get it done asap...and this is most-definitely NOT the time to figure out how a restore is supposed to work...in theory.  Your restore process needs to be completed, documented and TESTED before you can claim that you have a backup process in place.

LHammonds


Good points.

I don't yet have a complete backup scheme.

When I started down this road, for imaging, I wanted to get as close to a "VMWare Fusion-like" Snapshot process that I could... where the process of both imaging and restoring the entire server was a one-click type of thing, and the snapshots could be kept as long as needed. 

Of course, a snapshot does not a backup make... I'm not saying that.. however, it's a nice feature as a part of a backup scheme, or as a part of preparation for upgrades or significant changes to a server.

LVM 'snapshots' don't really have all the same purposes as vmware 'snapshots' or iso images, so I guess I need to be careful on how I use the term 'snapshot'. however, they all have many of the same characteristics.

I am going to continue to look at 'dd' (and maybe clonezilla) to see if I can find a better solution, but at least for now, I have a way to be safe before significant changes to the server and a way to attain a good backup of the volumes.

Anyway, I think hypervizor's have an advantage for easy snapshots... maybe Ubuntu's hypervizor features are the next thing to learn I guess.

Thanks for the comments!
Donovan

---

