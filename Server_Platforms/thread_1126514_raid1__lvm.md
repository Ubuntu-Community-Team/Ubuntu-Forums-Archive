---
title: "raid1 / lvm"
date: 2009-04-15
forum: Server Platforms
---

### Post by maclenin on 2009-04-15
With reference to [_this earlier post_]("http://ubuntuforums.org/showthread.php?t=1107309"), I am now rethinking my partition scheme; mulling the following RAID1/LVM configurations across three drives...

**Drive 1 - sda - 250gb**```

sda1 - RAID1 - (md0) - ext3 - /boot (1gb)
sda2 - swap (2gb)
sda3 - LVM - pvo1 - vgos - lv01 - ext3 - / (30gb) 
sda3 - LVM - pvo1 - vgos - lv02 - ext3 - /home (80gb)
sda3 - LVM - pvo1 - vgos - lv03 - ext3 - /tmp (20gb)
sda3 - LVM - pvo1 - vgos - lv04 - ext3 - /usr (20gb)
sda3 - LVM - pvo1 - vgos - lv05 - ext3 - /var (20gb)
sda3 - LVM - pvo1 - vgos - lv06 - ext3 - /usr/local (20gb)
sda3 - LVM - pvo1 - vgos - lv07 - ext3 - /opt (20gb)
*unused (37gb)*
```
**Drive 2 - sdb - 1000gb**```

sdb1 - RAID1 - (md0) - ext3 - /boot (1gb)
sdb2 - swap (2gb)
sdb3 - RAID1/LVM - (md1) - pv02 - vgserver - lv01 - ext3 - /shared (400gb)
sdb4 - RAID1/LVM - (md2) - pv03 - vgserver - lv02 - ext3 - /backup (500gb)
*unused* (97gb)
```
**Drive 3 - sdc - 1000gb**```

sdc1 - ext3 - /boot (1gb)
sdc2 - swap (2gb)
sdc3 - RAID1/LVM - (md1) - pv04 - vgserver - lv01 - ext3 - /shared (400gb)
sdc4 - RAID1/LVM - (md2) - pv05 - vgserver - lv02 - ext3 - /backup (500gb)
*unused* (97gb)
```
Questions:

1. Should I allocate more (gb) to swap (the system has 4gb ram)?
2. Do the allocations (gb), generally, look reasonable?
3. Does the LVM setup (Drives 2 and 3) look correct for the given RAID1 configuration?
4. Any other issues?

Thanks for any comments/suggestions!

---

### Post by ikonia on 2009-04-16
1.) 1GB /boot partition reallly ?
2.) why make it hard on your self using /usr and /opt and /usr/local as seperate partition, the multi partition setup was more common years ago due to smaller disks, thats no longer a problem so unless you have some sort of massive need to have these on seperate partitions why make it hard ?
3.) why have you got /boot listed 3 times, twice on raid (no problem) once on /dev/sdc1 as just /boot ???


my overall impression is that your system has massive amounts of waste, the system disk is not very flexible, your raid/mirroring is pointless as you've mirrored /boot, but not mirrored the rest of the OS file system, what good is /boot if the rest of your file system is dead ??

Looks a very bad setup in my opinion.

now for some overall comment and a suggested fix.

I personally don't like mirroring disks of different sizes it can make things quite tricky and often provide waste, so lets try to get around that. As mentioned above, I also don't see the point of mirroring /boot if the rest of the OS is dead.

Without knowing more about your system and what you want specifically I can't give you something tailor made, but I can offer a generic solution which I personally think is less wasteful, more flexible and provides a better overall solution.

