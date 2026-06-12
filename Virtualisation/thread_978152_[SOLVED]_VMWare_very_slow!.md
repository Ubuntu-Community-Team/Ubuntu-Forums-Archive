---
title: "[SOLVED] VMWare very slow!"
date: 2008-11-10
forum: Virtualisation
---

### Post by rlgoddard on 2008-11-10
Hi,

Ubuntu 8.10 is the host OS, and Windows XP is the guest OS.  I tried installing Windows OS as a VM in VMWare Workstation 6.5.  After about three hours and several lockups per minute, I gave up.  Is there anything I can do to greatly speed this up?

Thanks and take care,
Russ

---

### Post by tuxxy on 2008-11-10
Speed it up maybe try [Virtualbox]("https://help.ubuntu.com/community/VirtualBox") :)

---

### Post by darco on 2008-11-10
> **rlgoddard said:**
> Hi,

Ubuntu 8.10 is the host OS, and Windows XP is the guest OS.  I tried installing Windows OS as a VM in VMWare Workstation 6.5.  After about three hours and several lockups per minute, I gave up.  Is there anything I can do to greatly speed this up?

Thanks and take care,
Russ

I have VMware 6.5 and am running XP Pro,WIndows 7 and Vista SP2.
I know that when I tried installing Win 7, I too was having issues AFTER the install.  I had to change the HD to IDE rather than SCSI and after that, its all good.
VMware is awesome. Dont give up

darco

---

### Post by rlgoddard on 2008-11-11
Hi,
 
After a bit of tinkering, I finally managed to get it to install Windows XP. I had to reinstall the virtual machine outside of the NTFS partition I have, thinking that VMWare has the same file size limitations as Virtualbox if I installed the virtual machine in a non-NTFS partition.
 
Instead, I had the virtual machine installed on my /home partition, which is formatted with ext2, and installation proceeded without a hitch! It's faster than Virtualbox, and has the added bonus of being able to run my favorite game, Combat Arms, although it's too slow to be playable.
 
The problem with installing the virtual machine in an NTFS partition was that mount.ntfs-3g was taking up too much CPU power and not leaving enough to VMWare. Moving it to an ext2 partition solved this issue.
 
I hope this will help someone!
 
Take care,
Russ

---

