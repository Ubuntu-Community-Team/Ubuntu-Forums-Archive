---
title: "kalarm"
date: 2016-01-06
forum: Ubuntu Development Version
---

### Post by valereguerin on 2016-01-06
hello, good years community !

notification/system-message:

les fuseaux horaire ne sont pas accessibles :
Kalarm utilisera le fuseau horaire UTC

le service de fuseau horaire de KDE n'est pas disponible :
vérifiez que timezoned est installé  (but there isn't ktimezoned in the software center !)


How can i use kalarm with gnome-desktop with the good times zones ???

thanks for regards,):P

---

### Post by QDR06VV9 on 2016-01-06
issue's when trying to run kalarm in gnome. 
The solution for me was to install korganizer, then I executed it, I closed kalarm, I opened it again and voila I had all the time zones.

---

### Post by valereguerin on 2016-01-07
not for me, i install it (korganizer....splash bug...but korganizer works) close kalarm restart it ; close session and open again i have still message/notification ktimezoned is not installed kalarm use UTC, maybe next reboot (apt update/upgrade nothing change the same message)

---

### Post by QDR06VV9 on 2016-01-07
This was a bug left over from wily and seems still in Xenial...
[https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/1512107](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/1512107)
This was the workaround below...
> Installing plasma-workspace fixed the problem. So, plasma-workspace(?) 
So is it worth all that gets pulled-in with it?
Kind Regards

---

### Post by valereguerin on 2016-01-07
you are the king !

thanks:D

---

