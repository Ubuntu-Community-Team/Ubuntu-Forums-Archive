---
title: "Adaptec 8k-i lenovo td100 server, RAID"
date: 2014-12-04
forum: Server Platforms
---

### Post by Francisco_Morales on 2014-12-04
Hi.  I am trying to setup a td100 lenovo server with ubuntu 14.04.   The server has a Hot Swap 500GB Sata Hard Disk, controlled by adaptec 8k-i.  The adaptec recognize 465GB from hard disk, as RAID0.   I prepared a array and then start to install ubuntu 14.04.   It seems to work fine, but ubuntu 14.04 try to use to 500GB of the hard disk.   At first time I installed ubuntu on 500GB but, in some moment the server stops because didn't find a memory address. So I start again reducing the hard disk size to 465GB as adaptec uses.   I installed ubuntu and starts to work fine.  Some time after, the same problem.  Doesn't find a memory address.    So I reduced more the hard disk size, using only 400GB.  It starts to working fine.  Some days after, I have to res tart the server and the server doesn't start.  It remains in a grub menu and doesn't start ubuntu.     I have to say that I use /boot, /home, /var and swap partitions.   I don't know if some partitions is the reason to have a problem.  I don't know what to do.  Could you help me. Please.

---

### Post by nerdtron on 2014-12-04
I don't think this is a problem in Ubuntu. Are you sure that the RAID is properly configured on the configuration utility? Also if this is just a single disk why use RAID? Can't it be just a plain pass-through so that the OS will write directly to the disk?

---

### Post by Francisco_Morales on 2014-12-05
Thanks a lot.  The RAID is properly configured.  We use it with RAID just with a single disk because the server came in that condition. So I agree with you. I will put the disk directly to a SATA port to use without RAID card and allow Ubuntu Server to write on disk directly.  I will do it.  Thanks

---

