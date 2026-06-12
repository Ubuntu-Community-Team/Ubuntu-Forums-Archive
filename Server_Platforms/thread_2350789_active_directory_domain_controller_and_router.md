---
title: "active directory domain controller and router"
date: 2017-01-27
forum: Server Platforms
---

### Post by adamkent322 on 2017-01-27
Hello All
I currently have a Windows 2008r2 active directory domain controller which also routes internet traffic to Windows Clients. I want to replace this with an Ubuntu Server using samba4 as the active directory but I also want it to route the internet traffic to the client machines. I have found instructions on Help Ubuntu for adding dhcp3-server to Ubuntu as an internet gateway will this conflict with samba or is there a better way

Many thanks

---

### Post by darkod on 2017-01-27
It should not conflict with samba in any way.

But you mention routing and then mention dhcp. Those are separate things. Simple routing on linux box can be done very easily, if there are no filters or rules needed (if the router machine simple is routing all traffic it receives on the internal interface to the external).

If you need it to offer dhcp leases to workstations on the LAN that is separate from routing.

But in any case, it is easy to do both things, unless you require some very specific setup.

---

### Post by geeksmith on 2017-01-27
DHCP and Samba will not conflict with each other. One is a directory service, the other is an IP address distribution service. I prefer dnsmasq, personally.

That said, I can't recommend using a domain controller as an Internet router. Your DC has more sensitive information on it than possibly any other machine on the network, and as such should be carefully firewalled and monitored for intrusion and compromise.

You can get routers today for insanely cheap prices. You can use an old PC or a Raspberry Pi to perform this work, too. Plus, there's nothing like having all your eggs in one basket -- when your DC/DHCP/DNS/file server loses a power supply or disk or gets a bad software update, you're in for a world of hurt.

I would suggest using a separate system for your Internet gateway and DHCP server and let the DC just be a DC.

---

### Post by adamkent322 on 2017-01-28
Thank you. I know that what I have setup isn't best practice. But that will be changing in the near future plus there's no personal or business data stored on the network it purely a teaching network. Just so I've understood you both properly I can have Samba4 doing all my active directory, DNS and DHCP etc, and if I  add my router's IP to my  as a gateway in my '/etc/network/interfaces' then that traffic will get routed through the server to the client machines. Once again thank you

---

### Post by Doug S on 2017-01-28
> **adamkent322 said:**
> ..., and if I  add my router's IP to my  as a gateway in my '/etc/network/interfaces' then that traffic will get routed through the server to the client machines. Once again thank youIf I understand correctly, then no. You will need an iptables rule set (or equivalent) to add router functionality to your server.

---

### Post by darkod on 2017-01-29
Hold on, which router you are talking about now? You already have a lan router?
In such case, if you already have a router performing routing and dhcp you better leave those functions to be performed by the router. And the samba server will do ad and dns.
No need to route the traffic first through your router, then the samba server to reach the clients.
And the 'gateway' parameter in /etc/network/interfaces means it will server as gw for the server itself, not that all lan traffic will be routed through the server.

---

### Post by adamkent322 on 2017-01-29
I mean my ADSL router that then connects a wireless access point and to the domain controller which in does all the active directory DNS and DHCP and routes using NAT

---

### Post by darkod on 2017-01-29
Your adsl router will already have one external public IP and then internal LAN subnet, right? So what is the domain controller routing between? One private LAN to another private LAN?

---

### Post by Doug S on 2017-01-29
> **darkod said:**
> Your adsl router will already have one external public IP and then internal LAN subnet, right?If indeed it is a router and not just a modem. In my case I have an adsl modem, providing no router abilities at all (which is what I want, as I use an Ubuntu server as my router).

Anyway, we need some clarity.

---

### Post by adamkent322 on 2017-01-30
sorry for the confusion I've caused. But yes what I have is a standard ADSL router so it would be routing between two lans 
eg 192.168.1.x translated to 192.168.2.x

---

### Post by darkod on 2017-01-30
If you really insist on having separate 192.168.2.x subnet, you can make ubuntu server routing very easily.
The server needs to have two interfaces, connected one to 192.168.1.x and the other to 192.168.2.x. The interfaces in 16.04 are called differently, but lets assume eth0 is in .1.x and eth1 is in .2.x.

To make the server to route you need to:
1. Open as admin /etc/sysctl.conf and comment out the line for 'net.ipv4.ip_forward=1' (remove the # in front to enable it). Reboot the server.
2. Add masquerade iptables rule. If you do not use iptables firewall on this server, the easiest way to add sinle iptables rule is adding the following at the end of /etc/rc.local (but before the 'exit 0' line):
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
```

That allows traffic not to get "lost" when NATed between .1.x and .2.x. That's all you need for a basic linux router.

---

### Post by chewie814 on 2017-02-02
Hello All
this is still me Ive had a SSO login issue and had top change my username etc so apologies if I cause more confusion. I need to have two subnets as I am running a teaching network using game software I need an Active Directory Domain Controller to control the network traffic the internet link is for updates, time sync and if we need to link into other networks that off site although the permanent staff also require internet access whe nwe dont have any students. The whole reasoning what I am trying to achieve is that our server has system capacity for a linux ADDC and then two win7 headless virtual machines as dedicated game hosts this will double our the amount of game hosts available so the we can allowcate each one a particular role 

once again thanks for everyones help 

Adam

---

### Post by wildmanne39 on 2017-02-02
Please have a look here:
[https://ubuntuforums.org/showthread.php?t=2230004](https://ubuntuforums.org/showthread.php?t=2230004)
and follow the directions so we can get you back into your original account, post in the Resolution Centre here:
[https://ubuntuforums.org/forumdisplay.php?f=123](https://ubuntuforums.org/forumdisplay.php?f=123)
about the account issue please.
Thanks

---

### Post by adamkent322 on 2017-02-05
Thank you all for the advice. I'll edit my iptables accordingly

---

