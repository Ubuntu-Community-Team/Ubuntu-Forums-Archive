---
title: "Connecting to a machine behind firewall - Reverse Protocol/Tunneling?"
date: 2005-06-26
forum: Server Platforms
---

### Post by dmalopsy on 2005-06-26
The setup is below, pretty straightforward.

Me----------------INTERNET----------------------Firewall---------------------Server

I occasionlly need to connect to my dev server at work. The problem is that there is no easy way to connect to it, without forwarding ports, and access to the firewall server is not an option. So I can only have access to my machine at home, and the Server at work.
Is there a way to say use http tunneling or some sort of reverse protocol, that makes my Server connect to my machine first, thus allowing me to connect to it via SSH.
All ports on the Firewall from inside the network are open.
Any configuration and running of applications needs to be on "Me" or "Server" machines.

---

### Post by tonym on 2005-06-26
If "Me" has a fixed IP address you could set up openvpn on "Me" as server and "Server" as client.  This would then set up a usable line fully under your control.

---

### Post by spanishwasabi on 2005-06-30
Depending of the type of firewall, and the ports that are open, what about a ssh server in your Server running in an open port?

Just wandering, not sure if feasible...

G

---

