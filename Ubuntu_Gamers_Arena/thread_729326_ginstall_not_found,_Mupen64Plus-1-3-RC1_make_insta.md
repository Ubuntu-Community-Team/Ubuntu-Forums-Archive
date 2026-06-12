---
title: "ginstall not found, Mupen64Plus-1-3-RC1 make install error"
date: 2008-03-19
forum: Ubuntu Gamers Arena
---

### Post by Duffadash on 2008-03-19
Hello everyone.
I have downloaded the source code of the new release of [Mupen64Plus]("http://www.emutalk.net/showthread.php?t=43744"), and did a succesful 'make all', however when trying to 'make install' I get the following error message:
```
duffadash@Arkhe:~/Mupen64Plus-1-3-RC1-src$ sudo make install
[sudo] password for duffadash:
./install.sh /usr/local
Installing Mupen64Plus to /usr/local
./install.sh: 30: ginstall: not found
make: *** [install] Error 127

```

Anybody able to give a hint how to fix this?

---

### Post by Ariel MX on 2008-03-23
Edit the file install.sh and change "ginstall" to "install" and it would work fine. :D

---

