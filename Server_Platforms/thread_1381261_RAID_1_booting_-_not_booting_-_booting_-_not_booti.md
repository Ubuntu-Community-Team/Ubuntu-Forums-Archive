---
title: "RAID 1: booting - not booting - booting - not booting"
date: 2010-01-14
forum: Server Platforms
---

### Post by boudies on 2010-01-14
I am in the process of installing a Karmic 9.10 server on an HP Proliant ML110 G6. I have set up separate partitions for /boot, / (root), /var, /usr and /home. All have been set up for RAID 1.

I get the following strange behavior: server is running. I manually reboot (# sudo reboot). I get the message "GRUB loading", but then I get a "degraded raid" message and the startup drops to a BusyBox shell. I reboot ("reboot" command) and the system starts up just fine. 

The behavior is not predictable, i.e. the chances of successful or failing start-up are about 50-50. Yesterday I got 100% "successful boot"from Busybox reboot, and 100% failure from "ubuntu reboot"but today that appears to be not the case.

Any idea how I could get this solved?

---

### Post by fjgaude on 2010-01-14
It would appear the kernel can't create all the arrays in time, or in the time allowed. You do have an array for each partition?

I can't remember the text needed to be added in the menu.lst to allow more time for the **md** to assemble arrays at boot time. I'll try to location it and get back with you.

---

### Post by boudies on 2010-01-15
I do have arrays for each partition - running df generates:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/md1               9614052    413900   8711784   5% /
udev                   2025640       264   2025376   1% /dev
none                   2025640         0   2025640   0% /dev/shm
none                   2025640        96   2025544   1% /var/run
none                   2025640         0   2025640   0% /var/lock
none                   2025640         0   2025640   0% /lib/init/rw
/dev/md0                 93207     34977     53418  40% /boot
/dev/md2              48062344    184356  45436516   1% /home
/dev/md3              96124812    580276  90661588   1% /var
/dev/md4              78771120    944208  73825532   2% /usr
```
When the system manages to boot all devices are active - cat /proc/mdstat output is:
```
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0] sdc1[1]
      96256 blocks [2/2] [UU]

md2 : active raid1 sda5[0] sdc5[1]
      48829440 blocks [2/2] [UU]

md1 : active raid1 sda3[0] sdc3[1]
      9767424 blocks [2/2] [UU]

md4 : active raid1 sda7[0] sdc7[1]
      80027648 blocks [2/2] [UU]

md3 : active raid1 sda6[0] sdc6[1]
      97659008 blocks [2/2] [UU]

unused devices: <none>
```
and for each array mdadm --detail /dev/mdX looks like:
```
/dev/md0:
        Version : 00.90
  Creation Time : Mon Jan 11 20:07:19 2010
     Raid Level : raid1
     Array Size : 96256 (94.02 MiB 98.57 MB)
  Used Dev Size : 96256 (94.02 MiB 98.57 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan 15 08:31:43 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 0c8cda94:8e708953:74dbe486:d2cb712b
         Events : 0.26

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
```
I certainly would appreciate if someone could indicate how to increase the time to assemble the arrays at boot.

---

### Post by boudies on 2010-01-15
Searching though the archives this could be due to an [initramfs race condition SATA and MD]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg173625.html")
So far I was not able to identify a solution, though.

---

### Post by boudies on 2010-01-15
I tried adding a delay here (per [http://ubuntuforums.org/showthread.php?t=1004196](http://ubuntuforums.org/showthread.php?t=1004196)):

Edit this file, adding the sleep line after the **mount**: /usr/share/initramfs-tools/init   # to stop a race condition with md. The line numbers may not be the same for your system.

     ```

187 maybe_break mount
188 sleep 10
189 log_begin_msg "Mounting root file system..." 
```Then run this to rebuild the image
```
sudo /usr/sbin/update-initramfs -uk all 
```Unfortunately this did **NOT **fix the problem. Boot did slow down significantly, though.

---

### Post by fjgaude on 2010-01-16
Say, try 'sleep 100' and see what happens.

---

### Post by boudies on 2010-01-16
Tried "Sleep 100" as suggested. Problem is still there. 

The delay is part of the boot sequence - I timed a 100 second delay after the "Starting up ..." message. 

You can hear whether the boot will be successful: if it will be, you can hear harddisk activity right after the "System starting ..."message (i.e. at the beginning of the sleep delay).

FYI I downgraded to GRUB prior to these experiments - problem persists

---

### Post by boudies on 2010-01-16
In an attempt to further debug I commented the "quiet" statements from the grub menu:
```
title           Ubuntu 9.10, kernel 2.6.31-17-server (quiet)
root            (hd0,0)
kernel          /vmlinuz-2.6.31-17-server root=/dev/md1 ro
# kernel                /vmlinuz-2.6.31-17-server root=/dev/md1 ro quiet splash
initrd          /initrd.img-2.6.31-17-server
# Uncommented to generate diagnostics
# quiet
```Boot is now slower due to the messages that are being generated. But it is more reliable (though still not perfect).

---

### Post by fjgaude on 2010-01-16
There a parameter to add to the kernel grub line to delay things... I'm running grub2 now and don't have the man pages for grub. Try finding how to add delay in a menu.lst line from **man grub**.

---

### Post by boudies on 2010-01-17
Found the parameter in question - it's called > rootdelay.
 
I changed menu.lst accordingly ([http://www.debianhelp.org/node/3943](http://www.debianhelp.org/node/3943)):
```
title           Ubuntu 9.10, kernel 2.6.31-17-server (rootdelay=10)
root            (hd0,0)
kernel          /vmlinuz-2.6.31-17-server rootdelay=10 root=/dev/md1 ro quiet splash
# kernel                /vmlinuz-2.6.31-17-server root=/dev/md1 ro quiet splash
initrd          /initrd.img-2.6.31-17-server
# Add # comment to suppress diagnostics:
quiet
 
title           Ubuntu 9.10, kernel 2.6.31-17-server (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.31-17-server root=/dev/md1 ro  single
initrd          /initrd.img-2.6.31-17-server

```Problem persists:

[LIST=1]
[*]First item always complains about degraded RAID devices. If I comment the "quiet" parameter chances for succesfull boot increase significantly
[*]Second menu item starts up in 2 out of 3 cases - if it fails it does so for a degraded RAID
[/LIST]Note: increasing rootdelay to 100 doesn't make a difference.
 
Any further suggestions, anybody?

---

### Post by boudies on 2010-01-17
Two weeks ago I had never used linux, but having a problem like this certainly helps to get up to speed ;-).

It looks like the issue should be solved somewhere in initramfs. That's the direction I'm looking into - so far without a final resolution.

Reading though all posts, bugs, etc. that come up Googling I get the impression that this kind of problem is not unique to my situation, but then I haven't been able to find the ultimate solution yet. 

Any hints would be highly appreciated!

---

### Post by boudies on 2010-01-19
Finally - problem solved:

After messing around for a few days now, I decided to do a clean install of Ubuntu. This made matters WORSE: the drive that was supposed to be the other half of the RAID array now completely disappeared !

I then pulled the HP utilities disk and did a "complete erase" of the system.

Subsequently, I did a clean install of Ubuntu and now everything seems to be working allright.

Thanks, fjgaude, for your help.

---

### Post by fjgaude on 2010-01-21
Wow, you are welcome!

These kinds of issues can drive us all nuts... glad you have a working system now. Let us know if anything goes wrong.

---

