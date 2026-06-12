---
title: "Eland Pro Pedestal - Raid and Hot Swapping Backup"
date: 2008-04-05
forum: System76 Support
---

### Post by greavette on 2008-04-05
Hello,

I've been looking for a Server that comes pre-installed with Ubuntu on it and came across the System 76 site.  

I'm looking at using this server for a business that will be running 6 virtual machines on 1 PC.  5 of the VM's will be used remotely by PC's at workstations around the office.  The 5 VM's are used to input data into the 6th Virtual Machine's database.  I would like to ensure each of the VM's are backed up in the event a hard drive is lost.  I would also like to ensure that in the event of a power failure the PC will have backup power.

I've heard of Raid before but I don't really know how it works and I'm hoping someone would be kind enough to help me with these questions:

1.  How does the '500 GB: 3ware Hardware RAID 5 – 3 x 250 GB' work?  If a 250 Gig hard drive fails, will anything need to be done or will the computer automatically remove the failed 250 GB hard drive and only use the other two?  
2.  How will I know that one of the hard drives has failed?
3.  Can I buy any replacement hardrive and put it in or would I have to buy the Hot Spare?  
4.  How do I setup the Raid again to acknowledge the new hard drive?
5.  How does the 3ware backup power work?  Will it keep the PC running, or put it in sleep mode.

Thank You,

Charles.

---

### Post by thomasaaron on 2008-04-07
Here is a good overview of RAID technology.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

> 1. How does the '500 GB: 3ware Hardware RAID 5 – 3 x 250 GB' work?

The total storage available in a RAID5 array is n-1, where n is the total number of disks. So for 3x 250GB drives, the total memory is (250GB + 250GB + 250GB) - 250GB.  Thus, you really only have 500GB.

>  If a 250 Gig hard drive fails, will anything need to be done or will the computer automatically remove the failed 250 GB hard drive and only use the other two?

The computer will keep running and will alert you that a disk has failed. You will then have to shut the machine down and replace/rebuild the RAID array unless you have a hotswap set-up. (See below.)

> 2. How will I know that one of the hard drives has failed?

Depending on the 3ware RAID card you are using,  you can configure the card to email, page, or text message you when a HD fails.

> 3. Can I buy any replacement hardrive and put it in or would I have to buy the Hot Spare?

A Hot Spare is a drive that is in the system and is inactive until a drive fails. It is then automatically populated with the data from the good drives. It then takes the faulty drive's place in the RAID array. Hot-swapping allows failed drives to be replaced while the system is running.

Otherwise, you would just shut the machine down, put in an identical drive, rebuild the array via the 3ware bios, and turn the machine back on.

> 4. How do I setup the Raid again to acknowledge the new hard drive?

When you replace the faulty drive, you enter the 3ware card bios, and it gives you an option to re-build the raid array.

> 5. How does the 3ware backup power work? Will it keep the PC running, or put it in sleep mode.

In the event of ac power failure, any data still in cache (not written to the hard drive) is in danger of being lost. The battery backup keeps power going to the RAID card's cache memory to prevent data loss until power is restored. It does not keep the whole server going.

---

### Post by greavette on 2008-04-08
Hello Thomas,

Thank You, this was exactly what I needed to know!

To anyone else reading this thread, I just wanted to mention that I've since contacted System76 with other questions and they have been excellent with their customer service.

Thanks!

---

