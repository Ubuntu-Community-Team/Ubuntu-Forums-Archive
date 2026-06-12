---
title: "online drive"
date: 2006-03-30
forum: Server Platforms
---

### Post by RightCoast on 2006-03-30
is there any way to host an online drive via apache? prefferably, if there is a way to host the drive with apache using a registered domain like ____.com?

---

### Post by peanut butter on 2006-03-30
what do u mean by online drive?
if you mean a place where u can download files than yes.

---

### Post by RightCoast on 2006-03-30
yeah, just host a drive that can be accessed from any computer with internet access. i hope to use if for homework and such to access my files  at the library. how would you set up the partition?

---

### Post by peanut butter on 2006-03-31
basically if u used apache u could go to [http://domain.com/~user](http://domain.com/~user) you will have to edit the apache log files. u might also consider using an ftp server i use wu-ftpd because it workedfor me without any configuration. then in most borwasers you can just go to [ftp://user(collon)password@domain.com](ftp://user(collon)password@domain.com) and then type in your user etc than you have access to your home directory..

basically you would edit the dns servers on your domain (on godaddy called full dns control) and  put your ip address as a subdomain.

---

