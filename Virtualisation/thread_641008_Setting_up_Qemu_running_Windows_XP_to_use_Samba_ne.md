---
title: "Setting up Qemu running Windows XP to use Samba network?"
date: 2007-12-14
forum: Virtualisation
---

### Post by Githlar on 2007-12-14
OK, here's my situation. I have a FAT32 partition on my computer which I share on a Windows network using Samba. I installed XP under Qemu. OK, I would like one of two things:

1. Access the entire samba network.that I have set up at home.
2. Access my FAT32 partition through the Qemu Samba interface.

I've tried just mapping /dev/sdb6 (my FAT32 partition) to hdb, but I had no luck with that for some reason.

OK, here's how I have my internet connection, etc, set up:

Network Connection:
Static IP
IP Address: 10.0.2.16
Subnet Mask: 255.0.0.0
Gateway: 10.0.2.2

C:\Windows\System32\drivers\etc\lmhosts:
10.0.2.4 smbserver

/etc/samba/smb.conf:
...
[400Gig]
path = /media/sdb6
available = yes
browsable = yes
public = no
writable = yes
directory mask = 755
create mask = 755
...

But no matter what I try, I can't access qemu Samba or my actual Samba server. Any tips?

---

