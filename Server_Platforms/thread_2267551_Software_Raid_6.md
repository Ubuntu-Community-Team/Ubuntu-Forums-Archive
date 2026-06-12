---
title: "Software Raid 6"
date: 2015-03-02
forum: Server Platforms
---

### Post by ShapeShiftme on 2015-03-02
Good day all.

I have a software Raid6 over my hard drives.
1 Drive has failed

I know this is /dev/sde

However i need to boot of a live CD and mount the raid to confirm.

So my question is.
When i boot of a live CD - or if i had to redo the system drive.
How do i add the raid to the system.

Im scared to just try.
as the order of sda , sdb, sdc could of changed as im running of the live cd.

Or do i just add all the drives and mdadm is smart enough to figure the rest of it out itself.
Any help would be greatly appreciated.

regards

---

### Post by darkod on 2015-03-03
Raid6 should keep working with one failed member and the server should be able to boot without the need to boot with the live cd. Unless when creating the raid you selected the option not to boot degraded.

Booting with the live cd will not chage disk label because the cd does not get a label in the /dev/sdX format. So you don't need to worry about that. However after booting in live mode (each time) you will need to install mdadm package and to assemble the array so you can manipulate it. You do that with:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

After you do that please post the output of mdstat so we can see it:
```
cat /proc/mdstat
```

---

### Post by darkod on 2015-03-03
Oh, I forgot to add so you know for the future. By default mdadm assembles the arrays by uuid not by disk label. Unless you change that manually in mdadm.conf. So even if disk labels change mdadm should be able to assemble all your arrays without any problems.

---

