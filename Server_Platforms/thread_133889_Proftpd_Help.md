---
title: "Proftpd Help"
date: 2006-02-20
forum: Server Platforms
---

### Post by soon82 on 2006-02-20
Basically, i had setup ubuntu as my Ftp server... i can login to my server as Anonymous user... I only can read only but cannot write...

I try to add a user as nobody and the password...
But i cant login to ftp server by using the username (nobody) password (nobody)

This is my proftpd.conf... i had edit the user password, but it can't work.. 

User				nobody
Group				nogroup

UserPassword nobody nobody
UseFtpUsers off

---

### Post by lance bermudez on 2006-02-23
go to 
[http://ubuntuforums.org/showthread.php?t=79588&highlight=user+ftp](http://ubuntuforums.org/showthread.php?t=79588&highlight=user+ftp)

---

