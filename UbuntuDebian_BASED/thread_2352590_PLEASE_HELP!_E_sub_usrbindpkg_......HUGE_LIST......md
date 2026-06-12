---
title: "PLEASE HELP! E: sub /usr/bin/dpkg ......HUGE LIST......"
date: 2017-02-13
forum: Ubuntu/Debian BASED
---

### Post by kniightmaare on 2017-02-13
KALI 2.X.X ROLLING
GNOME
XFCE
ok so laptop died durring update and now when turning it on or off it dose a start job and stop job, every single time, when i start it up, theres a 2sec window where it flashes from whati can see a bunch of passes, with 1 failed at the very top, network something i believe it says, most programs failing to run (e.g. zaapprox, burp, scarab, oracal7/8 ect. and running apt-get update/upgrade -f --fix-missing dist-upgrade -simmulate ect ect ect all produce same results please can anyone help me fix this ive tried everything that i know of. and the list is just 2 big to remove one by one, and fresh install is not an option as DD dosent even work, all trying to create a new bootable dose is lock the drive indefently. thx ahead of time. and oh im new here lol so howdy yall!! =]

so first ```
sudo apt-get autoremove
```   =   ```
root@kali:~# sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
39 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba-common (2:4.5.4+dfsg-1) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package samba-common (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up initramfs-tools (0.127) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-base (2016.20170123-2) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
Setting up php7.0-common (7.0.15-1) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package php7.0-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.9.0-kali1-amd64 (4.9.6-3kali2) ...
/etc/kernel/postinst.d/apt-auto-removal:
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
run-parts: /etc/kernel/postinst.d/apt-auto-removal exited with return code 127
dpkg: error processing package linux-image-4.9.0-kali1-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-8-jre-headless:amd64 (8u121-b13-3) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package openjdk-8-jre-headless:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of php7.0-mysql:
 php7.0-mysql depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2016.20170123-2); however:
  Package texlive-generic-recommended is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2016.20170123-2); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2016.20170123-2); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-ldap:
 php7.0-ldap depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-ldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-readline:
 php7.0-readline depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-readline (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-opcache:
 php7.0-opcache depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-opcache (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on texlive-latex-recommended (>= 2016.20170123-2); however:
  Package texlive-latex-recommended is not configured yet.
 texlive-latex-extra depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jdk-headless:amd64:
 openjdk-8-jdk-headless:amd64 depends on openjdk-8-jre-headless (= 8u121-b13-3); however:
  Package openjdk-8-jre-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jdk-headless:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php7.0:
 libapache2-mod-php7.0 depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.
 libapache2-mod-php7.0 depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.

dpkg: error processing package libapache2-mod-php7.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jdk:amd64:
 openjdk-8-jdk:amd64 depends on openjdk-8-jdk-headless (= 8u121-b13-3); however:
  Package openjdk-8-jdk-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jdk:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2016.20170123-2); however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-mcrypt:
 php7.0-mcrypt depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mcrypt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-cli:
 php7.0-cli depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.
 php7.0-cli depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.
 php7.0-cli depends on php7.0-readline; however:
  Package php7.0-readline is not configured yet.

dpkg: error processing package php7.0-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-amd64:
 linux-image-amd64 depends on linux-image-4.9.0-kali1-amd64; however:
  Package linux-image-4.9.0-kali1-amd64 is not configured yet.

dpkg: error processing package linux-image-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jre:amd64:
 openjdk-8-jre:amd64 depends on openjdk-8-jre-headless (= 8u121-b13-3); however:
  Package openjdk-8-jre-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-sqlite3:
 php7.0-sqlite3 depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-sqlite3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-json:
 php7.0-json depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-json (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:
 texlive-generic-extra depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.127) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 samba-common
 smbclient
 texlive-base
 texlive-latex-recommended-doc
 texlive-fonts-recommended-doc
 samba
 php7.0-common
 texlive-fonts-recommended
 samba-common-bin
 texlive-generic-recommended
 texlive-latex-base
 texlive-latex-base-doc
 linux-image-4.9.0-kali1-amd64
 openjdk-8-jre-headless:amd64
 php7.0-mysql
 texlive-pstricks
 texlive-latex-recommended
 texlive-extra-utils
 php7.0-ldap
 php7.0-readline
 php7.0-opcache
 texlive-latex-extra
 texlive-pictures-doc
 prosper
 openjdk-8-jdk-headless:amd64
 libapache2-mod-php7.0
 openjdk-8-jdk:amd64
 texlive-pstricks-doc
 texlive-pictures
 php7.0-mcrypt
 php7.0-cli
 texlive-font-utils
 texlive-latex-extra-doc
 linux-image-amd64
 openjdk-8-jre:amd64
 php7.0-sqlite3
 php7.0-json
 texlive-generic-extra
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by wildmanne39 on 2017-02-13
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by kniightmaare on 2017-02-14
ty! =]

---

### Post by speartip on 2017-02-14
When I get this type of issue,
```
sudo apt-get -f install
```
usually fixes it for me.
Then Update & Upgrade to see if all is well.

---

### Post by kniightmaare on 2017-02-14
> **speartip said:**
> When I get this type of issue,
```
sudo apt-get -f install
```
usually fixes it for me.
Then Update & Upgrade to see if all is well. ty for your response!! But it continues to post the exact same :(

---

### Post by speartip on 2017-02-14
Try:
```
sudo dpkg --configure -a
```

---

### Post by steeldriver on 2017-02-14
I don't know anything about Kali, but if it is based on Ubuntu/Debian I doubt the system installs core libraries in /usr/local

```

awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP

```

So likely this is something you have installed that's introduced an incompatible readline library

---

### Post by kniightmaare on 2017-02-15
speartip , ```
sudo dpkg --configure -a
```
produces 
```
root@kali:~# sudo dpkg --configure -a
Setting up samba-common (2:4.5.4+dfsg-1) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package samba-common (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up initramfs-tools (0.127) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-base (2016.20170123-2) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
Setting up php7.0-common (7.0.15-1) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package php7.0-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.9.0-kali1-amd64 (4.9.6-3kali2) ...
/etc/kernel/postinst.d/apt-auto-removal:
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
run-parts: /etc/kernel/postinst.d/apt-auto-removal exited with return code 127
dpkg: error processing package linux-image-4.9.0-kali1-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-8-jre-headless:amd64 (8u121-b13-3) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package openjdk-8-jre-headless:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of php7.0-mysql:
 php7.0-mysql depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2016.20170123-2); however:
  Package texlive-generic-recommended is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2016.20170123-2); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2016.20170123-2); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-ldap:
 php7.0-ldap depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-ldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-readline:
 php7.0-readline depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-readline (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-opcache:
 php7.0-opcache depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-opcache (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on texlive-latex-recommended (>= 2016.20170123-2); however:
  Package texlive-latex-recommended is not configured yet.
 texlive-latex-extra depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jdk-headless:amd64:
 openjdk-8-jdk-headless:amd64 depends on openjdk-8-jre-headless (= 8u121-b13-3); however:
  Package openjdk-8-jre-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jdk-headless:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php7.0:
 libapache2-mod-php7.0 depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.
 libapache2-mod-php7.0 depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.

dpkg: error processing package libapache2-mod-php7.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jdk:amd64:
 openjdk-8-jdk:amd64 depends on openjdk-8-jdk-headless (= 8u121-b13-3); however:
  Package openjdk-8-jdk-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jdk:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2016.20170123-2); however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-mcrypt:
 php7.0-mcrypt depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mcrypt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-cli:
 php7.0-cli depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.
 php7.0-cli depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.
 php7.0-cli depends on php7.0-readline; however:
  Package php7.0-readline is not configured yet.

dpkg: error processing package php7.0-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-amd64:
 linux-image-amd64 depends on linux-image-4.9.0-kali1-amd64; however:
  Package linux-image-4.9.0-kali1-amd64 is not configured yet.

dpkg: error processing package linux-image-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jre:amd64:
 openjdk-8-jre:amd64 depends on openjdk-8-jre-headless (= 8u121-b13-3); however:
  Package openjdk-8-jre-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-sqlite3:
 php7.0-sqlite3 depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-sqlite3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-json:
 php7.0-json depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-json (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:
 texlive-generic-extra depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.127) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 samba-common
 smbclient
 texlive-base
 texlive-latex-recommended-doc
 texlive-fonts-recommended-doc
 samba
 php7.0-common
 texlive-fonts-recommended
 samba-common-bin
 texlive-generic-recommended
 texlive-latex-base
 texlive-latex-base-doc
 linux-image-4.9.0-kali1-amd64
 openjdk-8-jre-headless:amd64
 php7.0-mysql
 texlive-pstricks
 texlive-latex-recommended
 texlive-extra-utils
 php7.0-ldap
 php7.0-readline
 php7.0-opcache
 texlive-latex-extra
 texlive-pictures-doc
 prosper
 openjdk-8-jdk-headless:amd64
 libapache2-mod-php7.0
 openjdk-8-jdk:amd64
 texlive-pstricks-doc
 texlive-pictures
 php7.0-mcrypt
 php7.0-cli
 texlive-font-utils
 texlive-latex-extra-doc
 linux-image-amd64
 openjdk-8-jre:amd64
 php7.0-sqlite3
 php7.0-json
 texlive-generic-extra
 initramfs-tools
root@kali:~# 


```

---

### Post by kniightmaare on 2017-02-15
> **steeldriver said:**
> I don't know anything about Kali, but if it is based on Ubuntu/Debian I doubt the system installs core libraries in /usr/local

```

awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP

```

So likely this is something you have installed that's introduced an incompatible readline library

```
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
```

gives me, 

```
root@kali:~# awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
bash: awk:: command not found
root@kali:~# apt-get install awk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package awk is a virtual package provided by:
  original-awk:i386 2012-12-20-6
  mawk:i386 1.3.3-17
  gawk:i386 1:4.1.4+dfsg-1
  original-awk 2012-12-20-6
  mawk 1.3.3-17
  gawk 1:4.1.4+dfsg-1
You should explicitly select one to install.

E: Package 'awk' has no installation candidate
root@kali:~# apt-get install original-awk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  original-awk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
39 not fully installed or removed.
Need to get 69.9 kB of archives.
After this operation, 165 kB of additional disk space will be used.
Get:1 http://mirrors.ocf.berkeley.edu/kali kali-rolling/main amd64 original-awk amd64 2012-12-20-6 [69.9 kB]
Fetched 69.9 kB in 0s (70.7 kB/s)     
Selecting previously unselected package original-awk.
(Reading database ... 451808 files and directories currently installed.)
Preparing to unpack .../original-awk_2012-12-20-6_amd64.deb ...
Unpacking original-awk (2012-12-20-6) ...
Setting up original-awk (2012-12-20-6) ...
Setting up samba-common (2:4.5.4+dfsg-1) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package samba-common (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up initramfs-tools (0.127) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package smbclient (--configure):
 dependency problems - leaving unconfigured
Setting up texlive-base (2016.20170123-2) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package texlive-base (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-latex-recommended-doc:
 texlive-latex-recommended-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-recommended-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-fonts-recommended-doc:
 texlive-fonts-recommended-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-fonts-recommended-doc (--configure):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.6.1-2) ...
dpkg: dependency problems prevent configuration of samba:
 samba depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba (--configure):
 dependency problems - leaving unconfigured
Setting up php7.0-common (7.0.15-1) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package php7.0-common (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of texlive-fonts-recommended:
 texlive-fonts-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-fonts-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (= 2:4.5.4+dfsg-1); however:
  Package samba-common is not configured yet.

dpkg: error processing package samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-recommended:
 texlive-generic-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-generic-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base:
 texlive-latex-base depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-base-doc:
 texlive-latex-base-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-base-doc (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.9.0-kali1-amd64 (4.9.6-3kali2) ...
/etc/kernel/postinst.d/apt-auto-removal:
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
run-parts: /etc/kernel/postinst.d/apt-auto-removal exited with return code 127
dpkg: error processing package linux-image-4.9.0-kali1-amd64 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up openjdk-8-jre-headless:amd64 (8u121-b13-3) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package openjdk-8-jre-headless:amd64 (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of php7.0-mysql:
 php7.0-mysql depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks:
 texlive-pstricks depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.
 texlive-pstricks depends on texlive-generic-recommended (>= 2016.20170123-2); however:
  Package texlive-generic-recommended is not configured yet.

dpkg: error processing package texlive-pstricks (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-recommended:
 texlive-latex-recommended depends on texlive-latex-base (>= 2016.20170123-2); however:
  Package texlive-latex-base is not configured yet.
 texlive-latex-recommended depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-recommended (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-extra-utils:
 texlive-extra-utils depends on texlive-latex-base (>= 2016.20170123-2); however:
  Package texlive-latex-base is not configured yet.
 texlive-extra-utils depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-extra-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-ldap:
 php7.0-ldap depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-ldap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-readline:
 php7.0-readline depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-readline (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-opcache:
 php7.0-opcache depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-opcache (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra:
 texlive-latex-extra depends on texlive-latex-recommended (>= 2016.20170123-2); however:
  Package texlive-latex-recommended is not configured yet.
 texlive-latex-extra depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures-doc:
 texlive-pictures-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-pictures-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of prosper:
 prosper depends on texlive-latex-base; however:
  Package texlive-latex-base is not configured yet.
 prosper depends on texlive-pstricks; however:
  Package texlive-pstricks is not configured yet.
 prosper depends on texlive-latex-recommended; however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package prosper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jdk-headless:amd64:
 openjdk-8-jdk-headless:amd64 depends on openjdk-8-jre-headless (= 8u121-b13-3); however:
  Package openjdk-8-jre-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jdk-headless:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php7.0:
 libapache2-mod-php7.0 depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.
 libapache2-mod-php7.0 depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.

dpkg: error processing package libapache2-mod-php7.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jdk:amd64:
 openjdk-8-jdk:amd64 depends on openjdk-8-jdk-headless (= 8u121-b13-3); however:
  Package openjdk-8-jdk-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jdk:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pstricks-doc:
 texlive-pstricks-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-pstricks-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-pictures:
 texlive-pictures depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.
 texlive-pictures depends on texlive-latex-recommended (>= 2016.20170123-2); however:
  Package texlive-latex-recommended is not configured yet.

dpkg: error processing package texlive-pictures (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-mcrypt:
 php7.0-mcrypt depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-mcrypt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-cli:
 php7.0-cli depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.
 php7.0-cli depends on php7.0-opcache; however:
  Package php7.0-opcache is not configured yet.
 php7.0-cli depends on php7.0-readline; however:
  Package php7.0-readline is not configured yet.

dpkg: error processing package php7.0-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-font-utils:
 texlive-font-utils depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-font-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-latex-extra-doc:
 texlive-latex-extra-doc depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-latex-extra-doc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-amd64:
 linux-image-amd64 depends on linux-image-4.9.0-kali1-amd64; however:
  Package linux-image-4.9.0-kali1-amd64 is not configured yet.

dpkg: error processing package linux-image-amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-8-jre:amd64:
 openjdk-8-jre:amd64 depends on openjdk-8-jre-headless (= 8u121-b13-3); however:
  Package openjdk-8-jre-headless:amd64 is not configured yet.

dpkg: error processing package openjdk-8-jre:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-sqlite3:
 php7.0-sqlite3 depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-sqlite3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php7.0-json:
 php7.0-json depends on php7.0-common (= 7.0.15-1); however:
  Package php7.0-common is not configured yet.

dpkg: error processing package php7.0-json (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of texlive-generic-extra:
 texlive-generic-extra depends on texlive-base (>= 2016.20170123-2); however:
  Package texlive-base is not configured yet.

dpkg: error processing package texlive-generic-extra (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.127) ...
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 samba-common
 smbclient
 texlive-base
 texlive-latex-recommended-doc
 texlive-fonts-recommended-doc
 samba
 php7.0-common
 texlive-fonts-recommended
 samba-common-bin
 texlive-generic-recommended
 texlive-latex-base
 texlive-latex-base-doc
 linux-image-4.9.0-kali1-amd64
 openjdk-8-jre-headless:amd64
 php7.0-mysql
 texlive-pstricks
 texlive-latex-recommended
 texlive-extra-utils
 php7.0-ldap
 php7.0-readline
 php7.0-opcache
 texlive-latex-extra
 texlive-pictures-doc
 prosper
 openjdk-8-jdk-headless:amd64
 libapache2-mod-php7.0
 openjdk-8-jdk:amd64
 texlive-pstricks-doc
 texlive-pictures
 php7.0-mcrypt
 php7.0-cli
 texlive-font-utils
 texlive-latex-extra-doc
 linux-image-amd64
 openjdk-8-jre:amd64
 php7.0-sqlite3
 php7.0-json
 texlive-generic-extra
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kali:~# 


```

---

### Post by kniightmaare on 2017-02-15
is there a way to reinstall kali with a downloaded iso without having to make a bootable, sorta like win 8/10 where u can download and then run the installer, id like to just start fresh on my system but as i stated i cannot create bootable even with dd command becuase all it dose is just lock the drive to read only mode and not even chmod 777 or a few other code can change it, but i managed to get around it by sticking my sd into my rooted android and formating it, but my reg usb thumbs i had to toss because the "NULL" lol ty all for the reply also

---

### Post by termibuntu on 2017-02-15
hi. you need to reinstall the os. there might have been a large interuption. if you try to reinstall it, see what it says. and no. you have to make a bootable disk or usb.

---

### Post by steeldriver on 2017-02-15
> **kniightmaare said:**
> ```
awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
```

gives me, 

```
root@kali:~# awk: symbol lookup error: /usr/local/lib/libreadline.so.7: undefined symbol: UP
bash: awk:: command not found

```

I **wasn't** suggesting that you should try to **run the error message** - and the error from doing **that **is because there is no such command as `awk:` (with a colon at the end) - that doesn't mean you need to reinstall `awk`, which is clearly present on your system but is broken because you have a non-system version of the libreadline.so.7 library installed in /usr/local/lib/

Really Kali may not be the right distribution for you since it is does require a bit of Linux experience

---

### Post by kniightmaare on 2017-02-22
well , when i learn something i jump head first and teach myself the ropes for the most part. its how ive always done things and in only being on this system for just over a week and 1/2 now, i think ive "self" taught myself quite a bit, from installing the os, with no network, and not havin access to anther computer, to fixing the sources.lists and firguring out how to get it connecting finding the right sources, ect, now i have gotten the list alot smaller but im still having a bit of troube with these. 
i would appreciate some encouragement and positive help, telling me this might not be the os for me is negative and in which case , ty for your time and advice it is duly noted, but i like kali, im learning this os, and thats the end of it :) 
no disrespect intended i say that with the utmost respect. =] 
so here is what its reading now.
 ```
Errors were encountered while processing:
 samba-common
 smbclient
 texlive-base
 texlive-latex-recommended-doc
 texlive-fonts-recommended-doc
 samba
 php7.0-common
 texlive-fonts-recommended
 samba-common-bin
 texlive-generic-recommended
 texlive-latex-base
 texlive-latex-base-doc
 linux-image-4.9.0-kali1-amd64
 openjdk-8-jre-headless:amd64
 php7.0-mysql
 texlive-pstricks
 texlive-latex-recommended
 texlive-extra-utils
 php7.0-ldap
 php7.0-readline
 php7.0-opcache
 texlive-latex-extra
 texlive-pictures-doc
 prosper
 openjdk-8-jdk-headless:amd64
 libapache2-mod-php7.0
 openjdk-8-jdk:amd64
 texlive-pstricks-doc
 texlive-pictures
 php7.0-mcrypt
 php7.0-cli
 texlive-font-utils
 texlive-latex-extra-doc
 linux-image-amd64
 openjdk-8-jre:amd64
 php7.0-sqlite3
 php7.0-json
 texlive-generic-extra
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kali:~# 


```
i would really like to save the os ive brought her  back 3 times now from brokeness lol. we have a "bond" i aint givin up on her just yet so any possiblilty for 'not' reinstalling the os, i dont care if it takes work , i dont mind learning, infact i enjoy it, and i like work so bring it on lol =] again ty for any and all help. i really mean in.

---

### Post by steeldriver on 2017-02-22
Well... what did you install (possibly by compiling from source, or manually unpacking a binary archive) that caused /usr/local/lib to contain libreadline.so.7 ?

---

