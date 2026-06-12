---
title: "LVM to RAID1"
date: 2015-08-22
forum: Server Platforms
---

### Post by Marc-NJ on 2015-08-22
Does anyone have any good pointers or instructions about how I can go from an LVM set-up to a RAID1 set-up on my Ubuntu 12.04 server?  I don't mind if the server is offline for a bit during the process.  Right now, there's a 2 TB drive running the Ubuntu server (but it's not taking advantage of all the space on the 2 TB drive, only about 500 GB for Ubuntu and maybe another 100 GB or so for a separate Win7 partition), and a blank 750 GB drive.  

Also, if anyone has any suggestions on how I might be able to set up some sort of email notification so that if the RAID array begins to fail, I'd get notified about it, that'd be great also!

Thanks!

---

### Post by TheFu on 2015-08-22
To be notified of many system events, setup an MTA like postfix and set it up to forward to your real email address. On a home system, that last part is harder than on an internet server with a static IP because most ISPs block outbound email for non-authenticated users and force all email to go through their email gateway. That helps keep the spam down for the ISP subnet, which is a good thing.

mdadm - the Linux software RAID took - will send degraded array emails automatically to root@localhost. Just forward that account to your real account somewhere using the /etc/aliases file - be certain to run newaliases anytime the file is changed.  Using something like logwatch would be smart too.  Seems you could use some more guidance on running servers: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

To go from LVM to RAID1 isn't enough data for us to understand exactly what you want. Can you please be more exact in what you want.  This is where the flexibility of Linux can provide 20 different results for LVM --> RAID1. I wouldn't want to assume a solution, since using RAID1 across everything isn't always the smartest idea. Plus you can run LVM over RAID or you can run LVM under RAID ... we need more info to help.

But you should expect to backup everything, change the layout to whatever you want, then restore it and fix the disk subsystem depending on how it is laid out.

Anyway, hope this helps.

---

### Post by Marc-NJ on 2015-08-26
> **TheFu said:**
> To be notified of many system events, setup an MTA like postfix and set it up to forward to your real email address. On a home system, that last part is harder than on an internet server with a static IP because most ISPs block outbound email for non-authenticated users and force all email to go through their email gateway. That helps keep the spam down for the ISP subnet, which is a good thing.

mdadm - the Linux software RAID took - will send degraded array emails automatically to root@localhost. Just forward that account to your real account somewhere using the /etc/aliases file - be certain to run newaliases anytime the file is changed.  Using something like logwatch would be smart too.  Seems you could use some more guidance on running servers: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

So I can use the /etc/aliases file and simply set up a real email address in that file and it will forward to that address with no additional configuration on my server necessary?  Is there any place you can point me for guidance on configuring the /etc/aliases file?  Also, not sure if it makes a difference or not, but I have Webmin set up on my server, so don't know if that will help this process or help me with email notifications at all.  Also, just an FYI - the server I'm running is actually on a home broadband connection with a dynamic IP (and configured using dynamic DNS), but I believe my home broadband connection does allow port 25 traffic if I enabled it via their web interface.

> **TheFu said:**
> To go from LVM to RAID1 isn't enough data for us to understand exactly what you want. Can you please be more exact in what you want.  This is where the flexibility of Linux can provide 20 different results for LVM --> RAID1. I wouldn't want to assume a solution, since using RAID1 across everything isn't always the smartest idea. Plus you can run LVM over RAID or you can run LVM under RAID ... we need more info to help.

But you should expect to backup everything, change the layout to whatever you want, then restore it and fix the disk subsystem depending on how it is laid out.

Anyway, hope this helps.

Basically, I had previously set up the Ubuntu 12.04 LTS server with LVM so that it could span across two hard disks and take full advantage of all the space across those two hard drives (around 1.25 GB give or take).  This was well before I planned to do anything with it that could be considered mission-critical.  

Recently there were definitely some disk issues that caused me to have to run fsck on it, although it seems to have recovered nicely, but this led me to believe that one of the two disks (or possibly both) was beginning to fail.  So I went out and bought a 2 TB drive, and then shrunk the Ubuntu 12.04 LTS server down to only one of those two drives using a LiveCD and system-config-lvm.  I was then able to use Clonezilla to move the server to the 2 TB drive, although I didn't expand it afterwards to take advantage of all the free disk space on the 2 TB drive since I didn't want it to get bigger than the 750 GB drive (which I could hopefully use to do a RAID1 set-up).  

So right now, the server is running under LVM on a 2 TB drive, but only using maybe 100-200 GB of space out of a total of 500 GB available, and there is also another 100 GB or so on that 2 TB drive that is being used by a Win7 partition (which actually doesn't boot any longer - probably something I did when shrinking and cloning it, but it's unimportant so I don't care about the Win7 partition).  

And what I'd like to do is get it somehow set up (in the easiest and least-downtime way possible) so that it can work in a RAID1 (presumably software RAID1 - mdadm?) environment so that if something does happen to either drive in the future, I can replace it with another drive without losing the entire server potentially.  If there is any way to do this via cloning or some other manner so that I can keep the exact same configuration I have now with the server and not have to make changes, reinstall the OS, etc., that'd be the best I think, but am not sure how to go about doing that exactly, especially on an Ubuntu server.

I also do have backups (although, and this is definitely a separate topic - I am not quite sure what the best way is to take full system-wide backups of Ubuntu server - am using CrashPlan right now to do cloud backups of important data, but would love to find some way to actually take a bare metal backup every so often without having to bring the server down and manually do it).  I had posted about that here: [http://ubuntuforums.org/showthread.php?t=2283092](http://ubuntuforums.org/showthread.php?t=2283092) - I would have thought there was some software program or easy GUI way of doing this, but so far haven't come across one (similar to how Norton Ghost or other more recent applications work in Windows, etc.)

By the way, thanks very much for your help (and anyone else's that chimes in) thus far!

---

### Post by TheFu on 2015-08-26
No. The aliases is NOT all you need. You need to setup an MTA like postfix too. **man aliases** - manpages for every command and almost every config file are already on the system.  Most real email servers will block DHCP subnets from directly sending email. I do. You'll probably need to setup your MTA to relay through the ISP email gateway with authentication, for this to work.

I don't use webmin (and won't). It is just another attack vector, IMHO. Don't know if it interferes with anything normal or not.

On servers, I don't use any GUI tools.  Running a GUI tool on a box 2-5K away doesn't work. Learn the shell method, use it.

As far as the OS is concerned, provided the files appear in the expected places, the OS doesn't care. You can do **anything** you like.

There is a trivial way to make a clone of any storage device you like - dd. It has been around 40+ yrs. There are newer, smarter versions and different takes on it - ddrescue, partimage, clonezilla, fsarchiver ... probably others. All of these have 1 issue - the OS cannot be running when you make the image - basically booting off alternate media is required to ensure a safe image.

I don't use imaging for backup purposes for many reasons. Downtime is the primary reason.

LVM snapshots is probably what you want. [http://www.tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html](http://www.tldp.org/HOWTO/LVM-HOWTO/snapshots_backup.html)
ZERO downtime.  I don't know of any GUI for this.  That isn't the Unix way. Don't fight it. Servers don't have a GUI - learn it, know it, love it. Plus at 3am, a GUI doesn't help you make nightly automatic backups.

So - it seems like you might appreciate a nice, free, power-user book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by Marc-NJ on 2015-08-26
Thanks for the quick reply!  Honestly, I wish I had more time to learn Ubuntu more fully (including the shell method), but it's just not something I can dedicate a significant amount of time to presently.  

The Ubuntu server exists for me to run two applications I need, and that's basically it.  I just want to implement RAID1 and better backup to be more fully protected and avoid downtime.  I can figure out the backup question another time, but can you (or anyone else that wants to chime in) offer any assistance in just moving from the single-disk LVM setup I have right now to a RAID1 setup quickly and easily without having to rebuild my OS, etc.  Thanks very much!

---

### Post by cariboo on 2015-08-26
I'd suggest setting up a backup strategy before even thinking about raid. With RAID 1, if there are any corruption problems raid will not help you out. I used a fakeraid setup on my server, and ran into more corruption problems than I expected, I've since reverted to jbod with a good backup strategy.

---

### Post by Marc-NJ on 2015-08-26
> **cariboo said:**
> I'd suggest setting up a backup strategy before even thinking about raid. With RAID 1, if there are any corruption problems raid will not help you out. I used a fakeraid setup on my server, and ran into more corruption problems than I expected, I've since reverted to jbod with a good backup strategy.

I'd definitely be interested to hear what backup strategy you have in place (perhaps it could help me), but I actually do have a backup solution in place currently (CrashPlan).  It's not the greatest in that if my server went kaput I'd lose most of my configuration, but all my data would be safe and intact.  Given that, I do want to get RAID1 set up on the server so that, if one of the drives starts going, I can easily replace it without any real downtime or loss.  Also, my understanding is that fakeRAID is somewhat different than mdadm software RAID, right?  The system I have doesn't have any sort of fakeRAID capabilities, so that's why I want to use mdadm software RAID.  

Thanks!

---

### Post by darkod on 2015-08-29
So, you plan to create mdadm raid1 from the 750GB and 2 TB disks? That is possible, but the general recommendation is to use same size disks. The benefit of mdadm is that in theory you can use the rest of the 2TB disk as separate partition. This is because mdadm arrays are usually created from partitions, not from the whole disk devices. With fakeraid or HW raid you would lose the rest of the 2TB disk.

If you insist on continuing with these disks, do you need help with the commands? Do you need to minimize downtime?

You have two options:
1. Boot the server with the desktop live CD and work from there. That means downtime until you finish the whole procedure of configuration and data copying.

2. Make a partition on the 750GB disk and use it to create raid1 array with one member missing (you can do this in mdadm). That means your server is still running from the 2TB disk. Once you have the array running, you rsync the data from the 2TB, which still keeps your server online. When that is done, you boot into live mode and do another rsync which will finish fast because it will copy only the info missing from the last rsync. Adjust grub and /etc/fstab as needed, and the server will boot from the array. After you are sure it is working, you repartition the 2TB disk if needed and add one 750GB partition to the array. It will sync it automatically in a raid1 mirror.

That is it more or less...

---

### Post by Marc-NJ on 2015-08-30
> **darkod said:**
> So, you plan to create mdadm raid1 from the 750GB and 2 TB disks? That is possible, but the general recommendation is to use same size disks. The benefit of mdadm is that in theory you can use the rest of the 2TB disk as separate partition. This is because mdadm arrays are usually created from partitions, not from the whole disk devices. With fakeraid or HW raid you would lose the rest of the 2TB disk.

If you insist on continuing with these disks, do you need help with the commands? Do you need to minimize downtime?

You have two options:
1. Boot the server with the desktop live CD and work from there. That means downtime until you finish the whole procedure of configuration and data copying.

2. Make a partition on the 750GB disk and use it to create raid1 array with one member missing (you can do this in mdadm). That means your server is still running from the 2TB disk. Once you have the array running, you rsync the data from the 2TB, which still keeps your server online. When that is done, you boot into live mode and do another rsync which will finish fast because it will copy only the info missing from the last rsync. Adjust grub and /etc/fstab as needed, and the server will boot from the array. After you are sure it is working, you repartition the 2TB disk if needed and add one 750GB partition to the array. It will sync it automatically in a raid1 mirror.

That is it more or less...

Thanks so much for the response!  I think I'd like to try and stick with the two disks I have right now, especially since everything is set up and running (and both disks are installed already), plus I can then get some additional usable space on the 2 TB one after I set up the mdadm partitions (based on what you said - I think).

As far as procedure - I'm OK with some downtime as long as don't risk the data and I can control the process.  It seems like option 2 would have the least downtime but seems somewhat complex.  I'm OK with doing option 1 and having the server down and doing everything on the LiveCD (assuming that the server isn't down for days...lol).  Any chance you might be able to offer some assistance on the procedure?  Thanks again very much!

---

### Post by darkod on 2015-09-04
Sorry, I didn't see you replied. I'm at work now but over this weekend I will probably have time to help you out, no problem.

---

### Post by darkod on 2015-09-04
To start it off, please post the output of the following commands so that we can see which disks and partitions are used, and how.
```
df -h
sudo parted -l (that's small L)
```

Please post the results in CODE tags so that they are easy to read.

After that we can continue with the raid1 preparation.

---

### Post by Marc-NJ on 2015-09-04
> **darkod said:**
> Sorry, I didn't see you replied. I'm at work now but over this weekend I will probably have time to help you out, no problem.

Great - thanks so much!

---

### Post by Marc-NJ on 2015-09-04
> **darkod said:**
> To start it off, please post the output of the following commands so that we can see which disks and partitions are used, and how.
```
df -h
sudo parted -l (that's small L)
```

Please post the results in CODE tags so that they are easy to read.

After that we can continue with the raid1 preparation.

```

root@<SERVER>:~# df -h
Filesystem           Size  Used Avail Use% Mounted on
/dev/mapper/VG1-LV1  562G  227G  307G  43% /
udev                 3.9G   12K  3.9G   1% /dev
tmpfs                790M  704K  789M   1% /run
none                 5.0M  4.0K  5.0M   1% /run/lock
none                 3.9G  4.0K  3.9G   1% /run/shm
root@<SERVER>:~# parted -l
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  94.4GB  94.4GB  primary   ntfs
 2      94.4GB  722GB   627GB   extended
 5      94.4GB  722GB   627GB   logical                lvm
 3      722GB   732GB   10.5GB  primary   ntfs         boot
 4      732GB   750GB   17.9GB  primary   ntfs




Model: ATA ST3750525AS (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/VG1-LV2: 15.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  15.0GB  15.0GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/VG1-LV1: 612GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  612GB  612GB  ext4

```

Thanks again!

---

### Post by darkod on 2015-09-04
I forgot you also have LVM. While I'm reading this, give me also:
```
sudo pvdisplay
```

To show which partitions are you using in the LVM. It would also help if you give more info about the setup, the facts that you know.

---

### Post by Marc-NJ on 2015-09-04
> **darkod said:**
> I forgot you also have LVM. While I'm reading this, give me also:
```
sudo pvdisplay
```

To show which partitions are you using in the LVM. It would also help if you give more info about the setup, the facts that you know.

```

root@<SERVER>:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               VG1
  PV Size               584.29 GiB / not usable 1.00 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              149577
  Free PE               0
  Allocated PE          149577
  PV UUID               Tdcl7J-HYGs-4mZe-tMsG-bWgT-SrTQ-6OKxFe

```

And I'm happy to give you whatever information you need.  Basically, it was initially two drives (I believe a 750 GB drive and a 500 GB drive) that were set up using LVM so that I could take advantage of all the space on both drives.  Then, somehow something happened (I don't recall exactly what it was, but I had to run fsck I think) and the server came back up, although there were a few files in lost+found (but weirdly enough, they were from a few weeks prior to whatever it was that brought down the server this time around).  So, I decided it would be best to move the entire server to a new 2TB drive (in case one of those two initial drives was failing), but I apparently couldn't do that with clonezilla since they were spanned over two drives via LVM.  So I used system-config-lvm (I think) via a LiveCD to shrink everything to one drive, and then cloned that drive to the 2 TB drive which is where I'm at right now.  I removed the 500 GB drive, but left the 750 GB one in there, and would like to use that drive and the 2 TB drive to get a RAID1 set-up going (although if there's any way to check and make sure the 750 GB drive is in good shape first, that'd be great as well).  And then whatever space is left over on the 2 TB drive to be able to use as just extra space (for storing nothing important really) would also be great.  Hopefully that gives you a little idea of what the set-up is, but I'm happy to provide anything else you need, and definitely appreciate the help!

Oh, and one other thing - I believe there is also a Win7 install floating around on the drive too, but I couldn't boot to it after cloning to the 2 TB drive, and honestly we can do away with it at this point entirely.

---

### Post by darkod on 2015-09-04
OK, so the whole data is currently on the LVM on the 2TB disk (/dev/sda), more precisely on partition sda5 because that's the only one belonging to the LVM. And you are happy to lose the windows partitions, including the OS and all data that you might have on the ntfs partitions?

That makes things easier...

Another question. Do you want to keep using LVM or you will use this opportunity and drop it, and use only mdadm raid1? LVM will make sense only if you think you will need more space in close future, and that you will expand with new disks (space).

---

### Post by Marc-NJ on 2015-09-04
> **darkod said:**
> OK, so the whole data is currently on the LVM on the 2TB disk (/dev/sda), more precisely on partition sda5 because that's the only one belonging to the LVM. And you are happy to lose the windows partitions, including the OS and all data that you might have on the ntfs partitions?

That makes things easier...

Another question. Do you want to keep using LVM or you will use this opportunity and drop it, and use only mdadm raid1? LVM will make sense only if you think you will need more space in close future, and that you will expand with new disks (space).

Yup - I can definitely kill all the windows partitions - it was just a basic Win7 install (prior to my wanting to use this system solely as a server) and there's no real data on there so I can kill it entirely.

If all LVM will be good for is adding more space in the future (and I don't plan on doing that), then I guess mdadm RAID1 makes the most sense, right?  I plan to only use this server (12.04 Ubuntu) for the next few months before fully moving to an already-built mdadm RAID1 14.04 server with 4 TB drives in RAID1 and an extra 6TB drive (although I don't know what I'm going to use the extra 6TB for yet...maybe some sort of backups).

Thanks!

---

### Post by darkod on 2015-09-04
Well, for a few months it might not be worth all this work, but at least you will be learning... :)

We need to start with the 750GB disk, and make the partitions... First important thing to know when planning partitions for mdadm is that all md devices are assembled from separate partitions. So you need to plan your disks accordingly. HW raid creates the raid devices that you can later partition with the OS. mdadm doesn't work like that, you don't partition /dev/mdX later.

I see you have 15GB swap in the LVM, so if you want the same setup, you need one big partition on the 750GB disk and one 15GB partition at the end.

Lets see what you have on the 750GB now:
```
sudo parted /dev/sdb unit MiB print
```

That will print the partition table of sdb using MiB (MB as in 1024*1024, not 1000*1000).

---

### Post by Marc-NJ on 2015-09-04
> **darkod said:**
> Well, for a few months it might not be worth all this work, but at least you will be learning... :)

We need to start with the 750GB disk, and make the partitions... First important thing to know when planning partitions for mdadm is that all md devices are assembled from separate partitions. So you need to plan your disks accordingly. HW raid creates the raid devices that you can later partition with the OS. mdadm doesn't work like that, you don't partition /dev/mdX later.

I see you have 15GB swap in the LVM, so if you want the same setup, you need one big partition on the 750GB disk and one 15GB partition at the end.

Lets see what you have on the 750GB now:
```
sudo parted /dev/sdb unit MiB print
```

That will print the partition table of sdb using MiB (MB as in 1024*1024, not 1000*1000).

I apologize that it's only for a few months - it's just that the stuff on the server has become relatively important to my business, so I don't want to run the risk of having it crash and not having some way to get it back up and running quickly.  I do have CrashPlan backup for the critical data, but if a HD goes and it's in RAID1, at least it will presumably keep working and I can pop a new HD in there and not have to risk losing data or having downtime.  I do plan to ultimately transition to a new server that is much better overall.  But I do appreciate your help immensely!! :) And I will definitely be able to pick up on how it's done for the future, so thanks for that as well (and thanks for also explaining stuff as we go along - it's great for me to learn, and I imagine others will appreciate it upon reading this thread as well)!

