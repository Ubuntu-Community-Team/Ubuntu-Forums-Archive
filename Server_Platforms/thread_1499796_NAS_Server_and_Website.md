---
title: "NAS Server and Website"
date: 2010-06-02
forum: Server Platforms
---

### Post by XMolimoX on 2010-06-02
I've been searching online for a way to introduce a NAS on my Ubuntu Server.

I'm Currently running Ubuntu 9.04 and will be upgrading soon to 10.4 with a fresh install.

I've considered using FreeNAS but I don't want to give up Ubuntu.

I currently run a Website + Forum, FTP Hosting, Teamspeak 2&3.

I've set up the FTP so that friends can use it to backup and share files.
But when you have over 100 small files, FTP takes forever.
I've heard of SAMBA but never used it, would this be able to replace my FTP for my friends? Maybe redirect them to a Secondary HDD? If so, does it work like a NAS, I would just need to Map the Drive?

Thanks in Advance.

Molimo

---

### Post by arrrghhh on 2010-06-02
Well, you can easily build a NAS on Ubuntu... it's literally just network-attached-storage, so as long as people can access the files on your network, then you're good :D

So I'm assuming your friends are not on your LAN, as in they're not in your house?  You want people to connect from the WAN?  It's going to be slow then, no matter what.  Samba, NFS, they're great... but only for a LAN.  I wouldn't open up those protocols to the WAN.  You could use something like SFTP and they could 'mount' the drives with something like SFTP Pro... but that's Windows only and not free.  The only other options you have really is HTTP.  Which is fine, but FTP is preferred if all you're doing is transferring files.

---

### Post by XMolimoX on 2010-06-02
Thanks for replying, My Server is actually not at home, I have it running at the University, and the IT guy is my friend, he gave me a Static IP without Firewall (don't need to redirect ports, all are open)

The connection over there is a T1 Line, so bandwidth isn't really an issue.

So what would be the simplest way (Other than FTP) so set up a NAS on Ubuntu?

Thanks

Marc

---

### Post by arrrghhh on 2010-06-02
For accessing files across the WAN, FTP/SFTP is really the only way to go unless you want to setup something with HTTP...  In reality they're just as fast as Samba or NFS, but across WAN links anything is going to seem slow.

NFS/Samba are not meant to go across WAN links.  I've never tried it before, it just seems like a bad idea and I cannot recommend it.

---

