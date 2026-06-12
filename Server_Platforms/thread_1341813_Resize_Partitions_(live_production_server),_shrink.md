---
title: "Resize Partitions (live production server), shrink others"
date: 2009-11-30
forum: Server Platforms
---

### Post by v8YKxgHe on 2009-11-30
Morning,

This morning, the partition that /var is on ran out of space (it is a stupidly small partition of 2.8gb!) which I only realised after a restart of the server due to updates, resulting in MySQL not being able to start. Now I've managed to free enough space on /var to start MySQL, so the sites are running - but this needs sorting.

I need to resize 1 partition (/var), and shrink the others below it whilst moving them down. I've had to do this before, and remember it being quite fiddly and has a lot of danger for messing things up, hence why I'm posting here. Below are details of what needs doing, and the partition layout:

```
$ sudo fdisk -l

Disk /dev/sda: 249.3 GB, 249376538624 bytes
255 heads, 63 sectors/track, 30318 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2   *          12         307     2377620   83  Linux
/dev/sda4             308       30318   241063357+   5  Extended
/dev/sda5             308         915     4883728+  83  Linux
/dev/sda6             916        1280     2931831   83  Linux
/dev/sda7            1281        2031     6032376   82  Linux swap / Solaris
/dev/sda8            2032        2080      393561   83  Linux
/dev/sda9            2081       30318   226821703+  83  Linux

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             2.0G  302M  1.6G  16% /
tmpfs                1005M     0 1005M   0% /lib/init/rw
udev                   10M  788K  9.3M   8% /dev
tmpfs                1005M     0 1005M   0% /dev/shm
/dev/sda9             213G  1.5G  201G   1% /home
/dev/sda8             373M   12M  342M   4% /tmp
/dev/sda5             4.6G  874M  3.5G  20% /usr
/dev/sda6             2.8G  2.7G   12M 100% /var

$ df -B 4k
Filesystem           4K-blocks      Used Available Use% Mounted on
/dev/sda2               509779     77273    406301  16% /
tmpfs                   257256         0    257256   0% /lib/init/rw
udev                      2560       197      2363   8% /dev
tmpfs                   257256         0    257256   0% /dev/shm
/dev/sda9             55815466    385622  52594573   1% /home
/dev/sda8                95285      2906     87460   4% /tmp
/dev/sda5              1201726    223729    916951  20% /usr
/dev/sda6               721445    681945      2853 100% /var

$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              2039113    309089   1625204  16% /
tmpfs                  1029024         0   1029024   0% /lib/init/rw
udev                     10240       788      9452   8% /dev
tmpfs                  1029024         0   1029024   0% /dev/shm
/dev/sda9            223261864   1542496 210378284   1% /home
/dev/sda8               381138     11623    349837   4% /tmp
/dev/sda5              4806904    894916   3667804  20% /usr
/dev/sda6              2885780   2727788     11404 100% /var

```
As you can see, /dev/sda6 is the partition I need to resize, but there are 3 partitions below it. In my head, the following needs doing:

[LIST]
[*]Shrink /dev/sda9 to around 150gb
[*]Move /dev/sda5, /dev/sda8 and /dev/sda9 down to the bottom of the drive
[*]Resize /dev/sda6 to fill up the gap, expanding it by ~50gb.
[/LIST]

I'm not 100% sure on what I need to do here, and so would really appreciate any help on getting this sorted. As said in the topic title, this is a live production server (I have remote access via a Dell RAC if things get ugly), so one mistake can not happen =).

Thanks,

---

### Post by BkkBonanza on 2009-11-30
If I were doing this, since your /var partition is not next to a really large one, I think I would split the /home partition in two (it appears to be much larger than it needs to be and seems it's not involved in your running server software). Then I'd copy everything from /var into the new one and remap /var to that partition in fstab. After the split and copying /var the remap can be done in seconds allowing for almost no down time. Anyway, I think that would be my approach. Trying to resize /var with flanking small partitions would be a major downtime and probably far more prone to major screw up. In my opinion anyway.

(It looks like you could copy /home onto / temporarily so that /home can be unmounted for a split up, if you're interested in a step by step I could mock one up)

Another temporary measure (easy to do in a few minutes) would be to copy your database files in /var to the /home partition. Then install a symlink for the data directory mapping it to /home (somewhere). That gives you huge space just for that data area anyway. And it free up space on var (of course, after duping the data in /home and adding the synlink you would remove it from /var)

Symlink something like this (or whatever your correct paths are),

ln -s /home/mysql/data /var/local/mysql/data

---

### Post by v8YKxgHe on 2009-11-30
That sounds like it could work. Just started on it and 'umount /dev/sda9' said that /home was busy. How can I resolve this?

---

### Post by BkkBonanza on 2009-11-30
Hmm, ya of course. You can't umount while it's in use. 
With remote access I'm not sure off hand the best way around that.
Probably modifying the fstab and rebooting. Should cause it to start up on the new location (assuming you copy everything first). If /home is now in / partition then you would just comment out the /home line in fstab. If something goes wrong you may need console access to fix it (kvm or something, not sure if Dell RAC means the same thing).
Actually this needs a bit of thought to work as you won't be able to copy /home to / without using a different name temporarily, and then you'd have to manually rename and mount it after the reboot.
This is the kind of thing I'd feel confident doing myself but not really telling others to do.

How many users do you have in home? If just 1 or 2 then you could copy /home to /home2, then alter /etc/passwd to tell the system that those users home directory is now in /home2 and then reboot. Then do your partition changes (since /home is no longer in use) and after done copy them back and change /etc/passwd again.

---

### Post by v8YKxgHe on 2009-11-30
There are around 12 users. However, I don't think we'd need to copy /home to a new place. I have a backup of the home directory, so if anything goes wrong I can restore from  that.

I should be able to restart it with /home unmounted, and work from there. Yeah Dell RAC is just a Remote Access Controller with a web-based interface to manage the server if anything goes wrong, with a Java redirection console so I can still have access to it even at BIOS/POST stage.

---

### Post by BkkBonanza on 2009-11-30
That sounds reasonable then. Should only be down for a minute to complete that and then you can work on the partition.

---

