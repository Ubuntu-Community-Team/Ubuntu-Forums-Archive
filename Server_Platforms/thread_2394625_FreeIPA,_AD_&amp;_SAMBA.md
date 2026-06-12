---
title: "FreeIPA, AD &amp; SAMBA"
date: 2018-06-19
forum: Server Platforms
---

### Post by jadeg on 2018-06-19
HI

I'm trying to setup a FreeIPA central authentication server for our 150+ servers, I have it setup and tested and working. It authenticates against usersnames and creates home directories.
We have noticed an issue, When a Windows desktop (On Active Directory) accesses a Samba share from a server that is joined to FreeIPA, we get a samba panic or segfault, It looks like Samba dies and restarts.
There is no trust setup between the two domains, and the domain names are different, example.com and ipa.example.com. I'm not sure if we should try a completely different domain name. I've also tried a few different configs on Samba without much luck. Any ideas what direction I should be focusing on?
Using: 
Ubuntu Server 14.04.3 LTS
Samba:amd64/trusty-security 2:4.3.11

---

