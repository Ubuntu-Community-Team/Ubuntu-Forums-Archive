---
title: "Securing apache ?"
date: 2008-07-16
forum: Server Platforms
---

### Post by gunfus on 2008-07-16
since noone answered to my post about apache mod_proxy missing in 8.04 I am assuming that people secure their apache with other means... what ways do people out there are using?

---

### Post by cdenley on 2008-07-16
> **gunfus said:**
> since noone answered to my post about apache mod_proxy missing in 8.04 I am assuming that people secure their apache with other means... what ways do people out there are using?

mod_proxy is missing?
```

cdenley@www:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
cdenley@www:~$ dpkg -S mod_proxy.so
apache2.2-common: /usr/lib/apache2/modules/mod_proxy.so

```

---

### Post by windependence on 2008-07-16
> **gunfus said:**
> since noone answered to my post about apache mod_proxy missing in 8.04 I am assuming that people secure their apache with other means... what ways do people out there are using?

Depends on what you mean by "secure". 

For me, I run it on the most secure operating system in the world, OpenBSD, and it's CHROOTed. That's enough. how paranoid do you want to be?

-Tim

---

### Post by gunfus on 2008-07-18
> **cdenley said:**
> mod_proxy is missing?
```

cdenley@www:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
cdenley@www:~$ dpkg -S mod_proxy.so
apache2.2-common: /usr/lib/apache2/modules/mod_proxy.so

```

Good thing you pointed this to me.. I just realized that what I am looking for is mod_security.. Hmm I wonder where I find that.

---

