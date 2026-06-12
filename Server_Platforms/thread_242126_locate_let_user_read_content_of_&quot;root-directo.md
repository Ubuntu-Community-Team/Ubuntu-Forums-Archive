---
title: "locate let user read content of &quot;root-directory&quot;"
date: 2006-08-23
forum: Server Platforms
---

### Post by loko on 2006-08-23
EDIT:

Sorry,

this is normal, if the rights of the root-dir are set to 755.

i didn't noticed this.

---

### Post by jordilin on 2006-08-23
when you do
```
sudo updatedb
```
you are creating a database being root. So, the rights have nothing to do with this. Even if the rights were 700, you would be able to see the contents using locate.

---

### Post by loko on 2006-08-23
> **jordilin said:**
> when you do
```
sudo updatedb
```
you are creating a database being root. So, the rights have nothing to do with this. Even if the rights were 700, you would be able to see the contents using locate.

that is not true

i did:
```
sudo updatedb
``` while the root-dir had 755 rights, and it showed the normal user anything with locate.

now, setting the root-dir rights to 700, it shows:

```
locate /root*
```

```
user@w5f-laptop:~$ locate /root/*
/var/lib/nessus/users/root/auth
/var/lib/nessus/users/root/plugins
/var/lib/nessus/users/root/plugins/.desc
/usr/lib/frostwire/root/favicon.ico
/usr/lib/frostwire/root/magnet10
/usr/lib/frostwire/root/magnet10/canHandle.img
/usr/lib/frostwire/root/magnet10/badge.img
/usr/lib/frostwire/root/magnet10/limewire.gif
/usr/lib/frostwire/root/magnet10/options.js
/usr/lib/frostwire/root/magnet10/scripts.js
/usr/lib/frostwire/root/magnet10/silentdetect.js
/usr/lib/frostwire/root/magnet10/style.css
user@w5f-laptop:~$

```

It is showing nothing inside the root-dir anymore

---

