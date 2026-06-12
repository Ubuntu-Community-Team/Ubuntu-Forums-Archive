---
title: "Ubuntu Server 14.04 can't boot degraded soft RAID1"
date: 2015-11-25
forum: Server Platforms
---

### Post by kapela86 on 2015-11-25
I've been testing Ubuntu Server 14.04 on a spare desktop with two harddrives, so I can install it later to a proper server and I ran into a problem, that is it can't boot from degraded RAID1. I recreated that situation on VirtualBox so I can show it to you and hopefully you can help me set it up right. Here's the setup of partitions and softraid:
[IMG]http://i.imgur.com/1lplFnB.png[/IMG]

When two drives are present, it boots and works fine, here is some info from running system:

```
root@ubuntu:/# parted -l
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000MB  999MB   primary               raid
 2      1000MB  21.5GB  20.5GB  primary               boot, raid


Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sdb: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000MB  999MB   primary               raid
 2      1000MB  21.5GB  20.5GB  primary               boot, raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  999MB  999MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 20.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  20.5GB  20.5GB  ext4
```

```
root@ubuntu:/# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : active raid1 sda2[0] sdb2[1]
      19977088 blocks super 1.2 [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      975296 blocks super 1.2 [2/2] [UU]

unused devices: <none>

```

```
root@ubuntu:/# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Nov 25 20:40:09 2015
     Raid Level : raid1
     Array Size : 975296 (952.60 MiB 998.70 MB)
  Used Dev Size : 975296 (952.60 MiB 998.70 MB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Nov 25 20:42:21 2015
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:0  (local to host ubuntu)
           UUID : 6e6ea963:4cb851d8:f4464b30:21ca5aeb
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1


```

```
root@ubuntu:/# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Wed Nov 25 20:40:15 2015
     Raid Level : raid1
     Array Size : 19977088 (19.05 GiB 20.46 GB)
  Used Dev Size : 19977088 (19.05 GiB 20.46 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Wed Nov 25 20:54:33 2015
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:1  (local to host ubuntu)
           UUID : 6f791127:c3b26a7a:5bf92c4f:695f7b56
         Events : 19

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2


```

OK, so I shut down virtual machine, removed second "hdd" from virtual machine and then booted it. It booted without problems and showed raid is in degraded state

```
root@ubuntu:/# parted -l
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 21.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000MB  999MB   primary               raid
 2      1000MB  21.5GB  20.5GB  primary               boot, raid


Model: Linux Software RAID Array (md)
Disk /dev/md0: 999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system     Flags
 1      0.00B  999MB  999MB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 20.5GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  20.5GB  20.5GB  ext4

```

```
root@ubuntu:/# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda1[0]
      975296 blocks super 1.2 [2/1] [U_]

md1 : active raid1 sda2[0]
      19977088 blocks super 1.2 [2/1] [U_]

unused devices: <none>

```

```
root@ubuntu:/# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Wed Nov 25 20:40:09 2015
     Raid Level : raid1
     Array Size : 975296 (952.60 MiB 998.70 MB)
  Used Dev Size : 975296 (952.60 MiB 998.70 MB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Wed Nov 25 21:20:37 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:0  (local to host ubuntu)
           UUID : 6e6ea963:4cb851d8:f4464b30:21ca5aeb
         Events : 21

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed


```

```
root@ubuntu:/# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Wed Nov 25 20:40:15 2015
     Raid Level : raid1
     Array Size : 19977088 (19.05 GiB 20.46 GB)
  Used Dev Size : 19977088 (19.05 GiB 20.46 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Wed Nov 25 21:21:44 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : ubuntu:1  (local to host ubuntu)
           UUID : 6f791127:c3b26a7a:5bf92c4f:695f7b56
         Events : 75

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       0        0        1      removed


```

Everything seems "ok", raid degraded, system booted. So what am I complaining? Well, I did reboot and then this happened (please note that those errors "md0/1 unknown partition table" where present even with both harddrives):
[IMG]http://i.imgur.com/os9hJCH.png[/IMG]

So why first degraded boot is ok, but next ones aren't?

