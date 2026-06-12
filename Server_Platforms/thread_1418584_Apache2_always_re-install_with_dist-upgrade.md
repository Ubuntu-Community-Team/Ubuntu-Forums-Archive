---
title: "Apache2 always re-install with dist-upgrade"
date: 2010-02-28
forum: Server Platforms
---

### Post by BSK on 2010-02-28
Hi,

I have a small web server with ubuntu 9.10 that used to be running Apache2 but I switched to Lighttpd.  Everything runs fine but each time I run "apt-get dist-upgrade" it always wants to re-install Apache2.

So my two questions are ;
1. Why ?
2. How to fix it ?

Thanks!!!

---

### Post by stlsaint on 2010-02-28
try:
```
sudo aptitude purge apache2
```
if that doesnt fix than...
```
sudo aptitude install deborphan
```
then
```
sudo aptitude purge $(deborphan)
```

---

### Post by BSK on 2010-02-28
Thanks,

```
sudo aptitude purge apache2
```

worked.

---

