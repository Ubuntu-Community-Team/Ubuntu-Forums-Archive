---
title: "Sudo vs. root account"
date: 2005-11-20
forum: Server Platforms
---

### Post by RonDeen on 2005-11-20
Hi all, Having read this [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo) and reading the pro's and con's I have a question:
Since all users know their password (duh) It will allow all users to install, compile, change the system preferences etc.
On my usual system (note I do not name them "normal", I do not want to step on toes here) the "root" account prevents "users" from doing stupid things like disabeling the firewall, adding software from unknown sources etc. (think Windows behaviour)

What am I missing here? Is my concern based on something real.
I understand this is fine for a system I use myself, I do not trust "the others"

What are your thoughts on this?

Thanks

Ron

---

### Post by RonDeen on 2005-11-20
Oops:
The first user created is part of the admin group, which can use sudo. Any users created after that are not by default. It is recommended that all users of Ubuntu use sudo, as it provides clear benefits to security.

Sorry, completely read over that..

Cheers

---

### Post by rockrhino27 on 2005-11-20
That is true.  If you ever want to add another user to use sudo privledges.  You need to add them in the /etc/sudoers file.  If you read the file it is pretty self explanatory on how to do it. :cool: 

rich

---

### Post by LordHunter317 on 2005-11-20
No, simply adding them to the admin group by doing:```
sudo adduser user admin
``` would suffice.

---

### Post by RonDeen on 2005-11-21
thanks both,

It was just me reading headlines only.
Feel much better about the sudo approach

Regards

Ron

---

