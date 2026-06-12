---
title: "Windows 2003 SBS on VM temp files keep growing and Windows system crashes"
date: 2008-05-18
forum: Virtualisation
---

### Post by cgelectek on 2008-05-18
Hello and thank you for trying to help in advance.
this is a temp setup until the new hard ware for this office arrives and I can move the exchange server to its own box and have pdc and bdc for the office. I would like to resolve the problem before moving the VM to another box,I just want a clean move in case there are other issues.
  Hardware pentium 4 - 2.8 1 gig ddr and over 100 gig SCSI drives in raid.  The machine I am using now with the problem is Debian Etch.   I installed vmware on the Debian box, all is working perfect at this point. I install the 2003 sbs server, setup active directory import my data, setup exchange and my domain shares, then connect all clients to the system with a bridged nic and dedicated 512 ram and 70 gigs for the VM hard drive. My issue starts hours later (everything works fine for a long time then I get an error on the debian Monitor: **rtc: lost some interrupts at 2048Hz** this scrolls all down the screen over and over.
  At this point the windows server in the vm hangs I lose connections from all PC and cannot log in via console or remote desktop, until I delete some of the files in the root VM directory. These files are logs and vmem. The error shown on the console is, **[B][B]Temporary files for this virtual machine are stored in directory "/tmp/vmware-root", which is on an almost full file system. Please free some disk space. Would you like to continue? Select retry to continue, Abort to terminate the sesion.**[/B][/B] I cannot do anything but abort it just repeats the error over and over.
 I have 20 plus gigs shown as free space on the windows vm and on the underlying linux distro I have 3 to 5 gigs free space. The system runs fast and has no other problems once I delete a few files from the directory that the VM is in, I can log in via console or RDP, all is good for 7 to 9 hours then it happens again. I dump the logs and the vmem file which is around 512 MB to 1GIG in size. This is crashing the mail server and PDC once a day, It's really a nightmare. Please help, Any ideas on how to stop the logs from filling up or how to let the OS know the drive is not full? 

Any ideas are welcome I have 20 hours into this and have fixed all other issues this one is taking me for a spin. I have the logs for the debien box if that would help I would love to fix this and move on. Thanks:confused:

---

### Post by pietjanjaap on 2008-05-18
In vmware give 2003 less memory or more, less is often better. test it

In options from vmware/3003 , disable acceleration etc, Test it.

In debian disable time stamp, this makes file system quicker. Test again.

Install toolkit vmware?
More ram for pc is also better. 512 is only a little bit of ram.
Does your video driver go fast, is it installed good.


If he thinks he has no room left then i think something is slowing down somewhere, because of that he gets no info, so he thinks it's full, maybe.

You could delete every our the temp map, don't know if this is possible, thus if he deletes to much, in windows he does not.

---

### Post by cgelectek on 2008-05-18
Project update:

 I have turned off the snapshot option in VMware and deleted the snapshots, logs, and the vmem files in the root vm folder. This freed up 1 gig of space. I have come to realize issue here is the 3 gig partition on the linux box is to small for the vm and the vm will need to be resized smaller giving enough room for the debian os to function. I am working on this now any input is greatly appreciated. 
    I was able to login to the remote desktop on the 2003 server once I deleted the files as always the system hanged and I cannot now. I am no longer getting any more files in the root vm folder so I have to clean the debian partition up so there is enough room to run a program to resize the vm partition. The vm runns great with out any issues it is fast and I have no problems other then the crashing caused by the small linux partition that it sits on.

---

