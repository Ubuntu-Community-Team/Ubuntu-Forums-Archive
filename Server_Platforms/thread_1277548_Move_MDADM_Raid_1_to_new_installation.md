---
title: "Move MDADM Raid 1 to new installation"
date: 2009-09-28
forum: Server Platforms
---

### Post by tomgibson on 2009-09-28
I think this is probably a fairly straightforward problem to solve, however I cannot after several hours of forum scouring find a solution that will work.

Recently I set up a fileserver using Ubuntu 9.04 with a system disk and two additional disks configured as raid 1 using MDADM for redundancy and data integrity. However, I have decided that I want to change to using 8.04 LTS so that I don't have to upgrade my distro so frequently, however having installed 8.04 on another hard drive to test feasability I cannot work out how to get MDADM to recognise my raid array. This must be a simple thing, surely the point of software raid of this type is that it can be controller/system independent? At the moment my inability to access the raid on the alternate installation leaves me wondering what would happen were the system disk in my fileserver to fail, how would I access my data? :confused:

Any suggestions very much appreciated.

Thanks in advance!

---

### Post by fjgaude on 2009-09-28
I think all you need do is make sure you don't have a **/etc/mdadm/mdadm.conf** file on the computer, delete it if you do, then issue this command:

```
sudo mdadm --assemble --scan
```

A new **mdadm.conf** file will be auto created and you are good to go.

---

### Post by tomgibson on 2009-09-28
> **fjgaude said:**
> I think all you need do is make sure you don't have a **/etc/mdadm/mdadm.conf** file on the computer, delete it if you do, then issue this command:

```
sudo mdadm --assemble --scan
```A new **mdadm.conf** file will be auto created and you are good to go.

This is one of the things I tried after having searched around on the internet, but if I do this I simply get an error that no raid volumes can be found, the system I am attempting to load the raid drives into is a fresh install of 8.04 so I don't see any reason why standard procedures wouldn't work. Is there any reason why this might fail to detect the array? Thanks again!

EDIT: The precise error I see is "mdadm: No arrays found in config file or automatically"

---

### Post by fjgaude on 2009-09-28
Sounds like the drives are not connected at all.

What does this show:

```
sudo fdisk-l
```

---

### Post by tomgibson on 2009-09-29
sudo fdisk -l produces this output

```


Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00051c24

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4773    38339091   83  Linux
/dev/sda2            4774        4865      738990    5  Extended
/dev/sda5            4774        4865      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa508c174

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x764f3375

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect


```The first one is the system disk and the latter two the raid mirror. It seems to me unlikely to be a hardware problem since the only hardware change I have made is swap out the original system drive and replace with the one listed above on which I installed 8.04 yet it can't seem to find the raid array :confused:

EDIT: It won't make any difference will it that the data I have stored on the raid array is an LVM group? This raid array is the only storage allocated to that LVM group on my other installation, I'm none too sure how to read from the LVM group in this fresh install once the raid is working anyways but that's a separate issue, the main problem I have right now is that I can't recognize and therefore can't mount the raid.

---

### Post by tomgibson on 2009-09-29
Having since attempted to recreate my issue with a pair of virtual machines, I have verified that the steps suggested above seem to work on the virtual configuration. I assume there must be something odd about my particular configuration so I shall probably reinstall and recreate the arrays from scratch in a few days once I have more storage to back up to. In the meantime if anyone else can suggest what might be causing the problem I am more than willing to attempt anything else. Thanks!

---

### Post by fjgaude on 2009-09-29
Sorry but I have no idea what LVM would have to do with not being able to mount a raid array.

Let us know if you get your setup fixed. Would be interesting to know what the issue is. Thanks!

---

### Post by lcampagn on 2009-10-06
For a completely new system (with no /etc/mdadm/mdadm.conf) and a set of old drives attached, the command 
    ```
mdadm --assemble --scan --auto-update-homehost
``` 
should automatically detect the array, create the new device (probably /dev/md/0), and start the array. This will not create a new mdadm.conf for you, though.

---

### Post by fjgaude on 2009-10-09
It's been my long experience that **--assemble --sca**n will create a new **mdadm.con**f file. Of course you shouldn't have an old file on this new machine.

---

