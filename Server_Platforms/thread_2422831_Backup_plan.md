---
title: "Backup plan"
date: 2019-07-13
forum: Server Platforms
---

### Post by aljames2 on 2019-07-13
My setup:

1) 250gb ssd w/ Ubuntu Server LVM partitions.
2) 3TB HDD data storage only using LVM partitions.
3) 3TB HDD empty, to be backup drive.
* No RAID.
* Eventually I want a backup to a 4th USB portable drive but I don’t have that yet.

I am wondering what a good backup strategy would be here.  My thought is run LVM Snapshots & Rdiff in a cron script to back up both the OS and data drive to my 3rd drive.  Would tar be better to back up the data drive since that content is more static?  Any other suggestions?

---

### Post by TheFu on 2019-07-13
I like what you've written. It is a little light on details.

I use rdiff-backup and rsync.
rdiff-backup for non-media files that need to be versioned.
rsync for media files that don't change.  
gnutar was created for 250MB and smaller tapes.  Basically, if you'd use a ZIP file, then a tgz is fine.  I think  500MB size tgz files is beyond what I'd use for tar.

Of course, there is much more involved, since I don't backup the entire OS, just selected parts that aren't trivially recreated with a fresh, minimal, install during my recovery efforts.  I grab all of /etc/ since there are a few customized files in there.  I grab the ufw areas under /lib/ and some stuff under /var/ depending on the system setup and all of /usr/local/ since that is non-package installed stuff.  I also grab a list of manually installed packages using apt-mark showmanual.  At restore time, all that information is used to recreate an almost exact copy of the original machine.  Some examples of the data I grab.  It is a little different for each system.

```
root@hadar:/root/backup# ls
apt-mark.auto    crontab.tf    dpkg.list      pvdisplay.txt
apt-mark.manual  crontab.root  lshw.list      vgdisplay.txt
blkid.txt        df.txt        lvdisplay.txt
```
The crontabs are handy and the LVM information might be needed later.  I should probably change that over to using the pvs, vgs and lvs commands.  I should also get an lsblk since they are so much more compact and have the info. Some of my ext4 file systems have non-standard tune2fs settings. I should do something to capture that info too.

Of course, I grab /root/, and /home/  too.

One other consideration. Directly connected backup storage is a risk.  Obviously, the backup "server" has to have storage directly connected, but the other systems do not.  With both rsync and rdiff-backup, we can "pull" backups so the clients don't have any direct access to the backup storage. This would help mitigate crypto-malware issues.  Just keep the backup server far away from the internet and don't allow access that machine with any privileged accounts.

Would love to see more of your detailed plans.  I'm certain I could learn some good stuff.

---

### Post by aljames2 on 2019-07-28
Thanks, and sorry for the delay.  I've been working on this and learning along the way.  So far..

My pvs
```

  PV         VG         Fmt  Attr PSize   PFree
  /dev/sda3  LVG        lvm2 a--  231.95g 182.95g
  /dev/sdb1  WD-vg1     lvm2 a--   <2.73t   2.47t
  /dev/sdc1  WD-vg2-bak lvm2 a--   <2.73t   1.74t

```

My dft
```

/dev/mapper/LVG-root                     ext4       20G  967M   18G   6% /
/dev/mapper/LVG-usr                      ext4      4.9G  883M  3.8G  19% /usr
/dev/mapper/LVG-srv                      ext4      989M  2.7M  939M   1% /srv
/dev/mapper/LVG-home                     ext4      481M  2.3M  453M   1% /home
/dev/mapper/LVG-opt                      ext4      3.0G  1.1G  1.8G  37% /opt
/dev/sda2                                ext2      462M  145M  294M  33% /boot
/dev/mapper/LVG-tmp                      ext4      984M  2.8M  932M   1% /tmp
/dev/mapper/LVG-var                      ext4      4.0G  592M  3.2G  16% /var
/dev/sda1                                vfat      476M  6.1M  470M   2% /boot/efi
/dev/mapper/LVG-bak                      ext4      2.9G  3.1M  2.8G   1% /bak
/dev/mapper/WD--vg2--bak-lv_data_bak     ext4      503G   73M  498G   1% /media/WD3tbHDD2/backup-data
/dev/mapper/WD--vg2--bak-lv_serverOS_bak ext4      393G  3.7G  386G   1% /media/WD3tbHDD2/backup-serverOS
/dev/mapper/WD--vg1-dfay                 ext4      196G   61M  194G   1% /media/WD3tbHDD1/dfay-mount
/dev/mapper/WD--vg1-projects             ext4      9.8G   37M  9.7G   1% /media/WD3tbHDD1/projects-mount
/dev/mapper/WD--vg1-cloudy               ext4      4.9G   20M  4.8G   1% /media/WD3tbHDD1/cloudy-mount
/dev/mapper/WD--vg1-media                ext4       49G   53M   49G   1% /media/WD3tbHDD1/media-mount

```

