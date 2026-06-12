---
title: "Gnome does not recognize my Ethernet card"
date: 2007-11-26
forum: Sun Sparc Users
---

### Post by roadruner on 2007-11-26
Experts,

I use Ubuntu  on Sparc Ultra60.
Now, with your help, Gnome starts at boot.
But in Gnome, my network card is not recognize : 
In the upper right, in front of the clock, I have 2 screen (network status) with an explanation mark.
If I click on it, I have : no network connection

But I have Internet (I use this installation to write this post)

But, I can't send an email with evolution because it doesn't see the network.

How could I correct this ?

Thanks in advance

---

### Post by roadruner on 2007-11-26
ifconfig gives :

```
eth0      Link encap:Ethernet  HWaddr 08:00:20:A2:B3:F0  
          inet addr:134.244.141.178  Bcast:134.244.141.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:20ff:fea2:b3f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286652 (279.9 KiB)  TX bytes:1628 (1.5 KiB)
          Interrupt:14 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12500 (12.2 KiB)  TX bytes:12500 (12.2 KiB)


```

and in /etc/network/interfaces, I have :

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0

```

---

### Post by netztier on 2007-11-26
> **roadruner said:**
> ifconfig gives :

```
eth0      Link encap:Ethernet  HWaddr 08:00:20:A2:B3:F0  
          inet addr:134.244.141.178  Bcast:134.244.141.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:20ff:fea2:b3f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1663 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:286652 (279.9 KiB)  TX bytes:1628 (1.5 KiB)
          Interrupt:14 Base address:0xb800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12500 (12.2 KiB)  TX bytes:12500 (12.2 KiB)


```

and in /etc/network/interfaces, I have :

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

auto eth0

```

This definitely looks like you have working ethernet. Seems that Gnome's NetworkManager can be cumbersome on Sparc:

[http://ubuntuforums.org/showthread.php?t=592728](http://ubuntuforums.org/showthread.php?t=592728)

Try removing packages network-manager and network-manager-gnome. 

regards

Marc

---

### Post by roadruner on 2007-11-26
thanks for your answer, but I've already tried this.
After uninstall these packages and after a reboot, I had no network (Its seems to be nomal because I uninstalled the network), so I installed these packages again, and the problem was the same.

Can we use something else instead of Gnome (like KDE) with Ubuntu ?

Thanks

---

### Post by jcastill on 2007-11-26
Yes you can use kubuntu or even xubuntu. The problem here is that the problem will be there too. When you uninstall those packages you are not uninstalling the network drivers, you are simply disabling the GUI configuration for the ethernet. When you uninstall via apt those packages and restart; when you type "ifconfig -a" what does it show?

---

