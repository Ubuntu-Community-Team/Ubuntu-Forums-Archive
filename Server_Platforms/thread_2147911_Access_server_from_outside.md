---
title: "Access server from outside"
date: 2013-05-23
forum: Server Platforms
---

### Post by Tine1990 on 2013-05-23
[COLOR=#000000]Hi everybody,[/COLOR]

[COLOR=#000000]I have a task for school to work with technology, but I have really no experience in IT.[/COLOR]

[COLOR=#000000]I have already installed Virtualbox with Ubuntu12.04.[/COLOR]
[COLOR=#000000]Then I have installed Apache2 and Tomcat7 on Ubuntu12.04.[/COLOR]
[COLOR=#000000]I can access Apache2 from [/COLOR][http://localhost]("http://localhost/")[COLOR=#000000] and Tomcat7 from [/COLOR][http://localhost:8080]("http://localhost:8080/")[COLOR=#000000].[/COLOR]

[COLOR=#000000]Now my question is: how can I access these servers from outside?[/COLOR]

[COLOR=#000000]Greetz,[/COLOR]
[COLOR=#000000]Tine[/COLOR]

[COLOR=#000000]P.S.: Sorry for my bad English...[/COLOR]

---

### Post by Tine1990 on 2013-05-23
[COLOR=#000000][COLOR=#000000]Hi everybody,[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]I have a task for school to work with technology, but I have really no experience in IT.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]I have already installed Virtualbox with Ubuntu12.04.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Then I have installed Apache2 and Tomcat7 on Ubuntu12.04.[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]I can access Apache2 from [/COLOR][/COLOR][http://localhost]("http://localhost/")[COLOR=#000000][COLOR=#000000] and Tomcat7 from [/COLOR][/COLOR][http://localhost:8080]("http://localhost:8080/")[COLOR=#000000][COLOR=#000000].[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Now my question is: how can I access these servers from outside?[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Greetz,[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]Tine[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]P.S.: Sorry for my bad English...[/COLOR][/COLOR]

---

### Post by dino99 on 2013-05-23
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

get more by googling around "ubuntu remote server access"

---

### Post by prodigy_ on 2013-05-23
Mostly this depends on whether your server is behind a router (in which case you'll need to set up port forwarding on the router) or directly connected to the Internet.

Also if you don't have a static IP, you'll need to use [Dynamic DNS](https://help.ubuntu.com/community/DynamicDNS).

---

### Post by linuxtechguy on 2013-05-23
Does your server have an internet routeable ip? If not you would have to port forward the connections through your router.

---

### Post by Tine1990 on 2013-05-23
Hi linuxtechguy,

I have no idea. Is there a way to check that my server has an [COLOR=#000000]internet routeable ip? Maybe with a command in command-line?

Thanks,
Tine[/COLOR]

---

### Post by prodigy_ on 2013-05-23
```
ip addr show # lists IP addresses for all interfaces
ip route show # outputs IPv4 routing table 
```

---

### Post by Tine1990 on 2013-05-23
The first code gives me:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 08:00:27:67:5c:40 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global eth0
    inet6 fe80::a00:27ff:fe67:5c40/64 scope link 
       valid_lft forever preferred_lft forever

The second code gives me:

10.0.2.0/24 dev eth0  proto kernel  scope link  src 10.0.2.15  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000 

I don't know how to interpret it...

---

### Post by prodigy_ on 2013-05-23
> **Tine1990 said:**
> The second code gives me:

10.0.2.0/24 dev eth0  proto kernel  scope link  src 10.0.2.15  metric 1 
169.254.0.0/16 dev eth0  scope link  metric 1000
No default route? Then you probably don't have Internet access at all on that machine. You said it was a VM. How did you configure networking for it? I'm not familiar with VirtualBox settings but on VMWare I usually choose "Bridged: Connected directly to the physical network".

---

### Post by steeldriver on 2013-05-23
... it's similar in VirtualBox, you can go to the 'Devices' menu, then select 'Network Adapters...' and changed from 'NAT' to 'Bridged Adapter' using the 'Attached to: ' dropdown 

The VM will then get an IP in the same range as the host and can be connected to from other hosts in the LAN. To go outside the LAN, you would then need to do the port forwarding + static (or dynamically reconfigured) external IP

---

### Post by Tine1990 on 2013-05-23
Oké, I changed from 'NAT' to 'Bridged Adapter'.
But now, how do I do the port [COLOR=#000000]forwarding + static (or dynamically reconfigured) external IP?
[/COLOR]

---

### Post by prodigy_ on 2013-05-23
[http://www.noip.com/support/faq/frequently-asked-questions/](http://www.noip.com/support/faq/frequently-asked-questions/)
[http://www.noip.com/personal/](http://www.noip.com/personal/)

---

### Post by EmmEight on 2013-05-23
Tine1990

You need your server's inside IP address to never change. Type this command

```
ifconfig
```

you should see something like this

eth0      Link encap:Ethernet  HWaddr 00:0c:f1:ad:e7:b6  
          inet addr:**[COLOR=#ff0000]10.1.1.101[/COLOR]**  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fead:e7b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35277 errors:0 dropped:2 overruns:0 frame:0
          TX packets:26939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37262851 (37.2 MB)  TX bytes:4021421 (4.0 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400 (400.0 B)  TX bytes:400 (400.0 B)

The red is what you should use for your internal IP address.

Go into your network settings and enter the following.

Static IP - **[COLOR=#ff0000]10.1.1.101[/COLOR]**
Subnet Mask - 255.255.255.0
Gateway - **[COLOR=#ff0000]10.1.1.1[/COLOR]**

Obviously you will want to change the values in red to whatever values you work for your network. Those are just commonly used values, I think yours was10.0.2.15 or something similar

When you enter your Gateway address, simply change the last octect to a 1

IP Address XX.XX.XX.XX would have the gateway of XX.XX.XX.1

Once you have that set up report back and we will move on to the next step.

When you report back, please include what IP address you are using in reality, and we will move forward with that.

---