My lsblk
```

NAME                             MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                8:0    0 232.9G  0 disk
&#9500;&#9472;sda1                             8:1    0   476M  0 part /boot/efi
&#9500;&#9472;sda2                             8:2    0   477M  0 part /boot
&#9492;&#9472;sda3                             8:3    0   232G  0 part
  &#9500;&#9472;LVG-root                     253:0    0    25G  0 lvm  /
  &#9500;&#9472;LVG-usr                      253:1    0     6G  0 lvm  /usr
  &#9500;&#9472;LVG-var                      253:8    0     5G  0 lvm  /var
  &#9500;&#9472;LVG-tmp                      253:9    0     2G  0 lvm  /tmp
  &#9500;&#9472;LVG-bak                      253:10   0     4G  0 lvm  /bak
  &#9500;&#9472;LVG-srv                      253:11   0     2G  0 lvm  /srv
  &#9500;&#9472;LVG-opt                      253:12   0     4G  0 lvm  /opt
  &#9492;&#9472;LVG-home                     253:13   0     1G  0 lvm  /home
sdb                                8:16   0   2.7T  0 disk
&#9492;&#9472;sdb1                             8:17   0   2.7T  0 part
  &#9500;&#9472;WD--vg1-projects             253:2    0    10G  0 lvm  /media/WD3tbHDD1/projects-mount
  &#9500;&#9472;WD--vg1-media                253:4    0    50G  0 lvm  /media/WD3tbHDD1/media-mount
  &#9500;&#9472;WD--vg1-cloudy               253:5    0     5G  0 lvm  /media/WD3tbHDD1/cloudy-mount
  &#9492;&#9472;WD--vg1-dfay                 253:7    0   200G  0 lvm  /media/WD3tbHDD1/dfay-mount
sdc                                8:32   0   2.7T  0 disk
&#9492;&#9472;sdc1                             8:33   0   2.7T  0 part
  &#9500;&#9472;WD--vg2--bak-lv_serverOS_bak 253:3    0   500G  0 lvm  /media/WD3tbHDD2/backup-serverOS
  &#9492;&#9472;WD--vg2--bak-lv_data_bak     253:6    0   512G  0 lvm  /media/WD3tbHDD2/backup-data

```


As you can see my ServerOS (sda) is all lvm with separate container partitions.  

I used snapshots of each partitions and performed an rdiff-backup of each, to my (sdc) spinning HDD mounted at /media/WD3tbHDD2/backup-serverOS/...  subfolder structure matching my OS structure:
```

# ls -al
drwx------  4 root root  4096 Dec 31  1969 boot-efi-sda1
drwxr-xr-x  5 root root  4096 Jul 26 22:46 boot-sda2
drwxr-xr-x  6 root root  4096 Apr 12 20:30 home
drwx------  2 root root 16384 Jul 20 19:37 lost+found
drwxr-xr-x  4 root root  4096 Apr 14 21:03 opt
drwxr-xr-x 23 root root  4096 Jul 26 22:13 root
drwxr-xr-x  4 root root  4096 Feb  9 19:06 srv
drwxrwxrwt 10 root root  4096 Jul 28 17:11 tmp
drwxr-xr-x 12 root root  4096 Apr  9 20:35 usr
drwxr-xr-x 15 root root  4096 Apr  9 20:37 var

```

Each process involved essentially these same 5 steps as I show here on /root, except for the rdiff-backup logic varied some depending on what I wanted to backup in each filesystem:
```

1) lvcreate -L3G -s -n root_snap /dev/LVG/root
2) mount /dev/LVG/root_snap /mnt/snapshots/root_snap
3) rdiff-backup -v5 --print-statistics --exclude /mnt/snapshots/root_snap/mnt --exclude /mnt/snapshots/root_snap/media /mnt/snapshots/root_snap /media/WD3tbHDD2/backup-serverOS/root
4) umount /mnt/snapshots/root_snap
5) lvremove -f /dev/LVG/root_snap

```

Now I'm working on the best way to bash script this and invoke with a cron periodically.  However, I'm not sure if I should use 1 script file and sequentially rdiff each partition one at a time; or, if I should have a separate script for each partition and schedule them at intervals.  

Also, I haven't figured out if there is a way to do simultaneous snapshots of all partitions at once.  My thinking here is it would be nice to have a snapshot of the entire OS at the same exact point in time, but this just may not be feasible with OS broken up into separate partitions.

Anyway, here is my script for /root so far:
```

#!/bin/bash
####################################
#
# Creates LVM snapshot & invokes rdiff-backup then removes the snapshot. Will run using a cron job.
#
####################################
lvcreate -L3G -s -n root_snap /dev/LVG/root
sleep 2
mount /dev/LVG/root_snap /mnt/snapshots/root_snap

rdiff-backup -v5 --print-statistics \
  --exclude /mnt/snapshots/root_snap/media \
  --exclude /mnt/snapshots/root_snap/mnt \
  //mnt/snapshots/root_snap \
  /media/WD3tbHDD2/backup-serverOS/root

umount /mnt/snapshots/root_snap
lvremove -f /dev/LVG/root_snap
sleep 2
.
.
.

```

---

### Post by TheFu on 2019-07-28
I would .... 

Simplify the LVs. Any LV smaller than 6G isn't needed. Just merge them in /.  Managing tiny LVs/partitions isn't worth the hassles anymore.  All those old posts about having separate /usr and /srv and /opt were for a different age in storage that ended long, long, ago.  Having a separate /var/ could make sense, depending on the server.

I'd make all commands use the full path to the command. This will save dumb problems when you run in a crontab. Cron has much fewer environment variables, so set any you actually need. Don't trust the PATH, for example.

I'd verify that the mounts actually work. If they don't, bad things can happen.

There is an idea from priority programming called "data homogeneity" - it means that data on different priorities are exchanged a a specific time to ensure consistency.  What does this mean for your backup?  Create all the snapshots for all the LVs at the same time, so the data is all frozen at effectively the same instance, not 2 to 50 minutes apart.  There are times when that could be very bad if different parts of the backups aren't consistent. Just depends on the server processes involved.

For the rdiff-backup, you probably want --exclude-special-files as an option.
I didn't see the rdiff-backup where you remove old backups from 180day ago.  Best to built that into the backup script now.

