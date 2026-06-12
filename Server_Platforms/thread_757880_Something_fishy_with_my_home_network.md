---
title: "Something fishy with my home network"
date: 2008-04-17
forum: Server Platforms
---

### Post by tobydeemer on 2008-04-17
Hi all-

I have a small home network setup- an Ubuntu server with Xubuntu desktop installed, and an XP workstation, and my laptop running 7.10. 

So here's the issue- on the server, I keep getting attempted VNC connections, blocked by the firewall and displayed in Firestarter. No biggy. But today I looked in Active Connections under the status tab, and I had a ton of active connections under port 2086/gnunetd, with IPs like 65.60.202.26 , 85.25.67.118 , 216.139.209.22 etc. When I do a right click and select look up host names, they come back as d60-65-26-202-26.col.wideopenwest.com, etc, and the really unsettling thing is when I do that, Firestarter crashes out and I have to restart it. I looked in System Monitor, and network traffic is way more active than what I've done on the server today. My server's IP address is listed as the source, and these weired IPs are listed as the destination.

I have a LAMP stack running, as I was planning to host a small site to learn how, etc. I also have postfix installed.

So has my machine been compromised in some way, is this a part of the server system I was just ignorant of, is it now a spam bot, or what?

Forgive me for being a little ignorant, but what log files ought I to look in, where should I look for traces of illicit activity, etc? 

If I just let Firstarter sit there, nothing happens. It logs blocked events, tracks activity, etc. It's only when I try to look up the host names of the active connections that it crashes.

So am I being paranoid and these are just part of system processes, or is something going on?

Any and all help is appreciated.

---

### Post by tobydeemer on 2008-04-17
Edit:

I changed the policy in Firerstarter from blacklist to whitelist, and the strange connections have obviously stopped. I can still access the storage/shared folders I have set up on the network through Samba so that's good. But since I did that, I keep getting blocked attempted connections from the server aimed at all sorts of random IP addresses. One that's in a lot it 85.25.67.118. Another is 65.27.155.209, and many others. Someone please help, or tell me where to look. I feel kinda stupid right now...

---

### Post by tobydeemer on 2008-04-17
A little bump. 

I'm not trying to be a bother, I'm just wondering what's going on. I've been reading about gnunet, trying to decipher what may be happening. I never knowingly installed, initialized or autorized file sharing connections. So did I do it by accident somehow?

---

