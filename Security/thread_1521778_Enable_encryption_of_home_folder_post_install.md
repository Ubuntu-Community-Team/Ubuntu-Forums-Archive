---
title: "Enable encryption of home folder post install"
date: 2010-07-01
forum: Security
---

### Post by jhaquo on 2010-07-01
Hi
I was wondering how to activate encryption on my home folder, like sugested when creating the first user? in 10.04

Also, is it any good to use?
It's a work computer with sometimes private documents (cv, docs, etc) and i would like to be sure no one can access it, even as root.

Kind regards,
Jhaquo

---

### Post by FuturePilot on 2010-07-01
Follow this. [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html]("http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html")

To encrypt the swap partition too, then run
```
ecryptfs-setup-swap
```
Note: currently, encrypting the swap partition will break hibernate.

---

### Post by Snabbdist on 2011-07-24
there is also ```
ecryptfs-migrate-home
```
nowadays

---

### Post by bodhi.zazen on 2011-07-24
Or , rathere then migrating home, simply use a graphical tool such as cryptkeeper to make a crypt.

cryptkeeper is in the repositories.

---