I also generate a backup summary report daily and email that to my main email address. Something simple about the backup for each system - basically just greps from the statistics rdiff-backup created. This is run on my backup server, not any of the clients.
```
#!/bin/sh

DOMUS="spam2 icarus hadar romulus regulus blog44 nextcloud posc zcs45 pi3 pi2 abydos celestis istar"
SOURCE_DIR="/Backups" 
TODAY=`/bin/date "+%F"`
for D in $DOMUS ; do
    echo "=== Time for Backups to $D === "
    nice /bin/egrep 'TotalDestinationSizeChange|StartTime|EndTime|ElapsedTime' $SOURCE_DIR/$D/rdiff-backup-data/session_statistics.$TODAY*.data
    echo "
"
done
exit;
```
That script runs AFTER all daily backups complete, but can only be run on the same day to return anything. It could be more complex, but why?

But you do your situation.

---

### Post by LHammonds on 2019-07-29
I still prefer the separate partitions.  If you know exactly what is going to run on the server and where the data growth is, that can be adjusted to just those partitions but from experience, servers tend to get re-purposed or services added to them that were not originally planned and thus, might change the partition growth requirements.  I prefer to error on the side of caution to avoid situations that could cause my root partition to fill up and cause downtime.

Regarding the backup solution, no matter how you do the details, you should make sure to at least cover the 3-2-1 rule.  There are other variations to that general rule-of-thumb but its a great starting point.  Make sure you have 3 copies of your data on at least 2 different forms of media (such as 2 different physical disks) and have one of those copies offsite.  That will cover a lot of potential data loss scenarios.

LHammonds

---

### Post by aljames2 on 2019-08-04
Thanks for the help.

I see this —exclude-special-files in a lot of scripts.  The man page defines this as:  “Exclude all device files, fifo files, socket files, and symbolic links.”

Are these always unessential files to backup?

I should read up more on what these aspects in Linux are.  Any reading recomm would help.

---

### Post by oldfred on 2019-08-04
Good housekeeping also reduces your files that get backed up.
Log files can grow even with archives. Very old ones do not need to be saved.
Before system let number of kernels grow, now you only have two, normally.
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)

       Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders) & 
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by TheFu on 2019-08-04
First, I need to say, when LHammonds writes, I want to read it.  Good stuff to consider, even if it doesn't fit my current needs.

--exclude-special-files is a really good thing.  Try to backup /dev/zero .... let me know when that finishes.  Hint - never. 

Same for fifos, devices, and sockets. Your backup will never finish if it is trying to read from any of those.   I'd need to read more specifics about the symbolic links - I'm pretty certain it backs up the link, but doesn't follow it.  That is the behavior you want.  rdiff-backup currently doesn't handle sparse files well.  If you didn't specifically create a sparse file, then you probably don't need to worry about it.  gnutar and rsync have specific options to deal with sparse files.   I use zimbra for an email/communications server. In the last 2 yrs, that project decided to make an LDAP db file into a sparse file.  On disk, it is 2.5MB, but it will explode to 80GB if copied or backed up without those special options.  I make a tar.gz file of it just before doing my normal rdiff-backup. Also, I specifically exclude the sparse file from my backups.  Some people choose to use sparse files with their virtual machine storage.  Just something of which to be aware. 

I clean up lots of unwanted files in HOME before doing daily backups, so I don't need to exclude them.  Image caches, email caches, anything not profile related for browsers, and I wipe anything for adobe stuff - like flash local storage and html5 local storage, which is generally used to track users while online.

