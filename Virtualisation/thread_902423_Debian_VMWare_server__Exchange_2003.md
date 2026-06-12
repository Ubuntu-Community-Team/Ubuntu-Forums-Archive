---
title: "Debian VMWare server / Exchange 2003"
date: 2008-08-27
forum: Virtualisation
---

### Post by TheGameAh on 2008-08-27
Hello all.

I've had great success running what I call a poor man's VMWare server.  Debian Etch 64, loaded with just VMWare server, to host VMs.  Been running rock solid for a while now (Just a few VMs.  Blackberry server, Terminal Server, a special timeclock XP install).

I'm looking to maybe expand now.  I have an underutilized dual core that I'd like to use for the same idea.  But I'd like to just run 2 VMs, but they're beefier than what's above.  Mainly, a file server/solidworks vault, and an Exchange 2003 server (80 users, about 50 gigs of data).

I've been studying like crazy, and I'm finding a lot of info about Exchange on VMware's flagship stuff, like ESX(i).  But nothing regarding running Exchange on VMWare server.  I can understand why, VMWare server is the inferior product, and Exchange is a big boy.

But surely, someone must have tried it, and has a story or two to tell.  Can someone recommend a yah or nay, any experience at all with trying to either migrate Exchange 2003 to a VM, or flat out convert to a VM?

---

### Post by mellowd on 2008-08-27
I've heard good things with ESX server and databases. Not so good with vmware and the same thing

---

### Post by HermanAB on 2008-08-27
> **mellowd said:**
> I've heard good things with ESX server and databases. Not so good with vmware and the same thing

Yes, Exchange will run on VMware Server.

However, if you want a real mail server that can handle 256 TB of mail in an Oracle database, then you need Citadel.  Exchange is rather dinky compared to Citadel.

---

### Post by mellowd on 2008-08-27
> **HermanAB said:**
> Yes, Exchange will run on VMware Server.

However, if you want a real mail server that can handle 256 TB of mail in an Oracle database, then you need Citadel.  Exchange is rather dinky compared to Citadel.


It will run, but we're talking about high performance

---

### Post by Mart on 2008-10-27
Wow... I had to do a double take and make sure this wasn't posted by myself.  We have very similar setups and goals.

Basicly what I'm in the process of doing right now is moving a few virtual servers to a temporarty debian host so that I can reconfigure our primary server as a virtual host also using esxi managed by virtual infrastructure.  From what I've read so far an exchange p-v conversion is not the best path to take so I plan to do my exchange install directly on to a virtual guest.  I have the move and installations plotted out over the next month and a half since I'm a one man shop supporting 200 users.

I'll post up any gotchas I find as I go.

---

