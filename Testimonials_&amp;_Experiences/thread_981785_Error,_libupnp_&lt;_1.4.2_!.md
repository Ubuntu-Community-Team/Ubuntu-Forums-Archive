---
title: "Error, libupnp &lt; 1.4.2 !"
date: 2008-11-14
forum: Testimonials &amp; Experiences
---

### Post by gongjijiao on 2008-11-14
Error two:
[root@localhost ushare-1.1a]# ./configure --disable-dlna --disable-nls --with-libupnp-dir=$BASE/install/include --cross-prefix=arm-linux- --cross-compile
Checking for compiler available...
Checking for locales ...
Checking for ifaddrs ...
Checking for langinfo ...
Checking for iconv ...
Checking for libixml ...
Checking for libthreadutil ...
Checking for libupnp >= 1.4.2 ...
Error, libupnp < 1.4.2 !
See file "config.log" produced by configure for more details.
SOLVE:
export PKG_CONFIG_PATH=/home/huaqin/libupnp/install/lib/pkgconfig

---

### Post by Thelasko on 2008-11-14
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

