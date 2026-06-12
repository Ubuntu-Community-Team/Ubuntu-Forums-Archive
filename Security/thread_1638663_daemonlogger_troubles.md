---
title: "daemonlogger troubles :/"
date: 2010-12-05
forum: Security
---

### Post by 2uro on 2010-12-05
hey every body, first time actualy posting on the forums. gotta say yall have saved my can more times than i can count. 

so the problem im having is im trying to experiment with this program called daemonlogger, basicly takes two interfaces and bridges them and logs what passes between the two on to another iface.

im compiling from source on a old rig i have, 
its running ubuntu 10.10 server edition and i finaly got all the dependencys installed to a point where ./configure actualy worked. but whne i try and run make this is what i get.

anthony@node1:~/daemonlogger-1.2.1$ make
make  all-am
make[1]: Entering directory `/home/anthony/daemonlogger-1.2.1'
gcc -DHAVE_CONFIG_H -I.     -g -O2 -g -O0 -Wall -I/usr/include -c daemonlogger.c
daemonlogger.c:106: fatal error: dnet.h: No such file or directory
compilation terminated.
make[1]: *** [daemonlogger.o] Error 1
make[1]: Leaving directory `/home/anthony/daemonlogger-1.2.1'
make: *** [all] Error 2

any help apreciated. thanks guys

--2uro

---

### Post by Kinstonian on 2010-12-06
Did you read the error?  I googled "daemonlogger dnet.h" and it looks like the answer is in one of the first links.

[http://www.gamelinux.org/?p=17](http://www.gamelinux.org/?p=17)

You could of gotten the answer in literally less than 30 seconds instead of 8 hours. ;)

---

