---
title: "OpenVPN trouble installing (beginning)"
date: 2008-10-29
forum: Server Platforms
---

### Post by Shwick2 on 2008-10-29
I'm running ubuntu 8.04 and openVPN 2.1_rc7.

I'm stuck on running the vars script in the openVPN setup, [http://openvpn.net/index.php/documentation/howto.html#pki](http://openvpn.net/index.php/documentation/howto.html#pki).

I've run the vars script a number of ways, but it never creates the keys directory.

I've tried,
sudo sh vars
sudo sh ./vars
source vars
source ./vars
sudo /bin/bash ./vars

It seems that the vars script attempts to export environment variables, but when I call env or sudo env I don't see them.

If I try to execute the next install script, sudo sh clean-all, it tells me "Please source the vars script first (i.e. "source ./vars")".

I know it's something simple, but I can't figure it out right now.

---

### Post by pansz on 2008-10-31
you should not use sudo that way, if you want to set env var. because sudo by default uses the enviroment of the "current user" not the "root user"

try:
sudo -i
then you have a root shell which have the environment of root account, then you can do anything you want.

---

### Post by manpaz on 2008-10-31
You must use double "dot" separated by 1 space, try to run these commands:
```

# sudo su
# . ./vars

```
That must be enough.

  Thanks,

---

### Post by Shwick2 on 2008-11-04
Thanks got it working now.

---

