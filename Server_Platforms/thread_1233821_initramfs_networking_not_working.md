---
title: "initramfs networking not working"
date: 2009-08-07
forum: Server Platforms
---

### Post by DWGS on 2009-08-07
Hi,
I'm trying to unlock my encrypted root partition over ssh using dropbear.
But I can't seem to get my networking up in initramfs - I get the error messages:

ipconfig: eth0: SIOCGIFINDEX: No such device
ipconfig: no devices to configure
/scripts/init-premount/dropbear: .: line 32: can't open /tmp/net-eth0.conf

if I then unlock my root partiton and continue to boot I have eth0 up and running.

I have the kernel parameter ip set:
ip=:::::eth0:dhcp

I'm using ubuntu 9.04 64bit.
does anyone have an idea what I'm doing wrong?

Greetings
DWGS

---

### Post by mrsteveman1 on 2009-11-18
In case anyone stumbles upon this (or OP is still watching), this is a known bug already reported in launchpad for quite some time.

[https://bugs.launchpad.net/ubuntu/+source/dropbear/+bug/363958](https://bugs.launchpad.net/ubuntu/+source/dropbear/+bug/363958)

A fix is proposed in the comments but i have not gotten it to work yet.

---

