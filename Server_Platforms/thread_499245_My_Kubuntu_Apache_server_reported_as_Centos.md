---
title: "My Kubuntu Apache server reported as Centos?"
date: 2007-07-12
forum: Server Platforms
---

### Post by cookieforyou on 2007-07-12
If I do:
```
# nmap -A -O -P0 -p 79-80 (my server URL here)
```
the following is reported:
> Interesting ports on ...................:
PORT   STATE  SERVICE VERSION
79/tcp closed finger
80/tcp open   http    Apache httpd 2.2.3 ((Ubuntu) PHP/5.2.1)
Device type: general purpose
Running: Linux 2.6.X
OS details: Centos 4.3 Linux 2.6.17.11-grsec (Centos 4.3, X86)
Network Distance: 0 hops

Anyone know why?

---

### Post by MJN on 2007-07-13
The OS ID is a result of so-called 'fingerprinting' by NMAP. That is, it's attempting to identify the OS through a series of tests, the answers/responses to which are compared against known results from known OS's to create a match. It's not foolproof and hence won't always get it right.
 
I've never used NMAP but there is probably some means to configure what tests, to what level, are peformed - perhaps a more (or even less) thorough testing regime might match the OS correctly (assuming your OS is sufficiently fingerprinted in the database).
 
Mathew

---

