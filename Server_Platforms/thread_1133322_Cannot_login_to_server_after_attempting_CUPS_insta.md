---
title: "Cannot login to server after attempting CUPS install"
date: 2009-04-22
forum: Server Platforms
---

### Post by Jcarr_toonist on 2009-04-22
Having a bit of problem with my headless Ubuntu Intrepid server.

Whenever I attempt to login via SSH I get the following error message 

> Connection Closed by 192.168.1.130

When I try to login via tty1 I similarly cannot login. My screen simply outputs... > Ubuntu 8.10 tty1 and then it brings me back to the login. This happen on both accounts I have active on the server (one admin, one non-admin). 

This problem started while I was trying to get my printer to share using the CUPS web interface. Similarly, I can no longer access the CUPS interface along with everything else. Although I can still access my samba shares.

Any suggestions??? I am still quite new at the server side of linux and have no idea what to do next. Any help would be greatly appreciated.

---

### Post by roberto.ea on 2009-04-23
I had the very same problem last night, and I finally managed to login after removing libpam-smbpass and samba's secrets.tdb.

steps:

reboot and enter recovery mode, drop into root shell
dpkg --purge libpam-smbpass

restart, and hopefully you can now login to your server...

delete the samba's secrets.tdb

sudo rm /var/lib/samba/secrets.tdb
(or you can simply rename it to something different)

then you can reinstall libpam-smbpass. :)

sudo apt-get install libpam-smbpass

Hope this will help... :P

---

### Post by Jcarr_toonist on 2009-04-24
Worked like a charm, thanks

---

### Post by haydenSUDOuser on 2009-08-19
YES thank you, this solved a problem i ran into from a mistake i made from this tutorial on making a media server

[http://ubuntuforums.org/showthread.php?t=1232464&highlight=%2Fetc%2Fmysql%2Fmy.cnf](http://ubuntuforums.org/showthread.php?t=1232464&highlight=%2Fetc%2Fmysql%2Fmy.cnf)

---

