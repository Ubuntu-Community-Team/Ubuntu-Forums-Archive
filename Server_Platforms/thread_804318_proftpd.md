---
title: "proftpd"
date: 2008-05-23
forum: Server Platforms
---

### Post by f0b1c on 2008-05-23
I have an ubuntu 8.04 server but i just want my proftpd to work perfectly, for one thin i want root users to be able to login. I also want to have FULL rights like write and read from EVERY directory.

Please try and make me a config file for this. I have the default one now












Thanks a bunch.

---

### Post by samosamo on 2008-05-23
welcome to the forums.  everyone here is going to suggest that you do not allow root login to *anything* especially ftpd.  everyone will also suggest that you do not use ftpd to manage your filesystem (ssh is perfect for this, but you may want to try webmin).

now that i said those things, its your system do with as you wish... but i don't think proftpd allows root login, after taking a quick look at the conf.  you may want to look at another ftpd or read the proftpd docs.

---

### Post by f0b1c on 2008-05-23
i want to run sites off the server, i already have webmin installed, but it is NOT ideal for uploading large amounts of stuff.

---

### Post by samosamo on 2008-05-23
ftp is ideal for file transfer, yes.  so umm.. why do you need to do this as root again ?

---

