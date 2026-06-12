---
title: "Likewise-open"
date: 2008-12-29
forum: Server Platforms
---

### Post by killerdragon on 2008-12-29
I installed likewise-open from the repositories and started to mess with it. After getting everything up an running (or so it seems with AD authentication) there seems to be some things...missing?

Like in this [thread]("http://www.likewisesoftware.com/community/index.php/forums/viewthread/86/") the user is directed to /etc/likewise/lsassd.conf to change a setting, but the thing is I don't have that file...nor do I even have a likewise directory in my etc directory.

Is Ubuntu hiding the configuration for likewise? Or is that a file that is safe to create?

Btw I followed these directions: [https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

(Sorry if this got posted twice, but the ubuntuforums server bugged out!)

---

### Post by Knobody on 2009-01-02
It appears that you are running the version of Likewise Open provided with the Ubuntu 8.04 release. That is version 4.1.

The comments to which you refer in the other thread have to do with the next version of Likewise, which is 5.0.

You need to look in /etc/samba/lwiauthd.conf for the Likewise settings for version 4.1.

---

