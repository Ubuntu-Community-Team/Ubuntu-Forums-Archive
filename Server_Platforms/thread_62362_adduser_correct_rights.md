---
title: "adduser correct rights?"
date: 2005-09-04
forum: Server Platforms
---

### Post by [pl]ice on 2005-09-04
hi, 
  i just addred some users via adduser, and what i can see is that everyone got access to everyone's home dir. 
  i thought that wasn't standard ;)  or is it? better watch it...
thanks

---

### Post by adwait on 2005-09-04
I beleive you can read anyony else's directory but can't write to it.

---

### Post by [pl]ice on 2005-09-04
yes, that's true, but still i would consider that not private enough... if i can remember FC1 isn't like that.

---

### Post by LordHunter317 on 2005-09-04
You should be able to edit that in /etc/adduser.conf, or /etc/login.defs.

---

### Post by wmcbrine on 2005-09-09
chmod 700 /home/*

---

