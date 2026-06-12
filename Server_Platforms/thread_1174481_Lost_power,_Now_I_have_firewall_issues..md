---
title: "Lost power, Now I have firewall issues."
date: 2009-05-31
forum: Server Platforms
---

### Post by mistapotta on 2009-05-31
I run 8.04 LTS Server on my box, with LAMP.

I lost power Friday evening, and found out my uninterruptable power supply doesn't.  

Now I can't ssh onto this box, view pages from its web server, access CUPS, file sharing, incoming mail, what have you.  I'm pretty sure it's a firewall issue, but I've tried restarting the appropriate services (apache2, cupsys, postfix, nfs-kernel-server, portmap) to no avail.

I can view pages locally/receive e-mail locally from this machine, and have access to the outside internet (I'm posting from the machine as we speak.)  

Any ideas what I can do to remedy this server issue?

Thanks in advance,
TDP.

---

### Post by regala on 2009-05-31
> **mistapotta said:**
> I run 8.04 LTS Server on my box, with LAMP.

I lost power Friday evening, and found out my uninterruptable power supply doesn't.  

Now I can't ssh onto this box, view pages from its web server, access CUPS, file sharing, incoming mail, what have you.  I'm pretty sure it's a firewall issue, but I've tried restarting the appropriate services (apache2, cupsys, postfix, nfs-kernel-server, portmap) to no avail.

I can view pages locally/receive e-mail locally from this machine, and have access to the outside internet (I'm posting from the machine as we speak.)  

Any ideas what I can do to remedy this server issue?

Thanks in advance,
TDP.

dig into the logs, /var/log/*

---

### Post by mistapotta on 2009-05-31
Any particular log you had in mind?  I've looked in several but no obvious clues yet.  Thanks!

---

### Post by HermanAB on 2009-05-31
Howdy,

Does the machine have one or two ethernet ports?  
Is it a two port firewall or do you use an external router/firewall?  What is the IP address, netmask and default route?
Are the other machines that you use to contact this one on the same subnet?
Are your IP addresses hard coded in /etc/hosts or do you use DNS?

Usually one can spot the source of the trouble by executing these three commands:
$ /sbin/ifconfig
$ cat /etc/resolv.conf
$ sudo route

---

### Post by mistapotta on 2009-05-31
Hi HermanAB,

One ethernet port.  I do use other machines (both wired and wireless) to access this server, but haven't been able to connect from them.  IP addresses are hard-coded in my hosts file. 192.168.1.26/255.255.255.0 for my network.

```
/sbin/ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:20:d6:af:36
          inet addr:192.168.1.25  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:20ff:fed6:af36/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:33565341 (32.0 MB)  TX bytes:6798503 (6.4 MB)

ham0      Link encap:Ethernet  HWaddr 00:ff:8e:4a:5e:8d
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:41 errors:0 dropped:0 overruns:0 frame:0
          TX packets:837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500
          RX bytes:8922 (8.7 KB)  TX bytes:273734 (267.3 KB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4115 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1502351 (1.4 MB)  TX bytes:1502351 (1.4 MB)
```

```
cat /etc/resolv.conf

search satx.rr.com
nameserver 24.93.41.127
nameserver 24.93.41.128
```

```
sudo route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

```
cat /etc/hosts

127.0.0.1       localhost
127.0.1.1       draal.BABCOM    draal

192.168.1.25    alma
192.168.1.26    draal
192.168.1.27    gkar
192.168.1.28    kosh
192.168.1.29    olpc

5.212.7.191     xo-OC-D8-DE
5.217.200.191   gkarh


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Let me know if you need anything else.

---

