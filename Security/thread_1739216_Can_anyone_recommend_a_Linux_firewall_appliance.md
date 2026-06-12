---
title: "Can anyone recommend a Linux firewall appliance?"
date: 2011-04-25
forum: Security
---

### Post by Ron Jones on 2011-04-25
I have a SOHO network with three internal servers (Web, Mail, PBX), and a couple of PC's. It doubles as my home network, complete with Wii, Netflix, and Hulu.

> Yes, I know it would probably be cheaper to host them off site. But it is the way I like it.Right now, I use a PIX 501 firewall appliance, and the "static (inside,outside)..." command to assign three (out of my block of five) static IP addresses to the internal servers.

Like so:
```

static (inside,outside) 123.123.123.123 192.168.29.11 netmask 255.255.255.255 0 500
static (inside,outside) 123.123.123.124 192.168.29.12 netmask 255.255.255.255 0 500
static (inside,outside) 123.123.123.125 192.168.29.13 netmask 255.255.255.255 0 500
access-list 101 permit ucp any host 123.123.123.123 eq 5060 
access-list 101 permit tcp any host 123.123.123.124 eq www
access-list 101 permit tcp any host 123.123.123.125 eq smtp
ip address outside 123.123.123.126 255.255.255.248

```HOWEVER... I'm beginning to have the odd problem which requires the occasional reset. 

So... Can anyone recommend a good linux-based hardware firewall appliance that can do what a PIX does (I do not need a VPN)?

I do not want to use an old PC, I'd prefer to purchase a piece of commercial hardware that has flash memory, and is able to handle multiple static IP addresses behind the firewall (see above code example).

>  Why not buy a new/refurbished Pix 501? Because I don't want to... I like to tinker.

---

### Post by Claus7 on 2011-04-25
Hello,

I may give you a wrong answer on what you are asking, yet I would give a try. Do you know about firestarter than you can install from synaptic and is a fine firewall application for ubuntu?

I do not know, if this covers your needs though.

Regards!

---

### Post by tgm4883 on 2011-04-25
> **Claus7 said:**
> Hello,

I may give you a wrong answer on what you are asking, yet I would give a try. Do you know about firestarter than you can install from synaptic and is a fine firewall application for ubuntu?

I do not know, if this covers your needs though.

Regards!

](*,)

No no no, please don't recommend Firestarter anymore. It's old and deprecated and isn't what the OP is asking about. If you are going to recommend a software firewall, recommend UFW

---

### Post by Claus7 on 2011-04-25
Hello,

> **tgm4883 said:**
> ](*,)

No no no, please don't recommend Firestarter anymore. It's old and deprecated and isn't what the OP is asking about. If you are going to recommend a software firewall, recommend UFW

1) no reason to argue with you. I'm just using firestarter from...Dapper days and is still in the repos of maverick, which I have also installed, without using it though. By searching a little bit more the issue I saw that it is fully functional, yet not active in development.

2) by answering it caught your attention, which resulted in giving a firm answer. Just one query: since ufw is a firewall software and firestarter is one as well, both are not solutions for the OP's question?

Regards!

---

### Post by CharlesA on 2011-04-25
The OP wants a hardware firewall device, could be something running a distro like pfSense, or M0n0wall.

Not sure if they sell commercial appliances like those, but there could be out there.

EDIT: Actually, it looks like there is a [list]("http://www.pfsense.org/index.php?option=com_content&task=view&id=44&Itemid=50") of vendors that make hardware that you can run pfsense on.

---

### Post by collisionystm on 2011-04-25
> **Ron Jones said:**
> I have a SOHO network with three internal servers (Web, Mail, PBX), and a couple of PC's. It doubles as my home network, complete with Wii, Netflix, and Hulu.

Right now, I use a PIX 501 firewall appliance, and the "static (inside,outside)..." command to assign three (out of my block of five) static IP addresses to the internal servers.

Like so:
```

static (inside,outside) 123.123.123.123 192.168.29.11 netmask 255.255.255.255 0 500
static (inside,outside) 123.123.123.124 192.168.29.12 netmask 255.255.255.255 0 500
static (inside,outside) 123.123.123.125 192.168.29.13 netmask 255.255.255.255 0 500
access-list 101 permit ucp any host 123.123.123.123 eq 5060 
access-list 101 permit tcp any host 123.123.123.124 eq www
access-list 101 permit tcp any host 123.123.123.125 eq smtp
ip address outside 123.123.123.126 255.255.255.248

```HOWEVER... I'm beginning to have the odd problem which requires the occasional reset. 

So... Can anyone recommend a good linux-based hardware firewall appliance that can do what a PIX does (I do not need a VPN)?

I do not want to use an old PC, I'd prefer to purchase a piece of commercial hardware that has flash memory, and is able to handle multiple static IP addresses behind the firewall (see above code example).

I think you will be very happy with a Watchguard Firebox.

I have been using them for years. They are great. And linux based if that helps

---

### Post by Ron Jones on 2011-04-25
> **CharlesA said:**
>  Actually, it looks like there is a [list]("http://www.pfsense.org/index.php?option=com_content&task=view&id=44&Itemid=50") of vendors that make hardware that you can run pfsense on.

LOL... I've crawled all over their site in the last couple of hours (pfsense and M0n0wall) and didn't even notice the great big "hardware" link in the middle of the page :redface:.

Thanks!

 
[QUOTE=collisionystm]I think you will be very happy with a Watchguard Firebox.[/QUOTE]

Yes, I have used Watchguard products before, and they make top notch gear. But it's "purely commercial" like the PIX, and I'm looking for something I can "tinker" with when my PIX 501 dies... Rather like an old '67 Chevy pick-up.

---

### Post by sj1410 on 2011-04-26
[http://www.pisces.net.in/p/effortless-linux-based-firewall.html](http://www.pisces.net.in/p/effortless-linux-based-firewall.html)

---

### Post by deconstrained on 2011-04-26
---
Nevermind, I misunderstood O.P.

---

