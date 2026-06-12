---
title: "VPS Java server appears to be down - firewall issue?"
date: 2013-05-25
forum: Server Platforms
---

### Post by Zxoraz on 2013-05-25
Hi,
I've recently been trying to set up a java server on a VPS I rent.
It's a Minecraft server if that matters

I installed Java and it seems to work fine, the VPS is managed through a control panel named Parallels in which I opened the required port (25565)
The server seems to be able to bind to that port and it claims to be running yet I can't see that the server is running on other machines.
I edited iptables to allow all traffic, and I did the same on the control panel to just to see if it's the firewall that's blocking it but even when allowing all traffic the server won't allow me to connect to it.

I'll add that I have a few other servers running on the same VPS (Apache, Mysql, FTP) and they're all working just fine, and stop working if I choose to block them with the firewall.

I run the minecraft server manually by logging in through SSH and launching the jar file using java.

It's not only about Minecraft anymore, I'm just really curious why it won't work, and what I am missing here..

Thanks in advance.

---

### Post by DJ_Max on 2013-05-28
What do you mean by "other machines". What do you logs say on client/server

---

