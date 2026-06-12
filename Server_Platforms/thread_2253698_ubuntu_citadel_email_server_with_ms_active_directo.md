---
title: "ubuntu citadel email server with ms active directory"
date: 2014-11-21
forum: Server Platforms
---

### Post by des4 on 2014-11-21
I could not solve this issue.  I have tried for days.    here is how i  installed below but i get user is not found when i try to login. 
 I tried logging in as 
[email]administrator@medgroup.local[/email]
administrator@medgroup
administrator
but i cant log in.

I can not get all my windows 2003 server users in the register list.  I try to login as administrator and keep saying not found.  

  

 openssh 
lamp 
installed that

  
 CN=queries account,CN=Users,DC=medgroup,DC=local

  
active directory is 192.168.15.10



 
apt-get update

nano /etc/network/interfaces

nano /etc/resolv.conf
dns-nameservers 192.168.15.10


apt-get install libnss-ldap

apt-get install build-essential curl g++ gettext shared-mime-info libssl-dev


apt-get install citadel-suite


please if you know how to figure this out.  please let me know.

---

### Post by bashiergui on 2014-11-22
If no one here knows you can review the documentation & knowledge base on the citadel website. I saw the following instructions for setting up citadel with AD:
[http://www.citadel.org/doku.php/faq:installation:msadsso](http://www.citadel.org/doku.php/faq:installation:msadsso)

---

### Post by nerdtron on 2014-11-22
Not using Citadel but iRedMail, which also have a complete email suite and can integrate to active directory. (although i haven't tried the active directory integration yet).
[http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html](http://iredmail.org/docs/install.iredmail.on.debian.ubuntu.html)
[http://www.iredmail.org/docs/active.directory.html](http://www.iredmail.org/docs/active.directory.html)

---

