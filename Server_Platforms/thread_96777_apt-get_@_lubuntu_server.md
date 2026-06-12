---
title: "apt-get @ lubuntu server"
date: 2005-11-29
forum: Server Platforms
---

### Post by mirza.k on 2005-11-29
what the most important thing that i must always update ( using apt-get )
kernel ? or what ?
and what is the name of package ?
did i must using apt-get install or apt-get upgrade

---

### Post by matthew on 2005-11-29
If you just want to keep up to date with security releases, then every once in a while do this:
```
sudo apt-get update
```followed by```
sudo apt-get upgrade
```

---

### Post by mirza.k on 2005-11-29
so only use update & upgrade that enough ?
no need know the packaged names to update my ubuntu server ?

---

### Post by matthew on 2005-11-29
[quote=mirza.k]so only use update & upgrade that enough ?
no need know the packaged names to update my ubuntu server ?[/quote]That is correct. You only need to know package names if you are installing something new, not for security updates of already-installed packages.

---

