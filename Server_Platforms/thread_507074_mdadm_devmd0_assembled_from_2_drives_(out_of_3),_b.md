---
title: "mdadm: /dev/md0 assembled from 2 drives (out of 3), but not started"
date: 2007-07-22
forum: Server Platforms
---

### Post by aboutblank on 2007-07-22
I'm attempting to setup mdadm based RAID on a 7.04 fileserver. Everything works until I try to fail a drive by physically disconnecting the first one at which point it will tell me...

> mdadm: /dev/md0 assembled from 2 drives (out of 3), but not started
mdadm: /dev/md1 assembled from 2 drives (out of 3), but not started
mdadm: /dev/md2 assembled from 2 drives (out of 3), but not started

After a long pause it will dump me into ash.

I even tried to put "-R" into /etc/rcS.d/S25mdadm-raid where I think the script mounts the array. From the manpage of mdadm:
> -R, --run
    Attempt to start the array even if fewer drives were given than are needed for a full array. Normally if not all drives are found and --scan is not used, then the array will be assembled but not started. With --run an attempt will be made to start it anyway.

Another problem which may or may not be related is that I had the "mdadm: No devices listed in conf file were found" message but it *would* continue to boot. I fixed this message by following....

> Unfortunately, there is a bug in software RAID in Ubuntu 7.04 that didn't exist in Ubuntu 6.0.6.1 LTS, with a error message "mdadm: No devices listed in conf file were found" found, but which does continue to boot normally. The solution is to add "sleep 10" in the initramfs init script as described in [http://ubuntuforums.org/showpost.php...81&postcount=5](http://ubuntuforums.org/showpost.php...81&postcount=5)

    * Manually edit /usr/share/initramfs-tools/init
    * put sleep 10 after line log_begin_msg "Mounting root file system..."
    * Save the file, and then run update-initramfs -k all -u



**My Setup**

I'm running...
RAID1 over 3 drives for /boot - 100 MB
RAID1 over 3 drives for / - 3 GB
A swap on each drive (non-RAID) - 400 MB * 3 drives
RAID5 over 3 drives for /data  - 493 GB

sudo fdisk -l
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sda2              13         377     2931862+  fd  Linux raid autodetect
/dev/sda3             378         426      393592+  82  Linux swap / Solaris
/dev/sda4             427       30401   240774187+  fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdb2              13         377     2931862+  fd  Linux raid autodetect
/dev/sdb3             378         426      393592+  82  Linux swap / Solaris
/dev/sdb4             427       30401   240774187+  fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          12       96358+  fd  Linux raid autodetect
/dev/sdc2              13         377     2931862+  fd  Linux raid autodetect
/dev/sdc3             378         426      393592+  82  Linux swap / Solaris
/dev/sdc4             427       30401   240774187+  fd  Linux raid autodetect



cat /proc/mdstat
> Personalities : [raid1] [raid6] [raid5] [raid4] 
md2 : active raid5 sda4[0] sdc4[2] sdb4[1]
      481548160 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
      
md1 : active raid1 sda2[0] sdc2[2] sdb2[1]
      2931776 blocks [3/3] [UUU]
      
md0 : active raid1 sda1[0] sdc1[2] sdb1[1]
      96256 blocks [3/3] [UUU]
      
unused devices: <none>

sudo mdadm --query --detail /dev/md0
>         Version : 00.90.03
  Creation Time : Fri Jul 20 19:06:34 2007
     Raid Level : raid1
     Array Size : 96256 (94.02 MiB 98.57 MB)
    Device Size : 96256 (94.02 MiB 98.57 MB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Jul 22 14:39:03 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

           UUID : c626fbb5:3cbf1969:b8d73a08:b1deb631
         Events : 0.56

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1


**Thank you for any help**

---

### Post by Dawnthorn on 2007-08-18
I figured this out. It is a combination of the sleep fix and your attempt to add -R to /etc/rcS.d/S25mdadm-raid. The problem with that is that the raid device needs to come up during an earlier boot phase. Here's the procedure:
```

1. Manually edit:
/usr/share/initramfs-tools/scripts/local-top/mdadm
2. Find the line:
: "${MD_DEGRADED_ARGS:= --no-degraded}"
3. Remove :
--no-degraded
4. Run:
update-initramfs -k all -u

```

My fix is obviously a hack. It looks like someone intended to do something with MD_DEGRADED_ARGS, but I don't know much about the boot sequence, so I'm not sure where the proper place to fix this really is.

---

### Post by Dawnthorn on 2007-08-18
Ok. So that didn't work. The problem is more complicated. Of course, they added that --no-degraded line to fix another problem. So, I've come up with another solution. Apply [this patch]("http://launchpadlibrarian.net/8884018/failed-raid.patch") to initramfs-tools and run update-initfs like this:
```

cd /usr/share/initramfs-tools
sudo patch -b -p0 /tmp/failed-raid.patch
sudo update-initramfs -k all -u 

```

Then reboot. Now if you shutdown the machine and disconnect one of your RAID drives, it will pause for like 3 minutes during boot up (there is a 3 minute timeout). Then it will try mdadm again, but this time allow it to start with failed drives.

---

### Post by krsnendu on 2008-02-16
I am trying to run the patch at the moment. I have been waiting for over ten minutes. How long should it take to patch?

---

### Post by elventear on 2008-04-07
Quick note. In Ubuntu 7.10 you need to edit /etc/udev/rules.d/85-mdadm.rules and remove the '--no-degraded' option then update initramfs. Everything should work, afterwards.

---

### Post by rgotten on 2008-04-25
If i a doing the instalation of ubuntu server, how do i apply the patch..Do i have to copy it manually..I am new to all this

Thanks

rgotten

---

