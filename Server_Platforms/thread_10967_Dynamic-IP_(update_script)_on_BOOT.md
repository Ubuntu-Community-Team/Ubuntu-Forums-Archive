---
title: "Dynamic-IP (update script) on BOOT"
date: 2005-01-12
forum: Server Platforms
---

### Post by Benn on 2005-01-12
Hi, recently I registered a domain on dyndns.org. I downloaded a bash-script for updating the IP. By executing...

> 
/usr/bin/rundns -c /etc/rundns.config

...my IP is updated succesfully.

But, I need to add that command to be executed everytime the servers boots up.

How can I do this stuff ?

Thank everyone! =D>

---

### Post by az on 2005-01-12
I use ddclient.  It's all automatic.

---

### Post by frijolito on 2005-01-14
[http://www.ubuntulinux.org/wiki/UbuntuBootupHowto](http://www.ubuntulinux.org/wiki/UbuntuBootupHowto)

---

