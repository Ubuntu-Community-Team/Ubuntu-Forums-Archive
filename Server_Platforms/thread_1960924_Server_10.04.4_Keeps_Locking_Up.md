---
title: "Server 10.04.4 Keeps Locking Up"
date: 2012-04-18
forum: Server Platforms
---

### Post by skipgillespie on 2012-04-18
I am running Lucid 10.04.4.  It is being used as a file server with 3 - 2TB drives in a RAID5 array.  I keep having trouble with the server locking up.  I lose all control of it including local keyboard and monitor.  I thought that perhaps the VNC virtual Gnome desktop may have been causing problems or maybe one of the other programs I installed, so I reinstalled the OS and have so far only setup Samba and SSH.  Unfortunately, this has not resolved the issue.  Can anyone help?

---

### Post by Jonathan L on 2012-04-18
Hi Skipgillespie

> I reinstalled the OS and have so far only setup Samba and SSH .. not resolved

I'd suggest looking through the logs and see if your disk systems are complaining about anything.  Post anything you're suspicious of here and we'll see if we can help.

Kind regards,
Jonathan.

---

### Post by skipgillespie on 2012-04-18
I'm a little bit new to linux.  I have been learning a great deal though, thanks to everyone here and my own research and trial and error. Where would I find these logs and how do I access them?

---

### Post by Jonathan L on 2012-04-18
Hi again Skipgillespie

>  Where would I find these logs and how do I access them?

They are text files stored in /var/log

If you're new to them, the simpliest thing to do is look at the most recent ones (I often just fgrep the whole lot!) ... but the ones you want first are probably /var/log/dmesg and /var/log/messages

They have timestamps so if you know when your server stopped, you can look and see what was happening just beforehand.

Hope that helps.

Kind regards,
Jonathan.

---

### Post by skipgillespie on 2012-04-18
Since I reinstalled the OS, it's acting a little different.  Originally, after I would reboot from it freezing, I could immediately access my RAID.  Now it seems to unmount the RAID and I have to remount it each time I reboot.

These are what I saw that stood out:

**_/var/log/messages_**


Apr 18 08:46:41 ubuntu kernel: [ 1632.842719] EXT4-fs (md0): recovery complete
Apr 18 08:46:41 ubuntu kernel: [ 1632.843410] EXT4-fs (md0): mounted filesystem with ordered data mode
Apr 18 09:02:54 ubuntu kernel: [ 2606.262475] JBD: [COLOR="Red"]barrier-based sync failed on md0-8 - disabling barriers[/COLOR]



Apr 18 07:23:43 ubuntu kernel: [    0.000000] [COLOR="red"]Fast TSC calibration failed[/COLOR]
Apr 18 07:23:43 ubuntu kernel: [    0.000000] TSC: PIT calibration matches PMTIMER. 1 loops



Apr 17 21:45:12 ubuntu kernel: [ 3004.308161] EXT4-fs (md0): mounted filesystem with ordered data mode
Apr 17 21:45:31 ubuntu kernel: [ 3023.069255] JBD: [COLOR="red"]barrier-based sync failed on md0-8 - disabling barriers[/COLOR]


**_var/log/dmesg_**

Phoenix BIOS detected: [COLOR="Red"]BIOS may corrupt low RAM[/COLOR], working around it.


Marking TSC unstable due to TSC halts in idle


[    3.561427] [COLOR="red"]raid5: md0 is not clean -- starting background reconstruction[/COLOR]
[    3.561463] raid5: device sdd2 operational as raid disk 2
[    3.561467] raid5: device sdc2 operational as raid disk 1
[    3.561471] raid5: device sdb2 operational as raid disk 0
[    3.562060] raid5: allocated 3179kB for md0
[    3.562816] 2: w=1 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[    3.562823] 1: w=2 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[    3.562826] 0: w=3 pa=0 pr=3 m=1 a=2 r=3 op1=0 op2=0
[    3.562830] raid5: raid level 5 set md0 active with 3 out of 3 devices, algorithm 2
[    3.562832] RAID5 conf printout:
[    3.562834]  --- rd:3 wd:3
[    3.562838]  disk 0, o:1, dev:sdb2
[    3.562840]  disk 1, o:1, dev:sdc2
[    3.562843]  disk 2, o:1, dev:sdd2
[    3.562906] md0: [COLOR="red"]detected capacity change from 0 to 4000527024128[/COLOR]
[    3.566432]  md0:
[    3.566665] md: resync of RAID array md0
[    3.566669] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[    3.566672] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
[    3.566679] md: using 128k window, over a total of 1953382336 blocks.
[    3.600702]  [COLOR="red"]unknown partition table[/COLOR]
[    3.613257] mdadm: sending ioctl 1261 to a partition!
[    3.613266] mdadm: sending ioctl 1261 to a partition!

---

### Post by skipgillespie on 2012-04-19
Okay, I'm beginning to think that it has something to do with my RAID array.  I rebooted the server when I got home yesterday and did not remount the RAID.  It is in the process of syncing.  Here we are 17 hours later and the server has not frozen.  Could the syncing process of the RAID be causing this?  Are there any utilities available to monitor the drives within the array to look for problems?  I am using a hardware RAID card but it is turned off.  Could that be causing issues since I am using software RAID instead?

FYI.....it is a 4TB, RAID5 array using 3 - 2TB Seagate drives.

---

### Post by Gyokuro on 2012-04-19
Hi,

software raid is fine and much better as hardware with cheap onboard controllers (intel fake raid,...) except real raid controllers. You can monitor the health of your raid setup via:

sudo cat /proc/mdstat

or better to follow

sudo watch cat /proc/mdstat

or

sudo mdadm --query --detail /dev/md*

I have seen that your error correction took some time and therefore I suggest that you check:

sudo cat /proc/sys/dev/raid/speed_limit_min

and set it to something higher to shorten the time to recreate/rebuild/correct raids to something like

sudo echo 100000 >/proc/sys/dev/raid/speed_limit_min

which means 100 MB/s (depends on your setup, value can be stored in /etc/sysctl.conf) - you have to test maybe some different values or get them through benchmarking of your RAID setup.

---

