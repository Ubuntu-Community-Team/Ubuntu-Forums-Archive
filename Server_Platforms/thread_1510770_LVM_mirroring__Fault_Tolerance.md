---
title: "LVM mirroring / Fault Tolerance"
date: 2010-06-16
forum: Server Platforms
---

### Post by metzen_w on 2010-06-16
From what I have found there is nothing written on LVM mirroring on root or "/". I decided to test out LVM on one of my Ubuntu servers with the mirroring option. The reason I chose mirroring is two fold.

1) If I ever wanted to move the data from one drive to a new physical drive I could do this on a live system.

2) If one of my drives failed the end users would not be any wiser to the faulty drive.

Here is my setup

root@ubuntu:/home/jason# fdisk -l

Disk /dev/sda: 26.8 GB, 26843545600 bytes
255 heads, 63 sectors/track, 3263 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e8826

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3122    25077433+  83  Linux
/dev/sda2            3123        3263     1132582+   5  Extended
/dev/sda5            3123        3263     1132551   82  Linux swap / Solaris

Disk /dev/sdb: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
 
root@ubuntu:/home/jason# pvcreate /dev/sdb
  Physical volume "/dev/sdb" successfully created
  
root@ubuntu:/home/jason# pvcreate /dev/sdc
  Physical volume "/dev/sdc" successfully created
  
root@ubuntu:/home/jason# vgcreate test_vg /dev/sdb
  Volume group "test_vg" successfully created
  
root@ubuntu:/home/jason# lvcreate -L 4.9G test_vg --name test_lv
  Rounding up size to full physical extent 4.90 GB
  Logical volume "test_lv" created
  
root@ubuntu:/home/jason# vgextend test_vg /dev/sdc
  Volume group "test_vg" successfully extended
  
root@ubuntu:/home/jason# lvconvert -m 1 test_vg/test_lv /dev/sdc --corelog
  test_vg/test_lv: Converted: 100.0%
  Logical volume test_lv converted.
  
                        
root@ubuntu:/home/jason# lvs -a -o +devices
  LV                 VG      Attr   LSize Origin Snap%  Move Log Copy%  Convert Devices                                
  test_lv            test_vg mwi-a- 4.90G                        100.00         test_lv_mimage_0(0),test_lv_mimage_1(0)
  [test_lv_mimage_0] test_vg iwi-ao 4.90G                                       /dev/sdb(0)                            
  [test_lv_mimage_1] test_vg iwi-ao 4.90G                                       /dev/sdc(0)                            


After making the mirror I put the system through several test such as streaming movies, ftp, scp. All of which were not affected when I pull the main drive in the raid out of the system. I took this to a new level and created a Virtual server with three drives. The first contained boot and drives two and three would be in my mirror for "/". I found that I could remove the primary disk in the LVM mirror with out any ill effects to the server; after setting up the system following similar instructions as found above . 

So with that said here are some questions to the community.

1) Is this a good solution for a production system with LVM mirrored on "/"?

2) If the server has no alternative power supply, for some unknown reason, how secure is my investment solely relying on LVM and the journal file-system?

---