Here's the output you wanted:

```

root@<SERVER>:~# parted /dev/sdb unit MiB print
Model: ATA ST3750525AS (scsi)
Disk /dev/sdb: 715405MiB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start  End  Size  Type  File system  Flags

```

I know this is totally unrelated, but ultimately I want to also see if I can figure out the following (which typing the above response made me think of):

- how to do a repair to an mdadm RAID1 if one HD does go bad
- how to check on the HD's to see if they potentially could be going bad (via S.M.A.R.T status?)
- and most importantly, how I can set up email alerts to get notified if a drive is potentially going bad or has gone bad in an mdadm RAID1 so I know I need to replace it.

Thanks again!

---

### Post by darkod on 2015-09-05
So, there are no partitions on the disk and it has a total of 715405MiB. I usually leave about 15MiB unused at the end, it helps if in future making a mirror with other disks because depending on manufacturer and model they don't always have the same size up to the last MiB. And a mirror has to have same size partitions.

So lets say we will use 715390MiB from sdb. If you want swap to be 15GiB that's 15360MiB. The rest, or 700030MiB remains for root. Lets partition (I will put comments next to some commands, don't type them too):
```
sudo parted /dev/sdb (opens the parted prompt for sdb)
unit MiB (make the display unit MiB)
print (print current table, always double check you are working with the correct disk)
mkpart primary 1 700030 (create primary partition starting at 1 ending at 700030 MiB, always leave first 1MiB unpartitioned on a HDD)
mkpart primary 700030 715390 (second primary partition)
set 1 raid on (set the raid flag on partition 1)
set 2 raid on (same for 2)
print (take a look at the layout, it should have both partitions with correct sizes)
quit (if you are happy with layout, quit parted)
```

