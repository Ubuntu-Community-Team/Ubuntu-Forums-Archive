---
title: "can ubuntu 11.10 in virtualbox conncet to internet ? ?"
date: 2012-05-12
forum: Virtualisation
---

### Post by Docmero on 2012-05-12
[CENTER]Hi , I want to install ubuntu 11.10 in a virtualbox but
_1- can the system in the virtual machine connect to Internet itself ? or it's gonna be just an offline system ?_  

. I'd like to add that the host machine is also ubuntu 11.0 ,
 but I want another ubuntu in a virtualbox for experiments on the system 
because I'm a new linux user and I don't want to miss up my stable host system . Thanks .

[CENTER]_2-What should I use to ensure the Internet connectivity to the virtual machine and good performance ? Vmware or virtualbox or it doesn't matter ?_[/CENTER]

I'm not gonna the system for complex issues like servers for example .
 I want the Internet on the virtual system just for updating and installing apps .

Thanks [/CENTER]

---

### Post by memilanuk on 2012-05-13
Dude... fix that formatting.  Center justified is hard enough to read I just about didn't bother replying...

To answer your question, yes, the guest operating system inside virtualbox will have several options for network connectivity.  The simplest, and I believe default, is 'NAT'.  Basically your guest VM can connect to the physical network just fine for things like dhcp (automatically set up), dns, ntp, http, email, whatever.  Because it is effectively behind a NAT 'firewall' outside machines can't initiate connections directly to the guest VM.  There are other networking modes where that can change (bridged) or where multiple VMs can 'see' each other on a virtual LAN (internal networking).  But the default and simplest/most fool-proof for starting out is NAT, which will work fine for your stated needs.

---

