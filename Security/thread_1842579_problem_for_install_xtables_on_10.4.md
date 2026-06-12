---
title: "problem for install xtables on 10.4"
date: 2011-09-11
forum: Security
---

### Post by denis21-ru on 2011-09-11
Hi, I am new to ubuntu and few can understand some things.

> apt-get install module-assistant xtables-addons-source 
Reading package lists ... Finish 
Building dependency tree 
Reading state information ... Finish 
Will install the following additional packages: 
  cvs debhelper gettext html2text intltool-debian iptables-dev libmail-sendmail-perl libsys-hostname-long-perl po-debconf 
Suggested packages: 
  dh-make gettext-doc libmail-box-perl 
NEW packages will be installed: 
  cvs debhelper gettext html2text intltool-debian iptables-dev libmail-sendmail-perl libsys-hostname-long-perl module-assistant po-debconf 
  xtables-addons-source 
0 upgraded, installed 11 new packages, 0 to remove packages, and 6 not upgraded. 
Need to get 980kB of archives 4. 
After this operation, additional disk space will be 15,1 MB. 
Do you want to continue [Y / n]? d 
WARNING: The following packages can not be authenticated! 
  iptables-dev 
Install these packages without verification [y / N]? y 
Received: 1 [http://mydc.ru/ubuntu/](http://mydc.ru/ubuntu/) binary / iptables-dev 1.4.10-1ubuntu2 [109kB] 
Received: 2 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main cvs 1:1.12.13-12ubuntu1 [1 685kB] 
Received: 3 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main html2text 1.3.2a-14build1 [101kB] 
Received: 4 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main gettext 0.17-8ubuntu3 [1 732kB] 
Received: 5 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main intltool-debian 0.35.0 +20060710.1 [31,6 kB] 
Received: 6 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main po-debconf 1.0.16 [224kB] 
Received: 7 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main debhelper 7.4.15ubuntu1 [461kB] 
Received: 8 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main libsys-hostname-long-perl 1.4-2 [11,4 kB] 
Received: 9 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / main libmail-sendmail-perl 0.79.16-1 [26,5 kB] 
Received: 10 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / universe module-assistant 0.11.2ubuntu1 [111kB] 
Received: 11 [http://ru.archive.ubuntu.com/ubuntu/](http://ru.archive.ubuntu.com/ubuntu/) lucid / universe xtables-addons-source 1.21-1 [489kB] 
Received 4 980kB for 3s (316kB 1 / c) 
Pre-installation packages ... 
Selecting previously deselected package cvs. 
(Reading database ... currently installed 160 760 files and directories.) 
Unpacking cvs (from file .../cvs_1% 3a1.12.13-12ubuntu1_i386.deb) ... 
Selecting previously deselected package html2text. 
Unpacking html2text (from file .../html2text_1.3.2a-14build1_i386.deb) ... 
Selecting previously deselected package gettext. 
Unpacking gettext (from file .../gettext_0.17-8ubuntu3_i386.deb) ... 
Selecting previously deselected package intltool-debian. 
Unpacking intltool-debian (from file .../intltool-debian_0.35.0 +20060710.1 _all.deb) ... 
Selecting previously deselected package po-debconf. 
Unpacking po-debconf (from file .../po-debconf_1.0.16_all.deb) ... 
Selecting previously deselected package debhelper. 
Unpacking debhelper (from file .../debhelper_7.4.15ubuntu1_all.deb) ... 
Selecting previously deselected package iptables-dev. 
Unpacking iptables-dev (from file .../iptables-dev_1.4.10-1ubuntu2_i386.deb) ... 
Selecting previously deselected package libsys-hostname-long-perl. 
Unpacking libsys-hostname-long-perl (from file .../libsys-hostname-long-perl_1.4-2_all.deb) ... 
Selecting previously deselected package libmail-sendmail-perl. 
Unpacking libmail-sendmail-perl (from file .../libmail-sendmail-perl_0.79.16-1_all.deb) ... 
Selecting previously deselected package module-assistant. 
Unpacking module-assistant (from the file .../module-assistant_0.11.2ubuntu1_all.deb) ... 
Selecting previously deselected package xtables-addons-source. 
Unpacking xtables-addons-source (from file .../xtables-addons-source_1.21-1_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for install-info ... 
Processing triggers for doc-base ... 
Processing 5 added doc-base file (s) ... 
Registering documents with scrollkeeper ... 
Setting up cvs (1:1.12.13-12ubuntu1) ... 
Ignoring install-info called from maintainer script 
The package cvs should be rebuilt with new debhelper to get trigger support 
Ignoring install-info called from maintainer script 
The package cvs should be rebuilt with new debhelper to get trigger support 

Setting up html2text (1.3.2a-14build1) ... 

Setting up gettext (0.17-8ubuntu3) ... 

Setting up intltool-debian (0.35.0 +20060710.1) ... 
Setting up po-debconf (1.0.16) ... 
Setting up debhelper (7.4.15ubuntu1) ... 
Setting up iptables-dev (1.4.10-1ubuntu2) ... 
Setting up libsys-hostname-long-perl (1.4-2) ... 
Setting up libmail-sendmail-perl (0.79.16-1) ... 
Setting up module-assistant (0.11.2ubuntu1) ... 
Setting up xtables-addons-source (1.21-1) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
: ~ # Depmod-a 
: ~ # Module-assistant prepare 
Getting the kernel source with the version: 2.6.32-33-generic 
The kernel headers available in / usr/src/linux-headers-2.6.32-33-generic 
Creating symbolic links ... 
apt-get install build-essential 
Reading package lists ... Finish 
Building dependency tree 
Reading state information ... Finish 
Is already the newest version of the build-essential. 
0 upgraded, 0 newly installed, 0 to remove packages, and 6 not upgraded. 

Done! 
: ~ # Module-assistant auto-install xtables-addons-source 

Updated information about a package 
Getting the kernel source with the version: 2.6.32-33-generic 
The kernel headers available in / usr / src / linux 
Creating symbolic links ... 
Unable to create a symbolic link to / usr / src / linux! 
apt-get install build-essential 
Reading package lists ... Finish 
Building dependency tree 
Reading state information ... Finish 
Is already the newest version of the build-essential. 
0 upgraded, 0 newly installed, 0 to remove packages, and 6 not upgraded. 

Done! 
unpack 
Extracting the package tarball, / usr/src/xtables-addons.tar.bz2, please wait ... 
"/ Usr / share / modass / packages / default.sh" build KVERS = 2.6.32-33-generic KSRC = / usr/src/linux-headers-2.6.32-33-generic KDREV = 2.6.32-33.72 kdist_image 
Finished with / usr/src/xtables-addons-modules-2.6.32-33-generic_1.21-1 +2.6.32-33.72 _i386.deb. 
dpkg-Ei / usr/src/xtables-addons-modules-2.6.32-33-generic_1.21-1 +2.6.32-33.72 _i386.deb 
Selecting previously deselected package xtables-addons-modules-2.6.32-33-generic. 
(Reading database ... currently installed 161 575 files and directories.) 
Unpacking xtables-addons-modules-2.6.32-33-generic (from a file .../xtables-addons-modules-2.6.32-33-generic_1.21-1 +2.6.32-33.72 _i386.deb). .. 
dpkg: dependency problems prevent configuration xtables-addons-modules-2.6.32-33-generic: 
 xtables-addons-modules-2.6.32-33-generic depends on xtables-addons-common-1.21, but: 
  Package xtables-addons-common-1.21 is not installed. 
dpkg: error processing xtables-addons-modules-2.6.32-33-generic (- install): 
 dependency problems - leaving unconfigured 
When processing the following Errors were: 
 xtables-addons-modules-2.6.32-33-generic 

I: Direct installation failed, trying to run the post installation depending on 

apt-get-f install 
Reading package lists ... Finish 
Building dependency tree 
Reading state information ... Finish 
Correcting dependencies ... Finish 
Will install the following additional packages: 
  xtables-addons-common 
NEW packages will be installed: 
  xtables-addons-common 
0 upgraded, 1 newly installed, 0 to remove packages, and 6 not upgraded. 
not installed or removed before the end of a packet. 
You need to download 89.6 MB of archives. 
After this operation, additional disk space will be 492kB. 
Do you want to continue [Y / n]? d 
Received: 1 [http://ru.archive.ubuntu.com/ubuntu/lucid](http://ru.archive.ubuntu.com/ubuntu/lucid) /universe xtables-addons-common 1.21-1 [89,6 kB] 
Received 89.6 KB per 0s (474kB / c) 
Selecting previously deselected package xtables-addons-common. 
(Reading database ... currently installed 161 619 files and directories.) 
Unpacking xtables-addons-common (from file .../xtables-addons-common_1.21-1_i386.deb) ... 
dpkg: error processing / var/cache/apt/archives/xtables-addons-common_1.21-1_i386.deb (- unpack): 
 attempt to rewrite '/lib/xtables/ libxt_TEE.so', Kotor (th) th is also in package iptables 0:1.4.10-1ubuntu2 
When processing the following Errors were: 
 / Var/cache/apt/archives/xtables-addons-common_1.21-1_i386.deb 
E: Sub-process / usr / bin / dpkg returned an error code (1)

> uname -a
Linux lgroup 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
Help Please, what is my error?

---

### Post by Dangertux on 2011-09-11
This is how I install it and it works.

```
[FONT=monospace]
[/FONT]wget http://archive.ubuntu.com/ubuntu/pool/universe/x/xtables-addons/xtables-addons-source_1.21-1_all.deb 
wget http://archive.ubuntu.com/ubuntu/pool/universe/x/xtables-addons/xtables-addons-common_1.21-1_i386.deb[FONT=Verdana]
[/FONT]sudo apt-get install gdebi-core quilt [FONT=Verdana]
[/FONT]sudo gdebi xtables-addons-source_1.21-1_all.deb[FONT=Verdana]
[/FONT]sudo gdebi xtables-addons-common_1.21-1_i386.deb[FONT=Verdana]
[/FONT]sudo module-assistant --verbose --text-mode auto-install xtables-addons[FONT=Verdana]
[/FONT]
```

Hope that helps.

---

### Post by denis21-ru on 2011-09-12
No, Error: 
> $ sudo module-assistant - verbose - text-mode auto-install xtables-addons 
Update on xtables-addons-source 

Updated information about a package 
Getting the kernel source with the version: 2.6.32-33-generic 
The kernel headers available in / usr/src/linux-headers-2.6.32-33-generic 
Creating symbolic links ... 
apt-get install build-essential 
Reading package lists ... Finish 
Building dependency tree 
Reading state information ... Finish 
Is already the newest version of the build-essential. 
0 upgraded, 0 newly installed, 0 to remove packages, and 12 not upgraded. 

Done! 
unpack 
Extracting the package tarball, / usr/src/xtables-addons.tar.bz2, please wait ... 
 action tar - bzip2-x-f / usr/src/xtables-addons.tar.bz2 
 tar - bzip2-x-f / usr/src/xtables-addons.tar.bz2 
Target package file / usr/src/xtables-addons-modules-2.6.32-33-generic_1.21-1 +2.6.32-33.72 _i386.deb already 
There, we will not rebuild! 
(However, you could use the-f switch to ignore it) 
dpkg-Ei / usr/src/xtables-addons-modules-2.6.32-33-generic_1.21-1 +2.6.32-33.72 _i386.deb 
Selecting previously deselected package xtables-addons-modules-2.6.32-33-generic. 
(Reading database ... currently installed 166 182 files and directories.) 
Unpacking xtables-addons-modules-2.6.32-33-generic (from a file .../xtables-addons-modules-2.6.32-33-generic_1.21-1 +2.6.32-33.72 _i386.deb). .. 
dpkg: dependency problems prevent configuration xtables-addons-modules-2.6.32-33-generic: 
 xtables-addons-modules-2.6.32-33-generic depends on xtables-addons-common-1.21, but: 
  Package xtables-addons-common-1.21 is not installed. 
dpkg: error processing xtables-addons-modules-2.6.32-33-generic (- install): 
 dependency problems - leaving unconfigured 
When processing the following Errors were: 
 xtables-addons-modules-2.6.32-33-generic 

I: Direct installation failed, trying to run the post installation depending on 

apt-get-f install 
Reading package lists ... Finish 
Building dependency tree 
Reading state information ... Finish 
Correcting dependencies ... Finish 
Will install the following additional packages: 
  xtables-addons-common 
NEW packages will be installed: 
  xtables-addons-common 
0 upgraded, 1 newly installed, 0 to remove packages, and 12 not upgraded. 
not installed or removed before the end of a packet. 
Need to get 0B/89, 6kB archives. 
After this operation, additional disk space will be 492kB. 
Do you want to continue [Y / n]? y
(Reading database ... currently installed 166 226 files and directories.) 
Unpacking xtables-addons-common (from file .../xtables-addons-common_1.21-1_i386.deb) ... 
dpkg: error processing /var/cache/apt/archives/xtables-addons-common_1.21-1_i386.deb (- unpack): 
 attempt to rewrite '/lib/xtables/libxt_TEE.so', Kotor (th) th is also in package iptables 0:1.4.10-1ubuntu2 
When processing the following Errors were: 
 /var/cache/apt/archives/xtables-addons-common_1.21-1_i386.deb 
E: Sub-process / usr / bin / dpkg returned an error code (1)


$ iptables --version
iptables v1.4.10

---

### Post by denis21-ru on 2011-09-14
Hm, help me please.

---

### Post by cariboo on 2011-09-15
The output tells you what the problem is:

> dpkg: dependency problems prevent configuration xtables-addons-modules-2.6.32-33-generic: 
x[B]tables-addons-modules-2.6.32-33-generic depends on xtables-addons-common-1.21, but: 
Package xtables-addons-common-1.21 is not installed[/B]. 

---

### Post by denis21-ru on 2011-09-15
Ohm thx :P
Sorry

---

