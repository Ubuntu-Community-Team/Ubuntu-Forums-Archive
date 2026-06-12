---
title: "Mail server and network firewall on the same machine?"
date: 2006-10-20
forum: Server Platforms
---

### Post by ivanii on 2006-10-20
Does having mail server and firewall on the same machine affects security (on the Windows it does, as ISA server has different options when it is the only application installed and not).

---

### Post by hkgonra on 2006-10-20
Yes it is a dangerous thing to do.

---

### Post by ivanii on 2006-10-21
> **hkgonra said:**
> Yes it is a dangerous thing to do.

Probably, but I am still puzzled why then MS sells Small business server that installs mail server and firewall on the same machine? Yes, I don't think that MS is top of security, and specially not small business server, but I still wander whether they are selling something that is dangerous?

---

### Post by hkgonra on 2006-10-21
> **ivanii said:**
> Probably, but I am still puzzled why then MS sells Small business server that installs mail server and firewall on the same machine? Yes, I don't think that MS is top of security, and specially not small business server, but I still wander whether they are selling something that is dangerous?

I didn't know that small business server has that. 

There are a couple linux distro's made just to do that as well. 
SMEserver and Clarkconnect. Not to blast those two , in fact I like smeserver I just use it for everyhting but firewall. 
I just think as cheap as you can setup another ipcop box for a firewall (depending on traffic must p1 pc's will work fine) why do it on one machine.

---

### Post by elst on 2006-10-21
I think that the current version of SBS includes Exchange, and ISA, which does both firewalling and proxying. Putting everything on one box makes management easier. Also historically servers were expensive (particularly when proprietary licenses get involved), and routers were not powerful enough, so a small business might only have one server, and a router or even just a modem. And Microsoft are in the "big, expensive, but convenient software" business :).

Hardware router/firewall combination appliances are much more secure, and today there are cheap routers with enough processing power to do firewalling and VPN on their own. So exposing your Web proxy or mail server directly by making it the network firewall doesn't make much sense any more.

---

