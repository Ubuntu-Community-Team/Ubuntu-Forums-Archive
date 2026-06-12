---
title: "DHCP with Ununtu Server"
date: 2016-12-03
forum: Virtualisation
---

### Post by mikeybinec on 2016-12-03
Ugh.. I can't remember how to configure the system to get an ip address through dhcp. Right now, I'm getting that stupid
10.0.2.15 through virtual box.. I have centos also running and centos is configured running nmcli and or nmtui and does get an ip address in the
192.168.1.0 /24 network

I installed network manager but cant get it to launch.. /etc/sysconfig doesnt exist

someone point me in the right direction?

thanks

---

### Post by kpatz on 2016-12-03
Set the network adapter on the VM to bridged instead of NAT.  It's using DHCP but getting an IP from Virtualbox's virtual NAT router, hence the 10.x.x.x IP.

---

### Post by mikeybinec on 2016-12-03
YAAYY!!! Thanks Boss, I forgot all about that setting in VB.. 

Merry Xmas and thanks for your time

---

### Post by wildmanne39 on 2016-12-03
*Thread moved to **Virtualisation**.*

---

