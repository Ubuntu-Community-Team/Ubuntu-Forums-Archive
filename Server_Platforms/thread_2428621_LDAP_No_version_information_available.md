---
title: "LDAP: No version information available"
date: 2019-10-07
forum: Server Platforms
---

### Post by leof222 on 2019-10-07
Hello,
I've installed the newest version 2.4.48 of openldap on Ubuntu 18.04:
```
./configure --with-cyrus-sasl --with-tls=openssl --enable-overlays=mod --enable-backends=mod --disable-perl --disable-ndb --enable-crypt --enable-modules --enable-dynamic --enable-syslog --enable-debug --enable-local --enable-spasswd --disable-sql --enable-mdb
make depend
make

#test
make test > test_results.txt
grep '>>>>>.*failed' test_results.txt

#install
make install

```
If I run the scritp 'sudo sh updateOpenldap.sh' which includes the command
```
ldapdelete -x -r -D cn=admin,dc=aesettlingen,dc=ddnss,dc=de -w geheim ou=benutzer,dc=schule,dc=ddnss,dc=de >> updateOpenldap.log 2>> updateOpenldap.errorlog

```
everything works fine.
If I use a cronjob via crontab
```
*/1 * * * * /bin/bash /home/ldap/convertADtoOpenldap/updateOpenldap.sh
```
I get the errors:
```

ldapdelete: /usr/local/lib/liblber-2.4.so.2: no version information available (required by ldapdelete)
ldapdelete: /usr/local/lib/libldap-2.4.so.2: no version information available (required by ldapdelete)
LDAP vendor version mismatch: library 20448, header 20445
```
Here the content of /usr/lib/
```
root@ldapserver:/# ls -lah /usr/lib/lib*
lrwxrwxrwx 1 root root   21 Mai 14 09:07 /usr/lib/libDeployPkg.so.0 -> libDeployPkg.so.0.0.0
-rw-r--r-- 1 root root  31K Mai 14 09:07 /usr/lib/libDeployPkg.so.0.0.0
lrwxrwxrwx 1 root root   15 Dez 19  2018 /usr/lib/libgjs.so.0 -> libgjs.so.0.0.0
-rw-r--r-- 1 root root 820K Dez 19  2018 /usr/lib/libgjs.so.0.0.0
lrwxrwxrwx 1 root root   20 Mai 14 09:07 /usr/lib/libguestlib.so.0 -> libguestlib.so.0.0.0
-rw-r--r-- 1 root root  23K Mai 14 09:07 /usr/lib/libguestlib.so.0.0.0
lrwxrwxrwx 1 root root   16 Mai 14 09:07 /usr/lib/libhgfs.so.0 -> libhgfs.so.0.0.0
-rw-r--r-- 1 root root 160K Mai 14 09:07 /usr/lib/libhgfs.so.0.0.0
lrwxrwxrwx 1 root root   31 Sep 16 17:37 /usr/lib/libldap-2.4.so.2 -> /usr/local/lib/libldap-2.4.so.2
lrwxrwxrwx 1 root root   17 Sep  4  2018 /usr/lib/libnetpbm.so.10 -> libnetpbm.so.10.0
-rw-r--r-- 1 root root 143K Apr 23  2016 /usr/lib/libnetpbm.so.10.0
lrwxrwxrwx 1 root root   18 Mai 14 09:07 /usr/lib/libvgauth.so.0 -> libvgauth.so.0.0.0
-rw-r--r-- 1 root root  84K Mai 14 09:07 /usr/lib/libvgauth.so.0.0.0
lrwxrwxrwx 1 root root   19 Mai 14 09:07 /usr/lib/libvmtools.so.0 -> libvmtools.so.0.0.0
-rw-r--r-- 1 root root 609K Mai 14 09:07 /usr/lib/libvmtools.so.0.0.0
```
and /usr/local/lib/
```
root@ldapserver:/# ls -lah /usr/local/lib/lib*
lrwxrwxrwx 1 root root   22 Okt  3 18:11 /usr/local/lib/liblber-2.4.so.2 -> liblber-2.4.so.2.10.11
-rw-r--r-- 1 root root 222K Okt  3 18:11 /usr/local/lib/liblber-2.4.so.2.10.11
-rw-r--r-- 1 root root 223K Sep 12  2018 /usr/local/lib/liblber-2.4.so.2.10.8
-rw-r--r-- 1 root root 223K Sep 11  2018 /usr/local/lib/liblber-2.4.so.2.10.9
-rw-r--r-- 1 root root 375K Okt  3 18:11 /usr/local/lib/liblber.a
-rw-r--r-- 1 root root  827 Okt  3 18:11 /usr/local/lib/liblber.la
lrwxrwxrwx 1 root root   22 Okt  3 18:11 /usr/local/lib/liblber.so -> liblber-2.4.so.2.10.11
lrwxrwxrwx 1 root root   22 Okt  3 18:11 /usr/local/lib/libldap-2.4.so.2 -> libldap-2.4.so.2.10.11
-rw-r--r-- 1 root root 1,4M Okt  3 18:11 /usr/local/lib/libldap-2.4.so.2.10.11
-rw-r--r-- 1 root root 1,4M Sep 12  2018 /usr/local/lib/libldap-2.4.so.2.10.8
-rw-r--r-- 1 root root 1,4M Sep 11  2018 /usr/local/lib/libldap-2.4.so.2.10.9
-rw-r--r-- 1 root root 2,8M Okt  3 18:11 /usr/local/lib/libldap.a
-rw-r--r-- 1 root root  876 Okt  3 18:11 /usr/local/lib/libldap.la
lrwxrwxrwx 1 root root   24 Okt  3 18:11 /usr/local/lib/libldap_r-2.4.so.2 -> libldap_r-2.4.so.2.10.11
-rw-r--r-- 1 root root 1,6M Okt  3 18:11 /usr/local/lib/libldap_r-2.4.so.2.10.11
-rw-r--r-- 1 root root 1,6M Sep 12  2018 /usr/local/lib/libldap_r-2.4.so.2.10.8
-rw-r--r-- 1 root root 1,6M Sep 11  2018 /usr/local/lib/libldap_r-2.4.so.2.10.9
-rw-r--r-- 1 root root 3,1M Okt  3 18:11 /usr/local/lib/libldap_r.a
-rw-r--r-- 1 root root  899 Okt  3 18:11 /usr/local/lib/libldap_r.la
lrwxrwxrwx 1 root root   24 Okt  3 18:11 /usr/local/lib/libldap_r.so -> libldap_r-2.4.so.2.10.11
lrwxrwxrwx 1 root root   22 Okt  3 18:11 /usr/local/lib/libldap.so -> libldap-2.4.so.2.10.11
```
Does somebody has any idea?
Thanks a lot!
Leo

---

### Post by LHammonds on 2019-10-07
Crontab does not have a path environment so if any command issued uses a relative path, it will likely not work.

To test if this is the issue, add this command to the top of your script and see if it works:

```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

If it works, then you know what the issue is and can track down what command in your script or sub-scripts are using relative paths.

LHammonds

---

