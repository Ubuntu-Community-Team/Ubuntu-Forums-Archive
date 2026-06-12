---
title: "strange error with bind9 and ubuntu server 8.04"
date: 2008-11-22
forum: Server Platforms
---

### Post by javierccs on 2008-11-22
hello folks,

i have installed a master server with this well written guide:
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)

however, when trying to install the slave serveri get this error:

Nov 22 12:29:02 yuruani named[6000]: starting BIND 9.4.2-P2 -u bind -t /var/lib/named
Nov 22 12:29:02 yuruani named[6000]: found 1 CPU, using 1 worker thread
Nov 22 12:29:02 yuruani named[6000]: loading configuration from '/etc/bind/named.conf'
Nov 22 12:29:02 yuruani named[6000]: none:0: open: /etc/bind/named.conf: permission denied
Nov 22 12:29:02 yuruani named[6000]: loading configuration: permission denied
Nov 22 12:29:02 yuruani named[6000]: exiting (due to fatal error)


i have double checked the permissions on my files:

```
/var/lib/named/etc/bind# ls -l
total 44
lrwxrwxrwx 1 bind bind   23 2008-11-22 11:54 bind -> /var/lib/named/etc/bind
-rwxr-xr-x 1 bind bind  237 2008-10-10 12:23 db.0
-rwxr-xr-x 1 bind bind  271 2008-10-10 12:23 db.127
-rwxr-xr-x 1 bind bind  237 2008-10-10 12:23 db.255
-rwxr-xr-x 1 bind bind  353 2008-10-10 12:23 db.empty
-rwxr-xr-x 1 bind bind  270 2008-10-10 12:23 db.local
-rwxr-xr-x 1 bind bind 2878 2008-10-10 12:23 db.root
-rwxr-xr-x 1 bind bind  907 2008-11-22 12:23 named.conf
-rwxr-xr-x 1 bind bind  493 2008-11-22 12:11 named.conf.local
-rwxr-xr-x 1 bind bind  695 2008-10-10 12:23 named.conf.options
-rwxr-xr-x 1 bind bind   77 2007-12-03 19:04 rndc.key
-rwxr-xr-x 1 bind bind 1317 2008-10-10 12:23 zones.rfc1918

```

now i reallydont know wth is going on, i have been stuck in this for almost 2 days, and always getting the same error... ifigured that it was probably already running, but when i try to stop bind i get this:

```
/var/lib/named/etc/bind# /etc/init.d/bind9 stop
 * Stopping domain name service... bind                                                                                     rndc: connect failed: 127.0.0.1#953: connection refused
                                                                                                                     [fail]
```


now im getting two errors and i can't understand what is going on, i have checked the permissions on my master server and they look the same... can someone help me out here?

---

### Post by RealPSL on 2008-11-22
Can you send the output of ```
ls -l /etc/bind/named.conf
```

Can you also stop apparmor with ```
sudo /etc/init.d/apparmor stop
``` the try to start the server again.

---

