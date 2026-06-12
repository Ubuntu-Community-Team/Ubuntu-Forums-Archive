---
title: "Ubuntu 10.04 Host - WinXP Guest - Can I Share Files From Windows Using NAT?"
date: 2010-11-11
forum: Virtualisation
---

### Post by AlexanderDGreat on 2010-11-11
Hi my problem is simple, can anyone help me? I'm using:

Ubuntu 10.04 LTS (Host)
Windows XP (Guest)
Network Card 1: NAT

Can I share folders from Windows XP, that other Computers in my LAN be able to access?

The reason, I'm running Quickbooks Server on Windows XP, I want to access that program on my other computers in my local network via Quickbooks for workstations.

Also, I want to use Windows XP as the FILE SERVER, I want other computers in my local network (be it Windows or Ubuntu) to access that Windows XP guest file server, that is, hosted on my Ubuntu 10.04.

I'm using NAT on Ubuntu(Host) - Windows (Guest). Is this impossible or not?

What workarounds should I do? Thanks.

---

### Post by lmarmisa on 2010-11-11
You can not use NAT if you wish that other PCs of your LAN are able to access your XP VM.

The solution to your problem is very simple: switch from NAT to Bridged Adapter. After this change, your XP server (VM) will be conneced to your LAN in the same way than any other PC.

---

### Post by AlexanderDGreat on 2010-11-12
Hi Imarmisa - Thank you for that response. OK will just use Bridged. :)

---

