---
title: "ubuntu 9.10 cant define root password"
date: 2009-11-02
forum: Security
---

### Post by dharmagio on 2009-11-02
hi
when i try to define a password for root
i to go user and groups
then i unlock it
and in root properties i define a new password

when i am in terminal 
runing "su"
su: Authentication failure

i never had this problem 
this 9.10 release is starting with too many issues
can any helpme?
thanks

---

### Post by aysiu on 2009-11-02
We don't offer support here for enabling the root account:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

If you believe there is a bug in the actual password-setting interface, file a bug report at [https://bugs.launchpad.net](https://bugs.launchpad.net)

---

### Post by cariboo on 2009-11-02
If you need to run as root for longer that the timeout, I would suggest using:

```
sudo -i
```

This will drop you to a root prompt, and you can do what you need. So far I haven't found anything root can do that sudo -i can't.

---

