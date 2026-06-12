---
title: "hard disk label keep changing"
date: 2011-10-11
forum: Server Platforms
---

### Post by Eberx on 2011-10-11
Hello,


I have sda and sdb physical disk on my ubuntu 8.04.3 (Linux www 2.6.24-29-server #1 SMP Wed Aug 10 15:58:57 UTC 2011 x86_64 GNU/Linux). I have installed 2xSAS for OS and 2 SATA for file sharing on my server. These 2 SAS hard drives are connected to RAID controller PIKE1064E and 2 SATA hard drives are connected to rest of SAS/SATA connector.

Every day a SATA hard disk label has changed that currently used for file sharing. when hard drive label changed then mount is going to wrong and can't upload/download.

Oct 7 16:19:00 www kernel: [715906.738915] mptscsih: ioc0: attempting target reset! (sc=ffff8102b8934c40)
Oct 7 16:19:00 www kernel: [715906.738919] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 9b 17 5c 76 00 02 00 00
Oct 7 16:19:00 www kernel: [715907.252987] mptscsih: ioc0: target reset: SUCCESS (sc=ffff8102b8934c40)
Oct 7 16:19:00 www kernel: [715908.478737] lost page write due to I/O error on sda5
Oct 7 16:19:00 www kernel: [715908.478744] lost page write due to I/O error on sda5
Oct 7 16:19:00 www kernel: [715908.478749] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478753] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478758] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478764] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478769] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478774] lost page write due to I/O error on sda5
Oct 7 16:19:02 www kernel: [715908.478779] lost page write due to I/O error on sda5
Oct 7 16:19:02 www kernel: [715908.478785] lost page write due to I/O error on sda5
Oct 7 16:19:03 www kernel: [715910.344734] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Oct 7 16:19:29 www kernel: [715940.288492] mptscsih: ioc0: attempting task abort! (sc=ffff81026b8b81c0)
Oct 7 16:19:29 www kernel: [715940.288500] sd 0:0:0:0: CDB: Synchronize Cache(10): 35 00 00 00 00 00 00 00 00 00
Oct 7 16:19:33 www kernel: [715944.652908] mptbase: ioc0: LogInfo(0x31140000): Originator={PL}, Code={IO Executed}, SubCode(0x0000)
Oct 7 16:19:49 www kernel: [715944.709944] mptscsih: ioc0: task abort: SUCCESS (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715954.690627] mptscsih: ioc0: attempting task abort! (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715954.690634] sd 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct 7 16:19:49 www kernel: [715957.627896] mptbase: ioc0: LogInfo(0x31130000): Originator={PL}, Code={IO Not Yet Executed}, SubCode(0x0000)
Oct 7 16:19:49 www kernel: [715957.802114] mptscsih: ioc0: task abort: SUCCESS (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715957.802128] mptscsih: ioc0: attempting target reset! (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715957.802131] sd 0:0:0:0: CDB: Synchronize Cache(10): 35 00 00 00 00 00 00 00 00 00
Oct 7 16:19:49 www kernel: [715958.321106] mptscsih: ioc0: target reset: SUCCESS (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715959.642560] mptsas: ioc0: attaching sata device, channel 0, id 0, phy 0
Oct 7 16:19:49 www kernel: [715959.645492] scsi 0:0:3:0: Direct-Access ATA ST32000542AS CC34 PQ: 0 ANSI: 5
Oct 7 16:19:49 www kernel: [715959.646039] sd 0:0:3:0: [sdd] 3907029168 512-byte hardware sectors (2000399 MB)
Oct 7 16:19:49 www kernel: [715959.712116] sd 0:0:3:0: [sdd] Write Protect is off
Oct 7 16:19:49 www kernel: [715959.714698] sd 0:0:3:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 7 16:19:49 www kernel: [715959.715077] sd 0:0:3:0: [sdd] 3907029168 512-byte hardware sectors (2000399 MB)
Oct 7 16:19:49 www kernel: [715959.783179] sd 0:0:3:0: [sdd] Write Protect is off
Oct 7 16:19:49 www kernel: [715959.798095] sd 0:0:3:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 7 16:19:49 www kernel: [715959.798103] sdd: sdd1 < sdd5 >
Oct 7 16:19:49 www kernel: [715959.838438] sd 0:0:3:0: [sdd] Attached SCSI disk
Oct 7 16:19:49 www kernel: [715959.838479] sd 0:0:3:0: Attached scsi generic sg0 type 0

I did not unplug and plug hard drive. It is changing automatically. I don't know what is the reason. How do I fix this issue?

---

### Post by bab1 on 2011-10-11
> **Eberx said:**
> Hello,


