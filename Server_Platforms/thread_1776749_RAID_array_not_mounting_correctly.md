---
title: "RAID array not mounting correctly"
date: 2011-06-06
forum: Server Platforms
---

### Post by ljwobker on 2011-06-06
I have an ubuntu 10.04 machine that I use primarily as a file server.  I have a RAID5 array built with mdadm from 3 component disks that worked properly until a recent upgrade (I'm not sure exactly what broke it though).  The array is /dev/md0 and is set to mount at /var/media on bootup.

*Now*, when the system cold boots it hangs partway through the bootup sequence and throws the following error:

The disk drive for /var/media is not ready yet
Press S to skip ... 

Once I "S"kip this manually, I can see that LOWER in the boot sequence mdadm gets called and assembles the drive, and once fully booted into the system I can then simply do a "mount -a" and the array mounts properly.  

SO... my gut feeling is that some portion of one of the upgrades changed the order in which things are called, and now the "mdadm assemble" is not triggered until AFTER the system tries to mount the drives.  My problem is that I don't know the stuff that controls the boot sequence well enough to dig in the right place.  

As a workaround I can remove that entry from /etc/fstab, but then (of course) the system won't auto-mount the array.  It's better than the boot process completely hanging because as least THIS I can fix remotely, but I'd really like to know

1) why this broke in an upgrade and is it a known problem?
2) how to get it back to where it auto-assembles and then auto-mounts the array on bootup.

thanks!

---

### Post by YesWeCan on 2011-06-06
1) I don't know

2) Need to check your mdadm.conf to make sure it has the correct ARRAY directive. Then run 'update-initramfs -u'

You might want to post mdadm.conf and the output of mdadm --detail /dev/md0

---

### Post by ljwobker on 2011-06-07
fixing the ARRAY directive in mdadm.conf did the trick.  FYI, it was not necessary to run update-initramfs  (is this only necessary when the array in question is part of the boot sequence?)

What scripts/init files/etc control the interaction between mdadm and mount?  Prior to this fix the array was getting assembled, but not mounted... so while I'm quite happy this is fixed, I'd really like to understand why/how it was broken in the first place.  ;)

---

### Post by YesWeCan on 2011-06-07
> **ljwobker said:**
> fixing the ARRAY directive in mdadm.conf did the trick.  FYI, it was not necessary to run update-initramfs  (is this only necessary when the array in question is part of the boot sequence?)
Good :)
No, the initramfs update is not just for booting off the array. I am not exactly sure when this is required and when not, but it sometimes is. If yours is working then forget it. I don't think it does any harm in any event.

> What scripts/init files/etc control the interaction between mdadm and mount?  Prior to this fix the array was getting assembled, but not mounted... so while I'm quite happy this is fixed, I'd really like to understand why/how it was broken in the first place.  ;)
fstab defines the device name of the array to be mounted. AFAIK if during boot mdadm is not able to read the ARRAY directive or has the wrong directive it will assemble the array under the wrong device name.

---

### Post by Weidbrewer on 2011-08-02
> **ljwobker said:**
> fixing the ARRAY directive in mdadm.conf did the trick.


Was there a command that you ran for this, or was it a manual editing?  (If so, what?)

I'm having this exact same problem on my machine, and most of my googling has told me that it is the conf file (isn't it *alway*?) but I'm a little sketchy on the details of how to fix it.

---

### Post by Habitual on 2011-08-02
Weidbrewer:

```
mdadm --examine --scan --config=/etc/mdadm/mdadm.conf >> /etc/mdadm/mdadm.conf
```

Appends /etc/mdadm/mdadm.conf from the  examined configuration. !!! Examine  /etc/mdadm/mdadm.conf manually !!!

Usually in debugging situations, I just rem out any ARRAY statements there and run the above command and reboot.

---

### Post by Weidbrewer on 2011-08-02
Thanks for the fast reply!  just a few additional questions:

[LIST]
[*]Do I enter that code exactly, or are there values I need to substitute based on my system?
[*]Is there the remotest chance that I can screw up the data in the RAID with this? (I don't think so, but I'm paranoid :) )
[*]> !!! Examine /etc/mdadm/mdadm.conf manually !!!  Do you mean before or after (or both)?  Either way, what will I be looking for?
[/LIST]

Again, thank you for the fast reply.  This problem has been bugging the crap out of me for a month or so now.  I don't reboot that machine often, but when I do, it's a hassle.

---

### Post by Habitual on 2011-08-02
> **Weidbrewer said:**
> Thanks for the fast reply!  just a few additional questions:

[LIST]
[*]Do I enter that code exactly, or are there values I need to substitute based on my system?
[*]Is there the remotest chance that I can screw up the data in the RAID with this? (I don't think so, but I'm paranoid :) )
[*]  Do you mean before or after (or both)?  Either way, what will I be looking for?
[/LIST]
Q1: Yes, exactly.
Q2: make copy of /etc/mdadm/mdadm.conf first.
* cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.org

** examine manually is AFTER you run the command.
**REM** out (#) any ARRAY entries that relate to the array(s) giving you the grief **BEFORE** running the command.
you can afterwords check the status of the array with these 2 commands:

```
cat /proc/mdstat
mdadm -Q -D /dev/md0
```

After running "mdadm --examine --scan --config=/etc/mdadm/mdadm.conf >> /etc/mdadm/mdadm.conf" you should just be able to ```
mount -a
``` and be good to go.

Thank me if it works. :)

---

### Post by Weidbrewer on 2011-08-03
Welp...

```
$ sudo mdadm --examine --scan --config=/etc/mdadm/mdadm.conf >> /etc/mdadm/mdadm.conf
bash: /etc/mdadm/mdadm.conf: Permission denied
```

EDIT

I chmod'd the file so that I could do something (for when I'm done, what should the permissions be?) and ran the above command you suggested...didn't seem to change anything in the file, still doesn't mount on boot.  Attempted it with the RAID there and running, also tried it before I mounted it on the next reboot.


```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Thu, 21 Jul 2011 19:32:28 -0400
# by mkconf $Id$
```

---

### Post by Weidbrewer on 2011-08-03
Forget EVERYTHING I just posted!!!

```
sudo echo "DEVICE partitions" > /etc/mdadm/mdadm.conf
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

Bingo.

---

### Post by Habitual on 2011-08-03
So, it's working?

You have a comparable /etc/fstab entry for this raid?

---

### Post by Weidbrewer on 2011-08-03
Yes it is.  Thank you for the help.  Your suggestion might not have directly solved the problem, but it pointed me right where I need to go, and I appreciate it.

Last question:  What should I chmod that file back to to have the right security?

---

### Post by Habitual on 2011-08-03
On my production server, it is 644

```
-rw-r--r-- 1 root root 827 2011-04-15 16:09 /etc/mdadm/mdadm.conf
```

---

