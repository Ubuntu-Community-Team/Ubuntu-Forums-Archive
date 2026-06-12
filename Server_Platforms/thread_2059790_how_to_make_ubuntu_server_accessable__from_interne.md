---
title: "how to make ubuntu server accessable  from internet(server connected using 3g modem)"
date: 2012-09-18
forum: Server Platforms
---

### Post by ahmed23 on 2012-09-18
[SIZE=2]Hello all,
i have a ubuntu server 12.04 works as an Internet gateway for my  home LAN (using iptables NAT).  
the server is also running a LAMP server that host OwnCloud (similar to dropbox) and everything is OK until i want to make the server available on-line (accessible from Internet) [/SIZE]
[SIZE=2]
things done:[/SIZE]
 
[LIST]
[*][SIZE=2]i registered and      installed dynamic DNS (no-ip.com) client; running "host"     command get my correct ip address(the same address when i visit     WhatIsMyIP.com)[/SIZE]
[*][SIZE=2]a rule added to iptables to set destination NAT     to 127.0.0.1:80 
```
-A PREROUTING -i ppp0 -p tcp -m tcp     --dport 80 -j DNAT --to-destination 127.0.0.1:8080
```[/SIZE]
[/LIST]
  [SIZE=2]testing port 8080 on canYouSeeMe.org get's [/SIZE] 
 ```

 error: I could not see your service on ***.***.0.37 on port (8080)  
 Reason: Connection timed out
 
``` [SIZE=2]testing nmap -v -A ****.hopto.org
[/SIZE]```
[SIZE=2]
Starting Nmap 5.21 ( http://nmap.org ) at 2012-09-19 00:49 EAT
NSE: Loaded 36 scripts for scanning.
Initiating Ping Scan at 00:49
Scanning ****.hopto.org (197.252.0.37) [2 ports]
Completed Ping Scan at 00:49, 3.00s elapsed (1 total hosts)
Nmap scan report for ****.hopto.org (***.***.0.37) [host down]
Read data files from: /usr/share/nmap
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 3.63 seconds[/SIZE]
 
``` [SIZE=2]note:[/SIZE]
  [SIZE=2]the Ubuntu server is connected to Internet with 3g modem[/SIZE]

[SIZE=4]
Please help me setting things up[/SIZE]
-------------------------------------
problem was I dont have a direct access to public IP 

as "TheFu" saied
[QUOTE=TheFu]Redirecting to a private IP address space from outside your ISP will never work. Sorry[/QUOTE]

It looks my ISP is redirecting me to a public IP.
so it will not works.

---

### Post by TheFu on 2012-09-18
Inbound connections are probably blocked by your ISP. It is probably against their SLA for you to run any servers on their network.

You can check this by using a remote machine running **nmap** against your 3G IP or going to grc.com and running a "shields up" test.

The ISP is probably blocking.  Even if they don't block port 80, almost all ISPs block SMTP.

---

### Post by ahmed23 on 2012-09-19
[SIZE=3][COLOR=Black]
Hi TheFu, thanks you for speedy reply  
[/COLOR]
 this is the test result from grc.com ShieldsUp

[/SIZE]```
  [SIZE=3]
GRC Port Authority Report created on UTC: 2012-09-19 at 10:24:02  
Results from probe of port: 8080      
0 Ports Open     
0 Ports Closed     
1 Ports Stealth 
---------------------     
1 Ports Tested  

THE PORT tested was found to be: STEALTH.[/SIZE] [SIZE=3]
TruStealth: PASSED -ALL tested ports were STEALTH,
                   -NO unsolicited packets were received,
                   -NO Ping reply (ICMP Echo) was received. 
[/SIZE]
``` [SIZE=3]
is there is any hope to make any port opened? and how?
i also tried to remove iptables and make server opnend but nothing works.](*,):cry:
[/SIZE]

---

### Post by TheFu on 2012-09-19
It is a simple problem. You need to determine where the block is really happening. 

a) If it happens under your control, fix it.  
b) If it happens under someone else's control ask them to open it.

Find some other port that isn't blocked.  nmap will search all ports if you ask it.

However, if I were your 3G ISP, I would block all inbound connections and there is no way that I'd open them for a small, non-business account. For a business account, your monthly spend with the ISP would need to be over $1000 before I'd consider opening a single port.  I've worked on systems where our monthly mobile data costs were over US$300K.  It was amazing what the cell data company would do for us, but we never asked to have any client devices on the internet.  We had them setup a non-internet VLAN just for our devices to communicate back into our datacenter and no where else.  It one of our smartphones was stolen, they were completely worthless to anyone else.  Money talks.

---

### Post by darkod on 2012-09-19
If I'm not mistaken with that iptables rule you are forwarding port 80 to port 8080 on the same machine.

So when you use nmap or canyouseeme you should test for port 80, not 8080. Because until it reaches your server the traffic is using port 80, the server itself changes it to 8080.

Maybe the ISP is not blocking 8080 but there is no service listening on it, and the traffic from the outside is not traveling on port 8080.

This will be much more difficult to configure using 3G modem, since there is no router between the modem and the server. The traffic just arrives directly on the server.

PS. On top of everything said, with the money they will charge you for 3G data, you can probably get a VPS online cheaper. And I'm not sure what speed are you getting on 3G and what service exactly you plan to offer on the server, but I can't see it working on such low speed, especially if the upload is very low. When someone accesses your server, they are using the upload direction of the 3G modem.

---

### Post by ahmed23 on 2012-09-20
Hello All, thanks for replies.
the server is personal and I wont to setup it for learning and testing. so please bear with me.
 
on my country things are little different regarding internet, we have 4 ISPs thier internet available only through 3G (HSPA/EVDO) connections, and 1 ADSL provider, all of them has unlimited data plan which i currently used it.

