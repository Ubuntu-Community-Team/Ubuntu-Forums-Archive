---
title: "Squid HELP!!!!"
date: 2008-08-21
forum: Server Platforms
---

### Post by iae610 on 2008-08-21
Hi i am a noob a linux and I dont know how to set the Visible_hostname in squid. Can some one help or show me theirs? Thanks

---

### Post by Dr Small on 2008-08-21
Run:
```
sudo vim /etc/squid/squid.conf
```

Search for 'visible_hostname' and then set it to whatever your 'hostname' is.

Dr Small

---

### Post by iae610 on 2008-08-21
But were do I put my 'Hostname' also do i put the quotes. Do i put it next to visible_hostname or what? Thanks

---

### Post by iae610 on 2008-08-22
NVM i used the webmin

---

