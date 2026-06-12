---
title: "Services &amp; Ports"
date: 2008-08-07
forum: Security
---

### Post by pedja_portugalac on 2008-08-07
After checking my active network services I discovered 2 active services  I can't find what program use that and what for. So I need your help please?

**-First port is: 5353 (Mdns)**
Darren Spruell on 2007-12-07 said:

5353/udp is more generally associated with multicast DNS used commonly for Zeroconf service discovery on a LAN. Besides Apple's Bonjour, another notable implementation is found in the Avahi service discovery toolset.

******* I have tried to learn fast about Mdns, Zeroconf and also Avahi and this is where I am.
> Avahi is a system which facilitates service discovery on a local network. This means that you can plug your laptop or computer into a network and instantly be able to view other people who you can chat with, find printers to print to or find files being shared. This kind of technology is already found in Apple MacOS X (branded Rendezvous, Bonjour and sometimes Zeroconf) and is very convenient. Avahi is mainly based on Lennart Poettering's flexmdns mDNS implementation for Linux which has been discontinued in favour of Avahi.
I presume this is legitimate Avahi service on Ubuntu but I am confused by this IANA database?
```
wCrat	5343/tcp	#[trojan] WC Remote Administration Tool
BackConstruction	5400/tcp	#[trojan] Back Construction
BackConstruction	5400/tcp	#[trojan] Back Construction
BladeRunner	5400/tcp	#[trojan] Blade Runner
```
I can't see port 5353 and I'm afraid this possible trojans work on range between 5343 and 5400?

**-Second port is: 42067/udp (Service Unknown)**

Any comment welcome.

---

### Post by The Cog on 2008-08-07
The command
> sudo netstat -plnt
should tell you what process is opening the port, after which 
> ps -f <pid>
should give you all the command line that launched it.

---

### Post by pedja_portugalac on 2008-08-07
Thank you for this. I would like to ask you, also, if you have this services actives on your machine? 

[img]http://img520.imageshack.us/img520/1367/activenetworkservicesvi2.jpg[/img]

---

### Post by The Cog on 2008-08-08
I have 68 open - this is opened by the DHCP client - used when autoconfiguring the IP address of hte machine.

I don't have the other two, and don't know what they might be. Try
**sudo netstat -lun**
to get the process IDs

---

