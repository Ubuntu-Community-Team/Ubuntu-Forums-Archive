---
title: "Opening FTP service on public facing website"
date: 2010-11-04
forum: Security
---

### Post by albertwt on 2010-11-04
Hi All,

I'd like to know if this is common security flaw or normal to open up FTP to the public which is of course protected with password for 3rd party access to maintain our public facing / production website ?

If yes, what sort of FTP application to install in Ubuntu ?

Any kind of sharing and suggestion in regards to this thread will be greatly appreciated.

Thanks,

AWT

---

### Post by movieman on 2010-11-04
Ftp is insecure because it sends passwords in the clear, so anyone who can tap your network connection can steal the password. Fortunately that takes more effort than just trying to break in by trying random user names and passwords so it's not likely to happen, but you should be aware of it.

I think Ubuntu has vsftpd, or ideally you'd install ssh and use sftp which provides an encrypted connection and lets you use public keys for authentication as well as passwords.

Personally I'd try to avoid ftp unless you're on a secure network (e.g. external firewall preventing unauthorised users from connecting to the server) or you're providing anonymous access for the entire world.

---

