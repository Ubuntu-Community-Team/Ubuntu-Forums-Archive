---
title: "Ubuntu as Primary Domain Controller"
date: 2011-03-24
forum: Server Platforms
---

### Post by MMegaTron on 2011-03-24
Hi,

I need to setup windows Active Directory system and want to use our existing ubuntu server as Primary Domain Controller (samba).  What I'd like to know is if its possible to setup a machine running standard Ubuntu as the PDC, or if I would need to install Ubuntu server.  I've searched for quite a long time and have found absolutley no trace of an answer!  I guess I'm probably looking in the wrong place though.

Thanks,
Jack

---

### Post by cariboo on 2011-03-24
All the services work the same whether it is a desktop system, or a server install. Keep in mind a gui adds extra overhead if you are low on resources, and there could be security issues running a gui all the time. The best way to run a server with a desktop is to disable/remove gdm/kdm/xdm, and only start the desktop when you need it by using the startx command, and then logging out when you are done.

---

### Post by koenn on 2011-03-24
wrong question.

Begin by making sure you understand what you're trying to do (ag: a Primary Domain Controller is something from NT4 domains, yet you're talking about an Active Directory domain ... ), 

then check if the solution you're going for, actually solves your problem (eg: are you quite sure that it's possible to have Samba do Active Directory services ?)

then worry about whether you'd rather run this on a desktop, or a server.
As Cariboo907 pointed out, both can be done.

---

