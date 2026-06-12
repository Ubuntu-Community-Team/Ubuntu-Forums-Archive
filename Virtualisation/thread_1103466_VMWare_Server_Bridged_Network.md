---
title: "VMWare Server Bridged Network"
date: 2009-03-22
forum: Virtualisation
---

### Post by xavierbutt on 2009-03-22
I found a treasure of a post in the archive that explains a rather obscure way to enable bridged networking between a Windows host and an Ubuntu guest. I thought I would repost since it helped me solve my problem with W2K3 host and Ubuntu 8.04 Server guest

[http://ubuntuforums.org/showthread.php?t=223093](http://ubuntuforums.org/showthread.php?t=223093)

> Bridged vmware connections need a mac address of the form 00:50:56:XX:XX:XX, and you can set this in your virtual machine's .vmx file. you'll need to remove all the lines that start with ethernet0(or whatever interface you'll be using) and replace them with something like this.

ethernet0.addressType = "static"
ethernet0.address = "00:50:56:XX:XX:XX"

I reconfigured the vmx by changing the addressType to static, removing the generatedAddress for ethernet0, replaced it with ethernet0.address like the one above, started up the vm. Still no internet connection.

Running 'dmesg | grep eth0' I noticed Ubuntu had assigned eth0 to a new network node of eth1. I edited /etc/networking/interfaces and changed my static node from eth0 to eth1, ran /etc/init.d/networking restart. I now have a bridged connection.

---

