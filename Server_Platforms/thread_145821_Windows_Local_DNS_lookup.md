---
title: "Windows Local DNS lookup"
date: 2006-03-17
forum: Server Platforms
---

### Post by jazee on 2006-03-17
I have a ubuntu box running bind9. I have placed all of the zones in there and they look up fine. But thats not the problem. The problem lyes on the local Windows Boxes on the network. I have set the Primary DNS to the local ip on the ubuntu server and the secondary DNS as the router ip. If I use IE and type in the address it works just fine. But if I use firefox 1.5 it doesn't look up localy. Instead it only goes out to the internet and looks. So any local DNS record on the server doesn't work in Firefox. Very weird to me but any ideas.

---

### Post by claes on 2006-03-17
Windows will only use the first dns server in the list. It will only go to the second one if the first dns server does not answer. And if the first dns server answers that it don't know that will count as an answer, so it will not go to the next in the list. Not sure if this explains the problem or if I missunderstood you.

Claes

---

### Post by jazee on 2006-03-17
Primary DNS - Local DNS on network - 1st on list
Secondary DNS - Internet DNS - 2nd on list

The primary dns contains all the local to the network websites. The secondary dns is pretty much the ISP's DNS. The problem is that the windows computers aren't even asking the local DNS for a look up. The local DNS is running and is working fine being that the server and my other Ubuntu box both retrieve the local DNS's just fine.

---

