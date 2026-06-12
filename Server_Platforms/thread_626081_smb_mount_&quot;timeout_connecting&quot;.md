---
title: "smb mount &quot;timeout connecting&quot;"
date: 2007-11-28
forum: Server Platforms
---

### Post by nidelius on 2007-11-28
user@-zepto:~$ sudo mount -t smbfs //server/Down /media/down -o username=xxx,password=xxx
timeout connecting to xxx.xxx.xxx.xxx:445

If I try to access via "Remote Places" samba shares it workes!!!!!!!!!! :S

Any ideas how to get it to mount? or what commands to write to get more info

---

### Post by netlogic on 2007-11-28
try replacing smbfs with cifs
or
user@-zepto:~$ sudo mount.cifs //server/Down /media/down -o username=xxx,password=xxx

also make sure you turn off your firewall on your server or allow 137-139 and 445 in from that ip.

---

