---
title: "Ubuntu 10.04 LTS hangs on startup after editing fstab"
date: 2010-11-05
forum: Server Platforms
---

### Post by elijahmuha on 2010-11-05
I have been wading through different approaches in mounting an NFS folder from another one of my servers with very little success.  In the process I edited the fstab file per instructions from a former Admin in order to make this happen.  Upon rebooting my machine I get a mount error that does not clear and does not allow the boot process to complete.  The error is as follows:

[INDENT]mount.nfs4: No such device
mountall: mount /var/websites/lms/moodledata [621] terminated with status 32

[/INDENT]The message shows up twice and I cannot bypass it.  I tried to boot in recovery mode with the same results.  Does anyone know how I can get around this so I can fix my fstab file?  It would certainly save me heaps of time.  Thank you in advance!

---

### Post by drs305 on 2010-11-05
You can boot to the LiveCD, mount your Ubuntu partition and then edit the fstab file. If you don't know what to fix, post the contents. Change **XY** to your Ubuntu partition. If you don't know what it is, type this command and look for the "Linux" partition:  sudo fdisk -l  (lowercase L)

```
sudo mount /dev/sd**XY** /mnt
gksu gedit /mnt/etc/fstab
```

---

### Post by elijahmuha on 2010-11-05
Worked like a charm.  Thanks for the help!

---

### Post by CharlesA on 2010-11-05
You should be able to hit "s" to skip a failed mount.

---

### Post by fast_eddie on 2010-12-22
Hi,

I'm a Linux/Ubuntu novice and I've been a complete idiot and managed to overwrite the fstab file on a new installation (10.04). I was tired and hadn't copied or renamed the original file and so have no idea what was written in it, I thought I'd downloaded it but I hadn't and editted another fstab file (from 10.10) and uploaded that via ftp in error. I only have CLI access to the server (running under a vmware VDS) via SSH.

The server hasn't been rebooted and I wondered if there was anyway of recovering or rebuilding the fstab file correctly/safely. I have been able to establish the following:

Filesystem             1K-blocks          Used      Available    Use%    Mounted on
/dev/sda5                16820092     9459660     6506008      60%     /
none                              769732                184            769548        1%     /dev
none                              771860                    0              771860        0%     /dev/shm
none                             771860                  32             771828        1%     /var/run
none                              771860                    0              771860        0%     /var/lock
none                              771860                    0              771860        0%     /lib/init/rw
/dev/sda6                11533592       159716   10787996        2%     /tmp
/dev/sda1    119987             28615        85177      26%    /boot

Disk /dev/sda: 37.6 GB, 37591449600 bytes
255 heads, 63 sectors/track, 4570 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00093d6f

   Device       Boot            Start               End             Blocks    Id    System
/dev/sda1      *                      1                   16               123904   83    Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2                             16                4571    36583425      5     Extended
/dev/sda5                             16                2144       17088512 83     Linux
/dev/sda6                        2144                3603       11717632   83     Linux
/dev/sda7             3603                4571          7775232   82     Linux swap / Solaris

I also have the blkid.tab so have the corresponding UUID doe sda1, sda5, sda6 and sda7

Now that you've picked yoursleves up off the floor from laughing so much, could you please advise how I should proceed ;)

Many thanks, Ed

---

### Post by drs305 on 2010-12-22
fast_eddie

Welcome to the Ubuntu forums.  :-)

If you are in the affected installation, go to the second section. 

If not, and you can mount the Ubuntu partition, you can access the existing fstab for editing. Assumes sda1 is your Ubuntu partition.

```
sudo mount /dev/sda**[COLOR="Red"]1[/COLOR]** /mnt
sudo cp /mnt/etc/fstab /mnt/etc/fstab.bak
sudo nano /mnt/etc/fstab
```

All you need for it to boot in the fstab contents are the following; you can clean it up and add more later. If you formatted it as ext4, change that entry, and change sda1 to the Ubuntu partition:

> 
/dev/sda**[COLOR="Red"]1[/COLOR]** /  ext3  errors=remount-ro 0       1


---

### Post by fast_eddie on 2010-12-22
Hi 

Thank you for your prompt reply, you're correct sda[COLOR=Red]**1**[/COLOR] is the boot partition. 
All /dev/sda**[COLOR=Red]#[/COLOR]** devices have **[COLOR=Red]ext4[/COLOR]** as their type, except sda**[COLOR=Red]7[/COLOR]** which is configured as the SWAP partition.

Do I need to include the UUID for each device partition (within fstab) or is it enough that the blkid.tab file has these corresponding to each sda**[COLOR=Red]#[/COLOR]**?

