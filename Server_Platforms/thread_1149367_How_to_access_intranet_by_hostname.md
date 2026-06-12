---
title: "How to access intranet by hostname"
date: 2009-05-05
forum: Server Platforms
---

### Post by essolo on 2009-05-05
Hai, I'm new user use Ubuntu Server..

I install Ubuntu server in intranet on workstation.

the problem is, I cannot access my server use hostname... then I just can access by 

Ip Address..

so how can I do?

thanks..

---

### Post by miegiel on 2009-05-05
There are 2 ways to easily do this, each with their own (dis)advantages.
[LIST=1]
[*]Run a DNS server/service on 1 of the machines on your network.
[*]Add the server's name and ip# to all the workstations host file(s) on your network.
[/LIST]

---

### Post by essolo on 2009-05-05
> **miegiel said:**
> There are 2 ways to easily do this, each with their own (dis)advantages.
[LIST=1]
[*]Run a DNS server/service on 1 of the machines on your network.
[*]Add the server's name and ip# to all the workstations host file(s) on your network.
[/LIST]


but i have small LAN, I want to setup web base system.. so this system just on intranet.
No DNS. Just access like this [http://servername/index.html](http://servername/index.html)

---

### Post by m3bik on 2009-05-05
My DSL modem has a DNS server built in. I simply access my modem by the local IP and click the DNS link. I can then add hostnames and point them to any IP.

Don't know if you have this option, but it's worth a shot.

---

### Post by m3bik on 2009-05-05
It works great for my intranet. Granted I use the local domain name "inet" so my servers are accessed by [http://servername.inet/index.html](http://servername.inet/index.html)

---

### Post by miegiel on 2009-05-05
> **essolo said:**
> but i have small LAN, I want to setup web base system.. so this system just on intranet.
No DNS. Just access like this [http://servername/index.html](http://servername/index.html)

You can use DNS to link LAN ip# to names too ;)
It's not just for the internet.

---

### Post by m3bik on 2009-05-05
Just make sure that your TCP/IP settings for your LAN connection has the correct IP to your local DNS server.

---

### Post by essolo on 2009-05-05
I don't have internet connection...

before i user ubuntu server, i just install xampp at my workstation on windows..

i just access workstation like [http://servername/index.html](http://servername/index.html)

in ubuntu server, not running like that...

any configuration to I can access ubuntu like that?

---

### Post by miegiel on 2009-05-06
> **essolo said:**
> I don't have internet connection...

before i user ubuntu server, i just install xampp at my workstation on windows..

i just access workstation like [http://servername/index.html](http://servername/index.html)

in ubuntu server, not running like that...

any configuration to I can access ubuntu like that?

I guess [_this_]("https://help.ubuntu.com/8.04/serverguide/C/dns.html") is to difficult.

The simplest way is to edit */etc/hosts*.
```
sudo gedit /etc/hosts
```
*/etc/hosts* explained in short [_here_]("https://help.ubuntu.com/8.04/serverguide/C/network-configuration.html"). Scroll to the bottom and read **Managing Hosts**.

Doing it this way has the (dis)advantage that it's static, if the IP of the *servermane* changes you'll need to edit */etc/hosts* again on the other PC. And it's little work, if you only need to do it on a few machines. Adding a line or 2 to */etc/hosts* on a dozen machines is no fun at all :D

---

### Post by windependence on 2009-05-07
I'm sure /etc/hosts is the best way to go here. He just has a small LAN. Most people don't need to and probably don't want to set up a full blown DNS server on their network.

-Tim

---

