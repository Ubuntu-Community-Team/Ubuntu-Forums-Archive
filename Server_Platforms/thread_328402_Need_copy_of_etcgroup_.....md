---
title: "Need copy of /etc/group ...."
date: 2006-12-30
forum: Server Platforms
---

### Post by Transition on 2006-12-30
So, somehow all of my users disappeared from my groups in /etc/group.  I'm slowly recovering from this but i'm not sure what users were supposed to be assigned to what groups.  If someone here has a LAMP server w/ Samba i'd appreciate if you can post a copy of your /etc/group file.  

Thanks for the help

---

### Post by Transition on 2007-01-01
Can someone help?

---

### Post by ikonia on 2007-01-02
only you will know your user/group layout.

So you'll have to work out for yourself.

---

### Post by keithweddell on 2007-01-02
Do you still have /etc/group- and/or /etc/gshadow?  You should be able to reconstruct most of the entries from these.  Otherwise you're going to have to crawl through your system to work them out.

Keith

---

### Post by Transition on 2007-01-02
It was a vanilla install (less then a few hours old).  I'm not familiar with what the system defaults for groups might have been.  I'll just try to do a test vanilla install on another machine to get the appropriate groups.

---

### Post by ikonia on 2007-01-02
if its a vanilla install, do a re-install as who knows what else you have removed by accident.

---

