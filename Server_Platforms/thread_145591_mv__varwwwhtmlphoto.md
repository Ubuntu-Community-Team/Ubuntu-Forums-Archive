---
title: "mv /* /var/www/html/photo/"
date: 2006-03-16
forum: Server Platforms
---

### Post by yanik on 2006-03-16
Dammit!  Of course nothing works now.  How would I fix that?  can I simply boot the server on a livecd, mount the HD and type 

mv /var/www/html/photo/* /

?

thanks

Yanik

---

### Post by LKRaider on 2006-03-16
Oops! :-P

Yes, I guess that should work too, unless you moved stuff to a Fat32 partiton or somewhere that doesn't keep the permissions...

---

### Post by yanik on 2006-03-17
thanks, it worked.  I had to manually run fsck, fixed a couple a things and now everything is back to normal.

---

### Post by MJN on 2006-03-17
Nowt like learning the hard way why not to run as root! ;)

---

