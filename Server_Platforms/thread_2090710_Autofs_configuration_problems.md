---
title: "Autofs configuration problems"
date: 2012-12-03
forum: Server Platforms
---

### Post by TUXIFI on 2012-12-03
Hi,

I have some problems to configure autofs just by files configuration (not ldap),
my users are students, professors and administrators, all of them have their home directories in a separate group (e.g: /home/students, /home/professors ect...).
I want to configure autofs5 to make it work but i did'nt find how.

My server is an ubuntu 12.04 LTS server and clients are on 10.04 LTS.

my export is 

/home *(rw,sync,no_subtree_check,insecure)

the mount point on the client is /srv/samba/home/


thanks a lot.

---

