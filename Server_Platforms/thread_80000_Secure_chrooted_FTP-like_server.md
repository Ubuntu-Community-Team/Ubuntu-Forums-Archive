---
title: "Secure chrooted FTP-like server"
date: 2005-10-21
forum: Server Platforms
---

### Post by Sheep Me on 2005-10-21
I'm looking for an alternative to the FileZilla Server (Windows), that I can use with my Ubuntu desktop.

I've tried vsftpd, but apparently it wasn't compiled with SSL support for the Ubuntu repository. I could compile it myself, but I shouldn't have to.

I've also tried the OpenSSH server and the included SFTP server. I very much liked it, but the problem is that users, logging on to the server, can cd to any directory they want, and hence surf arround freely on my hard drive. So I need to chroot them to their home folder, but OpenSSH doesn't support that. Again I could compile it myself (there are patches out there for chrooting users of the server), but I still don't want to do that.

What I require from the server, is that commands and data are encrypted and that users can be chrooted to something else than my root. That's not unreasonable, is it?

---

### Post by Sheep Me on 2005-10-22
[QUOTE=Sheep Me]I've tried vsftpd, but apparently it wasn't compiled with SSL support for the Ubuntu repository.[/QUOTE]Why doesn't someone tell me that it is, and that I'm just an idiot?

Anyway, I got it started (vsftpd). But I'd like to know how to set a (real, not virtual) user's permissions, so that he can write but not delete.

---

### Post by ubernoob on 2005-10-22
You should try pure-ftp. Thats my favorite. [http://www.pureftpd.org/](http://www.pureftpd.org/)

---