---

### Post by darkod on 2015-11-25
Did you rebooted it as it was, degraded and without "switching" the disks?

Or you tried to boot it with only the second disk present? Or with both disks present?

---

### Post by kapela86 on 2015-11-25
I don't know what you mean by > degraded and without "switching" the disks?

I just removed second hdd (while VM was shut down) and booted VM, it booted fine into degraded state. Then i just rebooted it by command "reboot" and this is when it can't boot.
If I add that second hdd to VM and boot it, VM albo doesn't boot. BUT here's a weird thing, if then I reset VM, it boots fine into degraded state and I see this along the lines in dmesg
```
[   42.409103] md: kicking non-fresh sdb2 from array!

```

---

### Post by mastablasta on 2015-11-26
add empty disk and then try to restore RAID. I think that is the point of RAID. if disk goes you can shut down replace it and restore it all.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)
> [h=1]Boot from Degraded Disk[/h]
If the default HDD fails then RAID will ask you to boot from a degraded disk. If your server is located in a remote area, the best practice may be to configure this to occur automatically:  
[LIST=1]
[*]edit /etc/initramfs-tools/conf.d/mdadm 
[*]change "BOOT_DEGRADED=false" to "BOOT_DEGRADED=true" 
[/LIST]

# Please provide URL to support claim: (this option is not supported from mdadm-3.2.5-5ubuntu3 / Ubuntu 14.04 onwards) 
[LIST]
[*]Additionally, this can be specified on the kernel boot line with the bootdegraded=[true|false] 
[*]You also can use #dpkg-reconfigure mdadm rather than CLI!
[/LIST]


---

### Post by kapela86 on 2015-11-26
> **mastablasta said:**
> add empty disk and then try to restore RAID

It's not about restoring/rebuilding raid, I know the concept behind it and what to do when one drive fails. I just want to point in this thread, that there is a possible bug in Ubuntu how degraded raid is handled.

---

### Post by darkod on 2015-11-26
Can you remake the VM and retry the same again? I agree with you that the degraded raid1 should have started no matter how many reboots you do. I am just wondering if trying this into VBox might have "created" some other complication that we are not aware of.

I actually have tried the same in VBox I think, but long time ago. And I think it performed as expected.

---

### Post by kapela86 on 2015-11-26
I will quote myself
> **I've been testing Ubuntu Server 14.04 on a spare desktop with two  harddrives**, so I can install it later to a proper server and I ran into a  problem, that is it can't boot from degraded RAID1. **I recreated that  situation on VirtualBox so I can show it to you** and hopefully you can  help me set it up right...

---

### Post by darkod on 2015-11-26
Ah, ok. So it did the same on a physical machine? I didn't understand that, I thought it's a test in VBox before trying on the machine.

Was there an image attached with the error messages when trying to boot it second time? I can't seem to see it now. Did you notice what it was complaining about?

PS. Have you tried booting the machine in live mode using the desktop CD and checking out the degraded array state? When I say machine I mean the physical one. If you already have it for testing better to work on it than VBox (I do understand that you made a replica of the situation in VBox).

---

