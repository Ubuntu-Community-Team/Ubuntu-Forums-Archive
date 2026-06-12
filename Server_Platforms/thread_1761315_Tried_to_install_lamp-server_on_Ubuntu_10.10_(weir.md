---
title: "Tried to install lamp-server on Ubuntu 10.10 (weird error)"
date: 2011-05-18
forum: Server Platforms
---

### Post by rainleader on 2011-05-18
Ran the following command from a user account listed with ALL permissions in visudo.

```
    sudo tasksel install lamp-server
    debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
    tasksel: aptitude failed (100)
```

Any idea what this is/what caused it?

---

### Post by HugoSerrano on 2011-05-18
> **rainleader said:**
> Ran the following command from a user account listed with ALL permissions in visudo.

```
    sudo tasksel install lamp-server
    debconf: DbDriver "passwords" warning: could not open /var/cache/debconf/passwords.dat: Permission denied
    tasksel: aptitude failed (100)
```Any idea what this is/what caused it?


Don't know the reason, but try:
sudo apt-get install lamp-server^

Regards!

---

### Post by CharlesA on 2011-05-18
> **HugoSerrano said:**
> Don't know the reason, but try:
sudo apt-get install lamp-server^

Regards!

That won't work since lamp-server is a metapackage.

Does /var/cache/debconf/passwords.dat actually exist?

---

