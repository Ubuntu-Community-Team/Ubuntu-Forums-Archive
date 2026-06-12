---
title: "hardy/samba"
date: 2008-05-21
forum: Server Platforms
---

### Post by fredknex on 2008-05-21
I'm trying to set my desktop up as a basic media server type thing with samba for the windows compatibility, but when I try to start samba the gui crashes.  I've seen this bug posted but are there any work aroundsor fixes?

thanks for any help possible

---

### Post by untjake on 2008-05-22
I had this problem earlier today. It's looking for

/etc/libuser.conf

which isn't correctly created during the install.

solution is to run the following command:
```
sudo touch /etc/libuser.conf
```

then try opening it again.

---

### Post by fredknex on 2008-05-22
thanks alot untjake that fix worked perfectly

---