Also, there are parts of the pseudo-file systems that you don't want.  Don't backup /sys or /proc or /dev at all.  You only want real file systems, not fake ones. Because almost everything in Unix is a file ... 
[https://en.wikipedia.org/wiki/Everything_is_a_file](https://en.wikipedia.org/wiki/Everything_is_a_file) - see link to Unix Architecture in the article.
[https://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/](https://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/) 

No real book recommendations for normal people. 
Most of my knowledge came from being a cross-platform C developer for a long time.  Understanding the many different ways that different threads or processes can communicate between each other leads to an understanding of sockets, FIFOs, named-pipes, shared memory and shared libraries with the same CS, but different DSes.  In Windows, you can force a DS to be shared by the processes using the DLL, which can be a huge security problem.  There are a few books on those subjects, but they are for C programmers.

---

### Post by aljames2 on 2019-08-05
My script <below> is working and I verified my mounts and that snaps are all effectively removed after rdiff-backup completes.  I learned it's important to backup empty mount-point directories otherwise /etc/fstab mounts won't work.  However, I suppose as part of the restore process I could view the fstab file and manually recreate the mount points but that seems to be unnecessary work.

I would like learn a little more on streamlining my script with variables but that will be another day.

I'd like to add a few lines of code that writes the stdout (status/errors/etc) of the backup process to a file.  I'll play around with the script TheFu shared and figure out what works for me.

Open to other suggestions.

A big help everyone here was, many thanks !!  :cool:

```

#!/bin/sh
##########################
#
# Below performed on each Ubuntu serverOS LVM partition:
# Creates LVM snapshot & mounts it.
# Run rdiff-backup to separate local HDD, then unmounts & removes snapshot.
# Removes backups older than 180 days old.
# Will run using a cron job.
#
##########################

# backup package lists - credit TheFu
/bin/mkdir -p /tmp/backups

/usr/bin/apt-mark showauto > /tmp/backups/pkgs_auto.lst
/usr/bin/apt-mark showmanual > /tmp/backups/pkgs_manual.lst

########## ROOT ##########
/sbin/lvcreate -L3G -s -n root_snap /dev/LVG/root
sleep 2
/bin/mount /dev/LVG/root_snap /mnt/snapshots/root_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  --exclude /mnt/snapshots/root_snap/proc \
  --exclude /mnt/snapshots/root_snap/dev \
  --exclude /mnt/snapshots/root_snap/sys \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/projects-mount/** \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/media-mount/** \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/cloudy-mount/** \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/dfay-mount/** \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD2/backup-serverOS/** \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD2/backup-data/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/home_snap/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/opt_snap/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/root_snap/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/srv_snap/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/usr_snap/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/var_snap/** \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/tmp_snap/** \
  /mnt/snapshots/root_snap \
  /media/WD3tbHDD2/backup-serverOS/root

/bin/umount /mnt/snapshots/root_snap
/sbin/lvremove -f /dev/LVG/root_snap
sleep 2
########## VAR ##########
/sbin/lvcreate -L3G -s -n var_snap /dev/LVG/var
sleep 2
/bin/mount /dev/LVG/var_snap /mnt/snapshots/var_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /mnt/snapshots/var_snap \
  /media/WD3tbHDD2/backup-serverOS/var

/bin/umount /mnt/snapshots/var_snap
/sbin/lvremove -f /dev/LVG/var_snap
sleep 2
########## TMP ##########
/sbin/lvcreate -L2G -s -n tmp_snap /dev/LVG/tmp
sleep 2
/bin/mount /dev/LVG/tmp_snap /mnt/snapshots/tmp_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /mnt/snapshots/tmp_snap \
  /media/WD3tbHDD2/backup-serverOS/tmp

/bin/umount /mnt/snapshots/tmp_snap
/sbin/lvremove -f /dev/LVG/tmp_snap
sleep 2
########## HOME ##########
/sbin/lvcreate -L2G -s -n home_snap /dev/LVG/home
sleep 2
/bin/mount /dev/LVG/home_snap /mnt/snapshots/home_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /mnt/snapshots/home_snap \
  /media/WD3tbHDD2/backup-serverOS/home

/bin/umount /mnt/snapshots/home_snap
/sbin/lvremove -f /dev/LVG/home_snap
sleep 2
########## USR ##########
/sbin/lvcreate -L3G -s -n usr_snap /dev/LVG/usr
sleep 2
/bin/mount /dev/LVG/usr_snap /mnt/snapshots/usr_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /mnt/snapshots/usr_snap \
  /media/WD3tbHDD2/backup-serverOS/usr

/bin/umount /mnt/snapshots/usr_snap
/sbin/lvremove -f /dev/LVG/usr_snap
sleep 2
########## SRV ##########
/sbin/lvcreate -L2G -s -n srv_snap /dev/LVG/srv
sleep 2
/bin/mount /dev/LVG/srv_snap /mnt/snapshots/srv_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /mnt/snapshots/srv_snap \
  /media/WD3tbHDD2/backup-serverOS/srv

/bin/umount /mnt/snapshots/srv_snap
/sbin/lvremove -f /dev/LVG/srv_snap
sleep 2
########## OPT ##########
/sbin/lvcreate -L3G -s -n opt_snap /dev/LVG/opt
sleep 2
/bin/mount /dev/LVG/opt_snap /mnt/snapshots/opt_snap

/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /mnt/snapshots/opt_snap \
  /media/WD3tbHDD2/backup-serverOS/opt

/bin/umount /mnt/snapshots/opt_snap
/sbin/lvremove -f /dev/LVG/opt_snap
sleep 2
########## BOOT ##########
/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  --exclude /boot/efi \
  /boot \
  /media/WD3tbHDD2/backup-serverOS/boot-sda2
sleep 2
########## BOOT-EFI ##########
/usr/bin/rdiff-backup -v4 --print-statistics --exclude-special-files \
  /boot/efi \
  /media/WD3tbHDD2/backup-serverOS/boot-efi-sda1
######## REMOVE BACKUPS OLDER THAN 180 DAYS OLD
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/root
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/var
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/tmp
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/home
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/usr
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/srv
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/opt
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/boot-sda2
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/boot-efi-sda1
########## END ##########

```

---

### Post by TheFu on 2019-08-06
I have some concerns that this can't be restored. Let us know how the testing goes.  My method requires 30-45min for a restore, unless there is TB and TB of data too.  The core OS, apps, settings and everything that isn't TB and TB of data is ready and available in that timeframe.
 
Use variables to make things easier to read and easier to maintain.
```
RDIFF=/usr/bin/rdiff-backup 
DAYS=180D 
SRC_TOP=/mnt/snapshots
TGT_TOP=/media/WD3tbHDD2/backup-serverOS

```Then you can use those later so:
```
/usr/bin/rdiff-backup --remove-older-than 180D /media/WD3tbHDD2/backup-serverOS/root 
```
becomes
```
$RDIFF      --remove-older-than  $DAYS         $TGT_TOP/root
```
Which is still clear, but the differences jump out if there are 10 similar lines, which is really the important part.  Stupid typos are much less likely this way.

Because I backup about 20 systems, I need to have the hostname in the path, so it is clear which system backups are stored where.

---

### Post by aljames2 on 2019-08-12
I cleaned up my script and it runs without any errors.   I have a separate rdiff-backup for each LVM partition.  I also have backups of my boot partitions (non-LVM).  This is a bare metal setup with OS on SSD.

In my mind the worst case scenario is my root partition crashes and the system won’t boot up.  I want to practice restoring my root partition.  My concern is I’ve read that rdiff-backup restore command could wipe my mounted HDD backup drives if not careful, unless I indicate read-only.  

I’m also trying to figure out the best environment to boot up to in order to run the restore.  I have looked at SystemRescueCD but they do not integrate rdiff anymore.  Perhaps an Ubuntu Server on a USB pendrive is another option.  Basically, I don’t feel that I have a test environment or a method figured out yet.  If I set up a VirtualBox test environment  I am assuming I will need eight partitions matching my current set up in order to properly test?  I know I have achieved nothing yet until I have a restore plan...that much I know.

---

### Post by TheFu on 2019-08-13
I use a standard Ubuntu-Mate desktop install flash drive.  Really, any Ubuntu of the same release should be close enough.

I've already made my suggestions against having separate rdiff-backup commands run for each LV.  I think that is a bad idea and complicates things that don't need to be complicated and breaks data homogeneity.  Additionally, I wouldn't store stuff to be backed up in /tmp/. Some of that data is *sensitive*.  I put it into /root/backup/.  /root has 700 permissions, so non-root users can't see it.

Don't confuse partitions and LVs.  I suggested merging them which would also simplify the restore.  As long as the files "appear" to be in the correct places under /, the back-end storage used doesn't matter.  You'll just need to fix the fstab as needed. fstab stuff is really easy ... plus you'll have examples from backing up /etc/.

But it is your system. You do what makes sense to you.  I know my restores take 30-45 minutes.

---

### Post by aljames2 on 2019-08-25
I consolidated my logical volumes because in my use case as home server they are not large and more complexity is not needed.  I'm not serving all the employees at IBM ;)

Here's my latest, working script for using rdiff-backup to backup my server OS.  I could probably carve out more from my backups but since these are increments they aren't taking up much space.  Thanks again for the coding tips and suggestions throughout this thread :D

```

#!/bin/bash
##########################
#
# Creates LVM snapshot & mounts it.
# Runs rdiff-backup to separate local HDD, then unmounts & removes the snapshot.
# Removes backups older than 180 days old.
# Will run using a cron job.
#
##########################

RDIFF=/usr/bin/rdiff-backup
DAYS=180D
SRC_TOP=/mnt/snapshots
TGT_TOP=/media/WD3tbHDD2/backup-serverOS

# backup package lists
/usr/bin/apt-mark showauto > /root/backup/pkgs_auto.lst
/usr/bin/apt-mark showmanual > /root/backup/pkgs_manual.lst

########## ROOT ##########
/sbin/lvcreate -L6G -s -n root_snap /dev/LVG/root
sleep 2
/bin/mount /dev/LVG/root_snap /mnt/snapshots/root_snap

$RDIFF -v5 --print-statistics --exclude-special-files \
  --exclude /mnt/snapshots/root_snap/proc/'**' \
  --exclude /mnt/snapshots/root_snap/dev/'**' \
  --exclude /mnt/snapshots/root_snap/sys/'**' \
  --exclude /mnt/snapshots/root_snap/mnt/snapshots/root_snap/'**' \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/projects-mount/'**' \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/media-mount/'**' \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/cloudy-mount/'**' \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD1/dfay-mount/'**' \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD2/backup-serverOS/'**' \
  --exclude /mnt/snapshots/root_snap/media/WD3tbHDD2/backup-data/'**' \
  $SRC_TOP/root_snap \
  $TGT_TOP/root

/bin/umount /mnt/snapshots/root_snap
/sbin/lvremove -f /dev/LVG/root_snap
sleep 2
########## BOOT ##########
$RDIFF -v4 --print-statistics --exclude-special-files \
  --exclude /boot/efi \
  /boot \
  $TGT_TOP/boot-sda2
sleep 2
########## BOOT-EFI ##########
$RDIFF -v4 --print-statistics --exclude-special-files \
  /boot/efi \
  $TGT_TOP/boot-efi-sda1
########## REMOVE BACKUPS OLDER THAN 180 DAYS OLD ##########
$RDIFF --remove-older-than $DAYS $TGT_TOP/root
$RDIFF --remove-older-than $DAYS $TGT_TOP/boot-sda2
$RDIFF --remove-older-than $DAYS $TGT_TOP/boot-efi-sda1
########## END ##########

```

---

### Post by TheFu on 2020-02-21
aljames2, 

Just curious, how is this working?  Did the restore go as smooth as you'd like?

A results report would be helpful to others.
-TF

---

### Post by kevdog on 2020-02-21
One thing I've started doing, in addition to your scripts is having copies of common things -- like .zshrc, .z10 and a basic installed package list uploaded to a git repository.  This isn't really for backup purposes but rather useful when provisioning new machines.  I suppose it could be used for backup of some non-sensitive files.

I prefer borg over rdiff-backup. You can read about the differences in various places:[https://www.reddit.com/r/linux/comments/42feqz/i_asked_here_for_the_optimal_backup_solution_and/](https://www.reddit.com/r/linux/comments/42feqz/i_asked_here_for_the_optimal_backup_solution_and/)  [https://blog.mdda.net/oss/2019/01/09/borg-backup](https://blog.mdda.net/oss/2019/01/09/borg-backup).  Its probably most useful if you need encrypted backups.  Vorta is a nice GUI that can run borg on the backend, or you can do it the old fashioned way with either scripts and combination of crontabs or systemd timers.  I'm really into systemd timers lately so I prefer that method.  I don't like splitting things between cron and systemd timers since I forget what I put under which.

---

### Post by aljames2 on 2020-02-23
I am working to figure out a restore sequence.  The scenario I’m testing is a complete restore to a separate blank HDD.  I get stuck at boot-up giving me the GRUB2 command line.  The issue I suspect is the UUIDs are different and therefore the grub.cfg needs updating.  I already updated the /etc/fstab with the new UUIDs.  

I tried a Live USB boot and mounted my newly restored system partitions to it at /mnt:
```
sda1   /boot/efi
sda2   /boot
sda3   /
```

However, when I tried to install & update grub via chroot /mnt I keep getting failure with chroot not finding /bin/bash when it is really there.

I was able to rdiff-backup restore my backups to the partitions but of course, it’s not a solution until I get it to boot.

Still working on it.  I feel that I’m close..

---

### Post by TheFu on 2020-02-23
Which is part of the reason that I just do a fresh install, restore data, /home/, specific system settings (not FSTAB or BOOT anything!), then feed a list of manually installed programs (apt-mark) in the apt to be installed.  As the programs install, they see the prior system settings and data, don't touch any of it then bring up each program.  For under 15G of data, that is done in 30-45 min from the decision to reinstall.  When all done, it has all the data, settings, programs, that was on the prior-to-failure system, so it effectively **is** the same system.

During the installation, I can change almost any of the hardware or storage layout or add/remove LUKS encryption, since the backups aren't tightly coupled to the storage layout.  Most important, I don't care about the /boot/ area at all. The fresh install will address that.

---

### Post by kevdog on 2020-02-24
Can you post the error exacty?

I think what you are trying to do is going to work.  Once you changed the uuids, did you rebuild the initramfs with mkinitcpio?

I did something kind of similar to what you are doing -- albeit with arch linux and zfs on root.  I was working with snapshots and basically trying to copy the snapshots to a new installation.  I really wasn't concerned as you are with backups -- I was trying to use this as a base installation for a VM which then I could go onto modify -- I basically wanted to use this copy several times so I didn't have to reinstall everything from scratch over and over again.

My link is here:[https://bbs.archlinux.org/viewtopic.php?id=252587](https://bbs.archlinux.org/viewtopic.php?id=252587).  It's probably not going to be totally relevant to you however you'll see the steps are similar.  You might need to rename the host and might need to modify things for networking since the MAC address of the system is different -- idk.

---

### Post by aljames2 on 2020-02-24
@TheFu, lesson learned.  Given that a fresh server install on the new media is somewhat trivial and fast, it doesn’t make sense with my setup to try to glue all the pieces back together to rebuild the server.  I will work on an rdiff-backup —include method to backup the essentials including apt-mark references.  Thanks!

Thanks @kevdog, I may keep tinkering with it some in my test environment but I’m losing faith in it...especially from a time investment standpoint.  In my case I “only” changed the HDD.  If the server blew up and I introduced more than just a new HDD, such as a different motherboard and CPU, the complexity restoring (if possible) from my current backups just multiplied, and so did the risk.

---

### Post by kevdog on 2020-02-24
FWIW I'm using systemd-boot (aka gummiboot) which intergrates really well with zfs.  It really simplifies the boot process. I know you're using grub.   I know I'm like making your job a lot more difficult, but it is really useful to be able to do a zfs send/receive on your root partition, put the received partition into a new VM, chroot into installation, install kernels and regenerate initramfs, and boom your good to go.

---

### Post by aljames2 on 2020-02-25
Using —include I have to figure out all the critical parts to backup.  I’m thinking these:
/home /root /etc /usr/local ...others?  Along with my apt-mark reference docs which will be created inside the backup script.

Am I capturing enough, what about these?

-user account login information
-firewall UFW configuration
-fail2ban
-custom scripts in usr/local/bin & sbin
-SSH keys
-custom bash aliases
-netplan configuration

---

### Post by TheFu on 2020-02-25
I think you are trying to be too specific about tiny areas on a file system.  Get /etc/ and that's most of the configs.  IMHO, if customized comfigs are being put somewhere else, that's a design flaw.  The UFW guys do this (/lib/ufw/) if you manually use **sudo ufw** to add rules.  Bad, bad, admin for doing that.  System config belong in /etc/ ... period.

[https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432](https://ubuntuforums.org/showthread.php?t=2436006&p=13928432#post13928432) has a simple backup script. It doesn't 'pull" unfortunately.  Backups really should be "pulled" by the backup server to prevent malware problems.

isn&#8217;t the firewall confjg inside /etc/?
ssh keys will be in /root and /home/ .

yes, get /usr/local/  .. want /usr/local/etc/ and share and ..... 
fajl2ban confjg is in /etc/ , so are local users, groups, and any LDAP configs.

What about /var/lib/ ?   that's where DBs usually get placed?  For small DBs, just dump the DB to text usng the dump tool and gzip it. Lots of examples in these forums.  For larger DBs, probably want to backup using a quiesced snapshot.

/var/www/?

/opt/?

Some people install custom themes manually.  Those seem to go somewhere odd. I don't do that stuff. If you do, get those backed up.

Every system is a little different. Only the admin can know.

For exmple, sometimes I've been bad and installed ruby gems or perl cpan modules system-wide.  This was before I started usng rbenv and perlbrew to keep my development completely separate from the system stuff.  Where I made that mistake, I need to backup the gems and perl modules.  It is also handy to have a list of all of each installed, so I use the appropriate tool to make that list for each language AND ensure those lists get included in my backups.  Sometiimes haviing informaton about a system stored usng the normal commands is better than having the actual config files. Sure /etc/lvm/ has all the LVM data, but I'd rather have pvs, vgs, lvs output when it is time to restore a system.  Also want a custom lsblk and parted -lm which can be fed in later to have exactly the same partitions created on a new disk.  There are a few other specific system commands that generate tiny text files. Better to have them and not need them than the alternative.

---

### Post by aljames2 on 2020-02-27
Thanks!  This script seems to catch everything I need to do a restore and I managed to do it first time on a spare hard drive in about 50 minutes 'ish.  That's from using a GParted USB to wipe the old drive partitions and then a Ubuntu Server USB reinstall, to restoring mount-points, installing packages, SSH keys work, my firewall is happy, I guess I got it all.  If not, I know where to go get it :)

```

#!/bin/bash
##########################
#
# rdiff-backup script
#
# Not a full system backup. Creating daily versioned backups
# of data & apt-mark reference files to enable quick restoration
# onto # a freshly reinstalled server.
#
# Data to --include is /home /root /etc /usr/local
#
# FIRST: Clean up trash inside the HOME directories before running the backup
#
# Will run using a cron job
#
##########################

RDIFF=/usr/bin/rdiff-backup
DAYS=180D
SRC_TOP=/mnt/snapshots/root_snap
TGT_TOP=/backups/WD3HDD1/systems-mnt/Servers/ubt/rdiff_backups
REF=/root/backup

## backup package lists & other system info for restore reference ##
/usr/bin/dpkg --get-selections > $REF/pkgs_selection.lst
/usr/bin/apt-mark showauto > $REF/pkgs_auto.lst
/usr/bin/apt-mark showmanual > $REF/pkgs_manual.lst
/sbin/pvdisplay > $REF/pvdisplay.lst
/sbin/vgdisplay > $REF/vgdisplay.lst
/sbin/lvdisplay > $REF/lvdisplay.lst
/sbin/parted -lm > $REF/parted.lst
/sbin/blkid > $REF/blkid.lst
/bin/df -h > $REF/df.lst
/bin/lsblk -o name,size,type,fstype,mountpoint > $REF/lsblk.lst
/usr/bin/lshw -short > $REF/lshw_hardware.lst
/bin/ls -al > $REF/ls.lst

## MOUNT STORAGE LVs ##
/bin/mount -v /dev/WD-vg1/internet /backups/WD3HDD1/internet-mnt || { echo "$(date) mount storage internet-mnt failed" >> ~/backup_errors.txt ; exit 1; }
/bin/mount -v /dev/WD-vg1/storage /backups/WD3HDD1/storage-mnt || { echo "$(date) mount storage storage-mnt failed" >> ~/backup_errors.txt ; exit 1; }
/bin/mount -v /dev/WD-vg1/systems /backups/WD3HDD1/systems-mnt || { echo "$(date) mount storage systems-mnt failed" >> ~/backup_errors.txt ; exit 1; }
/bin/mount -v /dev/WD-vg1/windows /backups/WD3HDD1/windows-mnt || { echo "$(date) mount storage windows-mnt failed" >> ~/backup_errors.txt ; exit 1; }
sleep 2

## CREATE THE SNAPSHOT ##
/sbin/lvcreate -L6G -s -n root_snap /dev/LVG/root || { echo "$(date) create snapshot failed" >> ~/backup_errors.txt ; exit 1; }
sleep 2

## MOUNT THE SNAPSHOT ##
/bin/mount -v /dev/LVG/root_snap $SRC_TOP || { echo "$(date) mount snapshot failed" >> ~/backup_errors.txt ; exit 1; }

## THE BACKUP ##
$RDIFF -v5 --print-statistics --exclude-special-files \
  --include $SRC_TOP/home \
  --include $SRC_TOP/root \
  --include $SRC_TOP/etc \
  --include $SRC_TOP/usr/local \
  --include $SRC_TOP/DataShares \
  --include $SRC_TOP/backups/WD3HDD1/internet-mnt --exclude $SRC_TOP/backups/WD3HDD1/internet-mnt/'**' \
  --include $SRC_TOP/backups/WD3HDD1/storage-mnt --exclude $SRC_TOP/backups/WD3HDD1/storage-mnt/'**' \
  --include $SRC_TOP/backups/WD3HDD1/systems-mnt --exclude $SRC_TOP/backups/WD3HDD1/systems-mnt/'**' \
  --include $SRC_TOP/backups/WD3HDD1/windows-mnt --exclude $SRC_TOP/backups/WD3HDD1/windows-mnt/'**' \
  --exclude $SRC_TOP/'**' \
  $SRC_TOP \
  $TGT_TOP

## Checking rdiff-backup command success or error
status=$?
if [ $status != 0 ]; then
        echo "rdiff-backup exit Code: $status - Command Unsuccessful" >> ~/backup_errors.txt;
fi

## UMOUNT THE SNAPSHOT ##
/bin/umount -v $SRC_TOP || { echo "$(date) umount snapshot failed" >> ~/backup_errors.txt ; exit 1; }

## REMOVE THE SNAPSHOT ##
/sbin/lvremove -f /dev/LVG/root_snap || { echo "$(date) remove snapshot failed" >> ~/backup_errors.txt ; exit 1; }
sleep 2

## REMOVE BACKUPS OLDER THAN 180 DAYS OLD ##
$RDIFF --force --remove-older-than $DAYS $TGT_TOP

## UMOUNT STORAGE LVs ##
/bin/umount -v /backups/WD3HDD1/internet-mnt || { echo "$(date) umount storage internet-mnt failed" >> ~/backup_errors.txt ; exit 1; }
/bin/umount -v /backups/WD3HDD1/storage-mnt || { echo "$(date) umount storage storage-mnt failed" >> ~/backup_errors.txt ; exit 1; }
/bin/umount -v /backups/WD3HDD1/systems-mnt || { echo "$(date) umount storage systems-mnt failed" >> ~/backup_errors.txt ; exit 1; }
/bin/umount -v /backups/WD3HDD1/windows-mnt || { echo "$(date) umount storage windows-mnt failed" >> ~/backup_errors.txt ; exit 1; }

```

---

### Post by TheFu on 2020-02-27
Two concerns about the script.  

The mount doesn't get verified as completed.
The target storage should be validated as mounted with sufficient storage.

I've been burned by both of these issues.  They fail silently.


Oh ... and the remove-older-than ... if you run 2 backups in a single day, it needs the --force option to clean up the 2nd.  I don't know of any reason not to always use --force for that part.

---

### Post by aljames2 on 2020-02-29
I updated my script in #23 with some validations throughout.  

Not sure how to test the rdiff-backup output status if errors occur other than the if .. fi logic.  I guess I'll see the error in my log file if it does fail.

I tested the mount & umount validate commands and they work.

Couldn't figure out how to validate the --remove-older-than step.  I tried to test this step by inserting a mistake in the script that umounted the storage before running the --remove-older-than command.  This test returned fatal errors in the terminal but I couldn't get it to echo to my log file.  Therefore, I left out a validation on this step figuring it's not a critical step that is likely to fail.

---

### Post by TheFu on 2020-03-01
$? has the return code from the last command.  Non-zero means some fault.  That is common across all Unix programs.

0 = good
non-0 = bad - or, more likely, not perfect.

---

### Post by LHammonds on 2020-03-01
Example of how the "if error, if no error" code looks:

```

rdiff --option1=2 --option2=4
ReturnCode=$?
if [[ ${ReturnCode} != 0 ]]; then
  ## rdiff did not exit cleanly
  echo "`date +%Y-%m-%d_%H:%M:%S` ** ERROR: rdiff failed with code of ${ReturnCode} (Program Exit Code 2)" >> ${LogFile}
  f_cleanup
  exit 2
else
  ## Continue code here upon successful rdiff return code ##
  echo "`date +%Y-%m-%d_%H:%M:%S` -- rdiff completed." >> ${LogFile}
fi

```

It can be handled many different ways.  You could setup a case statement to handle specific return codes in a different manner.  The above example simply logs the error and quits the script assuming that continuing with this error is not practical.

You could log the error and even send yourself a txt alert message and/or email the log.

If you want to reference the return code multiple times, you need to save the return code in a variable like I showed because the 2nd time you reference $? will actually change because you then be getting the return code of the last command executed which was the if command.

---

### Post by aljames2 on 2020-03-01
```

rdiff --option1=2 --option2=4

```

I follow the script and understand it except this line.  I am using rdiff-backup vs. rdiff.  
I like that it writes to the log file if error or success.

And, is terminate script on exit code 2 preferable to exit code 1 for backup scripts?

---

### Post by LHammonds on 2020-03-02
It is just an example off the top of my head with fake options...sorry, thought that would have been obvious.  The rdiff line could have be shown as <INSERT COMMAND HERE>.

exit=1 or exit=2 or exit=3, etc. for a script doesn't matter in the slightest if you have nothing monitoring the exit code of your script.  But if you have email notification and include the exit code in your notification, it can help to pinpoint the exact exit point in your script which is helpful in large scripts with many potential exit points.

The "f_cleanup" is a custom function call that would be used to clean up any temporary files the script created before exit (which is something you would have to create in your script)

The ${LogFile} is a variable pointing to a log file and setup earlier in the script to be something like LogFile=/var/log/${0}.log.  The ${0} is the name of the script.

The example script was just to show some syntax.  If that were a real script, I would remove the else part completely as it is 100% not necessary.  Example:

```

<INSERT COMMAND HERE>
ReturnCode=$?
if [[ ${ReturnCode} != 0 ]]; then
  ## rdiff did not exit cleanly
  echo "`date +%Y-%m-%d_%H:%M:%S` ** ERROR: rdiff failed with code of ${ReturnCode} (Program Exit Code 2)" >> ${LogFile}
  f_cleanup
  exit 2
fi
echo "`date +%Y-%m-%d_%H:%M:%S` -- rdiff completed." >> ${LogFile}

```

The else part was unnecessary but if you needed to check for more conditions to handle a fatal error that requires the script to stop verses continuing on with warnings, then you could use a case statement like this:

```

<INSERT COMMAND HERE>
ReturnCode=$?
case ${ReturnCode} in
  2)
    ## command failure
    echo "ERROR: Command return code of ${ReturnCode}" >> ${LogFile}
    f_cleanup
    exit 2
    ;;
  0)
    ## command completed successfully.
    echo "INFO: Command completed." >> ${LogFile}
    ;;
  *)
    ## command completed with warning
    echo "WARNING: Command return code of ${ReturnCode}" >> ${LogFile}
    ;;
esac

```

In the above example, we know the return code of 2 is very bad so we handle the scenario by stopping the script.  It would be wise to log such an event and event send a txt message and/or email depending on how important it is to correct this error and re-run the script.

For all other return codes, we assume it to be safe enough to continue the script but we document in the log the 3 different states of the command (ERROR, WARNING or GOOD) and their return code in case you want to research it further.

When it comes to automating commands, the core of the automated commands might be 5 lines that you would type at the commandline but when automating via script, can turn into 100+ lines in order to handle the scenarios of the commands not working or partially working.  But usually, such things can be put inside custom functions and re-used over and over.

You just have to look at each core command of your script and think to yourself: "***how do I handle this command if it fails***"

LHammonds

---

### Post by aljames2 on 2020-03-02
Thanks for the details, this helps!

---

### Post by tasket on 2020-03-18
Hi,

Since LVM and virtual machines are part of the mix, you might find [Wyng]("https://github.com/tasket/wyng-backup") interesting. It backs up thin-provisioned LVs much the way btrfs-send and zfs-send do for their filesystems, using metadata for incremental backups so it doesn't have to compare (or hash) files byte-by-byte; it can find changes immediately. This is usually more efficient than traditional backup tools that ignore copy-on-write storage features. However, a matching storage format is not required for the backup archive... it only requires a Unix filesystem for back end storage.

I wrote a Wyng HowTo for Ubuntu here:
[https://ubuntuforums.org/showthread.php?t=2437700](https://ubuntuforums.org/showthread.php?t=2437700)

---

