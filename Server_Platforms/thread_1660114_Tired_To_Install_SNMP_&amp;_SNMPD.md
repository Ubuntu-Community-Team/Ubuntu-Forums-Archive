---
title: "Tired To Install SNMP &amp; SNMPD"
date: 2011-01-04
forum: Server Platforms
---

### Post by achoopani on 2011-01-04
Hi Dear Friends 
Happy New Year :KS
I Will To Make Project With Linux ,
I Choose Ubuntu For This Project
Im install ubunut server 9.10 , 10.10 for this and have so many problem
While Of Install SNMPD On Ubuntu Output this log:
[PHP]


root@ubuntu:~# apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libperl5.10 libsensors3 libsnmp-base libsnmp15 libsysfs2
Suggested packages:
  lm-sensors
The following NEW packages will be installed:
  libperl5.10 libsensors3 libsnmp-base libsnmp15 libsysfs2 snmp snmpd
0 upgraded, 7 newly installed, 0 to remove and 71 not upgraded.
Need to get 157kB/2,720kB of archives.
After this operation, 8,933kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/main snmp 5.4.1~dfsg-12ubuntu7 [157kB]
Fetched 157kB in 4s (34.2kB/s)
Preconfiguring packages ...
Selecting previously deselected package libperl5.10.
(Reading database ... 20260 files and directories currently installed.)
Unpacking libperl5.10 (from .../libperl5.10_5.10.0-24ubuntu4_i386.deb) ...
Selecting previously deselected package libsysfs2.
Unpacking libsysfs2 (from .../libsysfs2_2.1.0-5_i386.deb) ...
Selecting previously deselected package libsensors3.
Unpacking libsensors3 (from .../libsensors3_1%3a2.10.8-1_i386.deb) ...
Selecting previously deselected package libsnmp-base.
Unpacking libsnmp-base (from .../libsnmp-base_5.4.1~dfsg-12ubuntu7_all.deb) ...
Selecting previously deselected package libsnmp15.
Unpacking libsnmp15 (from .../libsnmp15_5.4.1~dfsg-12ubuntu7_i386.deb) ...
Selecting previously deselected package snmp.
Unpacking snmp (from .../snmp_5.4.1~dfsg-12ubuntu7_i386.deb) ...
Selecting previously deselected package snmpd.
Unpacking snmpd (from .../snmpd_5.4.1~dfsg-12ubuntu7_i386.deb) ...
Processing triggers for man-db ...
Setting up libperl5.10 (5.10.0-24ubuntu4) ...

Setting up libsysfs2 (2.1.0-5) ...

Setting up libsensors3 (1:2.10.8-1) ...
.udevdb or .udev presence implies active udev.  Aborting MAKEDEV invocation.

Setting up libsnmp-base (5.4.1~dfsg-12ubuntu7) ...
Setting up libsnmp15 (5.4.1~dfsg-12ubuntu7) ...

Setting up snmp (5.4.1~dfsg-12ubuntu7) ...
Setting up snmpd (5.4.1~dfsg-12ubuntu7) ...
update-rc.d: warning: snmpd stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)
 * Starting network management services:                                 [ OK ]

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

[/PHP]


The Problem is This Error 
[B]update-rc.d: warning: snmpd stop runlevel arguments (1) do not match LSB Default-Stop values (0 1 6)

Please Help Me To Fix This Problem 
I Need To SNMP For Graphing squid Traffic!!
If You Have A Suggest for Me Please Thread To this post ;):guitar:
[/B]

---

