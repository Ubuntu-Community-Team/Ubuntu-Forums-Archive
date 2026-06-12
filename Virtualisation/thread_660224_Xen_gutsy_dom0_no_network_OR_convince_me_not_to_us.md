---
title: "Xen gutsy dom0 no network OR convince me not to use Xen"
date: 2008-01-06
forum: Virtualisation
---

### Post by bxgrant on 2008-01-06
I have invested a lot in xen on ubuntu gutsy and am totally demoralized since I still can't get a network working in dom0 after turning on the xen bridge.  I can't ping out to anything including the gateway.

I used these tutorials to install xen on ubuntu using LVM:
[http://www.eadz.co.nz/blog/article/xen-gutsy.html](http://www.eadz.co.nz/blog/article/xen-gutsy.html)
[http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories](http://www.howtoforge.com/ubuntu-7.10-server-install-xen-from-ubuntu-repositories)

I have looked at [http://ubuntuforums.org/showthread.php?t=535309](http://ubuntuforums.org/showthread.php?t=535309).  I have thus added
   
```
up ethtool -K eth0 tx off
```

at the bottom of /etc/network/interfaces.  I have only one interface and it looks like this:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
```

I have read this: [https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631](https://bugs.launchpad.net/ubuntu/+source/xen-3.1/+bug/144631)

but I'm not even trying to create domUs yet.  I just want my network to work first on dom0.  If I execute

```
/etc/xen/scripts/network-bridge stop
```

everything works and I can ping everything again.

ANY ideas of how I've failed to follow instructions correctly would be welcome.  

OR convince me that there's a better virtualization technology that will allow me to use gutsy as the host and have two gutsy domUs that get the best possible performance for my dual core server.  I will be using this as a java application server platform and so performance matters.

Best,

bxgrant

---

### Post by theharshone on 2008-01-07
have you tried VirtualBox? installation is easy and performance is great

---

