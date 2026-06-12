---
title: "What's the best way to use a Authentication Server?"
date: 2017-07-26
forum: Server Platforms
---

### Post by centrixde on 2017-07-26
Hello :)

I currently use a VPS as an Authentication Server for my Proxmox Network. All the Servers are only accessible from the VPS through SSH (HTML, etc... are not affected). I only start the VPS when I need it because I currently don't use SSH Keys for the Proxmox VM's because I'm changing my overall setup. Now my question is, what's the best use case? SSH Agent forwarding, an own SSH Agent on the VPS or are they some other options?

I'm mainly using a Windows 10 Installation with multiple Ubuntu Installations on Server, so I have to use programs to use some sort of SSH Agent, etc...

Greetings,
CentrixDE

---

### Post by wildmanne39 on 2017-07-26
*Thread moved to **Server Platforms**.*

---

### Post by Paul Weaver on 2017-08-04
So your servers only accept ssh connections from this VPS? 

Only use ssh keys, if you want set up ssh to also require password authentication, at least into the VPS. I think that's a bit overblown to be honest.

Use SSH agent forwarding on the server, don't keep your private ssh keys on a VPS! Keep it on your laptop (encrypted partition) with a strong passcode. It's been over a decade since I used windows, but I think putty dealt with caching ssh keys just fine.

---

