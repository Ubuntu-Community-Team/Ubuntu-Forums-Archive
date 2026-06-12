---
title: "Software Raid - 2.7.27 kernels fail to boot off md0"
date: 2009-01-29
forum: Server Platforms
---

### Post by unixfudotnet on 2009-01-29
I upgraded my server from 8.04 to 8.10 and now the 8.10 kernels will not boot my software raid partition.

2.6.24 kernels boot it just fine (what is currently running on it now)
2.6.27 kernels are not able to boot it at all and drop into busybox.

I tried searching forums yet was unable to find an answer to this issue. Do you have suggestions? 

Works: 
```
title           Ubuntu 8.10, kernel 2.6.24-22-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.24-22-generic root=/dev/md0 ro quiet splash 
initrd          /boot/initrd.img-2.6.24-22-generic
quiet
```

Doesn't work:
```
title           Ubuntu 8.10, kernel 2.6.27-11-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.27-11-server root=/dev/md0 ro quiet splash 
initrd          /boot/initrd.img-2.6.27-11-server
quiet
```

---

### Post by fjgaude on 2009-01-29
Tell us, what raid level are you talking about? raid1?

The raid array was built under the 2.6.24 kernel?

Show us, please, what this looks like:

```
sudo mdadm -D /dev/md0
```

---

### Post by unixfudotnet on 2009-01-29
> **fjgaude said:**
> Tell us, what raid level are you talking about? raid1?

The raid array was built under the 2.6.24 kernel?

Show us, please, what this looks like:

```
sudo mdadm -D /dev/md0
```


Raid 1 and yes it was built under the 2.6.24 kernel.

```
root@go:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue Dec 16 11:17:59 2008
     Raid Level : raid1
     Array Size : 17775808 (16.95 GiB 18.20 GB)
  Used Dev Size : 17775808 (16.95 GiB 18.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Jan 29 10:51:12 2009
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : bac896c5:136c5083:402d092a:dc425496
         Events : 0.10

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
root@go:~# 
```

And the SCSI controller and drive, and PCI information.

```

root@go:~# dmesg | grep -i scsi
[   36.709280] SCSI subsystem initialized
[   52.435673] scsi0 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   52.435677]         <Adaptec aic7899 Ultra160 SCSI adapter>
[   52.435679]         aic7899: Ultra160 Wide Channel A, SCSI Id=7, 32/253 SCBs
[   52.649051] scsi 0:0:0:0: Direct-Access     COMPAQ   BF01863644       3B05 PQ: 0 ANSI: 2
[   52.649077] scsi0:A:0:0: Tagged Queuing enabled.  Depth 8
[   52.657337]  target0:0:0: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 63)
[   52.668997] scsi 0:0:1:0: Direct-Access     COMPAQ   BF01863644       3B05 PQ: 0 ANSI: 2
[   52.669018] scsi0:A:1:0: Tagged Queuing enabled.  Depth 8
[   52.677194]  target0:0:1: FAST-80 WIDE SCSI 160.0 MB/s DT (12.5 ns, offset 63)
[   67.649464] scsi1 : Adaptec AIC7XXX EISA/VLB/PCI SCSI HBA DRIVER, Rev 7.0
[   67.649468]         <Adaptec aic7899 Ultra160 SCSI adapter>
[   67.649470]         aic7899: Ultra160 Wide Channel B, SCSI Id=7, 32/253 SCBs
[   67.655941] scsi2 : ata_piix
[   67.656543] scsi3 : ata_piix
[   67.721071] sd 0:0:0:0: [sda] Attached SCSI disk
[   67.739990] sd 0:0:1:0: [sdb] Attached SCSI disk
[   67.759146] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   67.759186] sd 0:0:1:0: Attached scsi generic sg1 type 0
root@go:~# lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
02:05.0 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
02:05.1 SCSI storage controller: Adaptec AIC-7899P U160/m (rev 01)
02:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:07.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
02:08.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
root@go:~# 

```

---

### Post by fjgaude on 2009-01-29
Everything looks good, at least to me. The only thing I can think of is that 8.10 tries to boot from the other drive, not the one that 8.04 boots from.

Maybe if you install **grub** on both drives 8.10 will work. I guess the software that came with the SCSI board setup everything, eh?

Since I don't know anything about Adaptec on Linux I'm not of much help. OTOH, in the busybox try changing the boot drive to (hd1,0) and see what happens.

---

### Post by Cracauer on 2009-01-29
Can you post a screenshot from the dying gasps of the boot?

---

### Post by unixfudotnet on 2009-01-29
It boots off 2.6.24 kernel, so probably not a grub issue unless there is some UID funkiness involved that changed with kernel versions.

The same CONFIG_MD* params are in the kernel config files for both kernels. I'm guessing it may be a MD_AUTODETECT type of issue. Compiling my own kernel manually to see.

Edit: re-read what you posted, yes it may have flopped the drives around and grub may not be on both. I'm not sure yet will try again tomorrow when in the datacenter.

---

### Post by fjgaude on 2009-01-29
Okay, when grub meanu comes up, use the "e" command to change the drive to root (hd1,0). That's the easy way, I think.

BTW, I've gone through many kernel updates, 6.06 through 8.10 , using the same raid5 array.

If fliping the drives doesn't work I have another idea that has worked for many. Let us know what happens.

---

### Post by unixfudotnet on 2009-01-30
> **fjgaude said:**
> Okay, when grub meanu comes up, use the "e" command to change the drive to root (hd1,0). That's the easy way, I think.

BTW, I've gone through many kernel updates, 6.06 through 8.10 , using the same raid5 array.

If fliping the drives doesn't work I have another idea that has worked for many. Let us know what happens.


Tried my own kernel (think I missed something when doing it) and switching hd1 instead of hd0 in grub. Still no change.

Any other suggestions?

---

### Post by Cracauer on 2009-01-30
> **Cracauer said:**
> Can you post a screenshot from the dying gasps of the boot?

bump

---

### Post by unixfudotnet on 2009-01-30
> **Cracauer said:**
> bump

I don't really have a camera to take a screenshot of the server. It just can't find md0 and so drops to initramfs prompt (busybox I think). There isn't much to view. It tries to load the kernel and then it states it can't find md0 and drops to that prompt. 

It is failing to load something in the 2.6.27 kernels that is loaded in the 2.6.24 kernels.

I'm confused as to why this doesn't seem to be a more popular issue, I'm not getting much back from google and on here via search :\

---

### Post by unixfudotnet on 2009-01-30
Found the fix: rootdelay param, added rootdelay=120 and it seems to be long enough to detect md0 and boot off it. 60 was not enough.

---

### Post by fjgaude on 2009-01-30
> **unixfudotnet said:**
> Found the fix: rootdelay param, added rootdelay=120 and it seems to be long enough to detect md0 and boot off it. 60 was not enough.

Wow, we learn something new every day, eh?

---

### Post by Cracauer on 2009-01-30
Ouch.

I had that, too, with Debian some time back. Not with raid but I really wonder what they are doing there that it can't be an event synchronous with the root device appearing. If the root device isn't there, sleep 60 seconds, try again.

---

