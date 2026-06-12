---
title: "RAID Options to Lessen Any Performance Hit?"
date: 2020-10-12
forum: Virtualisation
---

### Post by Marc-NJ on 2020-10-12
I'm going to be setting up a Windows 10 Pro or Enterprise OS on an old (but powerful) Dell XPS PC.  I will then be running Ubuntu Server on top of it using VirtualBox.  I need to have redundancy on the Ubuntu Server (not as important for the Win10 host install, although it would be preferable).  The computer will have 3 HD's - 2 x 8 TB and 1 x 10 TB.  My question though is what is the best way to go about getting that redundancy to avoid any performance decrease/loss on the Ubuntu server?  


I think the Dell XPS has fakeRAID (although not certain of this), so I could just use that and let the host OS handle the redundancy (and use the 10 TB drive as a backup/spare).  Alternatively (or if it doesn't have fakeRAID), I could use Windows Storage Spaces (would probably need to use the 10 TB as a boot drive and the 2 x 8 TB for Windows Storage Spaces).  Or I could set up two virtual drives (one on each of the 8 TB drives) and use mdadm to get software RAID directly on the Ubuntu server.  


Any thoughts/suggestions?


Thanks!

---

### Post by TheFu on 2020-10-12
If performance is important, use an NVMe SSD.  Huge HDDs are terrible for performance and with RAID, especially fake-RAID, it will be worse.  SSDs are profoundly faster. Put the guest OSes on SSD and only put data on slow HDDs.

Next, if you want a stable, fast, VM platform, use KVM, not virtualbox. There's lots of good reasons why commercial VM providers use KVM as the hypervisor. A little research will provide those.  Vbox is fine for toy VMs. Not for production.

The hostOS should control the RAID, not the guests.

Probably not what you wanted to hear.

---

