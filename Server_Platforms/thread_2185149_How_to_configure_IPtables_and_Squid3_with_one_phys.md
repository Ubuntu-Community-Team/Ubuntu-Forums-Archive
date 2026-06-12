---
title: "How to configure IPtables and Squid3 with one physical network card?"
date: 2013-11-01
forum: Server Platforms
---

### Post by Roswebnet on 2013-11-01
Hi everyone
 
 I have following devices in my infrastructure:
 
 [TABLE="class: outer_border, width: 600"]
[TR]
[TD]Device[/TD]
[TD]IP[/TD]
[TD]Subnet[/TD]
[TD]Gateway[/TD]
[TD]DNS1[/TD]
[TD]DNS2[/TD]
[/TR]
[TR]
[TD]Router[/TD]
[TD]192.168.0.1[/TD]
[TD]255.255.255.0[/TD]
[TD]ISP IP[/TD]
[TD]ISP DNS[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Server[/TD]
[TD]192.168.0.10[/TD]
[TD]255.255.255.0[/TD]
[TD]192.168.0.1[/TD]
[TD]192.168.0.10[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]PC[/TD]
[TD]192.168.0.100[/TD]
[TD]255.255.255.0[/TD]
[TD]192.168.0.1[/TD]
[TD]192.168.0.10[/TD]
[TD]ISP DNS[/TD]
[/TR]
[/TABLE]

 The router is a SOHO router. Therefore, it has integrated 4x1Gbps switch. Further, it has own DHCP and DNS servers.
 The server is a Ubuntu Server 13.10. I have installed webmin and squid3. There is only one NIC.
 The PC is a windows 8 machine.
 
 I want to configure Squid in way to work with only 1 NIC. As I understood it is possible to do with IPTables. I tried this links:
 [http://superuser.com/questions/492128/squid-transparent-proxy-with-nics-on-same-subnet](http://superuser.com/questions/492128/squid-transparent-proxy-with-nics-on-same-subnet)
 [http://www.purplealienplanet.com/node/25](http://www.purplealienplanet.com/node/25)
 
 I prefer the first solution, but the router delivers IP addresses to the PC. I tried first solution with no luck. I do know how configure 2 NICs server, but 1 NIC still a problem.
 
 Any help is welcome.
 
 Thank you.

---

### Post by Doug S on 2013-11-01
I do not know much about squid, but don't you have to redirect traffic, yet allow traffic from your squid box, at your SOHO router? When you mention iptables, do you mean iptables in your SOHO router?

---

### Post by pqwoerituytrueiwoq on 2013-11-01
a command like this will create a virtual nic 
```
ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
```
based on your title that will make things easier for you

---

### Post by Roswebnet on 2013-11-02
Iptables are on Server.
The virtual nic solution should work.
However, for virtual NIC I must install the DHCP server. DHCP is already running on soho router. Moreover, the virtual nic needs other range of IP address and than SQUID plays as a router. I would like to prevent this.

See this diagram:
[IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/SQUID3-1NIC.png[/IMG]

In my opinion I should do something with router and something with IPtables, but I cannot figure out.

---

### Post by Doug S on 2013-11-03
O.K. You will need to figure out the router part of it first. It is not clear to me how we can help with that part of it.

---

### Post by Roswebnet on 2013-11-03
Doug S, 

How I would do this?
In my thoughts I need to put on the router something likethis:

[I]route add 192.168.1.100 mask 255.255.255.255 192.168.1.10

[/I]Am I right?

How I should configure the server?

Thank you.

In addition, the virtual nic will have one huge disadvantage. If Proxy fails, there will be no internet for the client PC.

---

### Post by Doug S on 2013-11-04
> How I would do this?
In my thoughts I need to put on the router something likethis:
*route add 192.168.1.100 mask 255.255.255.255 192.168.1.10*I'm not sure, and I can not comment on what abilities your router has or does not have. Yes, that might work. If possible with your router, you might also set 192.168.0.10 (or 192.168.1.10, whichever is correct) as the gateway for 192.168.0.100 (or 192.168.1.100, whichever is correct), then use your first link as what is needed on the server.

> In addition, the virtual nic will have one huge disadvantage. If Proxy fails, there will be no internet for the client PC.As I understand things, which might be wrong, there won't be anyhow.

---

### Post by houstonbofh on 2013-11-06
Why not just tell the Windows PC to use the Ubuntu server as a proxy?  If you can add DNS entries to the SOHO router you can even autoconfig this.

---

### Post by Roswebnet on 2013-11-08
Solved!
   
   it is very easy actually I do not need special rules or something like this. On my Ubuntu server I use the webmin to manage configuration files.
   
   There is no dependency on proxy server. If server fails the proxy settings can be disabled in browser and user could use a internet connection.
   
   1) Configure the port
   
   [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Squid/Screenshot%202013-11-08%2006.16.37.png[/IMG]
  
  2. Setup Firewall
  
  [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Squid/Screenshot%202013-11-08%2006.19.32.png[/IMG]
  
  3. Setup Port Redirection
  [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Squid/Screenshot%202013-11-08%2006.20.40.png[/IMG]
  
  4.Create ACL's
  [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Squid/Screenshot%202013-11-08%2006.22.17.png[/IMG]
  
  5.Setup Restrictions
  
  [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Squid/Screenshot%202013-11-08%2006.24.07.png[/IMG]
  
  6. Apply changes.
  
  7. Setup Network on W8 machine (US:192.168.1.130, W8:192.168.1.135, R:192.168.1.1, SN:255.255.255.0).
  
  [IMG]https://dl.dropboxusercontent.com/u/14719391/Screenshots/Squid/Screenshot%202013-11-08%2006.29.07.png[/IMG]
  
  Give server 10-30 seconds to update the settings.
 This is it. Enjoy

---

