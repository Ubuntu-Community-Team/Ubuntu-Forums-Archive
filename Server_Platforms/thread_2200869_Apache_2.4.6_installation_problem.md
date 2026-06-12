---
title: "Apache 2.4.6 installation problem"
date: 2014-01-21
forum: Server Platforms
---

### Post by brokengillou on 2014-01-21
Hi,
 I installed Apache 2.4.6 mpm worker from debphp on Ubuntu 12 LTS (after  uninstalling all kind of apache php mysql) it seems to work (page it's  ok) but some usual commands do not work and results are unexpected.

 1° Webmin shows event module activated instead of worker
2° apache2 -l doesn't return worker.c as compiled in module
3° apache2 -V complains about config variables not defined relying on  SUFFIX=??? in envvars (AH00526: Syntax error on line 74 of /etc/apache2/apache2.conf)
4° service apache2 restart or /etc/init.d/apache2 restart OK
5° apache2 -L same as apache2 -V error messages AH00526 AH00111
6° apache2ctl configtest gives Syntax OK
 
uname -a =>
Linux WORGANE 3.8.0-35-generic #50~precise1-Ubuntu SMP Wed Dec 4 17:25:51 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

 
lsb_release -a =>
Ubuntu 12.04.4 LTS \n \l

 
apache2 -v
Server version: Apache/2.4.6 (Ubuntu)
Server built:   Sep 23 2013 07:23:34

 apt-cache show apache2-mpm-worker=2.4.6* =>
Package: apache2-mpm-worker
Source: apache2
Priority: extra
Section: oldlibs
Installed-Size: 22
Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Version: 2.4.6-3+debphp.org~precise+1
Depends: apache2 (= 2.4.6-3+debphp.org~precise+1)
Filename: pool/main/a/apache2/apache2-mpm-worker_2.4.6-3+debphp.org~precise+1_amd64.deb
 apt-cache show apache2=2.4.6* =>
Package: apache2
Priority: optional
Section: httpd
Installed-Size: 435
Maintainer: Debian Apache Maintainers <debian-apache@lists.debian.org>
Architecture: amd64
Version: 2.4.6-3+debphp.org~precise+1
Recommends: ssl-cert
Replaces: apache2.2-common
Suggests: www-browser, apache2-doc, apache2-suexec-pristine | apache2-suexec-custom, apache2-utils
Depends: lsb-base, procps, perl, mime-support, apache2-bin (= 2.4.6-3+debphp.org~precise+1), apache2-data (= 2.4.6-3+debphp.org~precise+1)
Conflicts: apache2.2-common
Filename: pool/main/a/apache2/apache2_2.4.6-3+debphp.org~precise+1_amd64.deb

 

thanks by advance

 
Gilles

---