I have sda and sdb physical disk on my ubuntu 8.04.3 (Linux www 2.6.24-29-server #1 SMP Wed Aug 10 15:58:57 UTC 2011 x86_64 GNU/Linux). I have installed 2xSAS for OS and 2 SATA for file sharing on my server. These 2 SAS hard drives are connected to RAID controller PIKE1064E and 2 SATA hard drives are connected to rest of SAS/SATA connector.

Every day a SATA hard disk label has changed that currently used for file sharing. when hard drive label changed then mount is going to wrong and can't upload/download.

Oct 7 16:19:00 www kernel: [715906.738915] mptscsih: ioc0: attempting target reset! (sc=ffff8102b8934c40)
Oct 7 16:19:00 www kernel: [715906.738919] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 9b 17 5c 76 00 02 00 00
Oct 7 16:19:00 www kernel: [715907.252987] mptscsih: ioc0: target reset: SUCCESS (sc=ffff8102b8934c40)
Oct 7 16:19:00 www kernel: [715908.478737] lost page write due to I/O error on sda5
Oct 7 16:19:00 www kernel: [715908.478744] lost page write due to I/O error on sda5
Oct 7 16:19:00 www kernel: [715908.478749] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478753] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478758] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478764] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478769] lost page write due to I/O error on sda5
Oct 7 16:19:01 www kernel: [715908.478774] lost page write due to I/O error on sda5
Oct 7 16:19:02 www kernel: [715908.478779] lost page write due to I/O error on sda5
Oct 7 16:19:02 www kernel: [715908.478785] lost page write due to I/O error on sda5
Oct 7 16:19:03 www kernel: [715910.344734] sd 0:0:0:0: [sda] Synchronizing SCSI cache
Oct 7 16:19:29 www kernel: [715940.288492] mptscsih: ioc0: attempting task abort! (sc=ffff81026b8b81c0)
Oct 7 16:19:29 www kernel: [715940.288500] sd 0:0:0:0: CDB: Synchronize Cache(10): 35 00 00 00 00 00 00 00 00 00
Oct 7 16:19:33 www kernel: [715944.652908] mptbase: ioc0: LogInfo(0x31140000): Originator={PL}, Code={IO Executed}, SubCode(0x0000)
Oct 7 16:19:49 www kernel: [715944.709944] mptscsih: ioc0: task abort: SUCCESS (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715954.690627] mptscsih: ioc0: attempting task abort! (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715954.690634] sd 0:0:0:0: CDB: Test Unit Ready: 00 00 00 00 00 00
Oct 7 16:19:49 www kernel: [715957.627896] mptbase: ioc0: LogInfo(0x31130000): Originator={PL}, Code={IO Not Yet Executed}, SubCode(0x0000)
Oct 7 16:19:49 www kernel: [715957.802114] mptscsih: ioc0: task abort: SUCCESS (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715957.802128] mptscsih: ioc0: attempting target reset! (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715957.802131] sd 0:0:0:0: CDB: Synchronize Cache(10): 35 00 00 00 00 00 00 00 00 00
Oct 7 16:19:49 www kernel: [715958.321106] mptscsih: ioc0: target reset: SUCCESS (sc=ffff81026b8b81c0)
Oct 7 16:19:49 www kernel: [715959.642560] mptsas: ioc0: attaching sata device, channel 0, id 0, phy 0
Oct 7 16:19:49 www kernel: [715959.645492] scsi 0:0:3:0: Direct-Access ATA ST32000542AS CC34 PQ: 0 ANSI: 5
Oct 7 16:19:49 www kernel: [715959.646039] sd 0:0:3:0: [sdd] 3907029168 512-byte hardware sectors (2000399 MB)
Oct 7 16:19:49 www kernel: [715959.712116] sd 0:0:3:0: [sdd] Write Protect is off
Oct 7 16:19:49 www kernel: [715959.714698] sd 0:0:3:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 7 16:19:49 www kernel: [715959.715077] sd 0:0:3:0: [sdd] 3907029168 512-byte hardware sectors (2000399 MB)
Oct 7 16:19:49 www kernel: [715959.783179] sd 0:0:3:0: [sdd] Write Protect is off
Oct 7 16:19:49 www kernel: [715959.798095] sd 0:0:3:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Oct 7 16:19:49 www kernel: [715959.798103] sdd: sdd1 < sdd5 >
Oct 7 16:19:49 www kernel: [715959.838438] sd 0:0:3:0: [sdd] Attached SCSI disk
Oct 7 16:19:49 www kernel: [715959.838479] sd 0:0:3:0: Attached scsi generic sg0 type 0

I did not unplug and plug hard drive. It is changing automatically. I don't know what is the reason. How do I fix this issue?

You should use the UUID to ID the drives (or partitions) not the /dev/sd*x* designation.  See this /etc/fstab file.  Not the comment at the top (in red)```
# /etc/fstab: static file system information.
[B][COLOR="Red"]#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).[/COLOR][/B]
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
[COLOR="Red"]UUID=fb80eecb-e0cf-49a2-9936-6e219d09a7e1[/COLOR] /               ext3    errors=remount
-ro 0       1
# /home was on /dev/sda3 during installation
[COLOR="Red"]UUID=46a258bf-6ace-4d52-b4d7-db47e7b3de7b[/COLOR] /home           ext4    defaults      
  0       2
# swap was on /dev/sda2 during installation
UUID=69e4c9c7-a439-416d-85a9-c79162983068 none            swap    sw            
  0       0

```

To reveal the UUID's you can use ```
sudo blkid 
```

This is what I get ```
sudo blkid 
/dev/sda1: UUID="fb80eecb-e0cf-49a2-9936-6e219d09a7e1" TYPE="ext3" 
/dev/sda2: UUID="69e4c9c7-a439-416d-85a9-c79162983068" TYPE="swap" 
/dev/sda3: UUID="46a258bf-6ace-4d52-b4d7-db47e7b3de7b" TYPE="ext4"
```

Edit: As you are using a RAID setup you will need to use the UUID of the block device that you write to, not the drives that make up the RAID.

---

