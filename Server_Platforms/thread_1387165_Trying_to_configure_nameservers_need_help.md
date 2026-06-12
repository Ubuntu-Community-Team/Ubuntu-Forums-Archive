---
title: "Trying to configure nameservers need help"
date: 2010-01-21
forum: Server Platforms
---

### Post by wraglin on 2010-01-21
Trying to configure nameservers in Ubuntu

The procedure call for root access to the edit the file resolv.conf

$ sudo vi /etc/resolv.conf

domain

nameserver x.x.x.x
nameserver x.x.x.x


my question is what do I put as my domain name.  I am so confused. 


Will

---

### Post by cariboo on 2010-01-21
FF&H is not the right place for this question, moved to Server Platforms.

---

### Post by shred_eng on 2010-01-21
i think its the ip of your dns servers, i use dyndns so mine are

216.146.35.35
216.146.36.36

---

### Post by cdenley on 2010-01-21
You don't need to specify a domain in resolv.conf. My file looks like:
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```
```

man resolv.conf

```

---

### Post by R.Bucky on 2010-01-21
If you are not operating internal DNS, all you need are nameservers. Your router should take care of the rest.

---

### Post by steven.jones on 2010-01-21
domain is your fully qualified domain.......minus the machine name

so if the server is ubuntu.google.com

the line is,

domain google.com
nameserver1 <IP1>
nameserver2 <IP2>

---

