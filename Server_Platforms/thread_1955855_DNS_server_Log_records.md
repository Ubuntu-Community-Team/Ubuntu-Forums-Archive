---
title: "DNS server Log records"
date: 2012-04-10
forum: Server Platforms
---

### Post by mandza on 2012-04-10
hi,
does DNS server save log records of users that connect to internet.
Actualy what i want to do is next;

i have 30 PC's every one on different location, if i setup an DNS server and redirect all PC's dns to this server can i see logs of connected users who enter which site? and can i prohibite access to some sites???
thank you for your help ...

---

### Post by SeijiSensei on 2012-04-10
DNS servers don't log queries; any active server would fill up the disk pretty quickly.  You could add an iptables rules to the server that logs UDP traffic on port 53, which is the port to which queries are sent.

If you want to control access to web sites, you're better off learning how to build a transparent Squid proxy and use its "access control lists."  If, however, the clients are all over the Internet, each connected to its own ISP, this isn't going to work for you.  You need to be able to force the clients to use the proxy, usually by making it their default gateway via DHCP.

---

### Post by mandza on 2012-04-10
> **SeijiSensei said:**
> DNS servers don't log queries; any active server would fill up the disk pretty quickly.  You could add an iptables rules to the server that logs UDP traffic on port 53, which is the port to which queries are sent.

If you want to control access to web sites, you're better off learning how to build a transparent Squid proxy and use its "access control lists."  If, however, the clients are all over the Internet, each connected to its own ISP, this isn't going to work for you.  You need to be able to force the clients to use the proxy, usually by making it their default gateway via DHCP.

SeijiSensei Thank you for your replay.
Yes users/clients are all over the internet. I want to see where users go on internet and sometimes to prohibite access to some sites.

Does anyone know is this posible with firewall???
i dont know where to start :(

---

### Post by SeijiSensei on 2012-04-10
If you have no control over the clients via some type of centralized service like DHCP, I don't see any hope of this, no.  How are you planning on enforcing them to all use your DNS server in the first place?

---

### Post by mandza on 2012-04-10
All PC's belongs to my company branch offices, so i make all setting on PC's.
As i said i want to see what employees do on internet (does they work or they are on facebook or something else) and to prohibite access to some sites. but i want to do that from one place. When i make some changes i want to effect everyone.

Thank you for your help again.

---

### Post by SeijiSensei on 2012-04-10
You could configure their browsers to use a Squid proxy as I mentioned earlier.  Of course, any knowledgeable users would know how to disable that right away, or they could just install another browser that doesn't have the proxy set.

What you propose to do has to rely on naive users who can't figure out how to change their DNS or proxy settings.  Are you managing all the computers with something like Active Directory, or do you simply connect remotely to each one and configure it to your liking?  If you can't lock the settings, then any competent user will be able to end-run your controls.

How are the offices themselves connected to the Internet?  Do you manage the egress routers? You might be able to establish controls that way.

---

### Post by mandza on 2012-04-10
i have remote acces to all computers, also i have physical access to.
i use regedit to disable dns changing.
if you know any more effective i will be glad if you share it.
as i said i want to do this but i dont know how and where to start :(

---

### Post by mandza on 2012-04-10
mod can you delete this post.... this was hijacked.

---

### Post by SeijiSensei on 2012-04-10
If you can enforce a web proxy via regedit, then I'd suggest using that with Squid on your end.  I haven't used Windows for a very long time, so I don't know what you can and cannot control via the Registry.

---

### Post by mandza on 2012-04-10
Ok, thank you a lot.
i will try it in a few days.

---

