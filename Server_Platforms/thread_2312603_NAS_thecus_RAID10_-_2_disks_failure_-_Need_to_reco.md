---
title: "NAS thecus RAID10 - 2 disks failure - Need to recover data"
date: 2016-02-05
forum: Server Platforms
---

### Post by alain.roger on 2016-02-05
Hello,

i have a NAS Thecus with 4 HDDS in RAID 10.
For some unknown reason, HDD1 failed and i lost my RAID10... just few hours later my HDD4 failed from physical issue.

I cloned my HDD1 and therefore i have HDD 1,2,3 ok however my RAID configuration is lost. Worse, my HDD3 is like having no partition on it :(
i know it is possible from HDD to recover files (for sure not all but at least few of them).

NAS uses ubuntu 12.04 server but i would like to recover files from HDD1,2,3 at least to my desktop external HDD 3TB. For that i can use USB / SATA adapters or directly connecting them to Ubuntu 15.10 desktop computer.

However i was not able to do it.

Can you help me with step by step procedure ?

thanks a lot.

A.

---

### Post by darkod on 2016-02-05
So, HDD4 is completely dead? You will try to recover the data just with HDD1-HDD3?

You will need to connect all HDDs (3 or 4) to your desktop, if you have enough free SATA ports. Then you can use your ubuntu desktop to try and assemble the array. After you get it assembled you can try copying the data.

You can also work with your server as it is (with the disks inside), and boot it with ubuntu desktop live cd (or live usb) into live mode and work from there.

Which way do you prefer?

---

### Post by alain.roger on 2016-02-05
Yes i will use disks 1,2,3 connected to SATA connectors of my desktop computer... I just would like to know if there is a way to know what disk is the RAID1 so i could recovery data/file from it....
i checked the HDD3 and it seems it lost its partition :( so in fact i have really 2 safe disks and HDD3 i need to understand what's going on there.

1. How can i know which disk is RAI1 or RAID0 ?
2. how to mount single RAID1 disk to recover files and directories from it ?
3. if there is no "real" disk holding RAID1 but 2 disks (let's say HDD1 and HDD2) how can i do to recover files from them ? A simple mount is not enough and i'm not so good with mdadm command line :(

thx for help

---

### Post by darkod on 2016-02-05
Best connect all four disks... After that you will do some checks. There is no single disk with raid1. If you had raid1 then you would have the identical data on each disk but with raid10 is not so. Connect all disks and boot your desktop.

After that install mdadm if you already haven't done so, otherwise you can't use the command (it's not part of the desktop version by default).
```
sudo apt-get install mdadm
```

After that show us the output of this command to see which partitions are part of the raid:
```
sudo blkid
```

Lets start with that...

---

