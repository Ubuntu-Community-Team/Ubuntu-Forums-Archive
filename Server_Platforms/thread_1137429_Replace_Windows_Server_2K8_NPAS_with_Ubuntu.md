---
title: "Replace Windows Server 2K8 NPAS with Ubuntu"
date: 2009-04-25
forum: Server Platforms
---

### Post by Megalomania on 2009-04-25
Hello,

I'm working in an office where my predecessor was a Microsoft representative and thus used Windows Server for everything, to the point where we have one server (running Windows Server 2008) running 5 other servers (a mix of server 2003 and 2008).

While this is not in and of itself a problem, the Virtual Machine that has the NPAS role installed (Network Policy and Access Server) and acts as our router has convinced itself that it is not a genuine windows copy and must be activated.  It does this from time to time and I'm sick of it.  Towards that end, I would like to move the NPAS service to another machine, preferably running Ubuntu Server.

Does anyone have experience configuring Ubuntu Server to perform the same operations as Windows Server 2008 with the NPAS role installed?

Thanks for any help,
John

---

### Post by HermanAB on 2009-04-25
NPAS is a simply a firewall/VPN/router.  Any Linux machine can do that.  Install UFW or Shorewall.

---

### Post by Megalomania on 2009-04-26
thanks - I was hoping that would be the case, but my experience has always been that windows server is like the mafia and once you're in, you're not getting out.

---

### Post by HermanAB on 2009-04-26
Hmm, MS likes to give fancy names to simple things and then sell it to the unwashed masses.

---

### Post by koenn on 2009-04-26
> **Megalomania said:**
> thanks - I was hoping that would be the case, but my experience has always been that windows server is like the mafia and once you're in, you're not getting out.

> **HermanAB said:**
> Hmm, MS likes to give fancy names to simple things and then sell it to the unwashed masses.

MS likes to take simple things and combines them in lots of complex ways with lots of other simple things. Then they give it a fancy name and sell it to the unwashed masses. The result is that, once you're in, you're not getting out,

any linux box can do routing, firewalls, and vpn. to get those to behave exactly they way they do in NPAS is a different ball game.

---

### Post by puelly on 2009-04-26
Firestarter is a nice tool to assist with setting up of natting and firewall policies on a ubuntu server.

---

