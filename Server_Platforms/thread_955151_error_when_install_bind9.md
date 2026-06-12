---
title: "error when install bind9"
date: 2008-10-21
forum: Server Platforms
---

### Post by 4engine on 2008-10-21
root@89-124-243-223:/usr/src# sudo apt-get install bind9
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  bind9-doc dnsutils resolvconf
The following NEW packages will be installed:
  bind9
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/268kB of archives.
After this operation, 762kB of additional disk space will be used.
Selecting previously deselected package bind9.
(Reading database ... 47396 files and directories currently installed.)
Unpacking bind9 (from .../bind9_1%3a9.4.2-10ubuntu0.1_i386.deb) ...
Setting up bind9 (1:9.4.2-10ubuntu0.1) ...
wrote key file "/etc/bind/rndc.key"
ls: cannot access /sys/module/apparmor: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
$Loading AppArmor module: Failed.
invoke-rc.d: initscript apparmor, action "force-reload" failed.
 * Starting domain name service... bind                                         named: capset failed: Operation not permitted: please ensure that the capset kernel module is loaded.  see insmod(8)
                                                                         [fail]

how can I fix it?

---

### Post by 4engine on 2008-10-22
where is the answer?

---

