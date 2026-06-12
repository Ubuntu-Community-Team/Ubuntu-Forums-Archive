---
title: "Filesystem and partition confusion (fdisk, parted, dh)"
date: 2011-07-10
forum: Server Platforms
---

### Post by wminor on 2011-07-10
Apologies for the slightly vague question, but I'm confused as hell, and all the books and articles I'm reading aren't helping to clear this up.

So - I've just done a fresh installation of Ubuntu Server 10.04. I installed from a USB flash drive as the machine has no CD drive at the moment. I had some problems with getting the machine to boot after installation, it seemed that Grub had been installed onto the MBR of the USB stick or something, as when I tried to boot from the hard drive it wouldn't get anywhere. When I booted from the USB drive, it would boot into the system that was installed on the HDD - pretty weird right? The solution was to run grub-install, which installed grub on the HDD and now it boots fine. However, as a result of this confusion I wanted to take some time to check that nothing else had gone wrong with the partitioning or anything related. This is where I get confused:

So, my first step is to run 'fdisk -l' and 'parted -l' to see what the situation is:

```
wminor@akuma:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00055a74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5            9328        9730     3227648   82  Linux swap / Solaris

wminor@akuma:~$ sudo parted -l
Model: ATA ST380815AS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  76.7GB  76.7GB  primary   ext4
 2      76.7GB  80.0GB  3305MB  extended
 5      76.7GB  80.0GB  3305MB  logical   linux-swap(v1)
```

All looks fine, right? Or is it wrong that sda2 and sda5 both occupy the same blocks?

When I run 'df':

```
wminor@akuma:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             73744616    857948  69140620   2% /
none                    958304       216    958088   1% /dev
none                    962820         0    962820   0% /dev/shm
none                    962820        32    962788   1% /var/run
none                    962820         0    962820   0% /var/lock
none                    962820         0    962820   0% /lib/init/rw
```

That doesn't look right to me. I don't understand what's going on properly to be honest, and I don't seem to be able to find a proper explanation of the output anywhere. The bit that alarms me is that there are 6 entries, when I would expect 3. Also, why is the filesystem 'none' for all but the top row?

I'm probably missing a fundamental piece of understanding here, and it may well be something obvious, so apologies if that is the case. 

If anyone can shed any light on what's going on here, or educate me so that I can better understand the output of df, that would be much appreciated.

Thanks in advance :D

---

### Post by matt_symes on 2011-07-10
Hi

> All looks fine, right? Or is it wrong that sda2 and sda5 both occupy the same blocks?

That is fine. sda2 is an extended partition and is used as a container for the logical partition sda5.

> That doesn't look right to me. I don't understand what's going on  properly to be honest, and I don't seem to be able to find a proper  explanation of the output anywhere. The bit that alarms me is that there  are 6 entries, when I would expect 3. Also, why is the filesystem  'none' for all but the top row?


That is also not a problem. I have the same thing.
```

matthew@matthew-laptop:/proc/acpi/thermal_zone$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             48060296   9799180  35819748  22% /
none                   1407880       384   1407496   1% /dev
none                   1415440     12872   1402568   1% /dev/shm
none                   1415440       204   1415236   1% /var/run
none                   1415440         4   1415436   1% /var/lock
none                   1415440         0   1415440   0% /lib/init/rw
/dev/sda7             57677500  11261584  43486064  21% /home
/dev/sda5             44436512  40238560   1940652  96% /home/matthew/my_storage
/dev/sda16            53992184  11886292  39363200  24% /home/matthew/my_virtual_machines
/dev/sda8             10080488    465956   9102464   5% /home/matthew/my_documents
/dev/sdb1            961432072 429835416 482758656  48% /media/c0827580-aea2-4ca7-a6a9-384443feed39
matthew@matthew-laptop:/proc/acpi/thermal_zone$
```

The file systems marked with none are temporary file systems that reside in memory and have no physical location on any disc.

Kind regards

---

### Post by wminor on 2011-07-10
Ah, ok. Thanks. Glad to hear it's all ok.

For the curious, a bit more info about virtual filesystems can be found [in this thread.]("http://ubuntuforums.org/showthread.php?p=8428924")

---

