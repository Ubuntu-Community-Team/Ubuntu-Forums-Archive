---
title: "Pure-FTPd disable SSLv2 and SSlv3 (only TLS)"
date: 2015-06-18
forum: Security
---

### Post by lorenzosfarra on 2015-06-18
Good morning everyone,


I've read a lot of documentation and threads about this subject.
So I've configured FTPS with a good certificate, and configured the pure-ftpd service like so:


```
echo 2 > /etc/pure-ftpd/conf/TLS
```

So only TLS connections should be accepted.



Then configured the daemon to run with the following commands:

```
/usr/sbin/pure-ftpd -l puredb:/etc/pure-ftpd/pureftpd.pdb -l puredb:/etc/pure-ftpd/pureftpd.pdb -l pam -Y 2 -O w3c:/var/log/pure-ftpd/transfer.log -J HIGH:MEDIUM:+TLSv1:!SSLv2:+SSLv3@STRENGTH -H -8 UTF-8 -p 64000:65000 -u 99 -B
```


(Please take a look at the -J flag. I've tried different strings but the result is the same).


The problem is that the website passed every PCI vulnerability test, except 1:
*SSL Version 2 and 3 Protocol Detection*


Current version: **1.0.36**.


Any hints?


An additional question, if possible: do  you have any idea on how they perform this scan? Which tool they use,  just to check by myself before scheduling a new, complete scan?



PS:  I've read that this problem is solved by default on the 1.0.37 version  but I don't find some good repository (a ppa for example, even if I don't like them) to manage the upgrade with Ubuntu  Server (and I would like to avoid to compile it, if possible).




Thanks a lot,

  Lorenzo

---