### Post by kapela86 on 2015-11-26
> **darkod said:**
> Was there an image attached with the error messages when trying to boot it second time?
There is, here's a direct link if you can't see it in my 1st post [http://i.imgur.com/os9hJCH.png](http://i.imgur.com/os9hJCH.png)

> **darkod said:**
> PS. Have you tried booting the machine in live mode using the desktop CD and checking out the degraded array state? When I say machine I mean the physical one. If you already have it for testing better to work on it than VBox (I do understand that you made a replica of the situation in VBox).

I didn't try it, and I don't have that physical machine right now. I mean, I have it, but those two drives I tested are being used in one server right now. And it was about a month ago that I did this testing on real machine, I just recently decided to test this on VirtualBox and post here.


I just tested Debian 8.2.0 to see how it handles degraded raid and it's worse there. It always fails to boot with this errors

[IMG]http://i.imgur.com/OxJUJ7Y.png[/IMG]

I will later test Ubuntu 12.04

---

### Post by kapela86 on 2015-11-26
Guess what, Ubuntu Server 12.04 handles degraded raid AS IT SHOULD BE. So I'm 99% sure that it's a bug in Ubuntu Server 14.04.
Here's how it goes, during install it asked me this:
[IMG]http://i.imgur.com/b4YkZ0Q.png[/IMG]

And when I later booted it with one hdd, the first boot was slower, it waited 30 seconds at:
```
[    7.971195] md: bind<sda2>
[    7.973749] md: bind<sda1>
[   37.106451] md/raid1:md1: active with 1 out of 2 mirrors
[   37.106699] md1: detected capacity change from 0 to 9727508480
[   37.108368] md/raid1:md0: active with 1 out of 2 mirrors
[   37.108610] md0: detected capacity change from 0 to 998703104
[   37.122616]  md1: unknown partition table
[   37.123505]  md0: unknown partition table
[   37.270041] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)

```

but next boots are fast and into degraded state:
```
[    8.336452] md: bind<sda1>
[    8.339294] md: bind<sda2>
[    8.341378] md/raid1:md1: active with 1 out of 2 mirrors
[    8.341646] md1: detected capacity change from 0 to 9727508480
[    8.356554]  md1: unknown partition table
[    8.559047] md/raid1:md0: active with 1 out of 2 mirrors
[    8.559301] md0: detected capacity change from 0 to 998703104
[    8.561299]  md0: unknown partition table
[    8.636662] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)

```

After connecting second vdi and booting, it didn't automatically add it to array so I had to do it manually, it synced and everything was ok

---

### Post by mastablasta on 2015-11-27
wow if this is true it would be a major bug. have you tried posting on Launchpad as bug ?

it says unknown partition table. hmm.. reminds me when I did server install. I had debian installed before but then decided to do a fresh ubuntu after OS disk got ruined. and saw something similar in installer. it wouldn't recognise the RAID the first couple of tries. wasn't sure why. followed again the procedure instruction and suddenly it all worked, mounted properly etc. only disks & partitions got osme sztraneg numbers. other than that there is nothing suspicious on it these days.

I keep the OS on separate drive and ii plan to do some syncing or more likely rdiff-backup to another drive. and keep only data on sw RAID.

still I am interested in this. could this be a major bug non one else saw?

---

### Post by darkod on 2015-11-27
I would not be worried about the partition table message. I think that's normal for md devices, and depending if you are listing it with fdisk, or parted, etc. If you think about it, the md device really has no PT because it's not partitioned further on. It is used and formatted directly, the filesystem lies directly on it. The physical HDDs hold the partitions, the md devices no.

When I get back from work I will do VBox tests with 14.04.3 also. Lets see...

---

### Post by kapela86 on 2015-11-27
> **mastablasta said:**
> wow if this is true it would be a major bug. have you tried posting on Launchpad as bug ?

No I didn't. I first wanted to ask here if anyone else experienced it. I will wait for **darkod** tests results

---

### Post by darkod on 2015-12-04
I was able to reproduce this. Did a brand new VM with 2x8GB disks in VBox, installed as raid1, etc... Did a dist-upgrade to fully upgrade all packages.

Removed the /dev/sdb disk. It booted once, after reboot it drops to initramfs prompt. Tried few reboots from the prompt, still the same.

Did a few poweroff commands and starting it again, still the same. It stays on the initramfs prompt.

Now, this could be an issue with VBox + ubuntu combination. I have no physical machine to try...

Forgot to mention. I used the 14.04.3 64bit server image.

---

### Post by kapela86 on 2015-12-04
Like I said in my first post, it happend to me on physical machine and i reproduced it in virtualbox ;) So it seems it's really an issue with Ubuntu 14

---

### Post by mastablasta on 2015-12-07
IMO - has to be reported to Launchpad along with data.

I too have a server with RAID1, though my OS is on USB stick so it should not be affected with this. however some people do have OS on RAID as well and this is not good.

I doubt it is virtualbox since they update it quite regularly as well as 12.04 if I understand works well

---

