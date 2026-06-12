---
title: "[SOLVED] samba vs ftp server"
date: 2008-12-12
forum: Security
---

### Post by TreeFinger on 2008-12-12
I have a web server on my home network. My firewall does forward connections from the internet to my web server for http requests. Would it be more secure for me to use samba or to use ftp to upload files to the web server?

---

### Post by azzid on 2008-12-12
I'd go with SSH since neither ftp nor smb is encrypted. Never can be to sure when sending stuff over the internet.

---

### Post by TreeFinger on 2008-12-12
> **azzid said:**
> I'd go with SSH since neither ftp nor smb is encrypted. Never can be to sure when sending stuff over the internet.

well, i believe most uploading would be done while on the home network. do i need to be worried about someone sniffing passwords in this scenario?

---

### Post by azzid on 2008-12-12
Nah, thats true. ;)

But you most likely already have ssh running and with filezilla as the client that is just as good as any ftp server, but without all the trouble getting it to work.

I installed proftpd on my machine, discovered that filezilla could handle ssh, uninstalled proftpd.

---

### Post by bodhi.zazen on 2008-12-12
Over a LAN you can either samba or FTP.

Over the internet I second ssh

If you are on windows you can use winscp

---

### Post by HermanAB on 2008-12-12
FTP is less of a hassle to set up than Samba, but I use SSH for everything, even on a LAN.

---

### Post by TreeFinger on 2008-12-12
OK, well I am able to view the samba share from my windows xp partition, so I am guessing it will be the same on my ubuntu partition. I can't write to the folder though. If I am accessing as a guest, what permissions do I set on the folder? What user/group is accessing the folder of the samba share?

---

