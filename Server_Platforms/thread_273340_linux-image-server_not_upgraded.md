---
title: "linux-image-server not upgraded"
date: 2006-10-07
forum: Server Platforms
---

### Post by McHenry on 2006-10-07
When I try to upgrade my server I receive the following message:

root@declan:/# apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
The following packages have been kept back:
  linux-image-server
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@declan:/#


Is there a reason why linux-image-server is not upgraded ?


Thanks

---

### Post by rampant on 2006-10-11
'apt-get dist-upgrade'

this will do the kernel as well...

---

### Post by McHenry on 2006-10-12
Is this recommended as I have only just installed 6.06.1 and dont' want to stuff it up... :)

---

### Post by pppetter on 2006-10-12
dist-upgrade is standard procedure. For example: The update manager in ubuntu-desktop uses dist-upgrade, not just upgrade.

---

### Post by PriceChild on 2006-10-12
upgrade will upgrade all your packages unless it requires the instillation of new ones.

dist-upgrade will upgrade EVERYTHING and satisfy everything by installing all dependencies.

dist-upgrade will not update you from 6.06 (Dapper) to 6.10 (Edgy)

---

### Post by McHenry on 2006-10-13
great and thanks...

so disk-upgrade will not move me form a current release in to a beta or similar of an upcoming release ?

I thought that what I had downloaded was the std stable core and only the peripheral packages are upgraded, obviously not...

:)

---

### Post by McHenry on 2006-10-18
Just to check before I issue the command:

If dist-upgrade will not upgrade from dapper to edgy then what is the command that upgrades from dapper to edgy ?

Thanks

---

### Post by travislepp on 2006-11-12
To upgrade to edgy, you first need to modify your sources file.  Until you do this your version of ubuntu will never know that Edgy exists.

Running dist-upgrade will only upgrade your ubuntu to the highest level of the release (dapper in your case).

---

