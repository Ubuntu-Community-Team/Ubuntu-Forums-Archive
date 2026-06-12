---
title: "Wired network disconnected, Ubuntu12.04LTS in VMWare player 4.0.2"
date: 2013-01-17
forum: Virtualisation
---

### Post by BillyFan on 2013-01-17
Hello,

I just installed a fresh ubuntu 12.04LTS 64bit (ubuntu-12.04.1-desktop-amd64.iso) in a VMware vm in windows 7 64bit yesterday.

For some reason, I need the network setting in vmware to be bridged rather than NAT.

The wired network worked fine when I just installed it.

My host ip was 192.168.1.7 and the Ubuntu guest ip was 192.168.1.15. Both assigned by DHCP.

But when I switched my laptop on today, the network just stopped working.

My host ip changed to 192.168.1.15 and the Ubuntu guest just can't get an ip from DHCP anymore.

I tried to manually assign ip to Ubuntu, but it didn't work either.

I changed the vmware networking from bridged to NAT. Wow, it worked fine. But as long as I changed it back from NAT to bridged, the network in Ubuntu is gone again.

I checked a previous post in this forum,
[http://ubuntuforums.org/showthread.php?t=2080478](http://ubuntuforums.org/showthread.php?t=2080478)
And I tried the disabling ipv6 as suggested in that post. It didn't work.

I googled "vmware ubuntu 12.04 wired network disconnected bridged network" but didn't got any working solutions.

The same thing happened too when I was installing Ubuntu server 12.04LTS 64bit before.

basically, the condition is:
installed ubuntu 12.04 in vmware, used bridged network.
wired network connection in ubuntu worked fine at first
but it suddenly stopped working after a host reboot.
it worked with NAT in vmware, but not bridget in vmware
and it doesn't work with either manually assign or DHCP auto assign  

Could anyone help me to get it work in bridged mode please ?

Thanks a lot

---

