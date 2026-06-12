---
title: "Resolver error: undefined symbol: GeoIP_country_name"
date: 2009-12-04
forum: Server Platforms
---

### Post by limaunion on 2009-12-04
Hi all! I'm running Ubuntu Server Edition 9.10 (fully updated) and today while typing some commands I've found this error:

dig: symbol lookup error: /usr/lib/libdns.so.50: undefined symbol: GeoIP_country_name_by_ipnum_v6

I get the same error with nslookup/host and dig... any ideas what's going on here and how to fix this ?

Thanks in advance.
Limaunion

---

### Post by limaunion on 2009-12-04
I forgot to mention that this server was ugraded from a previous version, and have found some inconsistencies, i've these file that seem to be unreleated to release 9.10:

$ sudo ls -l /usr/local/lib/
total 188
-rw-r--r-- 1 root root  52292 2006-12-26 10:25 libGeoIP.a
-rwxr-xr-x 1 root root    799 2006-12-26 10:25 libGeoIP.la
lrwxrwxrwx 1 root root     17 2009-08-12 15:35 libGeoIP.so -> libGeoIP.so.1.4.0
lrwxrwxrwx 1 root root     17 2009-08-12 15:35 libGeoIP.so.1 -> libGeoIP.so.1.4.0
-rwxr-xr-x 1 root root  49146 2006-12-26 10:25 libGeoIP.so.1.4.0
-rw-r--r-- 1 root root  39170 2006-12-26 10:25 libGeoIPUpdate.a
-rwxr-xr-x 1 root root    845 2006-12-26 10:25 libGeoIPUpdate.la
lrwxrwxrwx 1 root root     23 2009-08-12 15:35 libGeoIPUpdate.so -> libGeoIPUpdate.so.0.0.0
lrwxrwxrwx 1 root root     23 2009-08-12 15:35 libGeoIPUpdate.so.0 -> libGeoIPUpdate.so.0.0.0
-rwxr-xr-x 1 root root  38419 2006-12-26 10:25 libGeoIPUpdate.so.0.0.0

and these seem to be the correct ones:

$ dpkg -L libgeoip1
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libgeoip1
/usr/share/doc/libgeoip1/README.Debian-source
/usr/share/doc/libgeoip1/TODO
/usr/share/doc/libgeoip1/AUTHORS
/usr/share/doc/libgeoip1/README.Debian
/usr/share/doc/libgeoip1/copyright
/usr/share/doc/libgeoip1/examples
/usr/share/doc/libgeoip1/examples/geolitecityupdate.sh
/usr/share/doc/libgeoip1/README.gz
/usr/share/doc/libgeoip1/changelog.Debian.gz
/usr/lib
/usr/lib/libGeoIP.so.1.4.6
/usr/lib/libGeoIPUpdate.so.0.0.0
/usr/lib/libGeoIP.so.1
/usr/lib/libGeoIPUpdate.so.0

Should I issue 'rm /usr/local/lib/libGeoIP*' ?
Thanks for comments.

---

### Post by limaunion on 2009-12-07
For the record:

I don't know if there's a bug or what but I found that the package 'libdns50' is dynamically linked to libGeoIP.so.1 => /usr/local/lib/libGeoIP.so.1 and that's the problem because the correct path for libGeoIP.so.1 is /usr/lib and not /usr/local/lib, so I solved this by simply creating a symlink pointing to the right path.
HTH.

---

