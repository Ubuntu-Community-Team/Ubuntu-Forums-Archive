---
title: "md raid set intermittent problem"
date: 2010-07-14
forum: Server Platforms
---

### Post by anothergene on 2010-07-14
I'm having some issues with my md raid set. I'm running 9.10 64bit Server.

It is a 6 disk RAID6 set.  It seems when I reboot the system it doesn't mount all the time.  it's obvious that one device is missing and I'm getting these error message is my /var/log/messages among other files.

```
/var/log/messages:Jul 13 21:54:45 thire kernel: [    4.292537] ata6: SATA link down (SStatus 0 SControl 301)
/var/log/messages:Jul 13 21:59:21 thire kernel: [    4.960223] ata4.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages:Jul 13 22:14:59 thire kernel: [    4.679200] ata4.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages:Jul 14 18:26:34 thire kernel: [    4.949786] ata4.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages:Jul 14 19:11:01 thire kernel: [    4.769633] ata3.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages.1:Jul  6 16:52:26 thire kernel: [    4.917125] ata4.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages.1:Jul  6 16:55:01 thire kernel: [    4.420293] ata6: SATA link down (SStatus 0 SControl 301)
/var/log/messages.1:Jul  6 22:15:46 thire kernel: [    4.716954] ata3.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages.2:Jun 30 20:36:50 thire kernel: [    4.398560] ata6: SATA link down (SStatus 0 SControl 301)
/var/log/messages.2:Jun 30 20:36:50 thire kernel: [    4.877318] ata4.00: SATA link down (SStatus 0 SControl 301)
/var/log/messages.2:Jul  1 09:43:33 thire kernel: [    5.106971] ata3.01: SATA link down (SStatus 0 SControl 301)
/var/log/messages.2:Jul  2 16:36:04 thire kernel: [    4.966861] ata4.01: SATA link down (SStatus 0 SControl 301)
```

Obviously, there is a bad drive, cable or port. from the above is it a different drive every time or is that because they are just getting discovered in a different order?  If I reboot a few times it will eventually find all the disk, assemble and mount the md set and all is fine.  

This is getting annoying if not worrisome.  what do I do next to track down what is causing my problem?

---

### Post by YesWeCan on 2010-07-15
I have a 2 disk RAID1 and had similar problems where reboots caused on of the disks not to be mounted as part of the array.
I made it work by changing the /etc/mdadm/mdadm.conf file to scan based on partition UUIDs rather than partition letters/numbers.

---

### Post by anothergene on 2010-07-15
> **YesWeCan said:**
> I have a 2 disk RAID1 and had similar problems where reboots caused on of the disks not to be mounted as part of the array.
I made it work by changing the /etc/mdadm/mdadm.conf file to scan based on partition UUIDs rather than partition letters/numbers.

It's not scanning that's my problem, the drive is periodically missing on reboots.

---

### Post by YesWeCan on 2010-07-15
Missing? You mean it is not listed when you do 'sudo fdisk -l'?

---

### Post by anothergene on 2010-07-15
> **YesWeCan said:**
> Missing? You mean it is not listed when you do 'sudo fdisk -l'?

Yes missing. Not there. The device is gone.  The device shows up in the bios but I get one of the above errors about the link being down.  

Now is it the same disk and and it's just getting assigned a different ata number or is it something else?  How do I track down what physical disk it is?

---

### Post by YesWeCan on 2010-07-15
Nasty. Could be a bad SATA cable or something. Seen this before.
If you use 'sudo hdparm -I /dev/sd*'
you should get all the drive serial numbers. Then you'll have to take a look at their physical labels and eliminate the good ones, etc.

---

### Post by anothergene on 2010-07-15
> **YesWeCan said:**
> Nasty. Could be a bad SATA cable or something. Seen this before.
If you use 'sudo hdparm -I /dev/sd*'
you should get all the drive serial numbers. Then you'll have to take a look at their physical labels and eliminate the good ones, etc.


Perfect. That's exact what I was looking for. A way to coralate the devices to physical drives.  I'll give it a try.

---

### Post by anothergene on 2010-07-22
Thought I would update this just incase any one is actually following it.  I've been keeping track of the drives that "go missing" on reboot.

It is not the same drive every time, so I would think it's either a driver/firmware or motherboard problem.  I'm pursuing with my mobo manufacturer next.

---

### Post by anothergene on 2010-08-04
another update.  reinstalled server from scratch.  problem seems to be gone, but will continue to monitor the drives in case any one cares.

---

