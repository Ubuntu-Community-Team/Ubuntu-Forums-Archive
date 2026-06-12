---
title: "How to FTP to local Ubuntu server"
date: 2009-02-21
forum: Server Platforms
---

### Post by clay7 on 2009-02-21
Hello,
I have a Ubuntu 8.10 desktop that I want to connect to a server running 8.04. The desktop and the server are each connected to a Netgear router. My desktop is 192.168.1.2 and the server is 192.168.1.3. (From my desktop, if I type in 192.168.1.3, I see "It works!")

How can I get files from my desktop onto the server? FTP? I tried but it said "Connection Refused." 

Thank you,
Clay

---

### Post by Perryg on 2009-02-21
> **clay7 said:**
> Hello,
I have a Ubuntu 8.10 desktop that I want to connect to a server running 8.04. The desktop and the server are each connected to a Netgear router. My desktop is 192.168.1.2 and the server is 192.168.1.3. (From my desktop, if I type in 192.168.1.3, I see "It works!")

How can I get files from my desktop onto the server? FTP? I tried but it said "Connection Refused." 

Thank you,
Clay

I don't use straight FTP for obvious reasons but you can go into your U-Server and setup ssh (sftp) to allow you to swap files with the other machine (client)

This link should help
[http://ubuntuforums.org/showthread.php?t=128321]("http://ubuntuforums.org/showthread.php?t=128321")

---

### Post by clay7 on 2009-02-21
Thanks!

---

### Post by spiderbatdad on 2009-02-22
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by Iowan on 2009-02-22
It might be worth mentioning that /var/www (the default location for files) is owned by root.  A few options: Change ownership of the directory, or change DocumentRoot to a more accessible location (or "**sudo**" the files into /var/www).

---

### Post by kustomjs on 2009-02-22
if you looking for a ftp client and if your using firefox use fireftp.

---

