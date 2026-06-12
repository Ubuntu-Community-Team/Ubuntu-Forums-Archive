---
title: "cvs authentication using Active Directory"
date: 2014-03-27
forum: Security
---

### Post by luca9 on 2014-03-27
hi all

I can't authenticate cvs using Acrive Directory


 ubuntu 13.04 config to authenticate usign AD seems correct
- on Ubuntu I can do ldapsearch to AD
- on Ubuntu I can login with uan AD user
- on Ubuntu I can change pass of an AD user

when I try to connect to cvs with command
cvs -d server:mariorossi@10.63.20.30:/cvsdata/repo1 login 
I get this errore
cvs [login aborted]: authorization failed: server 10.63.20.30 rejected access to /cvsdata/repo1 for user mariorossi


it seems is missing the config in /etc/pam.d/cvspserver
I tried to write donw config manually but still not working
I foud /etc/pam.d/cvspserver in an old distro LUCID now there is not

can anyone help me ?

thanx
ciao
Luca

---

### Post by mörgæs on 2014-03-28
Hi, welcome to the fora.

Both 13.04 and 10.04 (Lucid) are out of support. Before going further I suggest that you install 13.10.

---

### Post by luca9 on 2014-04-08
I installed Ubuntu 13.10 but I got the same error

any suggestion ??

thank
Luca

---

### Post by mörgæs on 2014-04-08
Now we at least know that the version is not the culprit. 
Moving to Security to see if anyone there is able to assist.

---