> **darkod said:**
> 
If I'm not mistaken with that iptables rule you are forwarding port 80 to port 8080 on the same machine.

So when you use nmap or canyouseeme you should test for port 80, not 8080. Because until it reaches your server the traffic is using port 80, the server itself changes it to 8080.

Maybe the ISP is not blocking 8080 but there is no service listening on it, and the traffic from the outside is not traveling on port 8080.

it's looks true, I fix it and make apache also work on port 8080 but nothing works i also tried to open port 10000 for webmin also nothing looks worked
 
the below code is the /etc/iptables.up.rules file
```

# Generated by iptables-save v1.4.12 on Thu Sep 20 11:58:45 2012
*filter
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
-A FORWARD -m state -s 192.168.0.0/24 -i eth0 -o ppp0 --state NEW -j ACCEPT
-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
COMMIT
# Completed on Thu Sep 20 11:58:45 2012
# Generated by iptables-save v1.4.12 on Thu Sep 20 11:58:45 2012
*mangle
:PREROUTING ACCEPT [850:197067]
:INPUT ACCEPT [383:34815]
:FORWARD ACCEPT [467:162252]
:OUTPUT ACCEPT [342:110795]
:POSTROUTING ACCEPT [810:273116]
COMMIT
# Completed on Thu Sep 20 11:58:45 2012
# Generated by iptables-save v1.4.12 on Thu Sep 20 11:58:45 2012
*nat
:INPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -m tcp -i ppp0 --dport 10000 -j DNAT --to-destination 127.0.0.1:10000
-A PREROUTING -p tcp -m tcp -i ppp0 --dport 8080 -j DNAT --to-destination 127.0.0.1:8080
-A POSTROUTING -o ppp0 -j MASQUERADE
COMMIT
# Completed on Thu Sep 20 11:58:45 2012

```
interfaces:
   ppp0 = 3g modem connection
   eth0 = LAN connection (192.168.0.0/24)
ports:
   10000    = Webmin
   80, 8080 = apache

running traceroute mydns.hopto.org
```

traceroute mydns.hopto.org
traceroute to mydns.hopto.org (###.###.0.99), 30 hops max, 60 byte packets
 1  * * *
 2  10.80.1.153 (10.80.1.153)  1029.279 ms  1119.236 ms  1279.219 ms
 3  10.80.1.161 (10.80.1.161)  1429.187 ms  1539.303 ms  1629.160 ms
 4  ###.###.0.99 (###.###.0.99)  1759.279 ms  931.855 ms  1011.670 ms
 5  ###.###.0.99 (###.###.0.99)  1249.775 ms  1359.760 ms  1559.739 ms
 6  * * *
 7  * * *
 8  * * *
 9  * * *
 .
 .
 .
30  * * *


```

running ifconfig in server
```

eth0      Link encap:Ethernet  HWaddr 00:13:d3:c7:51:7b  
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d3ff:fec7:517b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21443 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19743 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2797541 (2.7 MB)  TX bytes:14166039 (14.1 MB)
          Interrupt:23 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20532 (20.5 KB)  TX bytes:20532 (20.5 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.81.98.223  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:15240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:11022510 (11.0 MB)  TX bytes:1978452 (1.9 MB)


```

---

### Post by darkod on 2012-09-20
First of all, from any other computer on the LAN, does apache work correctly when you type in the browser 192.168.0.7:8080? Does it open apache?

---

### Post by ahmed23 on 2012-09-20
> **darkod said:**
> First of all, from any other computer on the LAN, does apache work correctly when you type in the browser 192.168.0.7:8080? Does it open apache?

Yes it open

---

### Post by darkod on 2012-09-20
OK.

First of all, you don't need a DNAT rule that will reroute port 8080 to 127.0.0.1:8080. That's the same machine and the same port, just let it arrive at 8080.

You only need to do DNAT if you change ports for example, to route port 80 to 8080, or the other way around.

Second, your current INPUT policies in both *filter and *nat are ACCEPT. With that policy, you don't need any other rules, it accepts everything (including attacks).

But to do a short test, you can leave it at ACCEPT. Otherwise, later you should change it to DROP.

So, temporarily comment out all the PREROUTING rules you have, leave the policy at ACCEPT and from the outside try opening in a browser http://<public ip>:8080.

Since apache is working on 8080 that should open it. Does it work from the outside?

---

### Post by TheFu on 2012-09-20
Those ifconfig results are concerning. You don't have any public IP addresses. Bit the 192.x.x. and 10.x.x.x addresses are private - not routed on the internet.  [https://en.wikipedia.org/wiki/Private_network#Private_IPv4_address_spaces](https://en.wikipedia.org/wiki/Private_network#Private_IPv4_address_spaces) explains.

Do you have any public IPs?

Unless you have static NAT from your ISP, which is doubtful, I think you are screwed.  

Doing port translation on your local "server" is complicating things that don't need to be complicated.  Just tell apache to listen on whatever port you want.
**/etc/apache2/ports.conf** controls that.

Was ****.hopto.org (197.252.0.37) your real ppp IP address at some point or is that just a public redirector service?  Redirecting to a private IP address space from outside your ISP will never work. Sorry.

---

### Post by ahmed23 on 2012-09-20
OK everyone thank you very much :D.

as "TheFu" saied
[QUOTE=TheFu]Redirecting to a private IP address space from outside your ISP will never work. Sorry[/QUOTE]

It looks my ISP is redirecting me to a public IP.
so it will never works.

I will make this thread as solved because it something not under my control;)

special thanks to TheFu:)  and darkod:)

---

### Post by cybercity@localhost on 2012-09-23
you may want to register your server at changeip.com

go to the site and create an account

next, add your free domain or purchase a .com or any other domain.

---

