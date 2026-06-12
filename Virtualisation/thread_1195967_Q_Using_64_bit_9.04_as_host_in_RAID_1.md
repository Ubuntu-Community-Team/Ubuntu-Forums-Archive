---
title: "Q? Using 64 bit 9.04 as host in RAID 1"
date: 2009-06-24
forum: Virtualisation
---

### Post by wanderingarticfox on 2009-06-24
I'm researching using Ubuntu 9.04 AMD64 as my Host for VBox and doing this in a RAID 1 set-up then using 2 guest of 9.04 (1)32 bit and (1) 6bit. The initial build will only have 4GB of RAM so the 64 bit guest will come after increasing the physical RAM to 8 GB.

Anyone see any problems that I might encounter?

---

### Post by wanderingarticfox on 2009-07-01
6 Days no reply; where's the Ubuntu Love?

---

### Post by Gillo on 2009-07-01
Hi,
I've a quite similar setup working flawlessly: Ubuntu 9.04 64 bits / Virtualbox PUEL 2.2.4 on a RAID1 partition and three guests (one Endian Firewall 2.2 and two Ubuntu 9.04 32 bits).
For information, I only have 2GB of RAM and I've no performance issues. Now, it all depends on what your guests will be doing ...
Regards,

---

### Post by wanderingarticfox on 2009-07-02
Thx a Lot :) I appreciate your response. I understand the RAM issues in respect to what I might have my guest running in the background :)

---

### Post by bhenderson on 2009-07-02
Working on a similar setup here.  The RAID part is dead easy and rock solid (well, relatively so when I look back on all the other issues I have tackled/encountered/run from ;) ) 

System
  Asus P5Q-E MOBO
  Intel Core2 Quad Q6600 @ 2.40GHz
  8G RAM
  Raid 1: 2 x Seagate 500G perp STAT2 drives
  Raid 5: 4 x Seagate 1T STAT2 drives

The bulk of the Jaunty x64 server heirarchy is on the Raid 1.  Each heirarchy is on individual LVMs as a mixture of ext3 and reiser filesystems.

The Raid5 is shared storage for music, video pictures, etc (reiser and xfs) with a little room to spare LOL

The host serves up shared homes and media to windows and linux systems via samba/nfs.

After setting up the RAIDs with mdadm I forgot about them.  No problems what so ever once I got the install completed as I wanted---each heirarchy on individual lvms was a bit tricky to get right until I got the hang of mdadm + lvm.  I mention this because I have 3 systems, 2 different MOBOs that support dmraid.  I spent way too much time trying to get a stable dmraid setup.

Again, the RAID part and base install is rock solid.  I spent a good bit of time looking into various virtualization solutions.  I like VBox for desktop virtualization and in fact I am posting this from my laptop in  Jaunty Desktop running as a VBox VM on Vista x64.  But I elected a different path for the server for a couple of reasons.  First, VBox is great for desktop virtualization but for server virtualization folks that know way more than me recommend KVM, VMware, or xen for server virtualization.  The main reason I went for KVM is that I am looking to pass through usb and pci hardware to one or more VMs.  KVM on ubuntu is closer to allowing me to meet those goals in the near future...I experimented with Proxmox for a while---which I may revisit once their kernel and storage options mature).  VMware, Xen, just weren't paths I wanted to puruse but they serve many well.

Right now I have the following kvm guests running:


1) windows 2k3 32 bit server running as a backup domain controller w DNS/DHCP servers (1 cpu, 512M Ram)



2) Jaunty 64bit CLI server (1 cpu, 512M Ram) which will do a lot of the mondane tasks when complete, mail, wiki, etc 

3) Jaunty 64bit server (4 cpus, 1024M Ram).  This will be the workhorse for media as a MythTV backend.  If possible I'll consolidate other media servers (e.g. mediatomb, fuppes, etc) but I certainly have the capacity to setup additional VMs if I run into conflicts/complications.  I'll allocate more ram as necessary as the real benefit for the 64 bit systems is when you need more than 2G ram.  This one will get the usb/pci tuners passed from the host to recieve/record tv back to the host 

Oh, the VMs reside as individual LVM block devices on the RAID1 (handy for snapshots/backups).

Bottom line on the virtualization choice, look way down stream at your ultimate goals.  If you are looking to simply compartmentalize some various functions/servers or have alternative installations available then VBox may be up to the task.  If you are looking for something more advanced (e.g. hardware pass through) then you may want to look at another option.

So that is probably a lot more than you wanted but hopefully some of it is useful.

Good luck

---

