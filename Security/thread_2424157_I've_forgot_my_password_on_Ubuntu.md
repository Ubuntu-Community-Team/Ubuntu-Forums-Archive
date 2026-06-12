---
title: "I've forgot my password on Ubuntu"
date: 2019-08-04
forum: Security
---

### Post by dunsate on 2019-08-04
I'm locked out of my account in Ubuntu linux. I tried this [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword) But I failed trying to do it. I entered my new password and reentered it multiple times, nothing worked. It kept saying 


passwd : Authentication token manipulation error
passwd : password unchanged.

Somebody help

---

### Post by TheFu on 2019-08-04
If you forgot your password, then there must not be anything important.  Just reinstall.

You could try the boot from install, "Try Ubuntu" and setup a chroot method, if you like.  There are guides for doing it all over the place.  Be certain to use the same version of Ubuntu so all the libraries are the same.  I know this method works, since I had to use it about 5 times in 1 day because I kept making a dumb mistake with my sudoer's file.

I have not attempted either method on any release newer than 16.04.

---

### Post by sisco311 on 2019-08-04
You have to (re)mount the root as rw:
```
mount -o remount,rw /
```

---

