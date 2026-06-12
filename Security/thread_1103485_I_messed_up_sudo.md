---
title: "I messed up sudo"
date: 2009-03-22
forum: Security
---

### Post by beardiggin on 2009-03-22
I was trying to follow these directions, [http://www.itsecurity.com/features/ubuntu-secure-install-resource/](http://www.itsecurity.com/features/ubuntu-secure-install-resource/),  to secure my system and I screwed up sudo.

I thought this:
```
sudo chown root:admin /bin/su sudo
```
was supposed to be one line.

So I did ```
which sudo
``` and found the path to sudo.  Then I ran this command: 
 ```
sudo chown root:admin /bin/su /usr/bin/sudo
```

Now when I try to run sudo or su I get this error message:
sudo: must be setuid root

I switched terminals with <ctrl><alt><f1>.  Logged in as root and set owner of sudo back to root, but I am still unable to use sudo.

What do I need to do to fix this?

ls /usr/bin/sudo
-rwxr-xr-x 2 root root 107936 2009-02-17 12:17 /usr/bin/sudo

---

### Post by beardiggin on 2009-03-22
I figured out how to fix it.  To set user ID the first digit need to be 4.

```
chmod 4751 /usr/bin/sudo
```

---

