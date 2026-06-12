---
title: "Setting up a ftp server"
date: 2008-09-29
forum: Server Platforms
---

### Post by aehirst on 2008-09-29
Hi,
Im trying to setup a public FTP server. I have ordered a cheap little server and an ADSL line with a few static IP addresses.

I was wondering what else I would need? I&#8217;m planning on installing Ubuntu server and running the FTP software on that. The server will be on its own network but other computers will go on it from time to time, do I need some sort of security or is that done by my router/firewall?

Thanks for any advice

---

### Post by devonps on 2008-09-29
I'd assign an internal static ip address to your FTP server and then setup port-forwarding on your router/firewall.

You may want to consider putting your public FTP server in a DMZ and therefore on a different sub-net to your private LAN. This is a good starting point for the securtiy minded.

Hope this helps,

Steve.

---

### Post by lykwydchykyn on 2008-09-29
Is this to be an anonymous server, or will you require accounts?  If you're doing accounts, I'd recommend using an ftp daemon like Pure-ftpd that uses virtual users instead of actual login accounts.

You also want to make sure to activate the chroot features of the FTP daemon -- this makes it impossible (well, harder anyway) for someone to access other parts of the server's filesystem.  

What you lock down depends on exactly what you do or don't want to provide to the public, I guess.  Write access?

---

### Post by inphektion on 2008-09-29
I'd go with vsftpd, chrooted virtual users.  easy to setup and a very secure ftp daemon.

---