That was the easy part, creating the correct partitions. To continue, boot the server with the desktop liveCD into live mode, and work from there. This is to avoid any files on root being changed while still copying the data. Also note that the live mode does not include mdadm or lvm2 so any time to reboot with the CD you have to "install" them in live mode again.

When you are in live mode lets install the packages and activate the lvm:
```
sudo apt-get install mdadm lvm2
sudo vgchange -ay (that should activate all LVs)
```

Create the raid1 with one member missing (sda1 will be added later to make the full mirror):
```
sudo mdadm --create /dev/md0 --verbose --level=1 --raid-devices=2 missing /dev/sdb1
sudo mdadm --detail /dev/md0 (that should show you details of the created md0 device)
sudo mdadm --create /dev/md1 --verbose --level=1 --raid-devices=2 missing /dev/sdb2
```

That will create md0 for root and md1 for swap. You can check their details with mdadm --detail or with cat /proc/mdstat.

Once you are happy with that, you can format md0 and start copying. You will need temp folders to use as mount points. And then rsync the data from current root to the new root.

```
sudo mkfs.ext4 /dev/md0
sudo mkswap /dev/md1
sudo mkdir /mnt/oldroot
sudo mkdir /mnt/newroot
sudo mount /dev/VG1/LV1 /mnt/oldroot
sudo mount /dev/md0 /mnt/newroot
sudo rsync -avx /mnt/oldroot/ /mnt/newroot/ (the 'v' option will list the files while copying, you can drop this as it will slow it a bit, but it helps knowing it is still copying and not stuck)
sudo umount /mnt/oldroot
```

That should finish with the copy part. In the rsync command make sure you don't forget the slash '/' at the end, they are very important.

After that is done you need to modify the fstab on the new root so that it boots md0 and md1 instead of the lvm from the old disk.
```
sudo nano /mnt/newroot/etc/fstab
```

Make /dev/md0 to be used for / and /dev/md1 for swap, save and close the file.

Put the arrays info in mdadm.conf so that it can reassemble at boot:
```
sudo mdadm --detail --scan >> /mnt/newroot/etc/mdadm/mdadm.conf
```

Now the last part is to chroot into the new root, update grub and reinstall it on the MBRs of both disks, and update the initramfs. This is the tricky part to make it boot correctly:
```
sudo mount --bind /dev /mnt/newroot/dev
sudo mount --bind /dev/pts /mnt/newroot/dev/pts
sudo mount --bind /sys /mnt/newroot/sys
sudo mount --bind /proc /mnt/newroot/proc
sudo chroot /mnt/newroot

update-grub
grub-install /dev/sda /dev/sdb
update-initramfs -u
exit
```

That's it. If you reboot now, with little luck, you should see new grub menu with the new OS on top, then the old OS from the lvm listed (it still detects the other installation too). Try to boot the first entry and see how it goes.

Even if the new system doesn't boot the important thing to remember is that the data is still intact on the LVM. Working from live mode helps that.

