---
title: "Ubuntu Server cannot connect outside LAN (but originally was able to)"
date: 2013-01-17
forum: Server Platforms
---

### Post by soundsfromsound on 2013-01-17
Hello.

I recently have installed Ubuntu Server 12.10 on my LAN here and it's working fine as far as within my home network, but I cannot connect to the web anymore.  I'm not sure what happened, but I was originally able to install applications, ping websites, etc but now I'm offline it seems.  I can ping websites but only when I use the IP address, fyi.  I can't figure it out because I was able to use the web no problem and recently it just stopped.  Did I mess up DNS or something?

Thank you for your help.  Here are some snippets:

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:0c:29:01:ca:22
          inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe01:ca22/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:643607 (643.6 KB)  TX bytes:1314518 (1.3 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5808 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1070212 (1.0 MB)  TX bytes:1070212 (1.0 MB)

```

route -n
```
ben@userver:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 192.168.1.13
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	dns-nameservers 8.8.8.8
```

---

### Post by papibe on 2013-01-17
Hi soundsfromsound.

Could you post the result of the following commands?
```
cat /etc/resolv.conf

nslookup ubuntuforum.org

dig ubuntu.com

ping -c3 192.168.1.1

tracepath ubuntu.com

```
Regards.

---

### Post by Warren Hill on 2013-01-17
This could be a problem with your router.

First we need to check that you can see you default gateway and the DNS server

```
ping -c5 192.168.1.1; ping -c5 8.8.8.8
```

Now in firefox what happens if you put 192.168.1.1 in the address box?
Many routers have a web page interface.  You may need to enter a password to get it

Finally in firefox what happens if you put 212.58.241.131 in the address box?
Does this open a web page (bbc web page)?

Not a fix but may give us a clue where to look next

---

### Post by soundsfromsound on 2013-01-19
Hi there,

Thank you all for your help.  I recently tried a simple reboot and for whatever reason the server is now 100% operational, including from outside the LAN.  Not sure what was the culprit but all is well now.  Thank you again!

sfs

---

### Post by Warren Hill on 2013-01-21
Glad to here all is fixed.  Please mark to question solved to close it.

If you don't know how see here
[http://ubuntuforums.org/showpost.php?p=4527051&postcount=6](http://ubuntuforums.org/showpost.php?p=4527051&postcount=6)

---

