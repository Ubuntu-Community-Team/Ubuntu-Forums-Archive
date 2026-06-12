---
title: "Is firewall configuration really necessary in ubuntu?"
date: 2011-10-10
forum: Security
---

### Post by newhere_m on 2011-10-10
Between these two options, which one is better?

1. Not having any firewall.
2. Using gufw to enable firewall, deny all incoming and outgoing program and services, except allowing http (80/tcp). (This is what I have right now.)

If ubuntu is practically closed to external world, is it really meaningful to configure firewall? (One source says one positive side of firewall is that it offers peace of mind.)

Now can anybody please help with my doubt?

---

### Post by Rasa1111 on 2011-10-10
if you're not running a server you don't really need it.
I keep mine on anyway.. but there's no need. lol :P
it doesnt hurt anything being on though, so I guess im with the "peace of mind" peoples.
also, Im still kind of a "Linux noob" (almost 2 years using it)..
so that may be a reason.:lol:

---

### Post by haqking on 2011-10-10
> **newhere_m said:**
> Between these two options, which one is better?

1. Not having any firewall.
2. Using gufw to enable firewall, deny all incoming and outgoing program and services, except allowing http (80/tcp). (This is what I have right now.)

If ubuntu is practically closed to external world, is it really meaningful to configure firewall? (One source says one positive side of firewall is that it offers peace of mind.)

Now can anybody please help with my doubt?


IPTables is the firewall built into the linux kernel which all the firewall interfaces manipulate such as Firestarter, UFW, GUFW etc.  Firestarter being out of date and no longer supported however.

On a server if you use a firewall it would be preferable to use IPTables CLI direct, or UFW if you want an easier interface.

However most home systems/servers are protected by the firewall in the router anyways.

cheers

---

### Post by collisionystm on 2011-10-10
> **newhere_m said:**
> Between these two options, which one is better?

1. Not having any firewall.
2. Using gufw to enable firewall, deny all incoming and outgoing program and services, except allowing http (80/tcp). (This is what I have right now.)

If ubuntu is practically closed to external world, is it really meaningful to configure firewall? (One source says one positive side of firewall is that it offers peace of mind.)

Now can anybody please help with my doubt?

I personally turn it on.

Why risk it?

---

### Post by collisionystm on 2011-10-10
> **haqking said:**
> A firewall does nothing really as ports are closed by default, you may need it if you install or setup certain services but if you pay attention to the correct security concerned with them then again a firewall is useless anyways.

IPTables is the firewall built into the linux kernel which all the firewall interfaces manipulate such as Firestarter, UFW, GUFW etc.  Firestarter being out of date and no longer supported however.

On a server if you use a firewall it would be preferable to use IPTables CLI direct, or UFW if you want an easier interface.

However most home systems/servers are protected by the firewall in the router anyways.

cheers

All ports are open by default.

Open a terminal and type

sudo iptables -L

---

### Post by haqking on 2011-10-10
> **collisionystm said:**
> All ports are open by default.

Open a terminal and type

sudo iptables -L

