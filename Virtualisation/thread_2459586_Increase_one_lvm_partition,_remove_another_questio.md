---
title: "Increase one lvm partition, remove another question"
date: 2021-03-22
forum: Virtualisation
---

### Post by Heeter on 2021-03-22
Hi all,

I currently have 2 LVMs that I need to resize, other remove.

This is on Ubuntu18LTS,

One LVM has 2 active webservers running, other is empty, both are ext4

```

 --- Logical volume ---
  LV Path                /dev/LVG/vmstorage
  LV Name                vmstorage
  VG Name                LVG
  LV UUID                Tk18eD-kT1s-RJaX-jSZ8-E0Oc-3QRf-ybNVo4
  LV Write Access        read/write
  LV Creation host, time serv, 2019-11-18 20:18:17 -0700
  LV Status              available
  # open                 1
  LV Size                500.00 GiB
  Current LE             128000
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:9
   
  --- Logical volume ---
  LV Path                /dev/LVG/vmbackup
  LV Name                vmbackup
  VG Name                LVG
  LV UUID                6j6gZY-NKNc-BnGd-N1X3-1CTi-Sufg-OOfOhG
  LV Write Access        read/write
  LV Creation host, time serv, 2019-11-22 15:12:50 -0700
  LV Status              available
  # open                 1
  LV Size                500.00 GiB
  Current LE             128000
  Segments               3
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:10

```

I would to remove the "vmbackup" LVM completely, and increase the "VMstorage" by 500GIG to 1000GIG (1Tera)

Here is the fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/LVG-root /               ext4    errors=remount-ro 0       1
/dev/mapper/LVG-bak /bak            ext4    defaults        0       2
# /boot was on /dev/sda1 during installation
UUID=149dbd96-62a6-4481-a1b4-0da7b1bfafbc /boot           ext2    defaults        0       2
/dev/mapper/LVG-home /home           ext4    defaults        0       2
/dev/mapper/LVG-opt /opt            ext4    defaults        0       2
/dev/mapper/LVG-srv /srv            ext4    defaults        0       2
/dev/mapper/LVG-tmp /tmp            ext4    defaults        0       2
/dev/mapper/LVG-usr /usr            ext4    defaults        0       2
/dev/mapper/LVG-var /var            ext4    defaults        0       2
/dev/LVG/vmstorage  /var/vmstorage  ext4    rw,noatime      0       0
/dev/LVG/isostorage /var/isostorage ext4    rw,noatime      0       0 
/dev/LVG/vmbackup   /var/vmbackup   ext4    rw,noatime      0       0
/opt/swapfile20g     none            swap    sw              0       0

```

Never done this before, and google results show several different ways that I don't know which one would be most secure.

---

### Post by TheFu on 2021-03-22
Please post 
```
sudo pvs
sudo vgs
sudo lvs
```
These are easier to read and understand.

To remove an LV, unmount the file system, then **lvremove** is the command. Look up the options.

To extend an LV, there must be space available inside the VG, use **lvextend**.  It looks like all the file systems are ext4, so you can do this on a mounted, used, running, file system.
**sudo lvextend -r -L +{amount to be added} /path/to/lv/device** or something close to that.  Look up the options.  If you forget the **-r**, which is the file system resize, then you'll have to use some other command to resize the ext4 file systems too.  Best not to forget.

I gotta say - why did you setup so many LVs?  It's like you were reading a how-to guide from the 1990s. Back then, splitting storage was very important because we didn't have 1 GB HDDs.  These days, maybe /boot, /var, /, and /home need to be separate - maybe.  Having a backup on the same physical device as the source maybe isn't so good.  Hopefully, you are using LV snapshots to grab completely quiesced backups.

---

### Post by Dennis N on 2021-03-22
Example for remove unwanted logical volume:

```
dmn@Kayleigh:~$ sudo lvremove /dev/common_vg/manjaro_lxqt
Do you really want to remove and DISCARD active logical volume manjaro_lxqt? [y/n]: y
  Logical volume "manjaro_lxqt" successfully removed

Space has been restored to common_vg as free.

```
To extend a logical volume:

First, Check available space in the relevant volume group:
```
sudo vgs
```

Example of extending:

```
sudo lvextend --resizefs --size +5G /dev/files_vg/data1
.
```
will add 5G to the size of the LV, and resize the file system at the same time.

The file system can be in use when you extend it. That's an advantage of LVM.

---

### Post by Heeter on 2021-03-22
Here you go!!

```

root@serv:/home/adminpc# sudo pvs
  PV         VG  Fmt  Attr PSize PFree   
  /dev/sda5  LVG lvm2 a--  1.63t <581.66g
root@serv:/home/adminpc# sudo vgs
  VG  #PV #LV #SN Attr   VSize VFree   
  LVG   1  11   0 wz--n- 1.63t <581.66g
root@serv:/home/adminpc# sudo lvs
  LV         VG  Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  bak        LVG -wi-ao----   7.50g                                                    
  home       LVG -wi-ao----   1.80g                                                    
  isostorage LVG -wi-ao----   5.00g                                                    
  opt        LVG -wi-ao----  52.00g                                                    
  root       LVG -wi-ao----   4.00g                                                    
  srv        LVG -wi-ao----   3.80g                                                    
  tmp        LVG -wi-ao----   3.50g                                                    
  usr        LVG -wi-ao----  10.00g                                                    
  var        LVG -wi-ao----   4.00g                                                    
  vmbackup   LVG -wi-ao---- 500.00g                                                    
  vmstorage  LVG -wi-ao---- 500.00g                                                    
root@serv:/home/adminpc# 

```

Looks lke I still have 581GIG of unused hard disk space. So as well as deleting the vmbackup Can I please add the unused to the vmstorage, Approx 1.5T?

Should I shutdown the 2 webservers while I do this process?

---

### Post by TheFu on 2021-03-22
> **Heeter said:**
>  Should I shutdown the 2 webservers while I do this process?

No need.  Just run the **lvextend** command with the options. Be certain to have it resize the file system too.  Should take less than 5 seconds. Leave the storage to be extended mounted too.  You wondered why we love LVM so much?  This is it. No changes needed to the fstab.

lvreduce, OTOH, needs to be done on storage that is unmounted. It is probably best to make a 100% backup before doing any lvreduce for the file system involved since sometimes it may be confused about where data is actually stored.

But lvextend is 5 seconds, no downtime.

As for the LV you want to delete. **umount** it first, then use lvremove.  You'll probably want to remove it from the fstab.  That's it.

---

### Post by Heeter on 2021-03-22
Thank you guys, and TheFU

I managed to do what I needed without giving myself a heart attack.

LOL

---

### Post by TheFu on 2021-03-23
Heeter, Glad you figured it out.

"Thread Tools" button - Mark SOLVED.  Please. Help the community.

---

