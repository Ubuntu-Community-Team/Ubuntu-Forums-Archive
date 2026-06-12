---
title: "apache webserver not accessible"
date: 2010-05-21
forum: Server Platforms
---

### Post by rogtek on 2010-05-21
Hello everyone!

I am having a rather complicated problem with apache server and I am really stuck!

So here is my situation:
In my company we have a Win Server 2008 Standard as a PDC and Active Directory. 
We have also deployed an Ubuntu LAMP Server 8.04 LTS virtual machine through VirtualBox (Win Server as Host) and installed SugarCRM which works just fine.

The problem is that I can't view SugarCRM through my external static ip.
When I try to connect from inside my lan with ubuntu's internal static ip at port 81, I don't have any problem.
When I try (from my lan again) through my public static ip at port 81, I can't connect. The same applies when I try from an external network.
I am using port 81 for apache because IIS is in 80.
I have made all the required settings in my router to allow incoming traffic.

What am I doing wrong? :confused:

---

### Post by cdenley on 2010-05-21
> **rogtek said:**
> Hello everyone!

I am having a rather complicated problem with apache server and I am really stuck!

So here is my situation:
In my company we have a Win Server 2008 Standard as a PDC and Active Directory. 
We have also deployed an Ubuntu LAMP Server 8.04 LTS virtual machine through VirtualBox (Win Server as Host) and installed SugarCRM which works just fine.

The problem is that I can't view SugarCRM through my external static ip.
When I try to connect from inside my lan with ubuntu's internal static ip at port 81, I don't have any problem.
When I try (from my lan again) through my public static ip at port 81, I can't connect. The same applies when I try from an external network.
I am using port 81 for apache because IIS is in 80.
I have made all the required settings in my router to allow incoming traffic.

What am I doing wrong? :confused:

Apache doesn't care where the connections are coming from. It will accept TCP connections from anywhere if it is listening on that interface. If you cannot establish a TCP connection, it is because it cannot reach apache. Either your NAT router isn't forwarding the traffic, or some firewall is filtering it.

---

### Post by evaristegalois on 2010-05-21
I am having precisely the same problem, although on a simple home PC. Here are things to check:

(i) Settings on the router. For me, I had to change Private IP in the Virtual Servers List from 0.0.0.0 to to my static LAN IP (192.168.0.150)

(ii) Filters on the router. There may be a filter on the router not letting traffic on 80 or 81 get through.

(iii) Your ISP may be blocking a port. You can test your port by using this service: [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2) (ShieldsUP).

None of this solved my problem. Just as in your case,

[http://192.168.0.150](http://192.168.0.150) works perfectly on the local machine, but

[http://myname.homelinux.org](http://myname.homelinux.org) or [http://--my](http://--my) temporary IP address--

don't work. Does anybody have further ideas how to isolate the problem?

---

### Post by cdenley on 2010-05-21
> **evaristegalois said:**
> 
[http://192.168.0.150](http://192.168.0.150) works perfectly on the local machine, but

[http://myname.homelinux.org](http://myname.homelinux.org) or [http://--my](http://--my) temporary IP address--

don't work. Does anybody have further ideas how to isolate the problem?

Did you try from outside your network? Many routers will not "port forward" for connections originating within your LAN. This isn't the problem for rogtek, though, since he said he tried and failed to connect from an external network. If shieldsup says your port is open, then the server can be accessed externally.

---

### Post by rogtek on 2010-05-21
Thank you for your replies.

I did the ShieldsUp test and showed that port 81 is open.

I have also forward port 80 to my Win PDC and works just fine. When I do the same procedure for port 81 with Ubuntu server I can't connect!

Could it be a DNS problem? In my network topology the internal DNS server is the Windows PDC server.

---

### Post by cdenley on 2010-05-21
> **rogtek said:**
> 
When I try (from my lan again) through my public static ip at port 81, I can't connect. The same applies when I try from an external network.

> **rogtek said:**
> I did the ShieldsUp test and showed that port 81 is open.

This sounds like an inconsistency. ShieldsUp can connect on port 81 from their external network, but you fail to connect from another external network? You're connecting to the same IP as ShieldsUp is, right?

---

### Post by rogtek on 2010-05-21
Yes I use the same public ip.

If I call my public ip in port 80 I can connect to Win Server, but I can' when I use my ip in port 81.

I have changed apache listening port to 8080, but still no luck. Also the log file does not show any record of connection (just like you said cdenley the request never passes to apache).

If the request is forwarded directly to the given ip then the problem is with my router.

---

### Post by cdenley on 2010-05-21
> **rogtek said:**
> Yes I use the same public ip.

If I call my public ip in port 80 I can connect to Win Server, but I can' when I use my ip in port 81.

I have changed apache listening port to 8080, but still no luck. Also the log file does not show any record of connection (just like you said cdenley the request never passes to apache).

If the request is forwarded directly to the given ip then the problem is with my router.

Except you said ShieldsUp showed port 81 was open, which means it could have established a TCP connection, which means your router is working. Are you sure you failed to establish a TCP connection from OUTSIDE your network on port 81? Could you provide us with your public IP so we can test for ourselves whether or not the port is open since your results are contradictory?

---

### Post by rogtek on 2010-05-21
It's worth a try!

cdenley, I have send you my ip through pm.

---

### Post by cdenley on 2010-05-21
It works fine. Your router probably doesn't "port forward" for connections originating within the LAN. You must have been mistaken when you said you failed to connect to your public IP from an external network.

---

### Post by rogtek on 2010-05-21
I found what was the problem.

I have put wrong public ip in my router in the first place.:mad:

Thanks for your help!

---

