---
title: "Degraded RAID5 Booting in Emergency Mode"
date: 2016-10-17
forum: Server Platforms
---

### Post by simoncaron on 2016-10-17
Hi everyone first time posting on the forum!

I'm currently testing my RAID5 configuration before moving my data to my new array and I having some trouble figuring out how to boot with a degraded array.
Just to be clear here's what I'm attempting to do...

I've installed Ubuntu 16.04.1 server + swap onto an SSD and created a RAID5 array with 4 other hard drives mounted on /data with mdadm. I've also installed grub on the SSD with the OS.
After the installation, I powered off my device and removed one the 4 drives of the array. I expected the system to boot and mdadm to notify me that the array was degraded but when I booted up the system I was greeted with the emergency mode instead. I've tried to continue the boot process (sysctl default) but it keeps going back to emergency mode. Is there anything I'm missing. Both the SSD and the array are in the fstab file. 

It also seems like the system is waiting for the array to show up while booting, it's waiting 1 minute and 30 secs to check if the array gets mounted.

What am I doing wrong here?

---

### Post by Speculos on 2016-10-18
Hi,

Can you post more details about your mdadm ARRAY ?

cat /etc/fstab
cat /etc/mdadm/mdadm.conf

and

mdadm -D /dev/mdxxx (where xxx is the number of your array).

Cheers.

---

### Post by simoncaron on 2016-10-18
Here's my fstab file:

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=5164241a-26dc-4b42-a380-ba93968ba82f /               ext4    errors=remount-ro 0       1


# /data was on /dev/md0 during installation
UUID=63135473-f5e4-48b1-ba97-bee988ade688 /data           ext4    defaults        0       2


# swap was on /dev/sda5 during installation
UUID=88548ece-7f19-48ad-8c0d-2da1933562aa none            swap    sw              0       0

```

Here's the mdadm config file:

```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays
ARRAY /dev/md/0  metadata=1.2 UUID=70f364dd:1ccc52b0:7fba5b18:9fd38a89 name=ubuntu-linux-server:0


# This file was auto-generated on Sun, 16 Oct 2016 19:19:00 -0400
# by mkconf $Id$

```

And here's the output of the [COLOR=#000000]mdadm -D /dev/md0 command:
[/COLOR]```

dev/md0:
        Version : 1.2
  Creation Time : Sun Oct 16 19:18:18 2016
     Raid Level : raid5
     Array Size : 15710208 (14.98 GiB 16.09 GB)
  Used Dev Size : 5236736 (4.99 GiB 5.36 GB)
   Raid Devices : 4
  Total Devices : 4
    Persistence : Superblock is persistent


    Update Time : Tue Oct 18 21:22:50 2016
          State : clean 
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 512K


           Name : ubuntu-linux-server:0  (local to host ubuntu-linux-server)
           UUID : 70f364dd:1ccc52b0:7fba5b18:9fd38a89
         Events : 21


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

```

---

### Post by macduke on 2016-10-19
Hello,

add "bootdegraded=true" to the kernel boot line. If you use grub you can edit the kernel boot line at start or you add the parameter to "/etc/default/grub" to GRUB_CMDLINE_LINUX_DEFAULT="bootdegraded=true"

Cheers

---

### Post by simoncaron on 2016-10-19
I added the line to my grub config and I ran update-grub.

When I reboot the machine, I still get :

*A start job is running for dev-disk-by uuid [COLOR=#000000][FONT=Ubuntu Mono]63135473-f5e4-48b1-ba97-bee988ade688[/FONT][/COLOR].device*
and then it goes back to emergency mode.

---

### Post by darkod on 2016-10-19
Lately I see many reports that ubuntu server degraded boot is not working, for either raid1 or raid5 arrays. This could be a major bug, if it really is a bug, but I'm not aware of any bug reports. Maybe try searching on launchpad.

You seem to have everything configured correctly, if it doesn't work it really starts looking like ubuntu's fault...

---

### Post by simoncaron on 2016-10-19
I tried the same config on 15.10 and got the same result however the same config is working in Debian Jessie...

---

