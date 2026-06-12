---
title: "up-to-date"
date: 2005-11-17
forum: Ubuntu Backports
---

### Post by fahad on 2005-11-17
Hi,

iam using ubuntu the Hoary Hedgehog Release.
and my system is up-to-date,
i am updating it every time i got the notifying msg,

Now,
do i have to change the Repositories List from the ones with hoary , for exaple these lines:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

TO: breezy
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

--
i like my system to be the lastest and up-to-date :confused:  ?

---

### Post by adwait on 2005-11-17
If you do that, you will be upgrading to a whole new version of Ubuntu. That would mean downloading about 300-400 MB of data. Yes, that would get you to the latest release of the Ubuntu OS. After you change everything to breezy run
```
sudo apt-get update
sudo apt-get dist-upgrade
```

This will upgrade your system.

---

### Post by fahad on 2005-11-17
thanks adwait,
iam upgrading right now... :D

---

