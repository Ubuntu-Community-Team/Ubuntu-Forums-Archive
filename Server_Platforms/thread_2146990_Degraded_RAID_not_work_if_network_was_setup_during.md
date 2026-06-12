---
title: "Degraded RAID not work if network was setup during installation"
date: 2013-05-20
forum: Server Platforms
---

### Post by lv99782 on 2013-05-20
Hi,

This could be a bug in Ubuntu 12.04.02 Server Installation (ubuntu-12.04.2-server-amd64.iso) and same thing happen on Desktop version (ubuntu-12.04.2-alternate-amd64+mac.iso) as well.

I found that if I setup networking and RAID 1 during installation, after installation complete, if I remove 1 disk to make the raid degrade to run on single disk, one of the disk can still boot (usually sda work) but the other won't. The GRUB menu will still show, but after that it goes blank and reboot itself.

I've tried all kind of combination during installation to find out why (because somehow my colleague was able to install one without any problem), eventually found that network setup causing this. The worst thing is that, no matter how I tried to rescue the other disk, it just won't boot, unless I use dd copy the /boot partition from the other bootable disk.

This is how I setup the system, you can follow the same and see whether you got the same problem or not. You can test this on VM. Most of the things I used are default setting unless otherwise state below:
1) Language Setup - English, UK
2) Configure network manually (press cancel when it try to get IP from DHCP), make sure it can connect to Internet
3) Manual setup partition for a 20GB disk. 200MB for /boot (raid1, ext4), 1GB for swap (raid1), give the rest of space to / (raid1. ext4)
4) Boot when RAID become degraded ? Yes
5) Install GRUB to MBR ? Yes
6) After installation finished, reboot then login to the system and check make sure the RAID are fully sync.
7) Shutdown the system, remove 1 disk and start it. If it can boot, then shut it down and test the other disk. Usually the first disk work, second won't.


I also tested on 13.04 version, look like this problem has been fixed in this version.


Regards
Louis

---

