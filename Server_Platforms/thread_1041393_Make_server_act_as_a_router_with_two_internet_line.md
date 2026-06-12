---
title: "Make server act as a router with two internet lines"
date: 2009-01-16
forum: Server Platforms
---

### Post by c_tower3 on 2009-01-16
Hi,

I'm considering the Ubuntu server edition for a server computer which will act as a router. It has three Ethernet adapters of which two are connected to two different modems. I've tried search a bit and looking at the documentation, but I couldn't find a clear answer to my question.

I want the following layout for the network:
[Computers] -> [Switch] -> [Server (DHCP)] -> [Modem #1/#2] -> [ISP #1/#2]

So basically the feature I'm looking for is the ability to spread the traffic seamlessly between the two Internet lines (depending on the load). Is this possible without facing too much trouble?

Thanks in advance!

---

### Post by Wiebelhaus on 2009-01-16
What your trying to do is a "poor man's network" Basiccally you do it with a [crossover cable]("http://www.makeitsimple.com/how-to/dyi_crossover.htm") which you'll need to make.

---

### Post by c_tower3 on 2009-01-16
Hi,

Sorry, but I didn't quite catch your drift there. Where would a cross-over cable go? Between the modems?

Anyway I thought cross-over cables were for linking two computers to each other without any additional hardware. What I want to do is to share 2 large Internet connections on a network of around 12 computers.

---

### Post by jerome1232 on 2009-01-16
Is this the only function of that server? If so you might want to look at [Smooth Wall]("http://www.smoothwall.org/") or [ip cop]("http://www.ipcop.org/"). They turn you computer into dhcp/dns server, Can also do nat and many much more advanced features that I know nothing about :)

It Gives you an easy to access/admin web gui (just like most routers)

---

### Post by Wiebelhaus on 2009-01-16
> **c_tower3 said:**
> Hi,

Sorry, but I didn't quite catch your drift there. Where would a cross-over cable go? Between the modems?

Anyway I thought cross-over cables were for linking two computers to each other without any additional hardware. What I want to do is to share 2 large Internet connections on a network of around 12 computers.

OH OK! I misunderstood , my bad.

---

