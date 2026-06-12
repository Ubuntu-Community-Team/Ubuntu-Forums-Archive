---
title: "cpu soft lock up 61 seconds"
date: 2009-02-01
forum: Server Platforms
---

### Post by Zillion on 2009-02-01
Hi

I installed Ubuntu Server 8.10 on a Intel D945GCLF2 with raid 1 and everything seemed to run fine.

I use Apache, Samba, SSH and Webmin.

Suddenly I often get these strange bugs when for example trying to check some stuff in Webmin or when trying to reboot :

> 
Bug : CPU soft lock CPU#0 stuck for 61 seconds [kacpid69]
Bug : CPU soft lock CPU#2 stuck for 61 seconds [kstop 25457]
Bug : CPU soft lock CPU#3 stuck for 61 seconds [kstop 35458]
Bug : CPU soft lock CPU#1 stuck for 61 seconds [kstop 15456]


And than it just keeps repeating...

Any help would be appreciated

[E D I T] sry saw it here reported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326)

---

### Post by Tuomas Jäntti on 2009-04-14
> **Zillion said:**
> Hi

I installed Ubuntu Server 8.10 on a Intel D945GCLF2 with raid 1 and everything seemed to run fine.

I use Apache, Samba, SSH and Webmin.

Suddenly I often get these strange bugs when for example trying to check some stuff in Webmin or when trying to reboot :



And than it just keeps repeating...

Any help would be appreciated

[E D I T] sry saw it here reported [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254326)

Hi. I wrote also on the above mentioned thread. On my system /usr/sbin/NetworkManager caused the system to freeze after some seconds. After a minute I get the BUG: soft lock etc... . The call itself did not block and my system froze during X startup that was called later in my start up scripts.

---

### Post by nicolasdiogo on 2010-09-11
just adding my voice here - it still a problem in Lynx x64 (10.04)

---

