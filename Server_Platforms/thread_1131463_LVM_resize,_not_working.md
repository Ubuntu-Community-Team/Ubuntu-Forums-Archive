---
title: "LVM resize, not working"
date: 2009-04-20
forum: Server Platforms
---

### Post by ppl on 2009-04-20
Hi, it is the first time I installed a LVM file system on my home server and spend the whole night last night trying to figure out how to resize a LVM lv. But despite lvdisplay tell me my \var have 30GB space after resize, it is actually still 3GB. I think I might miss something obviously as I am a totally newbie of LVM.

Basically, I want reduce my /home lv. and put some free space into /var. After unmount /home and /var and several reboots. I successfully reduce the size of /home by only reduce the lv size of my /home. and  increase my /var lv size to 30GB. and lvdispaly will show the following output:

> lvm> lvdisplay
  --- Logical volume ---
  LV Name                /dev/debian/root
  VG Name                debian
  LV UUID                vzGOLK-9L3Z-Bz0c-VaPr-AGjR-2mUx-o9Os0m
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                332.00 MB
  Current LE             83
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:0
   
  --- Logical volume ---
  LV Name                /dev/debian/usr
  VG Name                debian
  LV UUID                mgw10k-lm2T-1nlK-q0iu-Pbv2-vkWH-jG1a9z
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                4.66 GB
  Current LE             1192
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1
   
  --- Logical volume ---
  LV Name                /dev/debian/var
  VG Name                debian
  LV UUID                wXx8pU-hPcu-yzgB-1hYY-65ry-SDs7-m1eih3
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                30.00 GB
  Current LE             7680
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:2
   
  --- Logical volume ---
  LV Name                /dev/debian/swap_1
  VG Name                debian
  LV UUID                Y0vIF1-pood-x11O-geks-HnXd-s1Ko-04jUit
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.41 GB
  Current LE             362
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:3
   
  --- Logical volume ---
  LV Name                /dev/debian/tmp
  VG Name                debian
  LV UUID                9LrK46-Vkzh-uG1A-1UN7-QZG3-5LH3-BlXikx
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                380.00 MB
  Current LE             95
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:4
   
  --- Logical volume ---
  LV Name                /dev/debian/home
  VG Name                debian
  LV UUID                Jiie51-nw6f-CIpK-G4iW-RVbq-2osM-g1t8Cv
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                102.06 GB
  Current LE             26128
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:5


But when trying to copy something to my new /var
it filled out after about 3GB, so apparently it is
actually 3GB. What happened?

---

### Post by ppl on 2009-04-21
Hi, I solved my problem, what I need is: ```
resize2fs /dev/mapper/var
``` to expend my physical volume to utilize the full logical volume size. And resize2fs is could do online resize by the way, which is great.

BTW I think those two links: [how-to-resize-or-expand-lvm-partitions]("http://allaboutfedora.blogspot.com/2007/01/how-to-resize-or-expand-lvm-partitions.html") and [tldp.org VM-HOWTO]("http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html")are very useful to help me to figure out LVM, and everything seems quite straight forward now.

---

