---
title: "Comparison_of_privilege_authorization_features: su, sudo, gksudo"
date: 2009-09-01
forum: The Cafe
---

### Post by LewRockwell on 2009-09-01
Comparison_of_privilege_authorization_features

[http://en.wikipedia.org/wiki/Sudo](http://en.wikipedia.org/wiki/Sudo)

[http://en.wikipedia.org/wiki/Gksudo](http://en.wikipedia.org/wiki/Gksudo)

[http://en.wikipedia.org/wiki/Su_(Unix)](http://en.wikipedia.org/wiki/Su_(Unix))

[http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](http://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)


one should understand the differences between these...


.

---

### Post by Paddy Landau on 2009-09-01
Thanks for that.

I understand that it is **always** safe to use gksudo, even with a command line, whereas sudo and gksu are not always safe (e.g. if running Firefox as root).

---

### Post by LewRockwell on 2009-09-01
gksudo...super-user-do

current user(whoami) must be on super-user list


gksu...substitute-user(perhaps "super-user" on some systems)

current user is substituted with user specified during "su" call

if no substitute is specificied AND current user is on super-user list then perhaps this successfully changes privileges

still, better to actually call specifically what you intend

hence, the original discussions regarding "sudo" and "gksudo"

.

---

### Post by sisco311 on 2009-09-01
In Ubuntu, gksudo is a symbolic link to gksu:
```
ls -al /usr/bin/gksudo 
lrwxrwxrwx 1 root root 4 2009-07-21 10:36 /usr/bin/gksudo -> gksu

```

The default authentication mode is sudo, but one should be able to change it to su by running gksu-properties.

---

### Post by Paddy Landau on 2009-09-03
> **sisco311 said:**
> In Ubuntu, gksudo is a symbolic link to gksu...
The default authentication mode is sudo, but one should be able to change it to su by running gksu-properties.
Thank you, two new things that I've learned!

---

