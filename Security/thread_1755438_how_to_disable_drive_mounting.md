---
title: "how to disable drive mounting"
date: 2011-05-11
forum: Security
---

### Post by tjbradford on 2011-05-11
I wish to prevent a user account with sudo rights from mounting attached storage, i managed todo this with ubuntu Version 8 using gnome-polkit i think it was, however i'm not able todo this in 11.04 now , has anyone got a direction i can look in, i googled alot but my searches all come up with auto mounting or how to mount drives

---

### Post by Lars Noodén on 2011-05-12
You'll need to edit **/etc/sudoers** with **visudo** to grant only the access you want to grant.  Leave out the permissions for **mount** and you'll be all set.

Did you meant [gksu-polkit](http://packages.ubuntu.com/natty/gksu-polkit)?

---

