---
title: "how can I connect internet from VirtualBox"
date: 2009-12-31
forum: Virtualisation
---

### Post by chuina on 2009-12-31
Helo all, happy new year!:)

Never use any type of Virtualization before.

I install VirtualBox in my Karmic and inside that VirtualBox i install RHEL5 (also willing to add few more Linux)

But I don't know and can't connect to the Internet from that 
Virtual RHEL5.

In karmic i use an EDGE modem (which only detectable by Karmic)
with **gnome-ppp**

Now i want to use internet in VirtualBox.
So, please guide me.

Thanks.

---

### Post by mkvnmtr on 2009-12-31
I am probably not the one to help but I just installed Virtual box today. Right away I got Puppy linux working and used their connect app to connect to the internet. Thus I would assume you can connect the same way nyou would if you were installed normally.

---

### Post by chuina on 2009-12-31
thanks.

> connect app to connect to the internetmake me more baffled. 


> installed normallyno sir, i only install the text mode terminals. no gnome/kde.

also may be your Puppy detect your connection by default.

but for me the option to choose modem is limited.
this usb-modem is only brand modem in our local market !

At least thanks Karmic can detect it.:P

what now ?

---

### Post by inclusivedisjunction on 2010-01-01
Make sure you have a network adapter enabled in VirtualBox. Also, since you are using a text-mode system, what are you using to test internet connectivity? Are you pinging an external website, using a text-mode browser, etc...?

---

### Post by chuina on 2010-01-01
sorry for late.

i posting some command result i've learned from this site.

These are from my PC:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:34:3f:ef  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2156 (2.1 KB)  TX bytes:2156 (2.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.65.38.229  P-t-P:10.0.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:494 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:328778 (328.7 KB)  TX bytes:60285 (60.2 KB)

---------------------------------------------------------------------------------------

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.1        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```attached  image from virtualbox which shows the network adapter connected.

i try to ping [www.google.com](www.google.com), [www.ubuntu.com](www.ubuntu.com) result unknown host.
also i can't ping my host PC and vise-versa.

thanks

---

### Post by chuina on 2010-01-02
After I run in both OS this the following status arrived:

```
 route add default 192.168.10.254 dev eth0
```Here is my current status:

for pinging:
```
ping 
Host PC --------> VirtualBox    [ok]
VirtualBox-----> Host PC        [ok]
```for ssh login:

```
Host PC ---------> VirtualBox   [ok]
VirtualBox -----> Host PC       [failed]
```

Internet Connection:
```
VirtualBox -----> Internet       [failed]
```Also,
While running and connecting VirtualBox my Host PC can't connect to the 
Internet !

I've tried to add another gateway but failed.

Any suggestion will be great. 
thanks.

---

### Post by act28 on 2010-01-04
What type of network adapter attachment are you using?
NAT
bridged
internal
host-only

You may need to bridge the connection between the guest and the host.

---

### Post by chuina on 2010-01-04
@ act28: "What type of network adapter attachment are you using?"

Two type of adapter are connected: host-only,nat.
this image shows they are connected:


Thanks

---

### Post by chuina on 2010-01-20
Tuning to NAT's ip by dhcp I'm connecting to the internet.
Thanks for the help.

---

### Post by airtonix on 2010-04-29
> **chuina said:**
> Tuning to NAT's ip by dhcp I'm connecting to the internet.
Thanks for the help.

This hardly explains how you solved it.

You need to provide step by step instructions (using only language you see on the interface) for others who might need to solve this and you last comment is extremely vague and unhelpful.

---

