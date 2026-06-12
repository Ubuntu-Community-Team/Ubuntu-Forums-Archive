---
title: "Webmin Crashes"
date: 2009-07-29
forum: Server Platforms
---

### Post by serenityit on 2009-07-29
New user to Ubuntu server, but used to using Debian.

Installed a fresh copy of server today with Bind, Samba and Webmin.

Webmin seems to have a habit of crashing out when browsing it from the web browser which requires me to restart the webmin web server.

Dmesg seems to show perl errors... don't know if they're related.

Any ideas and suggestions appreciated,

Andy
Serenity Holidays IT

---

### Post by ibutho on 2009-07-29
Hi and welcome to the forums. What are the perl errors? How did you install webmin?

---

### Post by serenityit on 2009-07-29
> **ibutho said:**
> Hi and welcome to the forums. What are the perl errors? How did you install webmin?

Hi and thanks,

I installed webmin by downloading the DEB file and using dpkg --install

Pulled this out of dmesg

```
[  519.811020] miniserv.pl[2314] general protection ip:812738c sp:bfe4e9b0 error:0 in perl[8048000+134000]
[  599.935771] miniserv.pl[2638] general protection ip:812738c sp:bf8af470 error:0 in perl[8048000+134000]
[  624.209422] miniserv.pl[2654] general protection ip:8173465 sp:bfb1d000 error:0 in perl[8048000+134000]
[  637.660256] miniserv.pl[2669] general protection ip:812738c sp:bfb1cf90 error:0 in perl[8048000+134000]
[  641.598219] miniserv.pl[2670] general protection ip:8173465 sp:bfb1d000 error:0 in perl[8048000+134000]
[  675.355182] run-uninstalls.[2679] general protection ip:812738c sp:bf8c7cc0 error:0 in perl[8048000+134000]
[  813.251935] dpkg-preconfigu[2718] general protection ip:812738c sp:bfbf0860 error:0 in perl[8048000+134000]
[  850.541775] run-postinstall[3303]: segfault at 9e9 ip 080a59d6 sp bfff2580 error 4 in perl[8048000+134000]
[  850.634580] run-postinstall[3306] general protection ip:812738c sp:bfff2420 error:0 in perl[8048000+134000]
[  853.527150] run-postinstall[3364] general protection ip:812738c sp:bfff2420 error:0 in perl[8048000+134000]
[  853.674859] run-postinstall[3366] general protection ip:812738c sp:bfff2420 error:0 in perl[8048000+134000]
[  853.992079] ip_tables: (C) 2000-2006 Netfilter Core Team
[  894.380294] miniserv.pl[3434] general protection ip:812738c sp:bfc00830 error:0 in perl[8048000+134000]
[  894.382391] miniserv.pl[3425] general protection ip:812738c sp:bfbff9c0 error:0 in perl[8048000+134000]
[  931.682926] miniserv.pl[3545] general protection ip:812738c sp:bf824480 error:0 in perl[8048000+134000]
[  934.456183] miniserv.pl[3554]: segfault at 1 ip 0812738c sp bf824450 error 4 in perl[8048000+134000]
[  937.969033] miniserv.pl[3571] general protection ip:812738c sp:bf824460 error:0 in perl[8048000+134000]
[  939.117810] miniserv.pl[3572] general protection ip:812738c sp:bf824450 error:0 in perl[8048000+134000]
[  955.484571] miniserv.pl[3578] general protection ip:812738c sp:bf824450 error:0 in perl[8048000+134000]
[  965.561916] miniserv.pl[3584] general protection ip:812738c sp:bf824480 error:0 in perl[8048000+134000]
[  967.830930] miniserv.pl[3587]: segfault at 75 ip 08173462 sp bf8244b0 error 6 in perl[8048000+134000]
[  968.734259] miniserv.pl[3593] general protection ip:812738c sp:bf824450 error:0 in perl[8048000+134000]
[  991.996895] miniserv.pl[3594] general protection ip:812738c sp:bf824450 error:0 in perl[8048000+134000]
[ 1287.227778] python[3754]: segfault at 103 ip 0810ab5a sp bf803c60 error 4 in python2.6[8048000+1dd000]
[ 1617.668931] atboot.pl[3963] general protection ip:812738c sp:bfd0e0b0 error:0 in perl[8048000+134000]
[ 1617.713736] run-postinstall[3979] general protection ip:812738c sp:bfa518b0 error:0 in perl[8048000+134000]
[ 3747.391938] miniserv.pl[4938]: segfault at 30 ip 080ea38b sp bfe2dbf0 error 6 in perl[8048000+134000]
```

---

### Post by ibutho on 2009-07-29
Have you looked at webmins error logs to see if there is anything that can indicate what the problem is? The output you posted above shows that there is some sort of problem with webmins web server and perl but the logs may provide more accurate info.

---

