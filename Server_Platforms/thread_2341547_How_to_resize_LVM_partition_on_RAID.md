---
title: "How to resize LVM partition on RAID"
date: 2016-10-29
forum: Server Platforms
---

### Post by Nebucanezee on 2016-10-29
Hi all

This is my setup: Ubuntu server 14.04 configured with RAID 1. One of my LVM partitions (var) is completely filled up. How do I expand this partition?

Best regards

---

### Post by oldfred on 2016-10-29
Moved to Sever sub-forum where those who know servers may be able to help.

I do not know LVM, but have a few now older links. They should still be valid.
       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html
[/URL]
 lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html) 

If not encrypted, just skip those steps:

 How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724) 
      
 [http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume) 
    [URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]
[/URL]

---

### Post by darkod on 2016-10-29
If you have free space in the VG you can easily expand it. It doesn't matter if it's on raid or not.

So, first check the VG details with:
```
sudo vgdisplay
```

If it says you have free extents/space, perfect. You can expand any LV with something like (for example 5GB more):
```
sudo lvextend -L +5G /dev/vg-name/lv-name
```

If you do not have free space in the VG, it's much more complicated because in such case you have to shrink the filesystem on one of the other LVs, then shrink that LV, and then extend the var LV.

---

### Post by Speculos on 2016-10-30
Do not forget to expand your file system after that


```
resize2fs /dev/vg-name/lv-name
```

---

