---
title: "System management alternative"
date: 2008-12-12
forum: Server Platforms
---

### Post by folke on 2008-12-12
Hi,

I am looking in to an alternative to our old webmin installations.

Is the only option out there Landscape?
There are a lot of isp type of web apps but I can't really find anything on system management.

What I am looking for is somthing that can handle apt management and such.

--
Regards Folke
Sweden

---

### Post by gtdaqua on 2008-12-12
You can turn on automatic security updates so they are downloaded and installed automatically. 

Other than that, what exactly are you looking for?

---

### Post by vpsville on 2008-12-12
In all seriousness, I recommend the command line.  Webmin is not far away from it and Ubuntu makes the command line quite easy.

---

### Post by lykwydchykyn on 2008-12-12
I've heard a lot of Debian admins use cfengine, but I've never been able to get my head around it.

There's also puppet.

I do things the hard way still with cssh.

Think about it, though; if there were a good free alternative, why would Canonical be using Landscape as a selling point for support contracts?

---

### Post by folke on 2008-12-16
> **lykwydchykyn said:**
> I've heard a lot of Debian admins use cfengine, but I've never been able to get my head around it.

There's also puppet.

I do things the hard way still with cssh.

Think about it, though; if there were a good free alternative, why would Canonical be using Landscape as a selling point for support contracts?

Well, that's true. I was just checking out the alternatives.
From my point of view I think that Landscape is perfect if you want support from canonical. I am not saying that it is a bad thing.

We are today checking our servers with Zenoss core. And I will see if I can use Nagios check for apt status.


--
Regards Folke

---

### Post by gtdaqua on 2008-12-16
> **folke said:**
> Well, that's true. I was just checking out the alternatives.
From my point of view I think that Landscape is perfect if you want support from canonical. I am not saying that it is a bad thing.

We are today checking our servers with Zenoss core. And I will see if I can use Nagios check for apt status.


--
Regards Folke


I use Zenoss Core too. Its production-grade and brilliant. But its a 'monitoring' system and not 'management' system. It definitely gives 'eyes' on what you have but not 'hands'. But again, that is not the purpose of Zenoss.

Canonical offers Landscape as a service and from the looks, its brilliant. If you got some dosh, then go for it.

---

