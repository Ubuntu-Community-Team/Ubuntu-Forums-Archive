---
title: "Software RAID 1 (mirror)"
date: 2007-11-05
forum: Server Platforms
---

### Post by filips01 on 2007-11-05
Hi all,

I have just installed a 2x 500GB IDE drives in my media server at home running on a software raid 1 (mirror).

I used the mdadm raid management package to get the raid going and all is well. It mounts fine, i was able to simulate a faulty drive and recover with no issue.

The question I have is this. Let&#8217;s pretend for a second that either my motherboard fails or I get a new box and reinstall Ubuntu. How do I go about re- activating the the same raid set up the new system without totally killing the data on the current raid? What files would I need to keep an external copy of?

Thanks for any suggestions. =]

---

### Post by HermanAB on 2007-11-05
Hmm, I do this:
cd /
tar -zcvf etc.tgz etc

then put it on a CD.

---

### Post by Traxman on 2007-11-06
The paritions should be raid partitions and it will store the information
on the drives so even if you move your raid1 to another computer 
it will find them again and make your /dev/md0 again.

Check that its using persistent so the data is saved, else you need 
just to remember what drive names and parition is used and make
a new mdadm.conf for it.

---

### Post by filips01 on 2007-11-06
> **Traxman said:**
> The paritions should be raid partitions and it will store the information
on the drives so even if you move your raid1 to another computer 
it will find them again and make your /dev/md0 again.

Check that its using persistent so the data is saved, else you need 
just to remember what drive names and parition is used and make
a new mdadm.conf for it.

That's the dump that i get from 

```
sudo mdadm --details /dev/md0
```


Version : 00.90.03
  Creation Time : Mon Nov  5 01:19:20 2007
     Raid Level : raid1
     Array Size : 488383936 (465.76 GiB 500.11 GB)
    Device Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : **Superblock is persistent**

    Update Time : Wed Nov  7 08:17:05 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 13ded98c:5fdaf072:f6e22c10:ec1cb8f7
         Events : 0.210

    Number   Major   Minor   RaidDevice State
       0      22        1        0      active sync   /dev/hdc1
       1      22       65        1      active sync   /dev/hdd1


So i'm guessing I'm sweet. =]

Thanks

---

### Post by HermanAB on 2007-11-06
So, you need to keep copies of /etc/fstab and /etc/mdadm.conf for future reference.  I simply save the whole /etc to a CDROM and chuck the CD inside the server box...

---