all ports are effectively closed even though by default they are set to accepting, if nothing is listening on them then they are closed !
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)
[https://wiki.ubuntu.com/Security/Features#ports](https://wiki.ubuntu.com/Security/Features#ports)

if you want UFW then

```
sudo ufw default deny
```
```
sudo ufw default allow
```

```
sudo ufw enable
```

---

### Post by Dangertux on 2011-10-10
I think it is important to understand something. Ports are not "open" by default. An open port is defined as a port that has a service bound and listening to it. If there is no service bound and listening to a port, there is nothing there. An attacker can't just walk in through a closed port just because it's unfirewalled, it is not equivalent to locking your door.

This is a quite typical misunderstanding often propogated by sites like shields up. That create cool catch phrases like "Stealth Ports" when in reality there is not really any such thing. In terms of  iptables this is a closed port

```

iptables -A INPUT -p tcp --dport 80 -j REJECT

```in terms of iptables this is a "stealth" port.

```

iptables -A INPUT -p tcp --dport 80 -j DROP

```The only difference here is that REJECT will send TCP RST to the machine attempting to create a connection. Terminating the connection in a friendly matter and not hanging it out there to wait. DROP will simply not reply, and silently (or with logging) drop the traffic.

This is great for a desktop use, since you likely have no Internet facing services running, and the element of appearing as if you're not there has some purpose. That being said, this will not deceive attackers who are dedicated enough to spend a few minutes reading nmap's documentation. Also, it serves literally NO purpose if you have any internet facing services as the fact that the port will respond with TCP ACK blows away the fact that you're not "there".

Ultimately running with no services in terms of what an attacker sees is a lot like setting an iptables policy default reject as such

```

iptables -P INPUT REJECT

```That being said, in some cases restrictive outbound rules can limit what an attacker can do. However, since you will always need DNS and whatever other ports you wish to utilize 80? 443? they will always have an avenue for a reverse connection.

If you want to read more about how a potential attacker can bypass a firewall or how to defeat that read [here]("http://dangertux.wordpress.com/2011/10/03/a-firewall-is-not-a-catch-all/")

---

### Post by bodhi.zazen on 2011-10-10
Nice post. 

s/DENY/DROP =)

---

### Post by Dangertux on 2011-10-10
> **bodhi.zazen said:**
> Nice post. 

s/DENY/DROP =)

Woops, good catch it's way too monday morning :-P 

This is MY version of iptables :-P the one that combines UFW and iptables rules that I like :-P

J/K fixed lol

---

### Post by bodhi.zazen on 2011-10-10
> **newhere_m said:**
> Between these two options, which one is better?

A better question is what do you want to use a firewall for ?

If "just because" then the answer is no, Linux is not windows and by default there are no open ports of any significance, so there is nothing to firewall.

Are you running a service such as http or ssh ? If so, what do you want from a firewall ? White list ? blacklist ? what ?

Are you running a router ? Well then of course you will need to configure a firewall.

Best to stop and understand what you are doing and why.

[https://wiki.ubuntu.com/SecurityTeam/FAQ#UFW](https://wiki.ubuntu.com/SecurityTeam/FAQ#UFW)

[http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

[http://bodhizazen.net/IPTables.odt](http://bodhizazen.net/IPTables.odt)

---

### Post by newhere_m on 2011-10-17
Thanks for various suggestions. Meanwhile I have looked up a bit to understand things.
To answer bodhi.zazen's questions:
> 
A better question is what do you want to use a firewall for ?
Are you running a service such as http or ssh ? If so, what do you want from a firewall ? White list ? blacklist ? what ?

No, I'm not running any service like http or ssh.
> 
Are you running a router ? Well then of course you will need to configure a firewall.

I am using router provided by my ISP, and this is a combination of ADSL modem and router, used in conjunction with telephone. If you mean I am "running a router" in the sense that I am taking care of some network, then the answer is no.
It is said that such router already contains one (hardware) firewall but many people think that this is not good enough (from windows point of view). I guess I do not need to configure firewall.

---

### Post by haqking on 2011-10-17
> **newhere_m said:**
> Thanks for various suggestions. Meanwhile I have looked up a bit to understand things.
To answer bodhi.zazen's questions:

No, I'm not running any service like http or ssh.

I am using router provided by my ISP, and this is a combination of ADSL modem and router, used in conjunction with telephone. If you mean I am "running a router" in the sense that I am taking care of some network, then the answer is no.
It is said that such router already contains one (hardware) firewall but many people think that this is not good enough (from windows point of view). I guess I do not need to configure firewall.

I believe Bodhi meant are you running a router on your actual machine software wise, if you have a hardware router (99.9% of the time) it will have a firewall built in and thus protecting your network anyways.

So if you are not running any of the services mentioned then you should be ok without running one.

Peace

---

