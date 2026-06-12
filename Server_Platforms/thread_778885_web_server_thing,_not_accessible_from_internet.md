---
title: "web server thing, not accessible from internet"
date: 2008-05-02
forum: Server Platforms
---

### Post by fuzZzball on 2008-05-02
Hello,
I'm trying to setup a home web server. I've 3 comps here with
several ubuntu version (7.10, 8.04).

No matter what I do, the server is not accessible from internet. Perhaps I'm missing something out, something in ubuntu and someone with experience can point it out ..

I'm using LAMP and I've configured apache to listen to 10.0.0.150:80 and ServerName to 10.0.0.150 (not localhost). (I can access the server locally, [http://10.0.0.150/](http://10.0.0.150/))

So assume my WAN ip is 80.200.240.100, and my server IP is 10.0.0.150, I've set a NAT rule in my Modem/Router to forward 80.200.240.100:80 to 10.0.0.150:80, so far so good, on the site [www.canyouseeme.org](www.canyouseeme.org) it says my ISP is not blocking the port 80 and it's a success, but i cannot access the server thru [http://80.200.240.100/](http://80.200.240.100/) (it just gives a time out, server takes to long to respond). So I thought maybe my ISP is blocking port 80 (which most likely would be the case) so i configured everything to port 8080 and still nothing :(

When using nmap -P0 10.0.0.150 it gives the following output:

Interesting ports on (10.0.0.150):
Not shown: 1691 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
80/tcp   open  http
139/tcp  open  netbios-ssn
443/tcp  open  https
445/tcp  open  microsoft-ds
3306/tcp open  mysql


but nmap -P0 80.200.240.100 gives:

Interesting ports on 80.200.240.100:
Not shown: 1692 closed ports
PORT     STATE    SERVICE
21/tcp   open     ftp
23/tcp   open     telnet
80/tcp   filtered http
1723/tcp open     pptp
8080/tcp filtered http-proxy

so 8080 is filtered too? and testing [http://80.200.240.100:8080/](http://80.200.240.100:8080/) gives a time out also .. so I guess it's more likely I'm doing something wrong here!

I have no IPTABLES set, no firewall (at least, that's what i think, i've got nothing started so far because i just wanted to test the whole environment without a firewall) but perhaps I'm leaving something out in Ubuntu which I forgot to set? Some tricky variable? :)

---
Well, checked my modem if the firewall was on (through telnet), and it was, 
so i turned it off, but still no difference :( .. 
---
Anyone? thanks in advance
Fuzz

---

### Post by fuzZzball on 2008-05-02
Ok, i found it .. and it DOES work, although I cannot connect to it from within the network the server is located, but from a different computer on a different network with a different WAN adres it work perfectly .. the reason is:

Source: [http://forums.fedoraforum.org/showthread.php?t=75361](http://forums.fedoraforum.org/showthread.php?t=75361)
FSCK Wrotes: 

I Imagine this problem has to do with IP addresses. Let me try to explain.
First we assume your local LAN ip address for the web server is 192.168.0.10, and the client web browser is 192.168.0.20
The we say the internet-facing ip address (WAN, as you call it) is 30.40.50.60.
Your router will know that one side of its network, the local side, is on the 192.168.0.x network, and the other side is on 30.40.50.x. Also, it will understand that 192.168.0.x is a private address range, sometimes incorrectly called un-routable, and should never be seen on the real internet.
Thus, when a packet from 192.168.0.20 reaches the router bound for 30.40.50.60 it is rejected by the interface holding the 30.40.50.60 address because it is not a valid address for the internet side of the device, only the local side.
NAT will have trouble solving this because it will have to NAT your address (192.168.0.20) to the outside address (30.40.50.60), and connect from 30.40.50.60 to 30.40.50.60 and get that connecton NATed to 192.168.0.10, which won't work on many devices because we are connecting to ourself from ourself, and many devices don't like that, again for good reasons.

The reason all this doesn't work is called "IP Spoofing". It's a set of rules which include:
1) I should never see a connection from the internet which originates from a private IP. Reject it if I do.
2) I should never see a connection from the internet which originates from my IP address. Reject it if I do.

There are several ways to get around this problem:
1) allow private IPs to route from the internet - bad idea
2) force your web browser to use a proxy server on the internet, so traffic comes from a valid external address (this is why the-cloak.com works) - good idea
3) if you have a domain which resolves to an external IP, try adding a local entry in the clients /etc/hosts/ to force clients to use the local address, like so:
Code:

172.16.3.130 fukka.co.uk

I personally use 3) because I only have a couple of local clients.

Hope that makes sense!

C.

--

so, it works .. ;)

---

### Post by ghostknife on 2008-05-03
Give the output of the following command run on the server:
```

sudo iptables -nL
```

Then also see if your router has an option for a DMZ zone. If it does set it to your LAMP server. See if this works. If it does it probably means (1) Your router has problems with NAT (2) Your NAT configuration on the router is faulty.

---

### Post by fuzZzball on 2008-05-04
Hi ghost,

I've got no iptables set,
So it's default

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

I've not set the DMZ, altough i've test the setup with DMZ, it didn't work :) .. 
I think my router is having difficulties with NAT, it's a Sitecom and I've read 
more or like the same problems from different people, they all suggest Linksys 
or Cisco .. same company though, different quality :D

--
So I added static DNS resolving on my (only) local client for server testing
   192.168.0.10 -> [www.domain.whatever](www.domain.whatever) and furthermore add every vhost i declared
   (subdomain). It does the trick ..

--
Oh, first of all, my setup is like this. I have a Modem/Router with only one WAN output. This
goes in the Uplink of my router. So my Modem get's the IP from my ISP, 20.30.40.50 and the
local IP from my Modem is e.a. 10.0.0.150, So I set a NAT rule saying 20.30.40.50:80 - 10.0.0.150:80
and in the Sitecom router I forward the port to the server, 192.168.0.10:80

So like this:
20.30.40.50:80 <-> 10.0.0.150:80
10.0.0.150:80 <-> 192.168.0.10:80

I guess that's only way to do it? I mean I'm not an expert ..

Cheers

---

