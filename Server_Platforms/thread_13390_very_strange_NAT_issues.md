---
title: "very strange NAT issues"
date: 2005-01-31
forum: Server Platforms
---

### Post by adeh on 2005-01-31
Hello, 

This is a longshot, bu tif anyone can help I will be grateful.

I have Ubuntu AMD 64 running on a hand-built rackserver (AMD64 3000, 2 NICs) for a client. 

It's running tomcat through SSL and ssh so i can get in and tweak stuff. We have it sitting behind a Netgear broadband router with firewall and NAT enabled. On the firewall/router I open port 443 and 22, for https and ssh, respectively. 

For some time, this setup seemed to be working fine. However, lately, it all has come crashing down.

The problem is that every time the network interfaces are initialized, after some time, it automatically shuts down and ubuntu starts dropping packets from the router. Before the crash, everyting works fine. After the crash, I have no problem connecting from within the internal network, on either subnetworks. From the outside, timeouts only.

If I restart either the router/firewall or the web-server (or i suspect just bring the interface down and back up) then everything is happy again. 

](*,)

Has anyone run into anything like this before, or do you know what might be happening?

Thanks,
Adeh

---

### Post by adeh on 2005-01-31
Hi , 

Regarding my earlier post, I just want to clarify that I know that most likely no one can solve my problem directly. I am just in the discovery phase and I am trying to rule out possible causes.

Is there any possible way that something in the ubuntu IP stack makes packets from a certian IP (the router) get dropped if they come too often (maybe some kind of over-enthusiastic intrusion detection??)

At the moment this is what i am thinking and I just hope someone can tell me that I am crazy.

I am using IP tables to map external port 443 to 8443, so that I can run tomcat under tomat for safety. This is the only firewall type thing that I messed with in an otherwise clean installation of ubuntu AMD64.

Thanks,
Adeh

---

### Post by Rottweiler on 2005-02-02
Anything in the logs leading up to the problem?

---

### Post by adeh on 2005-04-14
Hi Sorry that I have seemed to abandon this thread, but maybe someone somewhere can help. Here's what I have done:

1. Verified the Netgear Router works by hooking a different computer up to a differnet port.

2. switched ethernet cards to a more reliable one

3. upgraded to hoary

4. checked the logs, found nothing in syslog, dmesg, or messages. (is there somethwhere else I should be checking?)

5. tried and tested for over 4 months to find some sort o pattern, failed...

The connection just comes and goes as it pleases. At first it seemed that it would go down, then resetting the router would fix it, but now we have determined that that is not the case. after resetting the router, the connection does not come back as often as it does.  

Could it be something with Ubuntu/Linux or should I focus on the hardware? the router? 

Thanks for any suggestions.

---

### Post by dataw0lf on 2005-04-14
Could be cabling.. have you switched out your cat5e? (or cat6)

---

### Post by heimo on 2005-04-14
Hi!

I don't know if this is related, but I mention this anyway. Something similar happened to me today with my mail server. I run mail server at home and connect to it through squirrelmail from Internet. Today I was unable to see my mail server from outside, but when I came back to home, I was able to connect to it via SSH as if everything was working.

I was puzzled what was going on, but the */sbin/route -n* showed that it had lost default gateway! That makes sense - I can connect from lan, but not outside, because the returning packets can't get to net! Restarting networking helps of course. But what caused this problem? And is it related to what you're experiencing? I don't know.

---

### Post by adeh on 2005-04-18
Hi,

Thanks Heimo, I did mess around with that a lot, but right now the connection has settled down and I am pretty sure it is working. When the website is in-accessible from the outside, I can still get out.
Here's my route -n

it@apps:~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
it@apps:~ $

The 192.168.0.0 network is teh one connected to the router, while the 192.168.1.0 network is connected to the internal network (which houses the database server)

dataw0lf:
Just switched cables to a really nice storebought one... still no luck. 

I really appreciate you guys trying to help out. I still have a sinking feeling that it is something with the hardware... but it is so strange.

Thanks,
Adeh

---

### Post by diebels on 2005-04-21
[QUOTE=adeh]
```
it@apps:~ $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
it@apps:~ $

The 192.168.0.0 network is teh one connected to the router, while the 192.168.1.0 network is connected to the internal network (which houses the database server)
[/QUOTE]
All private addresses. What about the routing table and packet filtering at the router?

---

