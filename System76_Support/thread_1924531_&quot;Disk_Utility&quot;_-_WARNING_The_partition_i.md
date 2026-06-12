---
title: "&quot;Disk Utility&quot; - WARNING: The partition is misaligned... System76-style"
date: 2012-02-12
forum: System76 Support
---

### Post by HunkirDowne on 2012-02-12
Just got my new laptop and I have few questions about partitioning.  I have not modified my partitions but get a warning from Disk Utility.  I eventually want to add partitions but this warning is making me a tad bit nervous.

**Disk Utility:** “*Warning: The partition is misaligned by 2048 bytes.  This may result in very poor performance.  Repartitioning is suggested.*”

My laptop is a System76 Gazelle Professional (gazp6) running Ubuntu 11.10 64-bit.  The hard disk is a Seagate Model: ATA ST9750420AS (scsi) and one of the 'Advanced Format' drives (4kB sectors).

Two partitions exist: sda1 and sda2/5, the latter being the extended and logical partition for swap and the former being the system files.

Being that this is the way the laptop shipped, I'm unsure if I have a real problem but would like to know how to proceed to shrink my primary partition, expand my extended partition, and then create more logical partitions for a dedicated /home as well as other partitions for other distros.

Furthermore, the swap partition shows as type 83, not type 82.  Not sure if this makes a difference but I'm not used to seeing it this way.

**fdisk:**
```
Disk /dev/sda: 750.2 GB, 750156374016 bytes 
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors 
Units = sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disk identifier: 0x0009fd8d 

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *        2148  1449562500   724780176+  83  Linux 
Partition 1 does not start on physical sector boundary. 
/dev/sda2      1449562501  1465149167     7793333+   5  Extended 
Partition 2 does not start on physical sector boundary. 
/dev/sda5      1449562502  1465149167     7793333   83  Linux 
Partition 5 does not start on physical sector boundary.
```

So what's the best utility (or utilities) to use and should I align my sectors?

**_My eventual configuration_:**

**/dev/sda1:** ~20 GB for System76 files, including /home (at least user config; may point to separate /home partition for user documents).

**/dev/sda2:** extended

**/dev/sda5:** ~8 GB for swap

**/dev/sda6:** ~500 GB for /home (except System76 user config which will stay on sda1 as noted above).

**/dev/sda7:** ~20 GB for Debian

**/dev/sda8(+):** the balance for other distro(s)

---

### Post by isantop on 2012-02-13
Unless you're noticing performance issues, this will probably not cause any problems. That said, it might not hurt to try and fix it. One thing you can try is re-creating the partition table from disk utility. You can do this by booting from a LiveCD and from disk utility, select the drive and choose "Format Drive" (Not format volume or format partition). Note that this will remove any paritions on the disk, so you should backup all data before you proceed. This will erase all of your data.

If that fails, then the culprit is likely a hardware problem. We would need to bring the machine in to diagnose and repair the problem.

---

### Post by HunkirDowne on 2012-02-13
Thanks **isantop**,

> **isantop said:**
> Unless you're noticing performance issues, this will probably not cause any problems.

The only performance issues I might be having are when resuming from Suspend.  The system is quite sluggish as are the apps but this may be to do at least in part to the size (and type?) of the swap partition, but that is probably best left for another thread if at all.  The only real question I have about my existing swap is that it is formatted type 83 whereas I have typically seen and used type 82 for swap in the past.

> **isantop said:**
>  That said, it might not hurt to try and fix it. One thing you can try is re-creating the partition table from disk utility. 

That is a bit drastic, but I do not rule it out.  I will likely first try to use GParted from LiveCD (like the Add Windows advice, [http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine]("http://knowledge76.com/index.php/Windows_-_Add_MS_Windows_to_Your_System76_Machine")), for reference.

> **isantop said:**
> 
If that fails, then the culprit is likely a hardware problem. We would need to bring the machine in to diagnose and repair the problem.

Even more drastic and I do not rule this out either.  Certainly would be the best timing because of the 172 MiB in my /home directory, only ~4 MiB is stuff I created by my own hand and would want to back up (I could, but typically do not back up config files).

Thanks again for the advice.  I will press on when I have some contiguous time and get to a faster Internet connection.  Good advice: Always backup (and backup your backups if you are truly '*paranoid*' :D).

---

