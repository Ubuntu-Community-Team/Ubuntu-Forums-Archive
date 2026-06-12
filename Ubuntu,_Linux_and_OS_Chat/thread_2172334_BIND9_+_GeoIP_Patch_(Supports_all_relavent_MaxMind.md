---
title: "BIND9 + GeoIP Patch (Supports all relavent MaxMind Databases)"
date: 2013-09-04
forum: Ubuntu, Linux and OS Chat
---

### Post by sandyd on 2013-09-04
Ive noticed that the bind9 verison in Ubuntu only supports Country geolocation.

With the [bind-geoip]("https://code.google.com/p/bind-geoip/") patch, I enabled support for all MaxMind GeoIP databases (Supporting both free/commercial versions).

You can build the package at [https://github.com/celenebjvl/bind-geoip-ubuntu](https://github.com/celenebjvl/bind-geoip-ubuntu)

Note that you need to install the geoip-database-contrib package in order to get geolocation.

As mentioned in the README, Security is not guarenteed, though I will try to keep up with updates.

Apparmor fix:
```

nano /etc/apparmor.d/local/usr.sbin.named
```
Add
```

/usr/share/GeoIP/** r,
```
and run
```

sudo service apparmor restart
```

---

