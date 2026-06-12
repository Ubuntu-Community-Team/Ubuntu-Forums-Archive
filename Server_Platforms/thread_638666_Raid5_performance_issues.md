---
title: "Raid5 performance issues"
date: 2007-12-12
forum: Server Platforms
---

### Post by nullness on 2007-12-12
Hey Guys,

Recently I setup a quad core Intel Q6600 CPU with Ubuntu 7.10 Server and raid5 using mdadm and 4 500gb Samsung HD501LJ Sata II drives and currently 4gb of ram.

The server is being used to host a few virtual machines under VMWare Server 1.04, but here is where the problem lies.  With one virtual machine running Windows XP with 1 GB of RAM I'm getting errors in the VMWare log indicating poor disk performance, for instance:

Dec 11 14:53:42: vmx| SCSI0:0: Command READ(10) took 4.395 seconds (ok)     
Dec 11 14:53:57: vmx| SCSI0:0: Command WRITE(10) took 11.213 seconds (ok)   
Dec 11 14:53:57: vmx| SCSI0:0: Command WRITE(10) took 11.228 seconds (ok)   
Dec 11 14:53:57: vmx| SCSI0:0: Command READ(10) took 11.283 seconds (ok)    
Dec 11 14:53:57: vmx| SCSI0:0: Command WRITE(10) took 11.304 seconds (ok)   
Dec 11 14:54:13: vmx| SCSI0:0: Command READ(10) took 12.155 seconds (ok)    
Dec 11 14:54:13: vmx| SCSI0:0: Command READ(10) took 12.155 seconds (ok)
Dec 11 14:54:13: vmx| SCSI0:0: Command WRITE(10) took 12.327 seconds (ok)   
Dec 11 14:54:19: vcpu-0| SCSI0:0: Command READ(10) took 3.847 seconds (ok)  
Dec 11 15:26:04: vmx| SCSI0:0: Command WRITE(10) took 15.659 seconds (ok)   
Dec 11 15:26:04: vmx| SCSI0:0: Command WRITE(10) took 1.380 seconds (ok)    
Dec 11 15:33:06: vmx| SCSI0:0: Command WRITE(10) took 15.441 seconds (ok)            


This is obviously quite poor, but I have been unable to get to the bottom of it.  hdparm tests show:

/dev/md0:
 Timing cached reads:   7476 MB in  2.00 seconds = 3741.05 MB/sec
 Timing buffered disk reads:  380 MB in  3.00 seconds = 126.64 MB/sec

Anyone have any ideas?

---

### Post by wirelessmonkey on 2007-12-12
I know this may seem linke a longshot, but I've found massive disk I/O errors with VMware, and after finding a post on a gentoo forum, I tried decreasing the VM ram by 64MB, and everything started working properly.  I think this is a vmware bug, and it was reported long ago.

---

### Post by nullness on 2007-12-12
Thanks for the suggestion, but it didn't help.  I'm beginning to wonder if its just IO scheduler problems.  This is a stock Ubuntu 7.1 server kernel so its using deadline for scheduling, I wonder if CFQ would help... BTW vmware is the only app using the RAID5 array and its only using it for VM storage/use.  The OS is on a separate drive (we keep images of the OS drive for backups).  And all these drives were thouroughly tested for faults, including a surface scan before being put into service so hardware error with the drives is unlikely.

---

### Post by rsw686 on 2007-12-12
I think the underlying issues is software RAID 5 is not known for speed as it has to calculate the parity underneath. Would you run your host OS off RAID 5? Probably not, then why would you run the guest OS's off RAID 5? I would be running RAID 10. Yes you loose disk space, but you gain performance.

---

### Post by nullness on 2007-12-12
Well reality is that we need the extra disk space because the side of the virtual HDs can be quite large.  The VM in question is using an 80 GB virtual HD split into 2gb files for efficiency.

There is no reasoning though why consecutive writes should be taking 10 to 12 seconds...to me that is insane, RAID5 or not...afterall we're not talking about writing a lot of data here under the circumstances.

---

### Post by rsw686 on 2007-12-12
Right but 500GB drives are $100. I can't see the logic from a business perspective not to spend $200 more to gain performance and data reliability. Especially on a box running multiple virtual systems.

How many virtual machines are running at once? A bunch of small random writes is the worst thing you can do to a RAID 5 volume. A smaller stripe size may help out, but you would have to recreate the RAID to test this.

---

### Post by rsw686 on 2007-12-12
I just took a look at the log for my fedora vmware guest running on a windows 2003 64 bit host with mirrored drives. Only in two occasions (system has been up for over a year) did I get the warnings and they were in the 2 second range. The last one was when the drives were getting heavily taxed as I was testing out recovery from various mdadm raid scenarios in an ubuntu linux guest.

Dec 11 17:16:05: vmx| SCSI0:0: Command WRITE(10) took 1.600 seconds (ok)
Dec 11 17:16:05: vmx| SCSI0:0: Command WRITE(10) took 1.672 seconds (ok)
Dec 11 17:16:06: vmx| SCSI0:0: Command WRITE(10) took 2.196 seconds (ok)
Dec 11 17:16:06: vmx| SCSI0:0: Command WRITE(10) took 2.196 seconds (ok)
Dec 11 17:16:06: vmx| SCSI0:0: Command WRITE(10) took 2.196 seconds (ok)

I still think the disk access your guest system needs is just too much for the RAID 5 to handle.

I was just thinking about this. Do you use LVM ontop of the RAID? If so you might check out the bottom of [http://www.mythtv.org/wiki/index.php/LVM_on_RAID](http://www.mythtv.org/wiki/index.php/LVM_on_RAID) for details on how to increase the performance.

---

### Post by sciurus on 2007-12-12
Test different kinds of reads and writes to the disk using iozone

---

### Post by nullness on 2007-12-17
I appreciate all the responses.  I'm not averse to redoing the raid as I have backups of all the vms anyways.

What would you guys recommend my choice of raid be (keeping in mind I'm using linux md) for the best balance of performance and stability?

---