/boot = md0 200meg made up from /dev/sdb1 and /dev/sdc1
/ = md1 40GB made up from /dev/sdb2 and /dev/sdc2
/home = md2 80GB made up from /dev/sdb3 and /dev/sdc3  (if you don't want to mirror home move it to /dev/sda)

this will cover your systems overall core stability, you can put /var on a mirror if you want.

/tmp /dev/sda1 = 20GB - or what ever size you want as this is none important data
/usr/local = sda2 - I wouldn't bother making a /usr/local/ seperate disk / mount point as you have tons of space on / - but you seem keen

create your md3 from the rest of /dev/sdb and /dev/sdc as you did before and dump that into vg00 lvm. then allocate /shared and /backup from that volume group, you don't need two raid devices to put into the volume group, that defeates the object of LVM, 

use the rest of /dev/sda as your scratch / swap / what ever disk for non important data.

---

### Post by maclenin on 2009-04-17
**ikonia:**

Thanks for the constructive criticism....

I have revised my raid/lvm configurataion:

**Drive 1 - sda - 250gb**
```
sda1 - RAID1 - (md0) - ext3 - /boot (500mb)
sda2 - swap (2gb)
sda3 - LVM - pv01 - vghome - lvhome - ext3 - /home (80gb)
sda3 - LVM - pv01 - vghome - lvtmp - ext3 - /tmp (10gb)
sda3 - LVM - pv01 - vghome - lvusr - ext3 - /usr (10gb)
sda3 - LVM - pv01 - vghome - lvvar - ext3 - /var (10gb)
sda3 - LVM - pv01 - vghome - lvlocal - ext3 - /usr/local (10gb)
sda3 - LVM - pv01 - vghome - lvopt - ext3 - /opt (10gb)
*unused/scratch* (~120gb)
```
**Drive 2 - sdb - 1000gb**
```
sdb1 - RAID1 - (md0) - ext3 - /boot (500mb)
sdb2 - swap (2gb)
sdb3 - RAID1/LVM - (md1) - pv02 - vgos - lvroot - ext3 - / (50gb)
sdb4 - RAID1/LVM - (md2) - pv03 - vgserver - lvshared - ext3 - /shared (400gb)
sdb4 - RAID1/LVM - (md2) - pv03 - vgserver - lvbackup - ext3 - /backup (400gb)
*unused* (150gb)
```
**Drive 3 - sdc - 1000gb**
```
sdc1 - ext3 - /boot (500mb)
sdc2 - swap (2gb)
sdc3 - RAID1/LVM - (md1) - pv04 - vgos - lvroot - ext3 - / (50gb)
sdc4 - RAID1/LVM - (md2) - pv05 - vgserver - lvshared - ext3 - /shared (400gb)
sdc4 - RAID1/LVM - (md2) - pv05 - vgserver - lvbackup - ext3 - /backup (400gb)
*unused* (150gb)
```

Questions:

1. /boot on sdc1 is merely a place holder - to maintain some consistent structure/balance to the partition scheme (i.e. /boot on s*1 and /swap on s*2 and so forth...). Can I add grub to the sdc1 partition - to have a third boot option in case the other two fail? Does it matter where the /boot mirror is placed - i.e. sda / sdb / sdc ?
2. I am assuming the *unused* portions can be incorporated or distributed using lvm - ad hoc? Do I need to assign the *unused* space to a partition - to make it available for distribution (across the various volume groups)?
3. Any other thoughts?

Thanks, again, for the previous review....

---

### Post by maclenin on 2009-04-24
Now, this is the latest (and most likely final) iteration of my pending RAID1/(newly-added)RAID5/LVM2 configuration...

**Drive 1 - sda - 250gb**
```
sda1 - RAID1 - (md0) - ext3 - /boot (500mb)
sda2 - swap (2gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvroot - ext3 - / (30gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvhome - ext3 - /home (80gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvtmp - ext3 - /tmp (10gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvusr - ext3 - /usr (10gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvvar - ext3 - /var (10gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvusrlocal - ext3 - /usr/local (10gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - lvopt - ext3 - /opt (10gb)
sda3 - RAID5/LVM - (md1) - pv01 - vgserver - unused (*gb)
```
**Drive 2 - sdb - 1000gb**
```
sdb1 - RAID1 - (md0) - ext3 - /boot (500mb)
sdb2 - swap (2gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvroot - ext3 - / (30gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvhome - ext3 - /home (80gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvtmp - ext3 - /tmp (10gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvusr - ext3 - /usr (10gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvvar - ext3 - /var (10gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvusrlocal - ext3 - /usr/local (10gb)
sdb3 - RAID5/LVM - (md1) - pv01 - vgserver - lvopt - ext3 - /opt (10gb)
sdb4 - RAID1/LVM - (md2) - pv02 - vgserver - lvshared - ext3 /shared (725gb)
sdb4 - RAID1/LVM - (md2) - pv02 - vgserver - unused (*gb)
```

**Drive 3 - sdc - 1000gb**
```
sdc1 - ext3 - /boot (500mb)
sdc2 - swap (2gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvroot - ext3 - / (30gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvhome - ext3 - /home (80gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvtmp - ext3 - /tmp (10gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvusr - ext3 - /usr (10gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvvar - ext3 - /var (10gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvusrlocal - ext3 - /usr/local (10gb)
sdc3 - RAID5/LVM - (md1) - pv01 - vgserver - lvopt - ext3 - /opt (10gb)
sdc4 - RAID1/LVM - (md2) - pv02 - vgserver - lvshared - ext3 - /shared (725gb)
sdc4 - RAID1/LVM - (md2) - pv02 - vgserver - *unused* (*gb)
```

...and I would like to use mdadm and lvm2 to set it all up via the Intrepid liveCD. These are the two guides I've been examining as an in-combination starting point for accomplishing this install:

raid: [http://www.howtoforge.com/install-ubuntu-with-software-raid-10](http://www.howtoforge.com/install-ubuntu-with-software-raid-10)
lvm: [http://www.sysadminsjourney.com/content/2008/12/16/use-lvm-installation-ubuntu](http://www.sysadminsjourney.com/content/2008/12/16/use-lvm-installation-ubuntu)

Any thoughts or suggestions?

Is the alternate CD a better idea?

---

### Post by maclenin on 2009-04-25
Done!

RAID1/RAID5/RAID1/LVM all running in blissful unison on Intrepid Ibex!

The alternate CD was, without question, the way to go!

---

### Post by fjgaude on 2009-04-25
Wonderful! Hope you keeps up-to-date backups of all important data. Think what happens as you lose a drive or two. Heaven forbid!

---

### Post by maclenin on 2009-04-25
Thanks for the comments - **fjgaude** - I am setting up the disaster recovery plan as I type!

In the meantime, however (and before valuable data is allowed to populate the new box), I am trying to resolve a wee wrinkle:  

a. I have discovered that the system does not boot from my bootable md0 RAID1 array (sda1 (hd0,0) and (in the event sda should fail) sdb1 (hd1,0)).

b. The system boots, rather, from my "plain vanilla" (non-RAID and non-LVM) sdc1 partition (hd2,0).

c. grub> find /grub/stage1 shows (hd2,0).

d. /dev/md0 (the bootable RAID1 array) does not show up in fstab.

All else seems to be in good order:

e. The md0 array shows up as it should when I run mdadm diagnostics.

f. fdisk -l shows all partitions (sda1, sdb1, sdc1) configured as bootable ("*").

Questions: 

1. Could it be that when the partition tables were being finalized during install - that the /dev/sdc1 /boot partition was somehow given priority to the /dev/md0 /boot "array" - and, therefore added to fstab (and assigned grub) by the installer while /dev/md0 was not?

2. Might it just be a "simple" matter of making certain that grub is properly installed or configured on the /dev/md0 array?

3. How can I tell whether things are (already) set up properly - grub-wise?

4. Might it just be a "simple" matter of adding the /dev/md0 array to fstab?

5. Any thoughts as to why /dev/md0 would not have been added to fstab during install?

6. Can multiple /boot partitions share a single fstab file?

Thanks for any insights....

---

### Post by chrisspelberg on 2009-04-26
One more thing I can think about is using RAID1 for the swap partition as well. This prevents the system from crashing when one of the drives fails.

---

### Post by maclenin on 2009-04-26
I've started a new grub-specific splinter, [_here_]("http://ubuntuforums.org/showthread.php?t=1138512")....

---

