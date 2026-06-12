---
title: "browsing for localhost"
date: 2010-05-25
forum: Server Platforms
---

### Post by Doulos1 on 2010-05-25
for some reason I can no longer access my server with [http://localhost](http://localhost) .  Browser can't find it.  The default website does come up if I use my lan IP address or my actual IP address.   (NOTE: I don't know if this have anything to do with it, but I have set up namebasedvirtual server which works, with all the domains I have actually gotten to resolve to my IP address.
 
127.0.0.1 localhost is in my /etc/hosts file.
 
 Is this normal?

---

### Post by CPPCrispy on 2010-05-25
127.0.0.1 is the loop back address that is the same as localhost. Did you try to put 127.0.0.1 in the browser? Also is the program/service (apache or something else) you are trying to access started?

EDIT: Punctuation.

---

### Post by clrg on 2010-05-25
Is your web server binding itself to a particular IP address?

---

### Post by cdenley on 2010-05-25
Post this output.
```

sudo netstat -tlnp
getent hosts localhost
cat /etc/hosts
nc -z -v -w 3 127.0.0.1 80

```

---