Many thanks, Ed

---

### Post by CharlesA on 2010-12-22
It's a good idea to use the UUID, as using the sdxy designation might change after a reboot.

---

### Post by fast_eddie on 2010-12-22
This is what I've created...
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# /boot was on /dev/sda1 during installation
UUID=ca1008d4-e8b8-4258-bcfe-41e3a7d2e63f /boot           ext4    errors=remount-ro 0       1
# / was on /dev/sda5 during installation
UUID=39b617a6-39dc-4410-95e3-9b38519924e9 /               ext4    errors=remount-ro 0       1
# /tmp was on /dev/sda6 during installation
UUID=0f6d2e62-15b9-4c01-a221-03a7d0c6ad53 /tmp            ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=8d45b1d7-7bf1-4aa7-955b-aa967e947366 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

I need to be able to execute a Parallels Plesk Panel 10 installer package, so hope this will work..?

---

### Post by drs305 on 2010-12-22
This should work. You only need the "errors" option on /. 

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0  0
# /boot was on /dev/sda1 during installation
UUID=ca1008d4-e8b8-4258-bcfe-41e3a7d2e63f /boot   ext4   defaults 0  1
# / was on /dev/sda5 during installation
UUID=39b617a6-39dc-4410-95e3-9b38519924e9 /      ext4    errors=remount-ro 0  1
# /tmp was on /dev/sda6 during installation
UUID=0f6d2e62-15b9-4c01-a221-03a7d0c6ad53 /tmp   ext4    defaults 0  1
# swap was on /dev/sda7 during installation
UUID=8d45b1d7-7bf1-4aa7-955b-aa967e947366 none   swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0  0

```

Just to verify the UUIDS, run the following to ensure you aren't getting cached UUIDs:
```
sudo blkid -c /dev/null
```

Can't answer your Parallels Plesk Panel 10 question though.

---

### Post by fast_eddie on 2010-12-22
Ok great made those changes and checked that the UUID's are current and weren't cached.

Is it just a case of uploading the revised /etc/fstab via ftp and then rebooting the server?

The only reason why I mentioned the Plesk Panel installer, was that was when I realsied I'd overwritten the original fstab, as I was getting an error saying that I couldn't execute the binary file!

Ed

---

### Post by CharlesA on 2010-12-22
That's pretty much all you need to do, yep.

The error you were getting with Plesk Panel doesn't have anything to do with fstab. :)

---

### Post by fast_eddie on 2010-12-22
[FONT=Arial]Hi,
[/FONT][FONT=Arial]
What would you receommend is the best command to use for the reboot to take account of the changes in /etc/fstab?[/FONT]
**hard-reboot** restart

[FONT=Arial]Many thanks once again!__[/FONT]

---

### Post by CharlesA on 2010-12-22
A normal reboot would be fine.

```
sudo reboot
```

---

### Post by fast_eddie on 2010-12-22
Many thanks Charles - that did the trick.

I just need to understand why I can get this installer package to execute now!

# ./parallels_installer_v3.7.1_build101014.17_os_Ubuntu_10.04_x86_64
-bash: ./p.arallels_installer_v3.7.1_build101014.17_os_Ubuntu_10.04_x86_64: cannot execute binary file

---

### Post by CharlesA on 2010-12-22
It would have to have execute permission:

```
chmod +x filename
```

---

### Post by fast_eddie on 2010-12-24
All fixed thank you!

---

### Post by fudoki on 2011-01-07
Thanks!  Maybe I'm just stupid, but I have been a Programmer and Electrical Engineer for over 30 years, using *nix the entire time.  How is there not a NOTE in the script that mentions this, in case a distant machine is down, broken, offline, etc.??  After almost 2 years and 2 versions, is it too soon to ask that this small addition be made to the script dialog; since the alternative is a a frozen, boat anchor, of a system.  Debian, Red Hat, etc., etc.  will time out and move on, eventually...  This might be an additional novel idea to put into the script..?

Thanks so much for the reminder.  I had not run into this since Xenix 386 back in 1989.  Sry, it's just the fact...

Again thx, "s" got me into the system.

---

### Post by CharlesA on 2011-01-08
> **fudoki said:**
> How is there not a NOTE in the script that mentions this, in case a distant machine is down, broken, offline, etc.??  After almost 2 years and 2 versions, is it too soon to ask that this small addition be made to the script dialog; since the alternative is a a frozen, boat anchor, of a system.  Debian, Red Hat, etc., etc.  will time out and move on, eventually...  This might be an additional novel idea to put into the script..?

What script?

---

