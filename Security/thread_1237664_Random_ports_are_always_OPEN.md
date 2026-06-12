---
title: "Random ports are always OPEN"
date: 2009-08-11
forum: Security
---

### Post by oomar on 2009-08-11
Ok Im stumped. Ive always heard about how ubuntu "stealths" its ports and thats its very secure. Well im sure its very secure but almost EVERY SINGLE TIME I run a port scan on my machine there is at least one open port. Usually extremely random like 36040 or 35432 or something else but almost every single port scan i do there is at least one if not more. One time I had 5 open ports.... I also have 631 open but thats CUPS so i HOPE i shouldnt be worried about that... I am running 9.04 with Gufw set to deny all incoming traffic.... so why are my ports randomly open? I always thought that security was simple enough if you just shut your ports until you needed them... well why wont they shut? anybody?

---

### Post by cdenley on 2009-08-11
Cups should be binding to 127.0.0.1, so it doesn't listen for remote connections. The two high random port probably aren't actually open, but a bug in the port scanner.

[https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/257042)
[http://bugzilla.gnome.org/show_bug.cgi?id=547598](http://bugzilla.gnome.org/show_bug.cgi?id=547598)

```

sudo netstat -tlnp

```

---

### Post by koenn on 2009-08-11
port scanners are useful tools, but only if you know how to use them correctly, and if you're capable of interpreting the results correctly

your post is too vague and random, so i won't try to guess what's happening there, but there's a good chance you're scanning the wrong way and interpreting the results the wrong way. 

try again, explain what you're scanning, where you're scanning it from, which scanner you use, with which options, and somebody will probably be able to explain what's happening.

---

### Post by cariboo on 2009-08-11
As cdenley pointed out it is a bug in the gnome network tools, it has been pushed upstream, but nothing has been done about it yet. If you want a gui port scan tool, install nmap and zenmap, Nmap is a much more reliable tool the the default port scanner. Nmap and zenmap are in the repositories.

BTW "stealth" when reffering to ports means nothing, it is just a marketing phrase the GRC uses.

---

### Post by The Tronyx on 2009-08-11
> **cariboo907 said:**
> 
btw "stealth" when reffering to ports means nothing, it is just a marketing phrase the grc uses.

<3

Aaaaaaand sig updated.

---

### Post by amac777 on 2009-08-11
> **cariboo907 said:**
> BTW "stealth" when reffering to ports means nothing, it is just a marketing phrase the GRC uses.

I was under the impression that a port can be:

**open**: when you try to connect, a service accepting connections on this port will respond.

**closed**: when you try to connect, you will receive a message that the connection attempt is refused (because there is no service accepting connections)

**stealth**: when you try to connect, you will will not receive any response at all and the connection will eventually timeout. It is like the computer you are trying to connect to is turned off.

So 'stealth' does appear to mean something when referring to ports. am I wrong?

---

### Post by pizmooz on 2009-08-11
nmap refers to what you call 'stealth' as 'filtered'.  The machine just drops the packet for this port.  If you want this behaviour on your machine use iptables.
Remember when you are behind a NAT router you need to forward a port for in order for someone to actually access an open port from rest of the internet.

---

### Post by cdenley on 2009-08-11
> **amac777 said:**
> I was under the impression that a port can be:

**open**: when you try to connect, a service accepting connections on this port will respond.

**closed**: when you try to connect, you will receive a message that the connection attempt is refused (because there is no service accepting connections)

**stealth**: when you try to connect, you will will not receive any response at all and the connection will eventually timeout. It is like the computer you are trying to connect to is turned off.

So 'stealth' does appear to mean something when referring to ports. am I wrong?

It means something, but nothing meaningful. If incoming packets are dropped instead of rejected, that doesn't necessarily make you more secure.

---

### Post by bodhi.zazen on 2009-08-12
> **cdenley said:**
> It means something, but nothing meaningful. If incoming packets are dropped instead of rejected, that doesn't necessarily make you more secure.

+1

see : [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

By default all ports are either closed or bound to 127.0.0.1

I am guessing you are seeing your clients in your port scan - firefox, torrents ??

---

### Post by dragos2 on 2009-08-12
If you installed nmap using the apt-get then you are running the buggy version.
Install a more recent version from source or from rpm's using alien.

---

