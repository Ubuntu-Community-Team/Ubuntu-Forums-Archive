---
title: "how to set up internet ubuntu server"
date: 2010-09-04
forum: Server Platforms
---

### Post by c2tarun on 2010-09-04
hello
i installed ubuntu server on my college system and by its by default settings there is not desktop provided to us from server.
we have to install desktop.
for that we are trying to use "sudo apt-get install ubuntu-desktop".
but internet is not working. can anyone please guide us to internet settings setup.
 
our proxy address is 10.11.12.1
 
how to assign this proxy in internet settings.
 
XP is also in this system where net is working fine.
 
thank you

---

### Post by c2tarun on 2010-09-04
please reply

---

### Post by koenn on 2010-09-04
> **c2tarun said:**
> please reply
please wait at least 24 hrs before bumping

---

### Post by koenn on 2010-09-04
fast:
```

sudo -i
http_proxy=http:/host:port/
apt-get install whatever

```

permanent:
put the following into /etc/apt/apt.conf
```

Acquire::http::Proxy "http://1233123.123.123:8080";

```

replace address and port number with the correct ones.

---

