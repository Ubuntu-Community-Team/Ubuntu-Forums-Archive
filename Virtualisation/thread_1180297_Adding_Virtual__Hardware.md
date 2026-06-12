---
title: "Adding Virtual  Hardware"
date: 2009-06-06
forum: Virtualisation
---

### Post by yazidarezki on 2009-06-06
I am using UBUNTU with KVM, I have a virtual machine (Windows 2008), I want to add virtual hardware so that it recognises the CD/DVD.
 
I choose add Hardware,
 
Hardware = Storage and press Forward
 
I then get:
 
in the source, block device, location I choose browse and select /dev/cdrom
 
In the target device type I choose IDE cdrom and then press forward. 
 
I get, Storage, Disk Image: /dev/cdrom and diak size 851 MB.
 
Finally if I press finish, the allocated space that the VM recognises on the cd/DVD is less than or equal to 851 MB. I would like to allocate more, because if I am installing  from cd/DVD and it has a data that more than 851MB it does not read it.
 
Is there another to allocate storage (i.e cd/dvd) the VM can read?
 
TIA
Yaz

---

### Post by veloce on 2009-06-07
Is there a CD in the drive?  

I don't get any size information except as a description of what is in the drive.  I suspect if you change the disk to a dvd you'd get a different value.

---

