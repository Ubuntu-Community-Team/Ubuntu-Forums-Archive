---
title: "Advice on building web server"
date: 2006-10-15
forum: Server Platforms
---

### Post by satimis on 2006-10-15
Hi folks,

I'm planning to build a web server on following PC;

CPU Athlon 64 3000+
RAM 1024M
HD SATA II 160G
OS Ubuntu on the server
[http://www.ubuntu.com/server](http://www.ubuntu.com/server)

Please advise what will be the best arrangement on the size of each of following partitions;

/dev/sda1 /boot
/dev/sda2 /
/dev/vg/home
/dev/vg/usr
/dev/vg/var
/dev/vg/tmp
/dev/sda4 swap

Any suggestion on above LVM order?  In following order?
/usr
/home
/var
/tmp

Is "Ubuntu on the server" easy to configure?


Apache, MySQL and PHP come with "Ubuntu on the server" as default.  What will be your opinion on MySQL vs PostgreSQL?


If allowing visitors sending webmail direct on the server what package will you recommend.

TIA


B.R.
satimis

---

