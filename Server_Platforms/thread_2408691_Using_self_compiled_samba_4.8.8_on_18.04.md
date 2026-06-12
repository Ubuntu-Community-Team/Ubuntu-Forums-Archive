---
title: "Using self compiled samba 4.8.8 on 18.04"
date: 2018-12-21
forum: Server Platforms
---

### Post by satpal_chander2 on 2018-12-21
Hi All,

I have followed the instructions on this webpage:
[http://wa.rwick.com/2018/04/08/minimal-ubuntu-time-machine-backup-service/](http://wa.rwick.com/2018/04/08/minimal-ubuntu-time-machine-backup-service/)
Basically installing the prerequistes and then grabbing 4.8.8 source and compiling it and install it.

However even after changing the /etc/init.d/smbd & sambaad-dc to point to the newly compiled version in /opt/samba4/ I'm still seeing 4.7.6 via smbstatus as myself.:
```
schander@elephant:/etc/init.d$ sudo smbstatus

Samba version 4.7.6-Ubuntu
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------


Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------


No locked files
```
The strange thing is that if i do sudo -i and then run smbstatus i see 4.8.8
```
root@elephant:~# smbstatus

Samba version 4.8.8
PID     Username     Group        Machine                                   Protocol Version  Encryption           Signing
----------------------------------------------------------------------------------------------------------------------------------------


Service      pid     Machine       Connected at                     Encryption   Signing
---------------------------------------------------------------------------------------------


No locked files
```
If I check the samba from a different machine it still show the old 4.7.6 shares.
I'm totally lost.

---

### Post by volkswagner on 2018-12-22
Was SAMBA package installed prior to compiling?
You should purge SAMBA package, no?

---

