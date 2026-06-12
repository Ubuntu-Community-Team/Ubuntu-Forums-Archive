---
title: "Samba problems with Ubuntu Server 11.10"
date: 2011-12-19
forum: Server Platforms
---

### Post by theatre_ on 2011-12-19
Hi!

Im using Ubuntu Server 11.10 and Samba file sharing.

The problem is when im trying to send files from a computer to my server or vice versa, after just some seconds it stops and says that the connection to the host is broken. 
Directly after that i try to connect to the server and it works... 

Smaller file size works though...

Anyone who knows why?

Best Regards, Jim!

---

### Post by luvshines on 2011-12-20
Try increasing the log level in smb.conf, restart the service then try. Maybe you'll get some useful logs [ /var/log/samba/log.smbd ]

---

