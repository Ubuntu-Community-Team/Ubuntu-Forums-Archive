---
title: "booting in emergency mode... what is wrong [read-only file system?]"
date: 2023-09-23
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2023-09-23
Power when out, UPS battery ran out of power, power was lost

BIOS powered up when power was restored, but the system was waiting on user input (Ctrl+D to continue) before it started my VM (pfsense; my router)

it said see [FONT=monospace][COLOR=#000000]journalctl -xb[/COLOR][/FONT] [SUP](attached)[/SUP] for details (had to connect my portable monitor and grab a keyboard)

```
---md Status---
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid1 sda2[1] sdb2[0]
      124965888 blocks super 1.2 [2/2] [UU]
      bitmap: 1/1 pages [4KB], 65536KB chunk

md1 : active raid1 sdh1[1] sdg1[0]
      124966912 blocks super 1.2 [2/2] [UU]
      bitmap: 1/1 pages [4KB], 65536KB chunk

unused devices: <none>
---zfs Status---
  pool: mypool
 state: ONLINE
  scan: scrub repaired 0B in 00:01:57 with 0 errors on Sun Sep 10 00:25:59 2023
config:

        NAME                        STATE     READ WRITE CKSUM
        mypool                      ONLINE       0     0     0
          mirror-0                  ONLINE       0     0     0
            wwn-0x50014ee263e2b396  ONLINE       0     0     0
            wwn-0x50014ee263ce2c81  ONLINE       0     0     0
          mirror-1                  ONLINE       0     0     0
            wwn-0x50014ee263e27e85  ONLINE       0     0     0
            wwn-0x50014ee265d71fad  ONLINE       0     0     0

errors: No known data errors
---Disk Usage---
Filesystem      Size  Used Avail Use% Mounted on
/dev/md0p1      117G   13G   99G  12% /
/dev/md1p1      117G   19G   93G  17% /mnt/Data
mypool          7.2T   31G  7.1T   1% /mnt/HDD
chad@niceserver:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md0p1 during curtin installation
/dev/disk/by-id/md-uuid-ede07d21:4114781a:b6762645:db22bf0e-part1 /         ext4 defaults,noatime 0 1
# /mnt/Data was on /dev/md1p1 during curtin installation
/dev/disk/by-id/md-uuid-28843301:920a306f:47f8cd80:d4d35fcd-part1 /mnt/Data ext4 defaults,noatime 0 1
#/dev/disk/by-id/md-uuid-a1a41d92:421eda05:59f6da66:3d3f0f6e       /mnt/HDD  ext4 defaults         0 1
/mnt/Data/kvm-images    /home/chad/kvm/images    bind x-systemd.requires=/mnt/Data,defaults,bind  0 0
/mnt/HDD/www            /var/www                 bind x-systemd.requires=/mnt/HDD,defaults,bind   0 0
/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind x-systemd.requires=/mnt/HDD,defaults,bind   0 0
/swap.img               none                     swap sw                                          0 0
```

my guess is some mount order stuff with zfs and fsatab, but i do not know
edit found this: [https://www.reddit.com/r/zfs/comments/hpnmiw/systemd_mount_order_between_zfs_and_etcfstab_bind/](https://www.reddit.com/r/zfs/comments/hpnmiw/systemd_mount_order_between_zfs_and_etcfstab_bind/)
just edited /etc/fstab with x-system.after=zfs-mount.service maybe that will solve this issue?

---

### Post by MAFoElffen on 2023-09-23
It's a ZFS cache thing. It lost power and corrupted the cache, which was keeping track of the mounts when it goes to boot next. Both 1fallen and I have had to do this a few times over time for various reason. (We tend to break things while pushing them to the limits during testing.) LOL

This is only going to be a summary, as I have to go do something right now:
Boot from a LiveUSB, install intiramfs-zfs, export the pools, import the pools, mount the pools and datasets, chroot into the system, update-initramfs image. Exit the chroot. Exit the filesystem gracefully. Unmount, Reboot.

If you need more details, mayb 1fallen can jump in... or I will be back later. It's not a biggee. Everything is still there.

---

### Post by MAFoElffen on 2023-09-23
Back. But see no replies from you yet.

Booted from an Installer LiveUSB. Try. Open a terminal session.
```

sudo su
apt update
apt install -y zfs-initramfs zfsutils-linux
zpool export -a
zpool import -N -R /mnt rpool
zpool import -N -R /mnt bpool
UUID=$(zfs list | grep -m 1 'rpool/ROOT/ubuntu_' | cut -b 19-24 )
zfs mount rpool/ROOT/ubuntu_$UUID
zfs mount bpool/BOOT/ubuntu_$UUID
zfs mount -a
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run /mnt/run
chroot /mnt /bin/bash --login
mount -a

apt update
update-intramfs -c -k all
exit

mount | grep -v zfs | tac | awk '/\/mnt/ {print $3}' | \
    xargs -i{} umount -lf {}
zpool export -a
reboot

```

---

### Post by pqwoerituytrueiwoq on 2023-09-24
so a power outage will cause this to happen? can i automate a repair attempt? (having to use a live GUI session on a headless server is no fun)

right now the server is booted and running, i should be able to do it without using a live session, guessing there is a faster way since the server is up and running

```
chad@niceserver:~$ apt-cache policy zfs-initramfs zfsutils-linux 
zfs-initramfs: 
  Installed: (none) 
  Candidate: 2.1.5-1ubuntu6~22.04.1 
  Version table: 
     2.1.5-1ubuntu6~22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
        500 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
     2.1.2-1ubuntu3 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
zfsutils-linux: 
  Installed: 2.1.5-1ubuntu6~22.04.1 
  Candidate: 2.1.5-1ubuntu6~22.04.1 
  Version table: 
 *** 2.1.5-1ubuntu6~22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages 
        500 http://us.archive.ubuntu.com/ubuntu jammy-security/main amd64 Packages 
        100 /var/lib/dpkg/status 
     2.1.2-1ubuntu3 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
$ zfs list 
NAME     USED  AVAIL     REFER  MOUNTPOINT 
mypool  31.0G  7.09T     30.9G  /mnt/HDD


```

the power did go out again after the original post, before the UPS battery died i used a laptop to ssh in and run poweroff, when it booted up again (assuming it did not go out again then boot again) that would have been a clean shutdown and it still happened
at this time i have this modification to my /etc/fstab, no idea if it will help or not (have not rebooted since saving it)

```
$ cat /etc/fstab
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/md0p1 during curtin installation 
/dev/disk/by-id/md-uuid-ede07d21:4114781a:b6762645:db22bf0e-part1 /         ext4 defaults,noatime 0 1 
# /mnt/Data was on /dev/md1p1 during curtin installation 
/dev/disk/by-id/md-uuid-28843301:920a306f:47f8cd80:d4d35fcd-part1 /mnt/Data ext4 defaults,noatime 0 1 
#/dev/disk/by-id/md-uuid-a1a41d92:421eda05:59f6da66:3d3f0f6e       /mnt/HDD  ext4 defaults         0 1 
/mnt/Data/kvm-images    /home/chad/kvm/images    bind x-systemd.requires=/mnt/Data,defaults,bind  0 0 
/mnt/HDD/www            /var/www                 bind x-systemd.after=zfs-mount.service,x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind x-systemd.after=zfs-mount.service,x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
/swap.img               none                     swap sw                                          0 0
```[FONT=monospace]

[/FONT]when i tried to use ctrl+d the next time it was not enough to get it working, i had to use the reset button and press enter then reboot or something like that


and my pool is degraded now... one scrub and clear and it looks fine

---

### Post by #&amp;thj^% on 2023-09-24
So is everything back to norm?? you keep getting asked to reply, but nothing from you yet?
Also did you try the suggestion from post #3
```
apt-cache policy zfs-initramfs zfsutils-linux 
zfs-initramfs:
  Installed: 2.2.0~rc3-0ubuntu4
  Candidate: 2.2.0~rc3-0ubuntu4
  Version table:
 *** 2.2.0~rc3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu mantic/main amd64 Packages
        100 /var/lib/dpkg/status
zfsutils-linux:
  Installed: 2.2.0~rc3-0ubuntu4
  Candidate: 2.2.0~rc3-0ubuntu4
  Version table:
 *** 2.2.0~rc3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu mantic/main amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by MAFoElffen on 2023-09-24
He has no internet, because his Local LAN's router was virtually hosted on that machine, right? You are going to have a challenge with that... 

He might want to try to create a persistent Bootable Rescue USB that already has packages initramfs-zfs and zfsutils-linux installed so it so it can work with ZFS. With that portable bootable recovery device, then he wouldn't need a working network connection to recover his server...

***
At the OP: Isn't this the second time the power has gone off and this system has been done from a power surge? You say you have a UPS, but this has happened to your multitple times now, very recently. I think it it where me, I would look into adding more surge suppression and adding some batteries to your your UPS so that you have a longer power loss time. 

--AND/OR--

The UPS'es I had connected to my servers via USB and Network ports and used UPS Management software, such as apcupsd or Power Panel for Linux, so that when the power fails, you have an alarm and the server(s), after a certain time, that if the power does not come back up when that timer hits, that the server(s) can be told (by the management software) shutdown gracefully. automatically. You should really think about adding these to your disaster recovery plan.

Fortunately, working with you last time on ZFS, I know you keep good backups. When you get this resolved this time, I think you have a reoccurring problem that you need to plan for to save you some work and heartbreak. Luckily, you recently converted this server to ZFS, where it has better recovery options, and is safer in it's filesystem integrity than what you had previously.

In that recovery plan, I think you need to add a portable Persistent  LiveUSB that can work with ZFS (noted above), or add a basic recovery  partition, that also has copies of those two packages stored locally.

---

### Post by #&amp;thj^% on 2023-09-24
> **MAFoElffen said:**
> He has no internet, because his Local LAN's router was virtually hosted on that machine, right? You are going to have a challenge with that... 
Good to know Thanks for that
> **MAFoElffen said:**
> 
He might want to try to create a persistent Bootable Rescue USB that has initramfs-zfs and zfsutils-linux installed o it so it can work with ZFS.
Yep i have one already, although I've not had to use it yet but it's good to have for such cases.

---

### Post by MAFoElffen on 2023-09-24
To import and export the pool(s) if ZFS-On-Root, then you need to boot from a different device... so it can update the caches.

But if "booted and running"... then the caches will update on their own, and doing all that is unneeded. Right? If booted and running, why isn't your virtual router up?

I guess I am missing something in that equation...

---

### Post by #&amp;thj^% on 2023-09-24
> **MAFoElffen said:**
>  why isn't your virtual router up?

I guess I am missing something in that equation...

That makes two of us...

---

### Post by pqwoerituytrueiwoq on 2023-09-24
the instructions in post #3 are for use on a live session, I am not sure  what needs to be omitted to run them on a normal session

yes if i can't boot my server i have no internet access (well unless i pull out my WTR54GL) which i have not resorted to


When the power came back up the system booted and my VM had not started  as it was at the prompt to press Ctrl+D in emergency mode, upon pressing  CTRL+D my VM was started


Order of events:

[LIST=1]
[*]Power went out 
[*]UPS battery died 
[*]I got home from work (I'd guess about a hour and a half into the power outage as one of my UPS units was still on and died when i got in the door) 
[*]went to my mom's so i could get a shower 
[*]power came back 
[*]i got back home 
[*]began trying to figure out why my DHCP server was down 
[*]upon getting my portable monitor and the 1st USB keyboard i could find connected i read the messages and pressed Ctrl+D and everything was working 
[*]I made the 1st post (no photos attached) 
[*]fell asleep in my chair 
[*]Power went out again and i woke up 
[*]safely shutdown the server over SSH with a laptop and went to bed (it was running on UPS power) 
[*]When i got up power was back and my server was down again... 
[*]plugged a USB keyboard in and pressed Ctrl+D 
[*]nothing happened and i got the portable monitor out again (see attached photo, the short one) 
[*]ended up pressing the chassis reset button 
[*]Pressed crtl+D again (see attached photo, the tall one) 
[*]ended up pressing the chassis reset button 
[*]pressed enter instead of Ctrl+D 
[*]started trying to troubleshoot stuff 
[*]suddenly stuff was working (my beep speaker must not have sounded or i missed it, it should have beeped when the VM was started and again when it gave my server it's IP address) 
[*]at this time there were no replies here 
[*]made a attempt to fix this issue with the /etc/fstab thing as the sometimes it works sometimes not seems like a mount order issue 
[*]i have not rebooted the system just in case the issue is not resolved, hoping to get a reply here 
[*]found out i did not have [FONT=monospace][COLOR=#000000]apcupsd[/COLOR][/FONT] installed, got it installed and configured (guess i forgot to do that months ago)
[*]now we are here and everyone is confused as to the state of things [FONT=monospace][COLOR=#000000]$ [/COLOR][/FONT][FONT=monospace][COLOR=#000000]uptime -p [/COLOR]up 1 day, 15 hours, 3 minutes
[/FONT] 
[/LIST]

We had a tropical storm here Friday night, this is the 1st time my UPS batter has been insufficient to outlast a power outage since it was deployed, though in my EXP it is always around 30-60 min after the battery dies power comes back

---

### Post by MAFoElffen on 2023-09-24
First you should back off any changes you made to the fstab file. You should really keep a copy of that in your User Home directory... So you have a copy of what was working.

With it running, it should have refreshed the zpool cache files in /etc/zfs/zfs-list.cache/ already. Just to make sure, and that all is loaded early in the ramdisk image during boot, as a failsafe to that, all you should have to do is
```

sudo update-initramfs -c -k all

```
Then reboot to test.

It came up by itself? (Hiting <Enter> instead of <Cntrl><D>) Good deal.

---

### Post by pqwoerituytrueiwoq on 2023-09-25
this morning i noted some errors in my array from, but i was able to pass a scrub so i cleared it and the drive shows good in SMART, if i have ANOTHER bad sata cable... anyone know where i can get some high quality sata cables? preferablly shielded case this is getting anying, maybe that was just related to the power issue, but i will be keeping a eye on it

i will try the fstab changes to see if it gives a error, as long is it does not hurt i'd rather keep that change, maybe the option is redundant, maybe it is not eigther way it needs to behave in that way

that cache dir does not exist...

```
chad@niceserver:~$ ls -l /etc/zfs/zpool.cache  
-rw-r--r-- 1 root root 3724 Sep 25 09:32 /etc/zfs/zpool.cache 
chad@niceserver:~$ tree /etc/zfs/  
/etc/zfs/ 
&#9500;&#9472;&#9472; zed.d 
&#9474;   &#9500;&#9472;&#9472; all-syslog.sh -> /usr/lib/zfs-linux/zed.d/all-syslog.sh 
&#9474;   &#9500;&#9472;&#9472; data-notify.sh -> /usr/lib/zfs-linux/zed.d/data-notify.sh 
&#9474;   &#9500;&#9472;&#9472; history_event-zfs-list-cacher.sh -> /usr/lib/zfs-linux/zed.d/history_event-zfs-list-cacher.sh 
&#9474;   &#9500;&#9472;&#9472; pool_import-led.sh -> /usr/lib/zfs-linux/zed.d/pool_import-led.sh 
&#9474;   &#9500;&#9472;&#9472; resilver_finish-notify.sh -> /usr/lib/zfs-linux/zed.d/resilver_finish-notify.sh 
&#9474;   &#9500;&#9472;&#9472; resilver_finish-start-scrub.sh -> /usr/lib/zfs-linux/zed.d/resilver_finish-start-scrub.sh 
&#9474;   &#9500;&#9472;&#9472; scrub_finish-notify.sh -> /usr/lib/zfs-linux/zed.d/scrub_finish-notify.sh 
&#9474;   &#9500;&#9472;&#9472; statechange-led.sh -> /usr/lib/zfs-linux/zed.d/statechange-led.sh 
&#9474;   &#9500;&#9472;&#9472; statechange-notify.sh -> /usr/lib/zfs-linux/zed.d/statechange-notify.sh 
&#9474;   &#9500;&#9472;&#9472; vdev_attach-led.sh -> /usr/lib/zfs-linux/zed.d/vdev_attach-led.sh 
&#9474;   &#9500;&#9472;&#9472; vdev_clear-led.sh -> /usr/lib/zfs-linux/zed.d/vdev_clear-led.sh 
&#9474;   &#9500;&#9472;&#9472; zed-functions.sh 
&#9474;   &#9492;&#9472;&#9472; zed.rc 
&#9500;&#9472;&#9472; zfs-functions 
&#9500;&#9472;&#9472; zpool.cache 
&#9492;&#9472;&#9472; zpool.d 
    &#9500;&#9472;&#9472; ata_err -> /usr/lib/zfs-linux/zpool.d/ata_err 
    &#9500;&#9472;&#9472; cmd_to -> /usr/lib/zfs-linux/zpool.d/cmd_to 
    &#9500;&#9472;&#9472; defect -> /usr/lib/zfs-linux/zpool.d/defect 
    &#9500;&#9472;&#9472; dm-deps -> /usr/lib/zfs-linux/zpool.d/dm-deps 
    &#9500;&#9472;&#9472; enc -> /usr/lib/zfs-linux/zpool.d/enc 
    &#9500;&#9472;&#9472; encdev -> /usr/lib/zfs-linux/zpool.d/encdev 
    &#9500;&#9472;&#9472; fault_led -> /usr/lib/zfs-linux/zpool.d/fault_led 
    &#9500;&#9472;&#9472; health -> /usr/lib/zfs-linux/zpool.d/health 
    &#9500;&#9472;&#9472; hours_on -> /usr/lib/zfs-linux/zpool.d/hours_on 
    &#9500;&#9472;&#9472; iostat -> /usr/lib/zfs-linux/zpool.d/iostat 
    &#9500;&#9472;&#9472; iostat-10s -> /usr/lib/zfs-linux/zpool.d/iostat-10s 
    &#9500;&#9472;&#9472; iostat-1s -> /usr/lib/zfs-linux/zpool.d/iostat-1s 
    &#9500;&#9472;&#9472; label -> /usr/lib/zfs-linux/zpool.d/label 
    &#9500;&#9472;&#9472; locate_led -> /usr/lib/zfs-linux/zpool.d/locate_led 
    &#9500;&#9472;&#9472; lsblk -> /usr/lib/zfs-linux/zpool.d/lsblk 
    &#9500;&#9472;&#9472; media -> /usr/lib/zfs-linux/zpool.d/media 
    &#9500;&#9472;&#9472; model -> /usr/lib/zfs-linux/zpool.d/model 
    &#9500;&#9472;&#9472; nonmed -> /usr/lib/zfs-linux/zpool.d/nonmed 
    &#9500;&#9472;&#9472; nvme_err -> /usr/lib/zfs-linux/zpool.d/nvme_err 
    &#9500;&#9472;&#9472; off_ucor -> /usr/lib/zfs-linux/zpool.d/off_ucor 
    &#9500;&#9472;&#9472; pend_sec -> /usr/lib/zfs-linux/zpool.d/pend_sec 
    &#9500;&#9472;&#9472; pwr_cyc -> /usr/lib/zfs-linux/zpool.d/pwr_cyc 
    &#9500;&#9472;&#9472; realloc -> /usr/lib/zfs-linux/zpool.d/realloc 
    &#9500;&#9472;&#9472; rep_ucor -> /usr/lib/zfs-linux/zpool.d/rep_ucor 
    &#9500;&#9472;&#9472; r_proc -> /usr/lib/zfs-linux/zpool.d/r_proc 
    &#9500;&#9472;&#9472; r_ucor -> /usr/lib/zfs-linux/zpool.d/r_ucor 
    &#9500;&#9472;&#9472; serial -> /usr/lib/zfs-linux/zpool.d/serial 
    &#9500;&#9472;&#9472; ses -> /usr/lib/zfs-linux/zpool.d/ses 
    &#9500;&#9472;&#9472; size -> /usr/lib/zfs-linux/zpool.d/size 
    &#9500;&#9472;&#9472; slot -> /usr/lib/zfs-linux/zpool.d/slot 
    &#9500;&#9472;&#9472; smart -> /usr/lib/zfs-linux/zpool.d/smart 
    &#9500;&#9472;&#9472; smart_test -> /usr/lib/zfs-linux/zpool.d/smart_test 
    &#9500;&#9472;&#9472; smartx -> /usr/lib/zfs-linux/zpool.d/smartx 
    &#9500;&#9472;&#9472; temp -> /usr/lib/zfs-linux/zpool.d/temp 
    &#9500;&#9472;&#9472; test_ended -> /usr/lib/zfs-linux/zpool.d/test_ended 
    &#9500;&#9472;&#9472; test_progress -> /usr/lib/zfs-linux/zpool.d/test_progress 
    &#9500;&#9472;&#9472; test_status -> /usr/lib/zfs-linux/zpool.d/test_status 
    &#9500;&#9472;&#9472; test_type -> /usr/lib/zfs-linux/zpool.d/test_type 
    &#9500;&#9472;&#9472; upath -> /usr/lib/zfs-linux/zpool.d/upath 
    &#9500;&#9472;&#9472; vendor -> /usr/lib/zfs-linux/zpool.d/vendor 
    &#9500;&#9472;&#9472; w_proc -> /usr/lib/zfs-linux/zpool.d/w_proc 
    &#9492;&#9472;&#9472; w_ucor -> /usr/lib/zfs-linux/zpool.d/w_ucor 

2 directories, 57 files

```

---

### Post by pqwoerituytrueiwoq on 2023-09-25
now the issue is worse and i have my WTR54GL out

my md array for / is read-only as a result nothing is working

```
xubuntu@xubuntu:~$ cat /proc/mdstat 
Personalities : [raid1]  
md1 : active raid1 sdc1[0] sdd1[1] 
      124966912 blocks super 1.2 [2/2] [UU] 
      bitmap: 0/1 pages [0KB], 65536KB chunk 

md0 : active raid1 sdb2[0] sda2[1] 
      124965888 blocks super 1.2 [2/2] [UU] 
      bitmap: 0/1 pages [0KB], 65536KB chunk 

unused devices: <none> 
xubuntu@xubuntu:~$ sudo mdadm --detail /dev/md0 
/dev/md0: 
           Version : 1.2 
     Creation Time : Tue Sep 20 15:23:38 2022 
        Raid Level : raid1 
        Array Size : 124965888 (119.18 GiB 127.97 GB) 
     Used Dev Size : 124965888 (119.18 GiB 127.97 GB) 
      Raid Devices : 2 
     Total Devices : 2 
       Persistence : Superblock is persistent 

     Intent Bitmap : Internal 

       Update Time : Mon Sep 25 15:16:55 2023 
             State : clean  
    Active Devices : 2 
   Working Devices : 2 
    Failed Devices : 0 
     Spare Devices : 0 

Consistency Policy : bitmap 

              Name : ubuntu-server:0 
              UUID : ede07d21:4114781a:b6762645:db22bf0e 
            Events : 2154 

    Number   Major   Minor   RaidDevice State 
       0       8       18        0      active sync   /dev/sdb2 
       1       8        2        1      active sync   /dev/sda2 
xubuntu@xubuntu:~$ sudo mdadm --detail /dev/md1 
/dev/md1: 
           Version : 1.2 
     Creation Time : Tue Sep 20 15:23:25 2022 
        Raid Level : raid1 
        Array Size : 124966912 (119.18 GiB 127.97 GB) 
     Used Dev Size : 124966912 (119.18 GiB 127.97 GB) 
      Raid Devices : 2 
     Total Devices : 2 
       Persistence : Superblock is persistent 

     Intent Bitmap : Internal 

       Update Time : Mon Sep 25 15:17:00 2023 
             State : clean  
    Active Devices : 2 
   Working Devices : 2 
    Failed Devices : 0 
     Spare Devices : 0 

Consistency Policy : bitmap 

              Name : ubuntu-server:1 
              UUID : 28843301:920a306f:47f8cd80:d4d35fcd 
            Events : 3426 

    Number   Major   Minor   RaidDevice State 
       0       8       33        0      active sync   /dev/sdc1 
       1       8       49        1      active sync   /dev/sdd1

```

---

### Post by pqwoerituytrueiwoq on 2023-09-25
found the cause in my fstab file
```

#/mnt/HDD/www            /var/www                 bind x-systemd.after=zfs-mount.service,x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
#/mnt/HDD/www            /var/www                 bind x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
#/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind x-systemd.after=zfs-mount.service,x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
#/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind x-systemd.requires=/mnt/HDD,defaults,bind   0 0

```

how do i make it work with ZFS?
preferably something better than a cron job to run a script

```
@reboot /usr/local/sbin/zfs_binds
```

```
$ cat /usr/local/sbin/zfs_binds    
#/bin/sh 
while [ ! -d /mnt/HDD/www ] || [ ! -d /mnt/HDD/apt-cacher-ng ];do 
        sleep 1 
done 
if mountpoint -q /var/www;then 
        echo "/var/www is already mounted" 
else 
        mount --bind /mnt/HDD/www /var/www 
fi 
if mountpoint -q /var/cache/apt-cacher-ng;then 
        echo "/var/cache/apt-cacher-ng is already mounted" 
else 
        mount --bind /mnt/HDD/apt-cacher-ng /var/cache/apt-cacher-ng 
fi 
exit 0

```

---

### Post by #&amp;thj^% on 2023-09-25
May we see this:
```
sudo zfs get all | grep mountpoint

```

---

### Post by pqwoerituytrueiwoq on 2023-09-25
```
mypool  mountpoint            /mnt/HDD               local
```
```

[FONT=monospace][COLOR=#000000]$ cat /proc/mounts [/COLOR]
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0 
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0 
udev /dev devtmpfs rw,nosuid,relatime,size=3943536k,nr_inodes=985884,mode=755,inode64 0 0 
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0 
tmpfs /run tmpfs rw,nosuid,nodev,noexec,relatime,size=800304k,mode=755,inode64 0 0 
/dev/md0p1 / ext4 rw,noatime 0 0 
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0 
tmpfs /dev/shm tmpfs rw,nosuid,nodev,inode64 0 0 
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k,inode64 0 0 
cgroup2 /sys/fs/cgroup cgroup2 rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiv
eprot 0 0 
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0 
bpf /sys/fs/bpf bpf rw,nosuid,nodev,noexec,relatime,mode=700 0 0 
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,m
axproto=5,direct,pipe_ino=25034 0 0 
hugetlbfs /dev/hugepages hugetlbfs rw,relatime,pagesize=2M 0 0 
mqueue /dev/mqueue mqueue rw,nosuid,nodev,noexec,relatime 0 0 
debugfs /sys/kernel/debug debugfs rw,nosuid,nodev,noexec,relatime 0 0 
tracefs /sys/kernel/tracing tracefs rw,nosuid,nodev,noexec,relatime 0 0 
fusectl /sys/fs/fuse/connections fusectl rw,nosuid,nodev,noexec,relatime 0 0 
configfs /sys/kernel/config configfs rw,nosuid,nodev,noexec,relatime 0 0 
none /run/credentials/systemd-sysusers.service ramfs ro,nosuid,nodev,noexec,relatime,mode
=700 0 0 
tmpfs /run/qemu tmpfs rw,nosuid,nodev,relatime,mode=755,inode64 0 0 
/dev/md1p1 /mnt/Data ext4 rw,noatime 0 0 
/dev/md1p1 /home/chad/kvm/images ext4 rw,noatime 0 0 
mypool /mnt/HDD zfs rw,xattr,noacl 0 0 
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0 
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=800304k,nr_inodes=200076,mode=70
0,uid=1000,gid=1000,inode64 0 0 
mypool /var/www zfs rw,xattr,noacl 0 0 
mypool /var/cache/apt-cacher-ng zfs rw,xattr,noacl 0 0[/FONT]
```

---

### Post by #&amp;thj^% on 2023-09-25
Sorry I'm playing catch up here, I was under the impression this was a full ZFS-Root, is that not right?

---

### Post by pqwoerituytrueiwoq on 2023-09-25
note the issue seems to be my binds in /etc/fstab, disabling them made the system happy, these binds are linked to my zfs array

No i have 3 arrays
2 are in md using raid1 (/ and /mnt/Data)
1 is in zfs using raid10: /mnt/HDD

md0 is / and md1 is /mnt/Data
```

$ cat /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]  
md1 : active raid1 sdc1[0] sdd1[1] 
      124966912 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

md0 : active raid1 sdb2[0] sda2[1] 
      124965888 blocks super 1.2 [2/2] [UU] 
      bitmap: 1/1 pages [4KB], 65536KB chunk 

unused devices: <none>
$ zpool status 
  pool: mypool 
 state: ONLINE 
  scan: scrub repaired 0B in 00:01:55 with 0 errors on Mon Sep 25 09:32:34 2023 
config: 

        NAME                        STATE     READ WRITE CKSUM 
        mypool                      ONLINE       0     0     0 
          mirror-0                  ONLINE       0     0     0 
            wwn-0x50014ee263e2b396  ONLINE       0     0     0 
            wwn-0x50014ee263ce2c81  ONLINE       0     0     0 
          mirror-1                  ONLINE       0     0     0 
            wwn-0x50014ee263e27e85  ONLINE       0     0     0 
            wwn-0x50014ee265d71fad  ONLINE       0     0     0 

errors: No known data errors

```

---

### Post by #&amp;thj^% on 2023-09-25
> **pqwoerituytrueiwoq said:**
> note the issue seems to be my binds in /etc/fstab, disabling them made the system happy, these binds are linked to my zfs array
Yep I'm caught up to that point
> **pqwoerituytrueiwoq said:**
> 
No i have 3 arrays
2 are in md using raid1 (/ and /mnt/Data)
1 is in zfs using raid10: /mnt/HDD

Ok I'll watch on the sidelines, I just do different is all.
Not to confuse you just how I do for my usage.
```
zfs mount poolname
zfs mount poolname/datasetname 
```

Yes, zfs instead of zpool with the poolname and then poolname/datasetname.
MAFoElffen is the right person for this task.

---

### Post by MAFoElffen on 2023-09-25
I know your problem. (You have multiple conflicting mounts.) It's just going to take a while on my part, sorry.

Please stop until I can type this all out to explain what is going o, and what to do to change it... and in the process explain how ZFS mounts work and what 'should be' in your fstab, and what should not.

It's just a learning curve thing with ZFS. 1fallen will see it once I point it out.

@1fallen -- do <Cntrl><F> on the thread page, and search on "/mnt/HDD", then notice that he has a ZFS Pool (mypool), with no underlying ZFS DataSets... Hint. See the problem now? I'm going to type out a plan for him that should explain everything about that. That script of his is going to blow it up further, even though he thinks that will work. The solution to this is much simpler.

@ pqwoerituytrueiwoq's  -- In the meanwhile, please post the results of this
```

sudo zfs list mypool

```
That output will make this all obvious. LOL

EDIT -- And backup anything in these two directories: /var/www and /var/cache/apt-cacher-ng... That's going to change, so if you want that data, you will have to restore it after the mounts are fixed. 

In fact, backup anything you want to keep that is in zpool mypool...

---

### Post by #&amp;thj^% on 2023-09-25
> **MAFoElffen said:**
> 
@1fallen -- do <Cntrl><F> on the thread page, and search on "/mnt/HDD", then notice that he has a ZFS Pool (mypool), with no underlying ZFS DataSets... Hint. See the problem now?

No i seen that I just had to ask and see a second time to be sure.
> **MAFoElffen said:**
> 
 I'm going to type out a plan for him that should explain everything about that. That script of his is going to blow it up further, even though he thinks that will work. The solution to this is much simpler.
I had a notion you would.
> **MAFoElffen said:**
> @ pqwoerituytrueiwoq's  -- In the meanwhile, please post the results of this
```

sudo zfs list mypool

```
That output will make this all obvious. LOL
It should. ;)

---

### Post by MAFoElffen on 2023-09-25
Part 1.

I'm going to use my workstation as an example. It has enough complex mounts from different sources that mount into that filesystem, into one seamless filesystem, to show that as a visual example.

It's /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / is rpool on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part3 during migration
# 
UUID=0A24D9F224D9E0AD             /home/mafoelffen/WIN_G  ntfs  defaults,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
UUID=828C01738C016351             /Media_H                ntfs  defaults,windows_names,uid=1000,gid=1000,fmask=0002,dmask=0002,rw   0   0 
# EFI at /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part1
/dev/disk/by-uuid/CBE6-0806 /boot/efi vfat defaults 0 0
/boot/efi/grub /boot/grub none defaults,bind 0 0
# swap is on /dev/disk/by-id/nvme-Samsung_SSD_990_PRO_2TB_S73WNJ0W310240K-part4
/dev/disk/by-uuid/943f90ef-079f-4a38-840f-f786d19127ab none swap discard 0 0

```
In this fstab file, there are only 4 mounts. None of the mounts there are from ZFS. Notice there is no "/", /home, etc.. Because those mounts are within ZFS itself, so not needed there in the fstab. Yours is more traditonal, so it has a root, but just understand that ZFS has it's own underlying mounts into the filesystem. (additonal to other mounting methods.)

To see those other mounts and visualize how they fit into the filsystem, look at this:
```

mafoelffen@msi-ubuntu:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                             USED  AVAIL     REFER  MOUNTPOINT
bpool                                            460M  2.18G      192K  /boot
bpool/BOOT                                       459M  2.18G      192K  none
bpool/BOOT/ubuntu_2204                           459M  2.18G      459M  /boot
dpool                                           2.96M   450G       96K  /dpool
dpool/DATA                                       192K   450G       96K  none
dpool/DATA/ubuntu_2204                            96K   450G       96K  /dpool
hpool                                            578M   346G      192K  /home
hpool/USERDATA                                   570M   346G      192K  none
hpool/USERDATA/ubuntu_2204                       570M   346G      570M  /home
kpool                                            406G   493G       96K  /kpool
kpool/QEMU-KVM                                   406G   493G       96K  none
kpool/QEMU-KVM/ubuntu_2204                       406G   493G      104K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                   406G   493G      406G  /kpool/ISO
kpool/QEMU-KVM/ubuntu_2204/KVM-VM                 96K   493G       96K  /kpool/KVM-VM
kpool/QEMU-KVM/ubuntu_2204/images                112K   493G      112K  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt               608K   493G      608K  /etc/libvirt/
rpool                                           17.5G   707G      192K  /
rpool/ROOT                                      17.4G   707G      192K  none
rpool/ROOT/ubuntu_2204                          17.4G   707G     7.29G  /
rpool/ROOT/ubuntu_2204/srv                       192K   707G      192K  /srv
rpool/ROOT/ubuntu_2204/usr                       488K   707G      192K  /usr
rpool/ROOT/ubuntu_2204/usr/local                 296K   707G      296K  /usr/local
rpool/ROOT/ubuntu_2204/var                      10.1G   707G      192K  /var
rpool/ROOT/ubuntu_2204/var/cache                 539M   707G      539M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                 192K   707G      192K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                  8.19G   707G     8.00G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService   240K   707G      240K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager    328K   707G      328K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt               106M   707G      106M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker            192K   707G      192K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg             83.8M   707G     83.8M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs               192K   707G      192K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                  1.34G   707G     1.34G  /var/log
rpool/ROOT/ubuntu_2204/var/mail                  192K   707G      192K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                 1.19M   707G     1.19M  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                 256K   707G      256K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                  12.2M   707G     12.2M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                   192K   707G      192K  /var/www
rpool/USERDATA                                  4.29M   707G      192K  none
rpool/USERDATA/root_2204                        4.10M   707G     4.10M  /root

```
See the mountpoint column in that output? Those are the ZFS internal mounts, and how they are mounting into the filesystem as a whole... Even though the underlying data is stored in ZPS, on various disks. We will look at this again later.

Here is your /etc/fstab file from post #4
```

$ cat /etc/fstab
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/md0p1 during curtin installation 
/dev/disk/by-id/md-uuid-ede07d21:4114781a:b6762645:db22bf0e-part1 /         ext4 defaults,noatime 0 1 
# /mnt/Data was on /dev/md1p1 during curtin installation 
/dev/disk/by-id/md-uuid-28843301:920a306f:47f8cd80:d4d35fcd-part1 /mnt/Data ext4 defaults,noatime 0 1 
[COLOR=#ff0000]#/dev/disk/by-id/md-uuid-a1a41d92:421eda05:59f6da66:3d3f0f6e       /mnt/HDD  ext4 defaults         0 1 
[/COLOR]/mnt/Data/kvm-images    /home/chad/kvm/images    bind x-systemd.requires=/mnt/Data,defaults,bind  0 0 
[COLOR=#ff0000]/mnt/HDD/www            /var/www                 bind x-systemd.after=zfs-mount.service,x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
/mnt/HDD/apt-cacher-ng  /var/cache/apt-cacher-ng bind x-systemd.after=zfs-mount.service,x-systemd.requires=/mnt/HDD,defaults,bind   0 0 
[/COLOR]/swap.img               none                     swap sw                                          0 0

```
You should not have ZFS mounts in your fstab file... Use the internal ZFS mounts to do that. Don't do them yet. There is other work to do first, after I explain a few things. I'll get to that later.

Before I show you the conflicts in your mounts, lets take a quick peek at your internal ZFS mounts... from Post #16
```

$ sudo zfs get all | grep mountpoint
mypool  mountpoint            /mnt/HDD               local

```
I don't see any clear mountpoint there. I don't see that your created any ZFS datasets within zpool mypool... I'll get back to that later also.

The ZFS mounts within the fstab, defined like that, and , and the internal mount when you created your zpool, all have the same pointers, so are causing conflicts. You can see that in your /proc/mounts output in Post #16
```

$ cat /proc/mounts
<filtered by my edits> 
mypool /mnt/HDD zfs rw,xattr,noacl 0 0 
mypool /var/www zfs rw,xattr,noacl 0 0 
mypool /var/cache/apt-cacher-ng zfs rw,xattr,noacl 0 0

```
See those? You have one storage container (mypool) pointing to 3 different places in your filesystem at the same time... That does not work. At least not there in that manner. It can work, but a bit differently. That's where I need to explain a few things, so you can see how it works underneath, and how we can fix this. That will be in Part 2...

This is about the max length of a post, so I will have to continue this in Part 2. I may not finish this tonight, but I'm working on it.

---

### Post by MAFoElffen on 2023-09-25
Part 2.

Look at the attached photo

Definitions:

A ZFS pool (Zpool) is a collection of one or more virtual devices, referred to as vdevs that appear as a single storage device accessible to the file system. The Zpool is the highest container in the whole ZFS system.

A ZFS Vdev is either a single disk, or two or more disks which mirrors each other, or a group of disks that organizes together.

A ZFS Dataset is a generic name for the following ZFS components: clones, file systems, snapshots, and volumes. Each dataset is identified by a unique name in the ZFS namespace. Datasets are identified using the following format: pool / path [ @snapshot ] pool.

File system: A ZFS dataset of type filesystem that is mounted within the standard system namespace and behaves like other file systems.

That is how things fit together... Presently, you just have a stroage container/zpool called mypool, with no other containers/datasets withi that...

If I do this:
```

sudo mkdir /mypool
sudo zpool create -O canmount=off -O mountpoint=/mypool mypool /dev/disk/by-label/cl001

```
That created a completely basic pool with one vdev, that is mounted within that filsystem with a mounpoint at the main filesystem directory off from / at folder /mypool...

** As an aside, different from what you did, it's not wrong to mount something at /mnt, it can be done, but it is not a good working best practice to do permanent mounts to that folder. As a past Administrator, Linux standards recoomed that that folder is for temporary mounts. As that, a lot of tools use that folder for their temporary mounts, and clean them up afterwards. As a contributor to the boot-repair script, that tool does that. Another two not to use are /tmp, and /media... Bascically /media is for temporary portable storage devices, and /tmp gets deleted on shutdown. Back to other things.

Then I create a container (dataset) within that outer container (pool), to start organizinig what is inside that pool. I create a main container, that I can create other containers within.

I like how OpenZFS organizes their datasets, and with my own interpretqtion of theirs, there is a method to the madness of that, as a Best Practice. Think of it like creating a base directory from the root directory, with a tree of subdirectories under that, for organizing of the datasets within your pool.

For example
```

# syntax:
#<pool_name>/ORGANIZATION_GROUP/<main_dataset_id>/...<path_to>.../<dataset_name>
mypool/DATA1/kubuntu_2204/var/www
mypool/DATA1/kubuntu_2204/var/cache/apt-cacher-ng

```
As you can start to see that tree structure building, you can see that I can take a branch of it in the path_to and grouping to take a dataset snapshot of that, or further down the path to take just a snaphot of the dataset itself... Doing it that way also helps me visualize where the mounts need to be, because the names there tell a story of where they should go.

To create those, I would then do this
```

# I create the Organization_Group dataset
sudo zfs create -o canmount=off -o mountpoint=none mypool/DATA1
sudo zfs create -o canmount=off -o mountpoint=none mypool/DATA1/kubuntu_2204
sudo zfs create -o canmount=off -o mountpoint=none mypool/DATA1/kubuntu_2204/var
sudo zfs create -o canmount=off -o mountpoint=none mypool/DATA1/kubuntu_2204/var/www
sudo zfs create -o canmount=on -o mountpoint=/var/www mypool/DATA1/kubuntu_2204/var/cache
sudo zfs create -o canmount=on -o mountpoint=/var/cache/apt-cache-ng mypool/DATA1/kubuntu_2204/var/cache/apt-cache-ng

```
If in that process, or if later down the road you find you need to rename any of that, you can use 'zfs rename' to change it.

There the tree is built with two distinctly unique datasets created, that respresent two different storage containers. They are locate within one pool, that in reality reside on disk /dev/disk/by-lable/cl001, but they are mounted into the physical (overall) filesystem in two different places. It ca do that without conflicts, because they are unique from each other.

If, at this point, you did
```

sudo zfs list

```
The output would show the pool, with all the datasets within it, and where they are mounted withi the system filsystem structure.
*** I'm hoping at this point, you hear a virtual "pop", can see where yours failed, and can see how yours can be fixed.

If not, this is the point to ask questions.

---

### Post by pqwoerituytrueiwoq on 2023-09-25
> **MAFoElffen said:**
> 
@ pqwoerituytrueiwoq's  -- In the meanwhile, please post the results of this
```

sudo zfs list mypool

```
That output will make this all obvious. LOL

EDIT -- And backup anything in these two directories: /var/www and /var/cache/apt-cacher-ng... That's going to change, so if you want that data, you will have to restore it after the mounts are fixed. 

In fact, backup anything you want to keep that is in zpool mypool...

```
$ sudo zfs list mypool 
NAME     USED  AVAIL     REFER  MOUNTPOINT 
mypool  31.0G  7.09T     30.9G  /mnt/HDD
$ ls /mnt/HDD/ 
apt-cacher-ng  testDir  www

```
the data is 100% on the ZFS array's drive 
i have 2 binds that point to a directory inside of mypool
i can run these:
```
sudo umount /var/www
sudo umount /var/cache/apt-cacher-ng
```
then to undo that i can run these
```
mount --bind /mnt/HDD/www /var/www
mount --bind /mnt/HDD/apt-cacher-ng /var/cache/apt-cacher-ng

```
i could probably replace these with symbolic links, but i just prefer to use binds
those are just binds that point to a directory inside of mypool

---

### Post by MAFoElffen on 2023-09-26
BUT--- 'mount' doesn't work that way...

Refer to man mount:
```

NAME
       mount - mount a filesystem
...

DESCRIPTION
       All files accessible in a Unix system are arranged in one big tree, the file hierarchy, rooted at /. These files can be spread out over
       several devices. [COLOR=#ff0000]The mount command serves to attach the filesystem found on some device to the big file tree.[/COLOR] Conversely, the umount(8)
       command will detach it again. The filesystem is used to control how data is stored on the device or provided in a virtual way by network
       or other services.

       The standard form of the mount command is:

          mount -t type device dir

       [COLOR=#ff0000]This tells the kernel to attach the filesystem found on device (which is of type type) at the directory dir.[/COLOR] The option -t type is
       optional. The mount command is usually able to detect a filesystem. The root permissions are necessary to mount a filesystem by default.
       See section "Non-superuser mounts" below for more details. The previous contents (if any) and owner and mode of dir become invisible,
       and as long as this filesystem remains mounted, the pathname dir refers to the root of the filesystem on device.

```
So using the same verbiage that I have been explaining with (for consistency), that explanation says that it mounts the whole filesystem within that indicated storage container... You can just 'mount' one directory within that filesystem to a mountpoint. 

That is why in /proc/mounts it tries to say that [COLOR=#ff0000]same device[/COLOR] 'mypool' is mounted to 3 different mountpoints. There are different column fields in /proc/mounts, the columns translate to this format for each line, which follow the same format as fstab:
```

col1=device (fs_spec)
col2=mountpoint (fs_file)
col2=filesystem type (fs_vfstype)
col3=options (fs_mntops)
col4=dump (fs_freq)
col5=fsck (fs_passno)

```
Specifically the first field is just this:
```

   The first field (fs_spec).
       This field describes the block special device, remote filesystem or filesystem image for loop device to be mounted or swap file or swap
       partition to be enabled.

       For ordinary mounts, it will hold (a link to) a block special device node (as created by mknod(2)) for the device to be mounted, like
       /dev/cdrom or /dev/sdb7. For NFS mounts, this field is <host>:<dir>, e.g., knuth.aeb.nl:/. For filesystems with no storage, any string
       can be used, and will show up in df(1) output, for example. Typical usage is proc for procfs; mem, none, or tmpfs for tmpfs. Other
       special filesystems, like udev and sysfs, are typically not listed in fstab.

       LABEL=<label> or UUID=<uuid> may be given instead of a device name. This is the recommended method, as device names are often a
       coincidence of hardware detection order, and can change when other disks are added or removed. For example, 'LABEL=Boot' or
       'UUID=3e6be9de-8139-11d1-9106-a43f08d823a6'. (Use a filesystem-specific tool like e2label(8), xfs_admin(8), or fatlabel(8) to set LABELs
       on filesystems).

       It&#8217;s also possible to use PARTUUID= and PARTLABEL=. These partitions identifiers are supported for example for GUID Partition Table
       (GPT).

       See mount(8), blkid(8) or lsblk(8) for more details about device identifiers.

       Note that mount(8) uses UUIDs as strings. The string representation of the UUID should be based on lower case characters. But when
       specifying the volume ID of FAT or NTFS file systems upper case characters are used (e.g UUID="A40D-85E7" or UUID="61DB7756DB7779B3").

```
So here is from my workstation's /proc/mounts
```

mafoelffen@msi-ubuntu:~$ grep 'zfs' /proc/mounts
rpool/ROOT/ubuntu_2204 / zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/srv /srv zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/usr/local /usr/local zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/cache /var/cache zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/games /var/games zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib /var/lib zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib/AccountsService /var/lib/AccountsService zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager /var/lib/NetworkManager zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib/apt /var/lib/apt zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib/docker /var/lib/docker zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib/dpkg /var/lib/dpkg zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/lib/nfs /var/lib/nfs zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/log /var/log zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/mail /var/mail zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/snap /var/snap zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/spool /var/spool zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/tmp /var/tmp zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204/var/www /var/www zfs rw,relatime,xattr,posixacl 0 0
rpool/USERDATA/root_2204 /root zfs rw,relatime,xattr,posixacl 0 0
bpool/BOOT/ubuntu_2204 /boot zfs rw,nodev,relatime,xattr,posixacl 0 0
dpool/DATA/ubuntu_2204 /dpool zfs rw,relatime,xattr,posixacl 0 0
hpool/USERDATA/ubuntu_2204 /home zfs rw,relatime,xattr,posixacl 0 0
kpool/QEMU-KVM/ubuntu_2204/libvirt /etc/libvirt zfs rw,relatime,xattr,posixacl 0 0
kpool/QEMU-KVM/ubuntu_2204 /kpool zfs rw,relatime,xattr,posixacl 0 0
kpool/QEMU-KVM/ubuntu_2204/images /var/lib/libvirt/images zfs rw,relatime,xattr,posixacl 0 0
kpool/QEMU-KVM/ubuntu_2204/ISO /kpool/ISO zfs rw,relatime,xattr,posixacl 0 0
kpool/QEMU-KVM/ubuntu_2204/KVM-VM /kpool/KVM-VM zfs rw,relatime,xattr,posixacl 0 0
rpool/ROOT/ubuntu_2204 /var/snap/firefox/common/host-hunspell zfs ro,noexec,noatime,xattr,posixacl 0 0

```
You see that even though those mounts are very complex, in field one, there are only unique storage container devices that column, right?

But using datasets, datasets are unique storage containers, within the larger container, with their own filesystem within that storage contatiner (dataset: type filsesystem)... Which can be mounted. You cannot mount or unmount just a directory/folder that resides within a filesystem. You mount the whole filesystem within a storage container. (That is what that effectively did on yours, 3 times to differnet mount points.) That is what your /proc/mounts file said.

---

### Post by pqwoerituytrueiwoq on 2023-09-26
Fine i'll just use symbolic links...

```
$ zfs list 
NAME     USED  AVAIL     REFER  MOUNTPOINT 
mypool  31.0G  7.09T     30.9G  /spinningRust


$ cat /etc/fstab           
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/md0p1 during curtin installation 
/dev/disk/by-id/md-uuid-ede07d21:4114781a:b6762645:db22bf0e-part1 /         ext4 defaults,noatime 0 1 
# /mnt/Data was on /dev/md1p1 during curtin installation 
/dev/disk/by-id/md-uuid-28843301:920a306f:47f8cd80:d4d35fcd-part1 /mnt/Data ext4 defaults,noatime 0 1 
/mnt/Data/kvm-images    /home/chad/kvm/images    bind x-systemd.requires=/mnt/Data,defaults,bind  0 0 
/swap.img               none                     swap sw                                          0 0


$ cat /proc/mounts  
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0 
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0 
udev /dev devtmpfs rw,nosuid,relatime,size=3943536k,nr_inodes=985884,mode=755,inode64 0 0 
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0 
tmpfs /run tmpfs rw,nosuid,nodev,noexec,relatime,size=800304k,mode=755,inode64 0 0 
/dev/md0p1 / ext4 rw,noatime 0 0 
securityfs /sys/kernel/security securityfs rw,nosuid,nodev,noexec,relatime 0 0 
tmpfs /dev/shm tmpfs rw,nosuid,nodev,inode64 0 0 
tmpfs /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k,inode64 0 0 
cgroup2 /sys/fs/cgroup cgroup2 rw,nosuid,nodev,noexec,relatime,nsdelegate,memory_recursiveprot 0 0 
pstore /sys/fs/pstore pstore rw,nosuid,nodev,noexec,relatime 0 0 
bpf /sys/fs/bpf bpf rw,nosuid,nodev,noexec,relatime,mode=700 0 0 
systemd-1 /proc/sys/fs/binfmt_misc autofs rw,relatime,fd=30,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=25034 0 0 
hugetlbfs /dev/hugepages hugetlbfs rw,relatime,pagesize=2M 0 0 
mqueue /dev/mqueue mqueue rw,nosuid,nodev,noexec,relatime 0 0 
debugfs /sys/kernel/debug debugfs rw,nosuid,nodev,noexec,relatime 0 0 
tracefs /sys/kernel/tracing tracefs rw,nosuid,nodev,noexec,relatime 0 0 
fusectl /sys/fs/fuse/connections fusectl rw,nosuid,nodev,noexec,relatime 0 0 
configfs /sys/kernel/config configfs rw,nosuid,nodev,noexec,relatime 0 0 
none /run/credentials/systemd-sysusers.service ramfs ro,nosuid,nodev,noexec,relatime,mode=700 0 0 
tmpfs /run/qemu tmpfs rw,nosuid,nodev,relatime,mode=755,inode64 0 0 
/dev/md1p1 /mnt/Data ext4 rw,noatime 0 0 
/dev/md1p1 /home/chad/kvm/images ext4 rw,noatime 0 0 
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,nosuid,nodev,noexec,relatime 0 0 
tmpfs /run/user/1000 tmpfs rw,nosuid,nodev,relatime,size=800304k,nr_inodes=200076,mode=700,uid=1000,gid=1000,inode64 0 0 
mypool /spinningRust zfs rw,xattr,noacl 0 0
```

now should i go about fixing the /mnt/Data thing to be correct? it is same issue but it works

```
$ tree /mnt 
/mnt
&#9492;&#9472;&#9472; Data
    &#9500;&#9472;&#9472; kvm-images
    &#9474;   &#9492;&#9472;&#9472; pfsense.qcow2 
    &#9492;&#9472;&#9472; lost+found  [error opening dir] 

3 directories, 2 files
$ tree /home/chad/kvm/ 
/home/chad/kvm/
&#9500;&#9472;&#9472; host-bridge.xml 
&#9500;&#9472;&#9472; host-direct.xml 
&#9500;&#9472;&#9472; host-macvtap0.xml 
&#9500;&#9472;&#9472; host-macvtap1.xml 
&#9492;&#9472;&#9472; images
    &#9492;&#9472;&#9472; pfsense.qcow2 

1 directory, 5 files
```

---

### Post by MAFoElffen on 2023-09-27
Yes, symbolic link to that... is a technique. Not the best option for that, but will work. But note that you could easily convert that by start adding datasets to your pool, and rsyncing the data to them to sync the existing data between... Then they would you mount to the internal ZFS mountpoints that you set them to (multiple mountpoints) Just an idea.

Your underlying filesystem that is mounted to /mnt/DATA comes from your mdadm arrays right? It follows the same functionality of 'mount'. In that it can mount one filesystem at a time to mount to one place. If you had multiple partitions (storage containers) in your array, then you could mount those multiple storage containers to multiple mountpoints... But you are only mounting it to one place in the end, right?

If the target directory that it ends up at is '/home/chad/kvm/', then why are you NOT using that as the mountpoint. That is where it ends up as and that is just one filesystem structure below that. It makes sense to me to just mount it to there. That is the file/directory structure that is in your array right? It doesn't make sense to me to mount it in one place and use it in another.

Or am I missing that it ends up in different 'places'. I think you said just one.

---

### Post by pqwoerituytrueiwoq on 2023-09-27
For the purpose of expansion and having different permissions on each folder on the partition

in other news...
```

  pool: mypool 
 state: ONLINE 
status: One or more devices has experienced an unrecoverable error.  An 
        attempt was made to correct the error.  Applications are unaffected. 
action: Determine if the device needs to be replaced, and clear the errors 
        using 'zpool clear' or replace the device with 'zpool replace'. 
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P 
  scan: scrub repaired 0B in 00:01:55 with 0 errors on Mon Sep 25 09:32:34 2023 
config: 

        NAME                        STATE     READ WRITE CKSUM 
        mypool                      ONLINE       0     0     0 
          mirror-0                  ONLINE       0     0     0 
            wwn-0x50014ee263e2b396  ONLINE       0     1     0 
            wwn-0x50014ee263ce2c81  ONLINE       0     0     0 
          mirror-1                  ONLINE       0     0     0 
            wwn-0x50014ee263e27e85  ONLINE       0     0     0 
            wwn-0x50014ee265d71fad  ONLINE       0     0     0 

errors: No known data errors

```

```

[97879.673089] ata10.00: exception Emask 0x10 SAct 0x1000 SErr 0x400100 action 0x6 
[97879.673154] ata10.00: irq_stat 0x08000000 
[97879.673181] ata10: SError: { UnrecovData Handshk } 
[97879.673214] ata10.00: failed command: WRITE FPDMA QUEUED 
[97879.673246] ata10.00: cmd 61/08:60:b8:e1:65/00:00:08:00:00/40 tag 12 ncq dma 4096 out 
                        res 40/00:60:b8:e1:65/00:00:08:00:00/40 Emask 0x10 (ATA bus error)                                                                                          
[97879.673339] ata10.00: status: { DRDY }
[97880.151601] sd 9:0:0:0: [sdf] tag#12 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_OK cmd_age=0s 
[97880.151607] sd 9:0:0:0: [sdf] tag#12 Sense Key : Illegal Request [current]  
[97880.151611] sd 9:0:0:0: [sdf] tag#12 Add. Sense: Unaligned write command 
[97880.151615] sd 9:0:0:0: [sdf] tag#12 CDB: Write(16) 8a 00 00 00 00 00 08 65 e1 b8 00 00 00 08 00 00 
[97880.151617] blk_update_request: I/O error, dev sdf, sector 140894648 op 0x1:(WRITE) flags 0x700 phys_seg 1 prio class 0 
[97880.151693] zio pool=mypool vdev=/dev/disk/by-id/wwn-0x50014ee263e2b396-part1 error=5 type=2 offset=72137011200 size=4096 flags=180880 
[97880.151721] ata10: EH complete

```
if this is ANOTHER bad sata cable...

---

### Post by MAFoElffen on 2023-09-27
You had asked about SATA cables... Sorry I didn't answer that. I was going to but thought other things were more of a priority at the time.

I buy "SATA III Cables, locking, with straight to straight connectors" on Amazon. There is not any difference in SATA cables between types they say they are for, as it relates to 1.5, 3, and 6 Ghz/s. They are all interchangeable, and there is no difference in bandwidth. I figure that is just for marketing. I have tested that. The reason I buy cables with locks, is that I just want to make 'sure' that the connection stays tight. Yes, I have had that problem and had to track it down. I feel you on that. They just seem to work better in that long-run and they keep a tighter connection. I tend to reconfigure my boxes over time.

I do buy SATA cables of different lengths... Logically, a straighter run has less chance of degradation that one that has a lot of bends or wraps to take up the length. But that comes from my experience in network cabling in datacenters... And most Ethernet UTP network cabling is, as the name is: "Unshielded Twisted Pair"...

I have not found shielded cables for SATA. They have them for eSATA because those are outside the case, to protect anything external from any possible RF emissions from. An eSATA connector will not fit on a SATA port because it has an extra tab. SATA cables will fit on eSATA ports, but not securely. I have not seen any problems with RF emissions from SATA cables inside a case. I have also tested that. 

As for permissions. Understand that this is only based on being a Windows, Unix and Linux Administrator for about 34 years... After a mount, then I set permission and ACL's to groups to the mountpount recursively, then any changes to the underlying folders that I want to be different from what is inherited from that. There is no reason to mount in one place and use it in another that relates to User and Group access and permissions that I can think of. But you can do things 100's of ways to get to the same point of things in Linux. Some of those ways are just not smart.

---

### Post by pqwoerituytrueiwoq on 2023-09-27
The sata controller i am using is not the ideal chipset, so i think it is VERY VERY picky and my box is not the best for EMI...[ i have a cable modem, boost converter, audio amp, and 5 port switch in there]("https://imgur.com/a/bJsP80E")

```
$ lspci -s 2e:00.0 -vvv 
2e:00.0 SATA controller: JMicron Technology Corp. JMB58x AHCI SATA controller (prog-if 01 [AHCI 1.0]) 
        Subsystem: JMicron Technology Corp. JMB58x AHCI SATA controller 
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx+ 
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx- 
        Latency: 0, Cache Line Size: 64 bytes 
        Interrupt: pin A routed to IRQ 50 
        IOMMU group: 11 
        Region 0: I/O ports at e200 [size=128] 
        Region 1: I/O ports at e180 [size=128] 
        Region 2: I/O ports at e100 [size=128] 
        Region 3: I/O ports at e080 [size=128] 
        Region 4: I/O ports at e000 [size=128] 
        Region 5: Memory at fce10000 (32-bit, non-prefetchable) [size=8K] 
        Expansion ROM at fce00000 [disabled] [size=64K] 
        Capabilities: <access denied> 
        Kernel driver in use: ahci 
        Kernel modules: ahci
```

i recently replaced 2 cables i was using and used contact cleaner and dielectric grease on all connections and it was solid till recently, it was far worse than this before, this has been a PITA

very much considering warping the cable in aluminum foil, heat shrinking/taping it, and attaching it to ground

---

### Post by MAFoElffen on 2023-09-27
> **pqwoerituytrueiwoq said:**
> The sata controller i am using is not the ideal chipset, so i think it is VERY VERY picky and my box is not the best for EMI...[ i have a cable modem, boost converter, audio amp, and 5 port switch in there]("https://imgur.com/a/bJsP80E")

```
$ lspci -s 2e:00.0 -vvv 
2e:00.0 SATA controller: JMicron Technology Corp. JMB58x AHCI SATA controller (prog-if 01 [AHCI 1.0]) 
        Subsystem: JMicron Technology Corp. JMB58x AHCI SATA controller 
        Capabilities: <access denied> 
        Kernel driver in use: ahci 
        Kernel modules: ahci
```

i recently replaced 2 cables i was using and used contact cleaner and dielectric grease on all connections and it was solid till recently, it was far worse than this before, this has been a PITA

[COLOR=#ff0000]very much considering warping the cable in aluminum foil, heat shrinking/taping it, and attaching it to ground[/COLOR]
LMFAO!!! Yup.

On this:
```

  pool: mypool 
 state: ONLINE 
status: One or more devices has experienced an unrecoverable error.  An 
        attempt was made to correct the error.  Applications are unaffected. 
action: Determine if the device needs to be replaced, and clear the errors 
        using 'zpool clear' or replace the device with 'zpool replace'. 
   see: https://openzfs.github.io/openzfs-docs/msg/ZFS-8000-9P 
  scan: scrub repaired 0B in 00:01:55 with 0 errors on Mon Sep 25 09:32:34 2023 
config: 

        NAME                        STATE     READ WRITE CKSUM 
        mypool                      ONLINE       0     0     0 
          mirror-0                  ONLINE       0     0     0 
            [COLOR=#ff0000]wwn-0x50014ee263e2b396  ONLINE       0     **1**     0 [/COLOR]
            wwn-0x50014ee263ce2c81  ONLINE       0     0     0 
          mirror-1                  ONLINE       0     0     0 
            wwn-0x50014ee263e27e85  ONLINE       0     0     0 
            wwn-0x50014ee265d71fad  ONLINE       0     0     0 

errors: No known data errors

```
It gets to 10 before it flips the drive to a fail mode, then degrades the array. Like I said, ZFS gives lots of warnings before it  flips a drive to fail, unlike mdadm. ZFS is also COW (Copy On Write), so it doesn't commit the write until it confirms that it wrote it successfully. So the data it was going to write originally, when it went to confirm if it was written successfully, it found an error with that... then picked another place to write it that was successful. (There was only one error.) So that data is safe.

I trust ZFS, which says a lot. I'm usually a skeptic until I prove things for myself.

What I would do now is:
```

# The follwoing clears the counters, and if a drive was failed, it sets it as good. But don't do this without doing a scrub after that.
sudo zpool clear mypool

# The following starts a scrub process, with it like fsck for ext4 filesystems, but does checks & fixes on the ZFS filesystem
sudo zpool scrub mypool

# Do this repeatedly to check the process of that scrub, and to ensure that finishes successfully.
sudo zpool status -v mypool

```
Any error it finds on that disk, it will mark as bad, which will tell it not to use that block in the future.

Which brings up a point, I have a cron job that runs 2 ZFS jobs a month. One for scrubs on all my pools. The second to run trim jobs on all my pools. This is something you need to wither run manually, or setup cron jobs to do...

Here is a copy on my cron jobs:
```

mafoelffen@msi-ubuntu:~$ grep . /etc/cron.d/zfsutils-linux
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
# TRIM the first Sunday of every month.
24 0 1-7 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/trim ]; then /usr/lib/zfs-linux/trim; fi
# Scrub the second Sunday of every month.
24 0 8-14 * * root if [ $(date +\%w) -eq 0 ] && [ -x /usr/lib/zfs-linux/scrub ]; then /usr/lib/zfs-linux/scrub; fi

```

---

