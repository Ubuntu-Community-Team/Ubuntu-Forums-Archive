---
title: "Windows does not connect to running instance"
date: 2011-09-28
forum: Ubuntu Cloud and Juju
---

### Post by Günter on 2011-09-28
one maschine with UEC-installed incl. NC (UEC 11.04)
UEC complete updated and upgraded (isn't simple because of a hangup)
3 running instances of centos.5-3.x86-64
Hybridfox installed and showing this
local DHCP- Server renames elastic IP's in his local IP's
192.168.10.10->192.168.2.115
192.168.10.11->192.168.2.116
192.168.2.10->192.168.2.117

I am able to Ping 192.168.2.115 from NC account,
I am able to Ping 192.168.2.115 from Win7 PC
192.168.10.10 or 192.168.2.10 not pingable

I am able to start Putty with 192.168.2.115 and receive a login, but I don't know the username and password of this image.
(Puttygen used to build correct key.ppk)

if I use putty with option ssh --> connection timeout 
if I use RDP with tunneling ssh via Putty  --> connection timeout
if I use launch instance with corrected IP in Hybridfox  --> connection timeout

never see any GUI Desktop of my Privat Cloud

thursday back in office, please use simple english I'm not natural english speaker

any suggestion is helpful

---

### Post by lisati on 2011-09-30
Thread closed: please see my answer in [http://ubuntuforums.org/showthread.php?t=1852414](http://ubuntuforums.org/showthread.php?t=1852414)

---

