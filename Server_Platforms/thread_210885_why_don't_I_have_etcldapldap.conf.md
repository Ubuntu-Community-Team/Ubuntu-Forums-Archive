---
title: "why don't I have /etc/ldap/ldap.conf?"
date: 2006-07-07
forum: Server Platforms
---

### Post by fizgig on 2006-07-07
I'm following the idealx guide and I'm supposed to modify the above file but it doesn't exist.  slapd.conf is there but ldap.conf is not.  Can anyone tell me what package it is in or how I can get it?

---

### Post by nkassi on 2006-07-07
Try downloading libnss-ldap. Also if this dosen't work try to purge the slapd  package and reinstall it (save your slapd.conf if you did anything to it.)

Nic

---

### Post by JackandJohn on 2006-09-17
What helped me on this issue was ```
dpkg-reconfigure slapd
```

Then, if need be (just incase it got moved)

```
sudo updatedb
locate slapd.conf
locate ldap.conf
```

---

