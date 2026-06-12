---
title: "aacraid in Ubuntu 8.1"
date: 2008-12-08
forum: Server Platforms
---

### Post by sierraloewe on 2008-12-08
Hello,

I'm having trouble and really need some help with my raid controller-

I've installed 8.1 Intrepid on my IBM x3650 with a ServeRAID 8k-l (Adaptec ATB-205) controller.

When I copy large files over the network to this machine- same result via scp or samba - the disks freeze for 10-15 seconds and i get lots of these errors...

aacraid: Host adapter abort request (0,0,0,0)
aacraid: Host adapter reset request. SCSI hang ?

Does anyone know how to fix this?

The controller firmware is the latest from IBM - 5.2.0-15421
The most current driver from IBM is 1.1.5.2451 but I don't know how to manually install it...
However, dmesg seems to believe a newer driver is being used: Adaptec aacraid driver 1.1-5[2456]-ms

---

### Post by sierraloewe on 2008-12-09
I found this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/249964") which says the queue size needs to be reduced... I guessing this change was already included in 8.1, but how can I check it to be sure?

Is there any way to temporarily adjust the aacraid hardware queue size without building a driver and changing the kernel (cuz I don't know how to..)

---

### Post by Andreas NWC on 2008-12-10
> **sierraloewe said:**
> 
Is there any way to temporarily adjust the aacraid hardware queue size without building a driver and changing the kernel (cuz I don't know how to..)

I am using an Adaptec RAID 5805 with 4 15k6 Barracudas in my workstation with an AMD X4 and ubuntu 8.10.

I am experiencing similar problems. When putting load to the raid array. The systems gets slower and slower until the applications no longer respond and grey out. 

This problem seems to maximize every time the controller flushes the write cache to the drives.

It gets a lot better, once you turn off the write cache of the Raid-Array.

This is not a permanent solution though. But it might help until the problem gets fixed or you can switch to another raid-controller from another maufacturer. 

regards,
Andreas

---

