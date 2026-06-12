---
title: "Network is not responding"
date: 2008-08-07
forum: Server Platforms
---

### Post by anindya23 on 2008-08-07
hello,
      i am facing a problem during configuration networking in Ubuntu Server Edition 8.04.

      after completing server installation i configured networking using "sudo vi/etc/network/interfaces" command. there i configured ip address,netmask,gateway,network and broadcast. i have 2 NIC card.i configured eth0 for real IP and eth1 for local network.when i execute "ifconfig" command, it shows both eth0 and eth1 configuration.how can i check my network configuration is perfect?i ping [www.google.com.but](www.google.com.but) it didn't response.i cant find what i made mistake during network configuration.

    this server is acting as a web server that can be accessed from outer world and the server is also connected to the local network where others computers r running on windows.


     while installing Ubuntu Server Edition, i installed LAMP.
If my network configuration is perfect then the browser of other pc,connected to the network,shows me the Apache page if i enter [http://ipaddress/](http://ipaddress/)

---

### Post by cdtech on 2008-08-07
Did you set up your "/etc/resolv.conf" file? Also, are you running a firewall?

---

### Post by hyper_ch on 2008-08-07
> **cdtech said:**
> Also, are you running a firewall?

A firewall runs by default on *buntu

---

### Post by cdtech on 2008-08-07
> **hyper_ch said:**
> A firewall runs by default on *buntu

Let me rephrase; Are you running a third party firewall.......

---

### Post by anindya23 on 2008-08-07
no,i didn't configure "/etc/resolv.conf" and firewall also.

---

### Post by hyper_ch on 2008-08-07
if you want to use dns you need to add a nameserver in /etc/resolv.conf. as with a static IP it just won't automatically get one like with dhcp.

---

### Post by anindya23 on 2008-08-07
Why, i need this. i just want to configure my network and want to access using ipaddress.

---

### Post by anindya23 on 2008-08-07
is there anyone who can help me?i am really getting bored of this problem.

---

### Post by hyper_ch on 2008-08-07
did you read my last posting in here?

---

### Post by windependence on 2008-08-07
> **anindya23 said:**
> is there anyone who can help me?i am really getting bored of this problem.

Well that probably isn't the way to get it solved but I will help you of you want.

Can you post the ouput of your ifconfig -a


-Tim

---

### Post by cdtech on 2008-08-07
The file "/etc/resolv.conf" should have the nameservers listed from your ISP. Mine looks like this:
```
search hsd1.xx.xxxxxx.xxx.
nameserver xx.xx.xx.xxx
nameserver xx.xx.xx.xxx
nameserver xx.xx.xx.xxx
```
It's not windows where it is automatically setup for you through dhcp.

---

### Post by anindya23 on 2008-08-07
eth0	Link encap:Ethernet	HWaddr 00:04:23:46:dd:e3
	inet addr:203.76.125.82 Bcast:203.76.125.255 Mask:255.255.255.0
	inet6 addr: fe80::204:23ff:fe46:dde3/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:192 errors:0 dropped:0 overruns:0 frame:0
	TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:100
	RX bytes:12712 (12.4 KB) TX bytes:4012 (3.9KB)
	Base address:0x7000 Memory:f0200000-f0220000

eth1	Link encap:Ethernet	HWaddr 00:04:23:46:e0:db
	inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
	inet6 addr: fe80::204:23ff:fe46:e0db/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:84 errors:0 dropped:0 overruns:0 frame:0
	TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:8611 (8.4 KB) TX bytes:3212 (3.1KB)

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Link
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:4 errors:0 dropped:0 overruns:0 frame:0
	TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:200 (200 B) TX bytes:200 (200 B)

---

### Post by anindya23 on 2008-08-07
do i have to edit /etc/hosts?if so,what i have to insert and update?

---

### Post by windependence on 2008-08-07
> **anindya23 said:**
> eth0	Link encap:Ethernet	HWaddr 00:04:23:46:dd:e3
	inet addr:203.76.125.82 Bcast:203.76.125.255 Mask:255.255.255.0
	inet6 addr: fe80::204:23ff:fe46:dde3/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:192 errors:0 dropped:0 overruns:0 frame:0
	TX packets:37 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:100
	RX bytes:12712 (12.4 KB) TX bytes:4012 (3.9KB)
	Base address:0x7000 Memory:f0200000-f0220000

eth1	Link encap:Ethernet	HWaddr 00:04:23:46:e0:db
	inet addr:192.168.1.3 Bcast:192.168.1.255 Mask:255.255.255.0
	inet6 addr: fe80::204:23ff:fe46:e0db/64 Scope:Link
	UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
	RX packets:84 errors:0 dropped:0 overruns:0 frame:0
	TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes:8611 (8.4 KB) TX bytes:3212 (3.1KB)

lo	Link encap:Local Loopback
	inet addr:127.0.0.1 Mask:255.0.0.0
	inet6 addr: ::1/128 Scope:Link
	UP LOOPBACK RUNNING MTU:16436 Metric:1
	RX packets:4 errors:0 dropped:0 overruns:0 frame:0
	TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes:200 (200 B) TX bytes:200 (200 B)

OK, wanted to make sure your interfaces were UP. What do you have the gateway set for on eth1? What is the internal address of your router?

-Tim

---

### Post by anindya23 on 2008-08-09
Gateway set for eth1 203.76.125.81.
i cant understand the internal address of router.

---

### Post by MobiusNZ on 2008-08-09
Unless your machine is on an ISP's network it is quite unlikely you'll have a public IP for your machine. Generally you'll need to have the IP address set to the same network as the router (gateway) for your network.

Maybe you could explain your network topology a bit better for us to help you - like describe the devices each network card is connected to...

---

