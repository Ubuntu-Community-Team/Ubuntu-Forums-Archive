---
title: "cannot login as superuser in 11.04"
date: 2011-09-24
forum: Ubuntu Studio
---

### Post by dexfos on 2011-09-24
Installed Ubuntu Studio 11.04 several times. Cannot start a login shell from the terminal as superuser, that is, su -l (or su -). Get a "su:Authentication failure" every time I try to login. Any suggestions?

TIA!

---

### Post by jejeman on 2011-09-24
Probably it wants a root password.
If you just need a root shell you can do
```
sudo su
```

---

### Post by snowpine on 2011-09-24
"su" doesn't work in Ubuntu. We use "sudo" instead, as you can read here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

