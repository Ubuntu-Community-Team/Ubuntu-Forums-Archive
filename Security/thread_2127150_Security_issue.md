---
title: "Security issue"
date: 2013-03-19
forum: Security
---

### Post by pop.horea on 2013-03-19
Hi,
Today I wanted to change my root password.
The story is as follows:
Terminal with 3 tabs open: one in the root, and two in which I changed the password 2 times other for root tabs open at all times.
I opened Nautilus in root.
If you open a new terminal I do not accept any password. Perhaps I was not too careful as I typed.


I have opened and functional root terminal and nautilus but noted that were opened before password change.
I did order the tab with root: cd / etc passwd and then I changed but not working.


What can I do with what I have to set a password function?
It can?

---

### Post by Stonecold1995 on 2013-03-19
Are you saying you changed your password (is it really root's or your password you use with sudo?), and you can't remember it, but you have a root terminal open from before you changed it?

I'm having a hard time understanding what you're saying, sorry.

---

### Post by tgalati4 on 2013-03-20
I believe *sudo* stays active for 15 minutes.  So your original tab will continue to have root privileges even after you have changed the password--for 15 minutes.  So yes, it is a security risk--for 15 minutes.

---

