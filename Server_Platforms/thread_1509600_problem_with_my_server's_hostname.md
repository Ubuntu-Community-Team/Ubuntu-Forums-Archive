---
title: "problem with my server's hostname"
date: 2010-06-14
forum: Server Platforms
---

### Post by yeayu on 2010-06-14
Hello:
I'm trying to install ubuntu sever 10.04 into my old machine.
I have followed some tutorials, but i have only one problem, I can't access from outside to my server, although i registered a hostname in [www.no-ip.com](www.no-ip.com)
It say:
I can access to my server inside my internal network:
my computer ip: 192.168.1.129
server ip: 192.168.1.131
so if i put in a web-browser this ip there is not any problem

but, when i try to access from outside using the hostname from no-ip.com
(misyte.sytes.net) don't work.

I opened port 80 to my router redirecting to 192.168.1.131 (label NAT in router menu "virtual server")  

what's happening? 
thankx

---

### Post by arrrghhh on 2010-06-14
So if you can access your server on your LAN, I assume you're doing it thru port 80?  Accessing a web site on apache perhaps?

Did you enable UFW?  If so, did you allow all traffic to port 80?  Also, do you have any other services like SSH you could test with?  Or perhaps change the port on apache?  Some ISPs like to block port 80...

---

### Post by yeayu on 2010-06-14
> **yeayu said:**
> 
but, when i try to access from outside using the hostname from no-ip.com
(misyte.sytes.net) don't work.

really it's work, but always redirect to router's gateway ip, so it's trouble to redirecting to server's internal ip.

---

### Post by yeayu on 2010-06-14
> **arrrghhh said:**
> So if you can access your server on your LAN, I assume you're doing it thru port 80?  Accessing a web site on apache perhaps?

Did you enable UFW?  If so, did you allow all traffic to port 80?  Also, do you have any other services like SSH you could test with?  Or perhaps change the port on apache?  Some ISPs like to block port 80...

No, i didn't enable UFW, so either allowed all traffic to this port. Is it necessary?
about ssh, how can test it?

---

### Post by arrrghhh on 2010-06-14
Install openssh and try to connect to the box?  I'm not sure how to help you here, no offense but there seems to be a language barrier...

---

### Post by CharlesA on 2010-06-14
Run a scan using Shield's Up! or nmap from a machine outside your network to see if port 80 is indeed open.

Sounds like port forwarding isn't set up correctly.

---

### Post by yeayu on 2010-06-14
> **CharlesA said:**
> Run a scan using Shield's Up! or nmap from a machine outside your network to see if port 80 is indeed open.

Sounds like port forwarding isn't set up correctly.

I have scanned all ports, and 80 port is open.
Yes, also i think it is a problem about port forwarding..

here you have my NAT configuration of my router (look at the last one row)
[IMG]http://img824.imageshack.us/img824/2249/screenshotk.png[/IMG]

---

### Post by arrrghhh on 2010-06-14
From that screenshot it says your server is 192.168.1.131... that doesn't seem like a static IP, is it?  If it isn't, you should setup your server with a static IP...

[This](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html) guide may be overkill, but it shows you all you would want to know about network configuration in Ubuntu Server 10.04...

---

### Post by yeayu on 2010-06-14
my server has static ip.
here you have /etc/network/interfaces from server:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static

address 192.168.1.131
netmask 255.255.255.0
gateway 192.168.1.1
nameserver 62.36.225.150 62.37.228.20

```

it's correctly connected to router by Ethernet wire.
i think my server is good connected cause i can make ping to google or whatever webpage from it. Also I'm connected it by ssh using my laptop, but just it work with the ip address not with hostname. 
For that reason must be problem of port forwarding, because if I use the hostname my web-browser open 192.168.1.1 (gateway of router)

---

### Post by arrrghhh on 2010-06-14
Are you testing this from outside your network?  

I don't think you'll be able to hit your hostname from inside your LAN, I could be wrong tho...

---

### Post by CharlesA on 2010-06-14
> **arrrghhh said:**
> Are you testing this from outside your network?  

I don't think you'll be able to hit your hostname from inside your LAN, I could be wrong tho...
Depends on how the router is set up. I've got one using DD-WRT and I can connect via hostname from inside the lan (but I rarely do it that way).

---

### Post by yeayu on 2010-06-14
> **arrrghhh said:**
> Are you testing this from outside your network?  

I don't think you'll be able to hit your hostname from inside your LAN, I could be wrong tho...
no, i was testing inside my network but finally works just ordered to my friend connect there, and it works, although i don't know why i can't connect from inside my network, any solution?
thank you

---

### Post by arrrghhh on 2010-06-14
> **CharlesA said:**
> Depends on how the router is set up. I've got one using DD-WRT and I can connect via hostname from inside the lan (but I rarely do it that way).

I use DD-WRT on my router as well, and this also does work for me.  Not sure why tho...

[quote=yeayu]no, i was testing inside my network but finally works just ordered to my friend connect there, and it works, although i don't know why i can't connect from inside my network, any solution?[/quote]

Get a router that is placed in front of your DSL router (this may not fix the issue...).  For whatever reason, your DSL modem/router isn't looping the request back properly... I'm sure there's a default route or something you can place in the router but it's **not** a good practice to test your outside connectivity from inside your LAN - as you've found out, it'll produce inconclusive results.  The ONLY good test is going thru another ISP.  I typically just use the data cxn on my phone to test, but not everyone has that luxury :P

---

