---
title: "Ubuntu small/medium business network theorycrafting"
date: 2009-04-08
forum: The Cafe
---

### Post by The Keeper on 2009-04-08
I have a little theorycrafting project going on and at some point I'm hoping to test it in practice. Unfortunately I haven't created business networks before, let alone linux networks.

The network infrastructure has following services running on Ubuntu servers;
- Firewall (+ NAT & Gateway)
- Domain Controller
- Email server
- File server
- Local APT mirror
- Intranet server

Now if I go and turn them into actual server boxes, the network looks something like this;

INTERNET
|
Firewall / Gateway / NAT server
runs firewall (iptables), DNS, DHCP services
|
Domain Controller
runs Samba file and printer services
|
Email server
runs POP3, IMAP, SMTP services, probably Squirrelmail
|
File server 
network storage to store personal files on and runs local APT mirror
|
Intranet server
hosts company intranet and other web applications via Apache/MySQL

And now to questions;
- How does the network infrastructure look in theory? This is supposed to be a small/medium business network.

- Should Domain Controller take care of DHCP and DNS services instead of the Fireall/Gateway server?

- I need some pointers how to add some redundancy to the network infrastructure. Each of the five servers would need an active backup server too that kick in if the primary server goes down or needs help to cope with load. But how do I keep all the data in sync between primary and secondary servers?

Thanks in advance. :)

---

