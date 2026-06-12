---
title: "Root password reset"
date: 2011-01-17
forum: Security
---

### Post by vjy587@gmail.com on 2011-01-17
Hi,
I am using ubuntu 8.04 desktop edition
I forgot the root password 
Now i am logging in as a normal user
How to reset my root password again??
Any help would be greatly appreciated...
Thanks

---

### Post by bodhi.zazen on 2011-01-17
The root account is locked in Ubuntu.

See:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sohail_linux on 2011-01-17
yes ,rightly said. u can run all commands requiring root access with sudo , or get root by sudo su , then enter ur normal password. But u must be in sudoers for that.

---

### Post by bodhi.zazen on 2011-01-17
> **sohail_linux said:**
> yes ,rightly said. u can run all commands requiring root access with sudo , or get root by sudo su , then enter ur normal password. But u must be in sudoers for that.

```
sudo -i
```

is the preferred method for a root shell, or for graphical applications, use gksu

---

