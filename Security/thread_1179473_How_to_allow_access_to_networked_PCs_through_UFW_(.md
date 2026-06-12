---
title: "How to allow access to networked PCs through UFW (on server 9.04) for email,net,files"
date: 2009-06-05
forum: Security
---

### Post by daaussie on 2009-06-05
RE: How to allow access to networked PCs through UFW (on server 9.04) for email,net,files????

**Details:**
2 Ubuntu 9.04 Workstations
1 Vista Workstation
Networked to a Ubuntu Server 9.04 (samba file system)
The samba file server is configured such that you need server user/pass for each workstation to logon to it. 

I achieved automatic logging on for each Ubuntu workstations by entering this into "sudo gedit /etc/fstab". **Not sure if this is the best and secure way to do it???**

**Needs for workstations:**
Internal access of files on server
email (POP) to be allowed to be sent/received
internet access to websites
some secure sites we access are https port 443

Can anyone provide a very basic step by step guide on what commands and ports that should be set up in the UFW to achieve highest security but still enable the above (I know how to enable UFW)?? _I have the commands, but don't know the numbers and what it does._

_**Also does anyone know how to tell the UFW to shut down all access overnight and on weekends?**_

---

### Post by bodhi.zazen on 2009-06-05
What is it you are trying to do ? Configure a router ? Or just configure your firewall ?

If you are trying to do a router, take a look at iptables or shorewall.

Otherwise, what is it you are not understanding ?

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by daaussie on 2009-06-06
Sorry I wasn't clear enough.

I want help/opnions with how to configure a firewall for the server.

Essentially I want opinions on how to have: **secure/passworded workstation access to files on server** Presently I use smbfs only with password.

I also am interested to know how to configure the UFW(only for when I eventually put the server in between router and the workstations):
Workstation access to email (POP) with ISP/host - 
Workstation access to the internet for general use
Workstation access secure sites we access are https port 443


I have a router as the front line of defence - I just use high settings (as I wouldn't know how to define the rules).

What I want is to have a go at setting up the UFW on the server (behind the router) just as a second layer of security in case the first line is broken.

---

### Post by brian_p on 2009-06-06
> **daaussie said:**
> 

I also am interested to know how to configure the UFW(only for when I eventually put the server in between router and the workstations):
Workstation access to email (POP) with ISP/host - 
Workstation access to the internet for general use
Workstation access secure sites we access are https port 443

These all involve outgoing requests, which I believe ufw doesn't handle. So you would have to delve into iptables rules. But why you would want to filter connections out is puzzling.

> What I want is to have a go at setting up the UFW on the server (behind the router) just as a second layer of security in case the first line is broken.

Quite how do you envisage this 'first line' being breached? I ask partly because if you don't have some idea you could not rely on the second layer.

---

### Post by The Cog on 2009-06-07
You want to put the server between the workstations and the routers? So the server acts as an internal router?

If so, UFW probably isn't good enough to allow the configuration you need. You need to either use an iptables script, or use guarddog which I think can handle the more complicated configuration of different zones that you need. But I would query why you want to complicate things like that in the first place.

---

### Post by cariboo on 2009-06-07
Have a look at arno's iptables firewall, it is in the repositories. This may be a little overkill for what you want, but it should be a good example of what you need to do.

---

