---
title: "iptables for a newb"
date: 2008-09-05
forum: Server Platforms
---

### Post by croutezt on 2008-09-05
I have been playing with ubuntu for about the last 6 months. I have been able to do all kinds of fun things with it. Now i am ready to dive into building my own firewall from scratch. I am testing this in VMware workstation. my setup is that i have a ubuntu desktop behind a nat on one side a ubuntu server acting as the firewall and the rest of my network on the opposite side of the server. one interface on the server is behind the nat the other is bridged to my pcs network connection. From the ubuntu desktop I can ping both interfaces of the server but nothing beyond. At this point i am about ready to start over. Can anyone provide a simple tutorial on how to get a basic working setup.

Many thanks ahead of time.

---

### Post by gen.alcazar on 2008-09-06
I know this is not exactly what you asked for, but have you looked at any GUI based software to achieve this?  Like "firestarter" for instance?  Or even "guarddog", which seems much more flexible and feature-rich.

---

### Post by schettj on 2008-09-06
I like Shorewall as training wheels to raw, manly iptables direct manipulation.

---

### Post by croutezt on 2008-09-06
Well thats just it the primary reason for wanting to do this is to learn how all of those nice GUIs work. Thats why i just need a basic configuration to get me started. I am actually using PFsense as a gateway right now. I have also used Untangle and Astaro in the past and i liked all of them. Now i want to know how they work in practice.

---

### Post by croutezt on 2008-09-06
Ok well ive setup shorewall and it is working it looks like i can see what it did using iptables -L and in the shorewall-init log file.

Thank You for the suggestions

---