I hope this will help. If you want to read more, I adjusted the commands for your specific case, and as a foundation you have this:
[http://ubuntuforums.org/showthread.php?t=1832812](http://ubuntuforums.org/showthread.php?t=1832812)

If all went well, the only thing remaining is to test if it works well from the raid, and then repartition sda too and add it to the array.

---

### Post by Marc-NJ on 2015-09-15
Hey - sorry about not replying sooner!  Unfortunately, I've been sick the past week or so and am having some health issues, so I have to put this somewhat on the back burner - at least for a week or two.  Would it be OK to try and pick this up in a week or two with your assistance?  And thanks again so much for all the help thus far!

---

### Post by darkod on 2015-09-15
Of course. Take your time. Get better...

---

### Post by Marc-NJ on 2015-09-19
> **darkod said:**
> Of course. Take your time. Get better...

Thanks again for everything!

So after all this is done, the system will boot up from the md0/md1 RAID1 configuration (with one portion of the RAID1 missing at this point), and then assuming it all works fine, the next step is to wipe sda (the original 2 TB LVM drive) and let the RAID1 rebuild itself on sda, right?  And that also then takes advantage of filling out all the space in the RAID1 array, right? (i.e. getting rid of those Win7 partitions)


Thanks again for all your help - I'm going to give this a try right now, but just wanted to make sure I understood the end result.

---

### Post by Marc-NJ on 2015-09-19
OK, so I ran through most of the instructions, but am getting stuck towards the end.

For the command:

```

sudo mdadm --detail --scan >> /mnt/newroot/etc/mdadm/mdadm.conf

```

I got this output:

```

-bash: /mnt/newroot/etc/mdadm/mdadm.conf: No such file or directory

```

I then tried creating the /mnt/newroot/etc/mdadm directory and trying again, and got this output:

```

-bash: /mnt/newroot/etc/mdadm/mdadm.conf: Permission denied

```

I then examined the commands given on this page ([http://ubuntuforums.org/showthread.php?t=1832812](http://ubuntuforums.org/showthread.php?t=1832812)) that you had recommended and tried this command:

```

sudo -s
mdadm -Ds >> /mnt/newroot/etc/mdadm/mdadm.conf

```

and it seemed to work.

I then ran through the mount --bind commands and all 4 seemed to work and so did the chroot command.  I next did the update-grub command and got this as output:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
/usr/sbin/grub-probe: error: no such disk.
Found memtest86+ image: /boot/memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done

```



But no idea if that's correct or not.  Finally, I tried this command: 

```

grub-install /dev/sda /dev/sdb

```

and got this as output:

```

More than one install_devices?
Usage: grub-install [OPTION] install_device
Install GRUB on your drive.


  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --modules=MODULES       pre-load specified modules MODULES
  --boot-directory=DIR    install GRUB images under the directory DIR/grub
                          instead of the /boot/grub directory
  --grub-setup=FILE       use FILE as grub-setup
  --grub-mkimage=FILE     use FILE as grub-mkimage
  --grub-mkrelpath=FILE   use FILE as grub-mkrelpath
  --grub-mkdevicemap=FILE use FILE as grub-mkdevicemap
  --grub-probe=FILE       use FILE as grub-probe
  --no-floppy             do not probe any floppy drive
  --allow-floppy          Make the drive also bootable as floppy
                          (default for fdX devices). May break on some BIOSes.
  --recheck               probe a device map even if it already exists
  --force                 install even if problems are detected
  --disk-module=MODULE    disk module to use


INSTALL_DEVICE can be a GRUB device name or a system device filename.


grub-install copies GRUB images into /boot/grub, and uses grub-setup
to install grub into the boot sector.


Report bugs to <bug-grub@gnu.org>.

```

Per that other thread, I tried

```

grub-install /dev/sdb

```

and got this as output:

```

/usr/sbin/grub-probe: error: no such disk.
Auto-detection of a filesystem of /dev/md0 failed.
Try with --recheck.
If the problem persists please report this together with the output of "/usr/sbin/grub-probe --device-map="/boot/grub/device.map" --target=fs -v /boot/grub" to <bug-grub@gnu.org>

```

And I stopped there since I didn't know how to proceed.  Any thoughts/suggestions??  Thanks!

Also, quick question - should I have installed mdadm and lvm2 on the initial Ubuntu 12.04 drive before proceeding with all of this (per step 4 in the other set of directions)?

Thanks!

---

### Post by darkod on 2015-09-20
Strange errors of update-grub and grub-install. Especially the grub-install. It complains "no such disk" for /dev/sdb, but the disk is there right? Did you confirm the disks are sda and sdb?

Also, are the arrays up and running?

---

### Post by Marc-NJ on 2015-09-20
> **darkod said:**
> Strange errors of update-grub and grub-install. Especially the grub-install. It complains "no such disk" for /dev/sdb, but the disk is there right? Did you confirm the disks are sda and sdb?

Also, are the arrays up and running?

I am pretty positive the disks were sda and sdb, but how can I confirm?

Also, how do I confirm if the arrays are up and running?

Thanks again!

---

### Post by darkod on 2015-09-20
To list all disks:
```
sudo parted -l
```

It should list the mdadm and lvm devices it can find too.

To check arrays:
```
cat /proc/mdstat
```

One thing you can do is boot the current install, add the mdadm package to it and then assemble existing arrays. That should report the arrays you created:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That command scans all disks and assembles arrays it can find. It might be easier to make the transition like that instead of doing it all from live mode.

---

### Post by Marc-NJ on 2015-09-20
```

root@ubuntu:~# parted -l
Model: ATA ST2000DM001-1ER1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  94.4GB  94.4GB  primary   ntfs
 2      94.4GB  722GB   627GB   extended
 5      94.4GB  722GB   627GB   logical                lvm
 3      722GB   732GB   10.5GB  primary   ntfs         boot
 4      732GB   750GB   17.9GB  primary   ntfs




Model: ATA ST3750525AS (scsi)
Disk /dev/sdb: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End    Size    Type     File system  Flags
 1      1049kB  734GB  734GB   primary  ntfs         raid
 2      734GB   750GB  16.1GB  primary               raid




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/VG1-LV2: 15.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  15.0GB  15.0GB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/VG1-LV1: 612GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  612GB  612GB  ext4




Model: Linux Software RAID Array (md)
Disk /dev/md0: 734GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End    Size   File system  Flags
 1      0.00B  734GB  734GB  ext4




Model: Linux Software RAID Array (md)
Disk /dev/md1: 16.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop


Number  Start  End     Size    File system     Flags
 1      0.00B  16.1GB  16.1GB  linux-swap(v1)




Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: hp DVD A DH16ACSH (scsi)
Disk /dev/sr0: 1044MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac


Number  Start   End     Size    File system  Name   Flags
 1      8192B   24.6kB  16.4kB               Apple
 2      42.3MB  51.8MB  9568kB               EFI

```

```

root@ubuntu:~# cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sdb2[1]
      15720320 blocks super 1.2 [2/1] [_U]


md0 : active raid1 sdb1[1]
      716698432 blocks super 1.2 [2/1] [_U]


unused devices: <none>

```

Does this info help?  What would you recommend I try next?  I'm obviously clueless at this point (although I do understand pretty much where we're at thanks to your great instructions and helpful pointers thus far).

---

### Post by darkod on 2015-09-20
OK, you can see md0 and md1 are good. However, there is a catch. The raid info does not exist inside your OS on the LVM, because you created it from live mode. But since that didn't work as expected, I think your best bet is the following:

1. Boot the LVM as normal.
2. Install the mdadm package, detect the arrays and create definitions for them that will assemble them on boot. That will create mdadm.conf in your OS (that was missing before from live mode).
3. Boot into live mode and do quick rsync to sync the data that changed from the last rsync. The process will finish fast because there will be little data changed.
4. Chroot into the mdadm OS and try to install its grub again. Hopefully that will work.

If the above finishes well, reboot and boot from the md devices.

What do you think?

---

### Post by Marc-NJ on 2015-09-20
Sure - that sounds good to me.  Could I ask you to give me the commands to try so I don't end up using the wrong ones?  Again, (and I know I'm saying this repeatedly), thanks so much for all the help!

---

### Post by darkod on 2015-09-20
OK then. Boot the machine as normal, it should boot the LVM. You can check mounted partitions easy way with:
```
df -h
```

To make sure what is mounted as /. It should say like /dev/mapper/VG1-LV1 or /dev/VG1/LV1.

Then install mdadm, assemble all arrays, and check in mdadm.conf if ARRAY definitions exist for both arrays (md0 and md1):
```
sudo -i
apt-get install mdadm
mdadm --assemble --scan
cat /etc/mdadm/mdadm.conf
```

If there are no ARRAY definitions add them with:
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
update-grub
```

Note, you do all the above as root. It makes it easier (that's why the command didn't work earlier). The update-grub should detect the mdadm OS and put it in the boot list as second (below the default LVM OS which is at the top. That should give you option to try and boot it when time comes.

Once that is done, boot into live mode as before, and do the mdadm and LVM activation part, then the rsync part and the chroot step. Just until the chroot step. Inside the chroot try something like:
```
update-initramfs -u
update-grub
grub-install /dev/sdb
```

Boot the machine and go into the Boot Menu, try booting from sdb (on sda the original grub from LVM should remain, and give you option to boot it if needed). When you confirm the mdadm works as expected, you will add its grub on sda too.

See if this works better...

---

### Post by Marc-NJ on 2015-09-20
OK, thanks - going through it right now, should be able to report back shortly.

By the way, what's the difference between "sudo -i" and "sudo -s" ?

Thanks again.

---

### Post by darkod on 2015-09-20
I haven't actually looked for differences between them. Now looking, they are almost the same. I have always used sudo -i.

---

### Post by Marc-NJ on 2015-09-20
OK, just went through everything, and I must have done something wrong, because now I'm just getting a blank screen when attempting to boot off of sdb (750 GB drive) and selecting to boot Ubuntu.

I initially booted back into the LVM Ubuntu (and checked with "df -h") and then installed mdadm (and postfix got installed too), assembled all arrays, and checked in mdadm.conf if ARRAY definitions exist for both arrays (md0 and md1) which they did (per your previous post with instructions on how to do this)

I ran "mdadm --detail --scan >> /etc/mdadm/mdadm.conf" and then checked the mdadm.conf file and it now had double entries for the md0 and md1, so I just commented out the double entries.  I then ran update-grub (not sure if I was supposed to do this)

I then booted back into the LiveCD, installed mdadm and lvm2 (I'm using a 14.04 LiveCD and lvm2 is already installed but not mdadm), ran "vgchange -ay" (to active the LVM), ran "mdadm --assemble --scan" (which I hope was right - to active the mdadm RAID1), mounted oldroot and newroot, did the rsync, and unmounted oldroot.

Then, I modified newroot's fstab (to change it to md0 and md1 - although now that I think about it, it's possible I screwed this up, but not sure), ran those 4 "mount --bind" commands, and then ran chroot.

Here's the output for the rest of what I did:

```

root@ubuntu:~# chroot /mnt/newroot
root@ubuntu:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-90-generic
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done
root@ubuntu:/# grub-install /dev/sdb
Installation finished. No error reported.
root@ubuntu:/# reboot
root@ubuntu:/# exit
exit
root@ubuntu:~# reboot


Broadcast message from marc@ubuntu
        (/dev/pts/22) at 21:11 ...


The system is going down for reboot NOW!
root@ubuntu:~#

```

And then tried rebooting and booting from sdb, and get the grub menu and then a blank screen.  

I'm attaching the bios listing of drives, the boot menu, and the grub menu I get when booting from SATA2 (the 750GB drive - sdb).

Any thoughts/suggestions?  Thanks!

---

### Post by darkod on 2015-09-20
I see small improvement from last time. Last time in the chroot update-grub and grub-install gave you errors, and this time it went well.

However, it should have booted from sdb and it didn't. Just to be clear, you tried to boot from SATA2 right? From your bios it's clear SATA2 is the 750GB disk, or /dev/sdb.

So, the grub menu shows up but when it tried to continue booting it gives only blank screen? No error messages, nothing?

---

### Post by Marc-NJ on 2015-09-20
Yup - you are correct.  Tried booting from SATA2 (750 GB disk or /dev/sdb) and got the grub menu, but when I selected the first option, it just gave me a blank screen. I can certainly try again if you think maybe I didn't wait long enough, although I think I waited about a minute or two and it just stayed blank.

---

### Post by Marc-NJ on 2015-09-20
Just left it running for quite some time, and still just a blank screen when trying to boot from SATA2 / sdb - haven't tried yet booting from the original LVM / sda though, but assuming that still works.

---

### Post by darkod on 2015-09-20
One thing I am not sure about is if it's only grub or the OS transition from non-raid LVM to raid without LVM.

Lets get the grub out of the way. Completely removing it and installing it again with new config. From live mode, do again the lvm and raid activation and chroot. Then:
```
apt-get purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sdb
```

During installation of grub it might ask you to select disks. Select only /dev/sdb for now. Don't forget that in a text menu you select with Space, not Enter. Enter might continue without selecting anything. When selected the disk will show * next to it. That's how you know the selection is made.

After that reboot again from sdb and see if it changed anything.

---

### Post by Marc-NJ on 2015-09-20
Got it - I just ran out actually to visit with a friend from out of town, but should be back in about 2 or so hours to give it a try.  Will report back then.  Thanks again!

---

### Post by Marc-NJ on 2015-09-21
Nope - no go this time around either, and I ran into some serious problems as well, including not being able to get the server to come up at all in sda either now.

I ran the following commands from live mode:

```

sudo -s
apt-get install mdadm lvm2
vgchange -ay
[COLOR=#000000]mdadm --assemble --scan
[/COLOR]mkdir /mnt/oldroot
mkdir /mnt/newroot
mount /dev/VG1/LV1 /mnt/oldroot
mount /dev/md0 /mnt/newroot
nano -w /mnt/newroot/etc/fstab

```

This is the fstab file by the way:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/md0 /               ext4    errors=remount-ro 0       1
/dev/md1 none            swap    sw              0       0

```

Continued commands I ran:

```

mount --bind /dev /mnt/newroot/dev
mount --bind /dev/pts /mnt/newroot/dev/pts
mount --bind /sys /mnt/newroot/sys
mount --bind /proc /mnt/newroot/proc
chroot /mnt/newroot
apt-get purge grub-pc grub-common

```

I got this prompt:




```

Package configuration










    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474;                                                                      &#9474;
    &#9474; Do you want to have all GRUB 2 files removed from /boot/grub?        &#9474;
    &#9474;                                                                      &#9474;
    &#9474; This will make the system unbootable unless another boot loader is   &#9474;
    &#9474; installed.                                                           &#9474;
    &#9474;                                                                      &#9474;
    &#9474; Remove GRUB 2 from /boot/grub?                                       &#9474;
    &#9474;                                                                      &#9474;
    &#9474;                   <Yes>                      <No>                    &#9474;
    &#9474;                                                                      &#9474;
    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

And I chose "Yes"

Continued commands:

```

apt-get install grub-pc

```

And here's where I ran into some issues.  Unfortunately, the PuTTY terminal window buffer ran out of space so I couldn't scroll back far enough to provide the output, but basically it wasn't allowing me to connect to the internet to install grub-pc (and whatever associated programs were necessary with it).  I think the issue had something to do with DNS, as I could ping 8.8.8.8 fine, but couldn't ping google.com.  I tried to do a little troubleshooting, but couldn't figure it out (although presumably this is some sort of big problem), so I finally figured I'd work around it by just adding the following to the /etc/hosts files:

```

91.189.91.14 us.archive.ubuntu.com

```

This worked, although it gave me some error about not being able to authenticate or confirm the validity of the files (something like that - I can't recall exactly what it said) and asked if I wanted to proceed, which I said I did - it then installed grub-pc again and I got these windows:

```

Package configuration


 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474;
 &#9474; The grub-pc package is being upgraded. This menu allows you to select
 &#9474; which devices you'd like grub-install to be automatically run for, if
 &#9474; any.
 &#9474;
 &#9474; Running grub-install automatically is recommended in most situations, to
 &#9474; prevent the installed GRUB core image from getting out of sync with GRUB
 &#9474; modules or grub.cfg.
 &#9474;
 &#9474; If you're unsure which drive is designated as boot drive by your BIOS,
 &#9474; it is often a good idea to install GRUB to all of them.
 &#9474;
 &#9474; Note: it is possible to install GRUB to partition boot records as well,
 &#9474; and some appropriate partitions are offered here. However, this forces
 &#9474; GRUB to use the blocklist mechanism, which makes it less reliable, and
 &#9474;
 &#9474;                                  <Ok>
 &#9474;                                                                           &#9474;
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;

```

```

Package configuration










                    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring grub-pc &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
                    &#9474; GRUB install devices:               &#9474;
                    &#9474;                                     &#9474;
                    &#9474;    [ ] /dev/sda (2000398 MB; ???)   &#9474;
                    &#9474;    
[*] /dev/sdb (750156 MB; ???)    &#9474;
                    &#9474;    [ ] /dev/md0 (733899 MB; ???)    &#9474;
                    &#9474;                                     &#9474;
                    &#9474;                                     &#9474;
                    &#9474;               <Ok>                  &#9474;
                    &#9474;                                     &#9474;
                    &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;



```

Per your instructions, I only selected /dev/sdb and continued.

Further commands I ran and the output from them:

(this picks up from part of the output of the install of grub-pc)

```

Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
Setting up grub-common (1.99-21ubuntu3.18) ...
runlevel:/var/run/utmp: No such file or directory
Setting up grub2-common (1.99-21ubuntu3.18) ...
Setting up grub-pc-bin (1.99-21ubuntu3.18) ...
Setting up grub-pc (1.99-21ubuntu3.18) ...


Creating config file /etc/default/grub with new version
Installation finished. No error reported.
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done
Setting up grub-gfxpayload-lists (0.6) ...
root@ubuntu:/etc# grub-mkconfig
Generating grub.cfg ...
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi


function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}


function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}


function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}


insmod raid
insmod mdraid1x
insmod part_msdos
insmod ext2
set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod raid
  insmod mdraid1x
  insmod part_msdos
  insmod ext2
  set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
  search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=30
else
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=0
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 0 ; then
    set timeout=0
  fi
fi
### END /etc/grub.d/00_header ###


### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###


### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
        set gfxpayload="${1}"
        if [ "${1}" = "keep" ]; then
                set vt_handoff=vt.handoff=7
        else
                set vt_handoff=
        fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
menuentry 'Ubuntu, with Linux 3.2.0-90-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-90-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-90-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-90-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-90-generic ...'
        linux   /boot/vmlinuz-3.2.0-90-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-90-generic
}
submenu "Previous Linux versions" {
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
menuentry 'Ubuntu, with Linux 3.2.0-89-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-89-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-89-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-89-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-89-generic ...'
        linux   /boot/vmlinuz-3.2.0-89-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-89-generic
}
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
menuentry 'Ubuntu, with Linux 3.2.0-88-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-88-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-88-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-88-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-88-generic ...'
        linux   /boot/vmlinuz-3.2.0-88-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-88-generic
}
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
menuentry 'Ubuntu, with Linux 3.2.0-87-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-87-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-87-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-87-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-87-generic ...'
        linux   /boot/vmlinuz-3.2.0-87-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-87-generic
}
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
menuentry 'Ubuntu, with Linux 3.2.0-86-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-86-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-86-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-86-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-86-generic ...'
        linux   /boot/vmlinuz-3.2.0-86-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-86-generic
}
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
menuentry 'Ubuntu, with Linux 3.2.0-85-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-85-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-85-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-85-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-85-generic ...'
        linux   /boot/vmlinuz-3.2.0-85-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-85-generic
}
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
menuentry 'Ubuntu, with Linux 3.2.0-84-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-84-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-84-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-84-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-84-generic ...'
        linux   /boot/vmlinuz-3.2.0-84-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-84-generic
}
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
menuentry 'Ubuntu, with Linux 3.2.0-83-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-83-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-83-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-83-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-83-generic ...'
        linux   /boot/vmlinuz-3.2.0-83-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-83-generic
}
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
menuentry 'Ubuntu, with Linux 3.2.0-82-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-82-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-82-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-82-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-82-generic ...'
        linux   /boot/vmlinuz-3.2.0-82-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-82-generic
}
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
menuentry 'Ubuntu, with Linux 3.2.0-80-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-80-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-80-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-80-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-80-generic ...'
        linux   /boot/vmlinuz-3.2.0-80-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-80-generic
}
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
menuentry 'Ubuntu, with Linux 3.2.0-79-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-79-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-79-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-79-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-79-generic ...'
        linux   /boot/vmlinuz-3.2.0-79-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-79-generic
}
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
menuentry 'Ubuntu, with Linux 3.2.0-77-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-77-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-77-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-77-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-77-generic ...'
        linux   /boot/vmlinuz-3.2.0-77-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-77-generic
}
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
menuentry 'Ubuntu, with Linux 3.2.0-76-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-76-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-76-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-76-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-76-generic ...'
        linux   /boot/vmlinuz-3.2.0-76-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-76-generic
}
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
menuentry 'Ubuntu, with Linux 3.2.0-75-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-75-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-75-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-75-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-75-generic ...'
        linux   /boot/vmlinuz-3.2.0-75-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-75-generic
}
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
menuentry 'Ubuntu, with Linux 3.2.0-74-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-74-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-74-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-74-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-74-generic ...'
        linux   /boot/vmlinuz-3.2.0-74-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-74-generic
}
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
menuentry 'Ubuntu, with Linux 3.2.0-72-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-72-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-72-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-72-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-72-generic ...'
        linux   /boot/vmlinuz-3.2.0-72-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-72-generic
}
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
menuentry 'Ubuntu, with Linux 3.2.0-70-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-70-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-70-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-70-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-70-generic ...'
        linux   /boot/vmlinuz-3.2.0-70-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-70-generic
}
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
menuentry 'Ubuntu, with Linux 3.2.0-69-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-69-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-69-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-69-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-69-generic ...'
        linux   /boot/vmlinuz-3.2.0-69-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-69-generic
}
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
menuentry 'Ubuntu, with Linux 3.2.0-68-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-68-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-68-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-68-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-68-generic ...'
        linux   /boot/vmlinuz-3.2.0-68-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-68-generic
}
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
menuentry 'Ubuntu, with Linux 3.2.0-67-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-67-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-67-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-67-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-67-generic ...'
        linux   /boot/vmlinuz-3.2.0-67-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-67-generic
}
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
menuentry 'Ubuntu, with Linux 3.2.0-65-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-65-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-65-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-65-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-65-generic ...'
        linux   /boot/vmlinuz-3.2.0-65-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-65-generic
}
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
menuentry 'Ubuntu, with Linux 3.2.0-64-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-64-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-64-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-64-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-64-generic ...'
        linux   /boot/vmlinuz-3.2.0-64-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-64-generic
}
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
menuentry 'Ubuntu, with Linux 3.2.0-63-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-63-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-63-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-63-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-63-generic ...'
        linux   /boot/vmlinuz-3.2.0-63-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-63-generic
}
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
menuentry 'Ubuntu, with Linux 3.2.0-61-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-61-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-61-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-61-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-61-generic ...'
        linux   /boot/vmlinuz-3.2.0-61-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-61-generic
}
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
menuentry 'Ubuntu, with Linux 3.2.0-60-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-60-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-60-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-60-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-60-generic ...'
        linux   /boot/vmlinuz-3.2.0-60-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-60-generic
}
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
menuentry 'Ubuntu, with Linux 3.2.0-59-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-59-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-59-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-59-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-59-generic ...'
        linux   /boot/vmlinuz-3.2.0-59-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-59-generic
}
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
menuentry 'Ubuntu, with Linux 3.2.0-58-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-58-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-58-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-58-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-58-generic ...'
        linux   /boot/vmlinuz-3.2.0-58-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-58-generic
}
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
menuentry 'Ubuntu, with Linux 3.2.0-57-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-57-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-57-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-57-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-57-generic ...'
        linux   /boot/vmlinuz-3.2.0-57-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-57-generic
}
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
menuentry 'Ubuntu, with Linux 3.2.0-56-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-56-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-56-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-56-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-56-generic ...'
        linux   /boot/vmlinuz-3.2.0-56-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-56-generic
}
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
menuentry 'Ubuntu, with Linux 3.2.0-55-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-55-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-55-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-55-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-55-generic ...'
        linux   /boot/vmlinuz-3.2.0-55-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-55-generic
}
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
menuentry 'Ubuntu, with Linux 3.2.0-54-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-54-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-54-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-54-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-54-generic ...'
        linux   /boot/vmlinuz-3.2.0-54-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-54-generic
}
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
menuentry 'Ubuntu, with Linux 3.2.0-53-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-53-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-53-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-53-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-53-generic ...'
        linux   /boot/vmlinuz-3.2.0-53-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-53-generic
}
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
menuentry 'Ubuntu, with Linux 3.2.0-52-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-52-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-52-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-52-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-52-generic ...'
        linux   /boot/vmlinuz-3.2.0-52-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-52-generic
}
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
menuentry 'Ubuntu, with Linux 3.2.0-51-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-51-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-51-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-51-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-51-generic ...'
        linux   /boot/vmlinuz-3.2.0-51-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-51-generic
}
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
menuentry 'Ubuntu, with Linux 3.2.0-48-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-48-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-48-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-48-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-48-generic ...'
        linux   /boot/vmlinuz-3.2.0-48-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-48-generic
}
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
menuentry 'Ubuntu, with Linux 3.2.0-45-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-45-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-45-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-45-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-45-generic ...'
        linux   /boot/vmlinuz-3.2.0-45-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-45-generic
}
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
menuentry 'Ubuntu, with Linux 3.2.0-44-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-44-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-44-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-44-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-44-generic ...'
        linux   /boot/vmlinuz-3.2.0-44-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-44-generic
}
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
menuentry 'Ubuntu, with Linux 3.2.0-43-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-43-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-43-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-43-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-43-generic ...'
        linux   /boot/vmlinuz-3.2.0-43-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-43-generic
}
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
menuentry 'Ubuntu, with Linux 3.2.0-41-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-41-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-41-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-41-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-41-generic ...'
        linux   /boot/vmlinuz-3.2.0-41-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-41-generic
}
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
menuentry 'Ubuntu, with Linux 3.2.0-40-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-40-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-40-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-40-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-40-generic ...'
        linux   /boot/vmlinuz-3.2.0-40-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-40-generic
}
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
menuentry 'Ubuntu, with Linux 3.2.0-39-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-39-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-39-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-39-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-39-generic ...'
        linux   /boot/vmlinuz-3.2.0-39-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-39-generic
}
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
menuentry 'Ubuntu, with Linux 3.2.0-38-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-38-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-38-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-38-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-38-generic ...'
        linux   /boot/vmlinuz-3.2.0-38-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-38-generic
}
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
menuentry 'Ubuntu, with Linux 3.2.0-37-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-37-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-37-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-37-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-37-generic ...'
        linux   /boot/vmlinuz-3.2.0-37-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-37-generic
}
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
menuentry 'Ubuntu, with Linux 3.2.0-36-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-36-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-36-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-36-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-36-generic ...'
        linux   /boot/vmlinuz-3.2.0-36-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-36-generic
}
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
menuentry 'Ubuntu, with Linux 3.2.0-35-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-35-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-35-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-35-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-35-generic ...'
        linux   /boot/vmlinuz-3.2.0-35-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-35-generic
}
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
menuentry 'Ubuntu, with Linux 3.2.0-29-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux   /boot/vmlinuz-3.2.0-29-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro   quiet splash $vt_handoff
        initrd  /boot/initrd.img-3.2.0-29-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-29-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        echo    'Loading Linux 3.2.0-29-generic ...'
        linux   /boot/vmlinuz-3.2.0-29-generic root=UUID=d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2 ro recovery nomodeset
        echo    'Loading initial ramdisk ...'
        initrd  /boot/initrd.img-3.2.0-29-generic
}
}
### END /etc/grub.d/10_linux ###


### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###


### BEGIN /etc/grub.d/20_memtest86+ ###
Found memtest86+ image: /boot/memtest86+.bin
menuentry "Memory test (memtest86+)" {
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux16 /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod raid
        insmod mdraid1x
        insmod part_msdos
        insmod ext2
        set root='(mduuid/dfa90a6f52b4e3a53fc2660c1567dc26)'
        search --no-floppy --fs-uuid --set=root d7fda575-5bbb-48f5-a2c1-f2c60cf01ea2
        linux16 /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###


### BEGIN /etc/grub.d/30_os-prober ###
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
Found Windows 7 (loader) on /dev/sda3
menuentry "Windows 7 (loader) (on /dev/sda3)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root 58C1C5EA71B064B8
        chainloader +1
}
Found Windows Recovery Environment (loader) on /dev/sda4
menuentry "Windows Recovery Environment (loader) (on /dev/sda4)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos4)'
        search --no-floppy --fs-uuid --set=root AEF25C6EF25C3D31
        drivemap -s (hd0) ${root}
        chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###


### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###


### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
done
root@ubuntu:/etc# update-grub
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
  /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed.
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done
root@ubuntu:/etc# grub-install /dev/sdb
Installation finished. No error reported.
root@ubuntu:/etc# nano -w hosts
root@ubuntu:/etc# nano -w hosts
root@ubuntu:/etc# exit
exit
root@ubuntu:~# reboot


Broadcast message from marc@ubuntu
        (/dev/pts/1) at 4:03 ...


The system is going down for reboot NOW!
root@ubuntu:~#

```

After doing all that, I removed that entry from the hosts file, rebooted and tried to get into Ubuntu on sdb (SATA2) and the same thing happened - got the grub menu and then a blank screen after selecting to boot Ubuntu.

At this point, I tried to boot back into Ubuntu off of sda (SATA0 / 2 TB drive) since I needed to have access to the data and services on the server for Monday, and that gave me a blank screen as well, so now I can't get back into my server at all.  I know my data is most likely all still there (and the data itself is also backed up to the cloud), but now I can't get the server to boot up at all.  

Any thoughts/suggestions?

Thanks again!

---

### Post by darkod on 2015-09-21
For chroot into the raid OS there is no need to mount the LVM part. Now that the data is synced it doesn't depend on the LVM.

The bootloader on sda was never touched, but if you want to quickly re-install the MBR part linked to the LVM, from live mode you can do (you said lvm2 package is already included):
```
sudo -i
vgchange -ay
mount /dev/VG1/LV1 /mnt
grub-install --root-directory=/mnt /dev/sda
```

That mounts the LV1 temporarily at /mnt and then uses /mnt as parameter to tell grub-install which one is the root partition when doing the installation on /dev/sda.

That is basic grub recovery on the MBR. Provided all is good inside the OS (and you never did changes in the LVM, only in the mdadm partition) it should work.

---

### Post by Marc-NJ on 2015-09-21
> **darkod said:**
> For chroot into the raid OS there is no need to mount the LVM part. Now that the data is synced it doesn't depend on the LVM.

The bootloader on sda was never touched, but if you want to quickly re-install the MBR part linked to the LVM, from live mode you can do (you said lvm2 package is already included):
```
sudo -i
vgchange -ay
mount /dev/VG1/LV1 /mnt
grub-install --root-directory=/mnt /dev/sda
```

That mounts the LV1 temporarily at /mnt and then uses /mnt as parameter to tell grub-install which one is the root partition when doing the installation on /dev/sda.

That is basic grub recovery on the MBR. Provided all is good inside the OS (and you never did changes in the LVM, only in the mdadm partition) it should work.

Unfortunately, still no success even getting back into sda - after doing the above, I rebooted the machine and chose to boot up to SATA0 (the 2 TB drive | sda) from the boot menu, and got the grub menu.  I chose the first option, and then all I get is "Press any key to continue..." and of course, pressing any key does nothing.

Even if we haven't solved the issue yet, this has been a great learning experience which I really appreciate, and I also really appreciate you sticking with me on this!

---

### Post by darkod on 2015-09-21
This is all very strange. Maybe there was an error somewhere, maybe not, I really don't know why it would "mess up" the LVM boot process when it was never touched.

If you want, we can try reinstalling grub now in LVM chroot (like you tried earlier for the raid chroot). Also you should check the content of /boot/grub/grub.cfg file in the LVM. To make sure if its menuentry is trying to boot the LVM or not. But I expect that to be correct...

---

### Post by Marc-NJ on 2015-09-21
I'm at a loss too (but then again, I was at a loss to begin with...lol).  I was thinking it over, and it seems like the only thing we did that could possibly have impacted the LVM on sda was rsync (if it's bidirectional?) - does that make any sense or help at all?

So, I got this far on what to do right now via the LiveCD:

```

marc@ubuntu:~$ sudo -i
[sudo] password for marc:
root@ubuntu:~# vgchange -ay
  2 logical volume(s) in volume group "VG1" now active
root@ubuntu:~# mkdir /mnt/oldroot
root@ubuntu:~# mount /dev/VG1/LV1 /mnt/oldroot
root@ubuntu:~# chroot /mnt/oldroot
root@ubuntu:/# 

```

But now do you want me to try this:

```

update-grub
grub-install /dev/sda
update-initramfs -u
exit

```

Or this:

```

apt-get purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda

```

Or something else?

Also, I think that there's now also something wrong with DNS via chroot in sda, since I can't ping google.com, but can ping 8.8.8.8 fine (and this could be an issue if I have to uninstall and then reinstall grub-pc):

```

root@ubuntu:/# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=58 time=8.56 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=58 time=8.42 ms
^C
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 8.423/8.495/8.568/0.117 ms
root@ubuntu:/# ping google.com
ping: unknown host google.com

```

Thanks!

Oh, and I also looked at /boot/grub/grub.cfg but it's a big file and I have no idea what I'm looking for exactly.  Should I try and post it here?

---

### Post by darkod on 2015-09-21
rsync is never bidirectional, it's always source to destination. So there was no chance of data going the other way.

If you want full chroot to try reinstalling grub or running update-initramfs, you need the bind commands too (they all go in a group). Like:
```
mount /dev/VG1/LV1 /mnt/oldroot
mount --bind /dev /mnt/oldroot/dev
mount --bind /dev/pts /mnt/oldroot/dev/pts
mount --bind /proc /mnt/oldroot/proc
mount --bind /sys /mnt/oldroot/sys
mount --bind /run /mnt/oldroot/run
chroot /mnt/oldroot
```

I added a bind to /run in there too, I saw it in one thread that involved LVM. It can't hurt. In tha past I have used only /dev /proc and /sys and it was enough, but it doesn't hurt if you add /dev/pts and /run in there too.

If you suspect DNS failure in the chroot, try to add dns servers manually to /etc/resolv.conf (I'm not sure if you can use that once you are inside the chroot or you need to use /mnt/oldroot/etc/resolv.conf). Anyway, if there are no nameservers there try the google ones:
```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

Honestly I haven't played with chroot much and I'm not sure right now if it takes over DNS from the live mode, or not. After you modify the resolv.conf try the ping yahoo.com again. Also check that your live mode has no dns issues too, it might be problem on that level.

As for the commands to run in the chroot, lets try them in slightly different order (without removing grub first):
```
update-initramfs -u
grub-mkconfig
update-grub
grub-install /dev/sda
exit
```

If that doesn't work you can try purge and install, just add them at the top.

---

### Post by Marc-NJ on 2015-09-21
OK, so here's what I ran:

```

marc@ubuntu:~$ sudo -i
[sudo] password for marc:
root@ubuntu:~# umount /mnt/oldroot
root@ubuntu:~# mount /dev/VG1/LV1 /mnt/oldroot
root@ubuntu:~# mount --bind /dev /mnt/oldroot/dev
root@ubuntu:~# mount --bind /dev/pts /mnt/oldroot/dev/pts
root@ubuntu:~# mount --bind /proc /mnt/oldroot/proc
root@ubuntu:~# mount --bind /sys /mnt/oldroot/sys
root@ubuntu:~# mount --bind /run /mnt/oldroot/run
root@ubuntu:~# chroot /mnt/oldroot
root@ubuntu:/# cd /etc/
root@ubuntu:/etc# nano -w resolv.conf
root@ubuntu:/etc# nano -w resolv.conf

```

I then added those two nameserver entries into the /etc/resolv.conf and that seemed to fix the DNS issue (at least for now, although I'm guessing that resolv.conf gets overwritten since it said in the actual file it did?)

I then did:

```

root@ubuntu:/# update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-90-generic
root@ubuntu:/# grub-mkconfig

```


This was followed by a lot of output that the buffer didn't fully capture so I can't post it all here (and not sure if it's necessary to post all here or not).

Then:

```

root@ubuntu:/# update-grub
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# exit
exit
root@ubuntu:~# reboot


Broadcast message from marc@ubuntu
        (/dev/pts/3) at 22:46 ...


The system is going down for reboot NOW!
root@ubuntu:~#

```

I then booted up to SATA0 (2 TB drive | sda) and got a grub menu again, and then when I chose the first option, got a bunch of output that flew by quickly on the screen and eventually ended with the attached image.  So maybe we're getting somewhere??

What do you think are the next steps?  Thanks!

---

### Post by darkod on 2015-09-22
OK, on the question whether you want to start degraded, did you select anything or you waited and it timed out?

This is only a message that detects a degraded array (you have only one member for a mirror raid1) and asks you if you want to continue booting. Select Y because we know the array is degraded plus we are not even running the OS on it (yet). So select yes and see if it will boot the LVM OS.

Off topic, you can see in each update-grub or grub-mkconfig that it lists a large number of old kernels. You should remove old kernels from time to time, no need to keep 20+ kernels. But I didn't want to comment on that because we have more important things to do now. Also that's why grub.cfg is large because it also lists entry for each kernel it can find in the system.

PS. If you manage to boot, to confirm which OS you are running do a:
```
df -h
```

Take a look which device you have mounted as /. It can be the LVM or the md0 depending which one you booted.

---

### Post by Marc-NJ on 2015-09-22
> **darkod said:**
> OK, on the question whether you want to start degraded, did you select anything or you waited and it timed out?

This is only a message that detects a degraded array (you have only one member for a mirror raid1) and asks you if you want to continue booting. Select Y because we know the array is degraded plus we are not even running the OS on it (yet). So select yes and see if it will boot the LVM OS.

Off topic, you can see in each update-grub or grub-mkconfig that it lists a large number of old kernels. You should remove old kernels from time to time, no need to keep 20+ kernels. But I didn't want to comment on that because we have more important things to do now. Also that's why grub.cfg is large because it also lists entry for each kernel it can find in the system.

PS. If you manage to boot, to confirm which OS you are running do a:
```
df -h
```

Take a look which device you have mounted as /. It can be the LVM or the md0 depending which one you booted.

Yes!  So answering "Y" and hitting enter seems to work and I can boot back into sda.  Thank you!!  Previously I had just let it time out as I didn't even realize I could enter anything during that stage of the boot-up process.

As far as removing old kernels - am happy to do that, although I don't know how to...lol...but I guess that's outside of this topic, and it doesn't necessarily hurt to leave them, right?

After booting up, I ran "df -h" and it reported what I believe it is reporting that I'm running the LVM which is correct since I'm booting from sda, right?  (see attached image).

So I guess at this point, at least I'm in good shape in that I can get back into sda and run my server.  I really do appreciate all you've done to assist me, and would love to continue so that I can hopefully get the mdadm RAID1 working, but fully understand if you just want to stop at this point.  However, if you want to continue, let me know what you think we should try next?  

And also, since I've now booted into sda again, I'm assuming we'll have to run another rsync to copy over changed data from sda to sdb, right?

Thanks again!

---

### Post by darkod on 2015-09-23
If at any time, during boot or normal operation, there is a message from the OS asking you something, you can always interact. In fact in most cases it will wait for you to reply (or simply time out like in this case).

Yes, the rsync will have to be done for the small changed from the last one. But that's for the end.

What I would like to try now is if update-grub can detect our "mirrored" OS on the raid. Because in theory it should scan all devices, and i believe the raid now gets assembled even when booting the LVM, like you did.

So run sudo update-grub and watch carefully towards the end, after it lists all kernels from the LVM. Before it reports the windows loaders found, it should also report Linux found on /dev/md0 or similar. If it does that, it will make an entry for it in the grub menu, so you can boot again from SATA0 and select booting the /dev/md0 instead of the LVM. But that is just to try, don't run the raid OS too long because we don't want too much difference in the files between the LVM and the raid. The LVM still has to remain the principle OS until we complete all migration. I'm not sure if I explained that good... :)

So give the update-grub a shot and check if it reports another Linux found on the raid.

---

### Post by Marc-NJ on 2015-09-23
> **darkod said:**
> If at any time, during boot or normal operation, there is a message from the OS asking you something, you can always interact. In fact in most cases it will wait for you to reply (or simply time out like in this case).

Yes, the rsync will have to be done for the small changed from the last one. But that's for the end.

What I would like to try now is if update-grub can detect our "mirrored" OS on the raid. Because in theory it should scan all devices, and i believe the raid now gets assembled even when booting the LVM, like you did.

So run sudo update-grub and watch carefully towards the end, after it lists all kernels from the LVM. Before it reports the windows loaders found, it should also report Linux found on /dev/md0 or similar. If it does that, it will make an entry for it in the grub menu, so you can boot again from SATA0 and select booting the /dev/md0 instead of the LVM. But that is just to try, don't run the raid OS too long because we don't want too much difference in the files between the LVM and the raid. The LVM still has to remain the principle OS until we complete all migration. I'm not sure if I explained that good... :)

So give the update-grub a shot and check if it reports another Linux found on the raid.

I think I understand...at least somewhat :)  

Unfortunately, I just ran "sudo update-grub" but don't think I got the results you were expecting.  Here is the output:

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-90-generic
Found initrd image: /boot/initrd.img-3.2.0-90-generic
Found linux image: /boot/vmlinuz-3.2.0-89-generic
Found initrd image: /boot/initrd.img-3.2.0-89-generic
Found linux image: /boot/vmlinuz-3.2.0-88-generic
Found initrd image: /boot/initrd.img-3.2.0-88-generic
Found linux image: /boot/vmlinuz-3.2.0-87-generic
Found initrd image: /boot/initrd.img-3.2.0-87-generic
Found linux image: /boot/vmlinuz-3.2.0-86-generic
Found initrd image: /boot/initrd.img-3.2.0-86-generic
Found linux image: /boot/vmlinuz-3.2.0-85-generic
Found initrd image: /boot/initrd.img-3.2.0-85-generic
Found linux image: /boot/vmlinuz-3.2.0-84-generic
Found initrd image: /boot/initrd.img-3.2.0-84-generic
Found linux image: /boot/vmlinuz-3.2.0-83-generic
Found initrd image: /boot/initrd.img-3.2.0-83-generic
Found linux image: /boot/vmlinuz-3.2.0-82-generic
Found initrd image: /boot/initrd.img-3.2.0-82-generic
Found linux image: /boot/vmlinuz-3.2.0-80-generic
Found initrd image: /boot/initrd.img-3.2.0-80-generic
Found linux image: /boot/vmlinuz-3.2.0-79-generic
Found initrd image: /boot/initrd.img-3.2.0-79-generic
Found linux image: /boot/vmlinuz-3.2.0-77-generic
Found initrd image: /boot/initrd.img-3.2.0-77-generic
Found linux image: /boot/vmlinuz-3.2.0-76-generic
Found initrd image: /boot/initrd.img-3.2.0-76-generic
Found linux image: /boot/vmlinuz-3.2.0-75-generic
Found initrd image: /boot/initrd.img-3.2.0-75-generic
Found linux image: /boot/vmlinuz-3.2.0-74-generic
Found initrd image: /boot/initrd.img-3.2.0-74-generic
Found linux image: /boot/vmlinuz-3.2.0-72-generic
Found initrd image: /boot/initrd.img-3.2.0-72-generic
Found linux image: /boot/vmlinuz-3.2.0-70-generic
Found initrd image: /boot/initrd.img-3.2.0-70-generic
Found linux image: /boot/vmlinuz-3.2.0-69-generic
Found initrd image: /boot/initrd.img-3.2.0-69-generic
Found linux image: /boot/vmlinuz-3.2.0-68-generic
Found initrd image: /boot/initrd.img-3.2.0-68-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.2.0-65-generic
Found initrd image: /boot/initrd.img-3.2.0-65-generic
Found linux image: /boot/vmlinuz-3.2.0-64-generic
Found initrd image: /boot/initrd.img-3.2.0-64-generic
Found linux image: /boot/vmlinuz-3.2.0-63-generic
Found initrd image: /boot/initrd.img-3.2.0-63-generic
Found linux image: /boot/vmlinuz-3.2.0-61-generic
Found initrd image: /boot/initrd.img-3.2.0-61-generic
Found linux image: /boot/vmlinuz-3.2.0-60-generic
Found initrd image: /boot/initrd.img-3.2.0-60-generic
Found linux image: /boot/vmlinuz-3.2.0-59-generic
Found initrd image: /boot/initrd.img-3.2.0-59-generic
Found linux image: /boot/vmlinuz-3.2.0-58-generic
Found initrd image: /boot/initrd.img-3.2.0-58-generic
Found linux image: /boot/vmlinuz-3.2.0-57-generic
Found initrd image: /boot/initrd.img-3.2.0-57-generic
Found linux image: /boot/vmlinuz-3.2.0-56-generic
Found initrd image: /boot/initrd.img-3.2.0-56-generic
Found linux image: /boot/vmlinuz-3.2.0-55-generic
Found initrd image: /boot/initrd.img-3.2.0-55-generic
Found linux image: /boot/vmlinuz-3.2.0-54-generic
Found initrd image: /boot/initrd.img-3.2.0-54-generic
Found linux image: /boot/vmlinuz-3.2.0-53-generic
Found initrd image: /boot/initrd.img-3.2.0-53-generic
Found linux image: /boot/vmlinuz-3.2.0-52-generic
Found initrd image: /boot/initrd.img-3.2.0-52-generic
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
Found Windows Recovery Environment (loader) on /dev/sda4
done

```

So since that didn't work, what do you think we should try next?  Sorry I'm absolutely no help here, but I'm definitely out of my element on this...on the plus though I definitely think I'm picking up a bunch of stuff, so that's good at least :)

---

### Post by darkod on 2015-09-24
Yes, there is no Linux detected on the raid as I expected/hoped. Lets try something. In linux you can always temporarily mount stuff at /mnt and later unmount it. The mount point already exists so no need to create it first. That a good way to quickly look into a partition/device that is normally not mounted.

So, while running the lvm OS try looking into the md0:
```
sudo mount /dev/md0 /mnt
ls /mnt/boot
sudo umount /mnt
```

If the kernels are rsynced there correctly it should show the large list of kernel files. You can unmount the /mnt mount point right after that just in case.

Lets see first what that says.

---

### Post by Marc-NJ on 2015-09-25
Hey - my apologies - am just in the process of packing for a move next week - I will definitely respond sometime next week once I finish the move - and thanks again for all the help!!!

---

### Post by Marc-NJ on 2015-10-05
Hey Darko - hopefully you are still around.  Again - my apologies for the delay in responding to this thread (just completed my move although still have plenty left to unpack!).  Anyway, I had to shut down the server yesterday in order to move it temporarily, and figured I could just restart it the same way I previously did (boot menu to SATA0 [2 TB drive] and then when prompted I could make the appropriate selection during the startup screen process).  Unfortunately, it now doesn't seem to let me do that - when I select SATA0 I get the grub menu, and when I select the first option, I just get the blank black screen again.  Any thoughts on what I can do to get it back to where I can at least boot up into the LVM?

I might have also accidentally installed Ubuntu updates to the LVM before shutting it down the other day, as I'm used to doing that before I have to shut down anyway, and completely forgot in the midst of my move that we were in the middle of this process.  I'm wondering if that maybe is impacting my ability to restart it now?

Any help, as always, is greatly appreciated.  Thanks!

---

### Post by darkod on 2015-10-05
Running the updates shouldn't influence it. I didn't expect this either.
What if you try to load a previous kernel from Advanced Options in the grub menu?

If that fails too try redoing the procedure you did previously when it couldn't boot the lvm. It seemed to help booting it.

---

### Post by Marc-NJ on 2015-10-21
> **darkod said:**
> Running the updates shouldn't influence it. I didn't expect this either.
What if you try to load a previous kernel from Advanced Options in the grub menu?

If that fails too try redoing the procedure you did previously when it couldn't boot the lvm. It seemed to help booting it.

Darko - sorry for the late reply, and thank you once again for all your help.  I was able to get the Ubuntu server up and running a week or two ago using an older kernel from the Advanced Options in the grub menu - I think it was one that was two versions out-of-date, but don't recall right this second off the top of my head (and am hesitant to take the machine down again without checking with you first on what you think the next steps are).  So, if you are still up to helping me (and if not, I completely understand), would love to know what you think would be the next steps to stabilize things and ultimately try and get the mdadm RAID1 working.  Thanks!!

**UPDATE: **So I went back and looked at some pictures I took from a week or two ago, and I think the kernel that allowed me to boot was Linux 3.2.0-89-generic if that helps at all.  And then I still had to hit "Y" during the boot process to get it to bypass the message on boot (about starting the degraded RAID).  Hope that helps a little.

---

### Post by darkod on 2015-10-21
So, you can boot the LVM by selecting a previous kernel, right?

When you boot into it, does it assemble the raid by default or not? I don't remember how we left it. If there is no raid assembled, try installing the mdadm package and assembling the raid:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

Let me know how that works out.

---

### Post by Marc-NJ on 2015-10-21
Thanks for the quick reply.  Let me ask you this - our initial plan was to set up the 750 GB drive as a degraded RAID1 array running the entire up-to-date Ubuntu 12.04 that was previously running on the 2 TB drive (via rsync), and then once we got that working, wipe the 2 TB drive and let the RAID1 array rebuild itself on that drive as well, right?  Does it make sense to try and continue this (and work on the 750 GB drive) instead of making more changes on the 2 TB drive (that for the time being is letting me get back into the system and is working)?  I'm just fearful of going down again since I rely upon some of the services and data on the system for day-to-day use (hence my rationale for wanting to get it in a redundant state :) ).  

I actually have another system that is doing nothing right now and has a brand new 2 TB blank drive in it - do you think I should clone the existing 2 TB drive in this system we're working on to that other system so I can be up and running if necessary?  Would Ubuntu boot from a different system if it was cloned over to it?

Thanks!

---

### Post by darkod on 2015-10-21
Yes, ubuntu should work from a cloned disk even if the HW is not identical. If you have really bad luck it might get stuck with some HW component, but that would be very rare.

We will not be working on the LVM much. My idea with the latest suggestion is to get mdadm included in the OS (it will need to be there later anyway because you want to move to raid) and see if that helps us with the transition. Remember how so far update-grub is not able to see the raid and report as an OS. Right now you have your LVM and the rsynced system to the raid. So grub should show two ubuntu OSs if it can read everything correctly. Obviously it can't so I'm trying to determine why. I think it's because we worked with mdadm from live mode so the LVM OS has no notion of the raid and is not setup to bring it up on boot.

Some tutorials for moving to raid do it like that, by installing mdadm in the current OS and doing only the rsync from live mode. Others do everything from live mode but in our case that didn't lead us where we expected. Otherwise you would have been able to boot into the raid OS right now, and you're not, right? The effort to boot from grub on the 750GB disk into the raid failed if I remember correctly.

---

