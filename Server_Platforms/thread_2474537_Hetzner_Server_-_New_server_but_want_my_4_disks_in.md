---
title: "Hetzner Server - New server but want my 4 disks in RAID-5. Not sure what to do."
date: 2022-05-02
forum: Server Platforms
---

### Post by zigzagsmoker on 2022-05-02
Hello,

This is a brand new server I ordered from their auction that I just deployed. It doesn't have IPMI or KVM access so I can't set the server up with that, I only have access to reinstall via their templates. It looks like the default storage setup was a weird combination of RAID-1 and RAID-6?

I've only setup RAID once before and it was during a graphical install.

I have 4x 10TB drives and I want to use software RAID-5 as I'm going to use this as an offsite backup server for some important things.

```

root@Ubuntu-2204-jammy-amd64-base ~ # df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           3.2G  1.3M  3.2G   1% /run
/dev/md2        2.0T  2.7G  1.9T   1% /
tmpfs            16G     0   16G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
/dev/md1        989M  247M  692M  27% /boot
/dev/md3         17T   24K   16T   1% /home
tmpfs           3.2G     0  3.2G   0% /run/user/0
root@Ubuntu-2204-jammy-amd64-base ~ # lsblk
NAME    MAJ:MIN RM  SIZE RO TYPE  MOUNTPOINTS
sda       8:0    0  9.1T  0 disk  
&#9500;&#9472;sda1    8:1    0   16G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sda2    8:2    0    1G  0 part  
&#9474; &#9492;&#9472;md1   9:1    0 1022M  0 raid1 /boot
&#9500;&#9472;sda3    8:3    0 1007G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sda4    8:4    0  8.1T  0 part  
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sda5    8:5    0    1M  0 part  
sdb       8:16   0  9.1T  0 disk  
&#9500;&#9472;sdb1    8:17   0   16G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sdb2    8:18   0    1G  0 part  
&#9474; &#9492;&#9472;md1   9:1    0 1022M  0 raid1 /boot
&#9500;&#9472;sdb3    8:19   0 1007G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sdb4    8:20   0  8.1T  0 part  
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sdb5    8:21   0    1M  0 part  
sdc       8:32   0  9.1T  0 disk  
&#9500;&#9472;sdc1    8:33   0   16G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sdc2    8:34   0    1G  0 part  
&#9474; &#9492;&#9472;md1   9:1    0 1022M  0 raid1 /boot
&#9500;&#9472;sdc3    8:35   0 1007G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sdc4    8:36   0  8.1T  0 part  
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sdc5    8:37   0    1M  0 part  
sdd       8:48   0  9.1T  0 disk  
&#9500;&#9472;sdd1    8:49   0   16G  0 part  
&#9474; &#9492;&#9472;md0   9:0    0   16G  0 raid1 [SWAP]
&#9500;&#9472;sdd2    8:50   0    1G  0 part  
&#9474; &#9492;&#9472;md1   9:1    0 1022M  0 raid1 /boot
&#9500;&#9472;sdd3    8:51   0 1007G  0 part  
&#9474; &#9492;&#9472;md2   9:2    0    2T  0 raid6 /
&#9500;&#9472;sdd4    8:52   0  8.1T  0 part  
&#9474; &#9492;&#9472;md3   9:3    0 16.2T  0 raid6 /home
&#9492;&#9472;sdd5    8:53   0    1M  0 part  



```

---

### Post by TheFu on 2022-05-02
A remote server without IPMI/DRAC/RIBLO isn't good. Too easy to be screwed.  You can by a console switch with remote access capabilities for $300 or you can build your own using a Raspberry Pi v4 and $150 in extra hardware.  PiKVM is the search term for that.

The easy answer is to use no RAID for the OS partition (35G), and setup the other partitions to be identical in size and setup RAID5 after the fact. I'd get an SSD installed inside it and use that for the OS and swap needs, then the 10TB drives can all be partitioned identically (always use partitions pre-RAID). You're using partitions - excellent.

Actually, RAID5 on really huge disks is something I avoid for a number of good and bad reasons. You can research that yourself.  For drives over 1TB, I use RAID1 if I must have RAID.  The next time I build a RAID1 setup, it will use LVM+LVM-RAID1, not mdadm.  I've been playing with it a few months and it brings all the enterprise features of LVM, but with RAID and completely removes the extra layer of mdadm.  Simplifying where possible is great.

OTOH, RAID is never a replacement for backups. There are times when RAID fails and the only fix is to wipe the RAID, start over, rebuilt the array and restore all the files from backups.

I know lots of places use RAID5 or RAID6 for their backup storage.  I don't.  My backup storage is all partitioned/sized to be 4TB and I buy storage in sizes that are divisible by 4TB (which turns out to be 3.6TB after formatting).  My backup storage doesn't use any fancy things, since the chances of having 2 HW failures the same week is pretty small in my estimation.  The main storage would need to fail AND the backup storage with the files needed would need to fail before the replacement storage arrives and is rebuilt.  That tiny risk is worth the savings to me.  In a business, I'd have at least 3 copies of everything critical - 2 local and 1 remote (over 500 miles away), with a plan to get the remote storage shipped overnight when needed. What do they say?  *Never underestimate the bandwidth of a station wagon full of tapes?* I believe that.

And there's always ZFS for data too. I don't think it is ready for the OS, but for data, ZFS has been ready over 5 yrs.

A few helpful aliases for looking at storage which provide the extra, helpful data, and strip out stupid non-storage devices:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```

---

### Post by ameinild on 2022-05-03
Look into ZFS, it only has advantages over traditional software raid. Completely wipe the data disks of all partitions, and create a RAID-Z1. ZFS will do the rest for you.

---

