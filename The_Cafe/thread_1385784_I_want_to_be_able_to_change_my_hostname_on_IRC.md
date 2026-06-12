---
title: "I want to be able to change my hostname on IRC"
date: 2010-01-20
forum: The Cafe
---

### Post by CJ Master on 2010-01-20
I've googled for BNCs, Vhosts, all that yadda... I don't really understand it. Is there anyway to easily change my hostname on IRC?

(Using Xchat on Windows)

---

### Post by baddog144 on 2010-01-20
No, not really (as far as I know). You need to get a cloak generally, and that's network dependent. You should probably ask in the support channel for whatever network you're on.

---

### Post by CJ Master on 2010-01-20
I registered a hostname under DynDNS, now I just have to find a bouncer for windows that actually works and isn't insanely confusing.

Thanks for the advice, but I'd rather have it changed then cloaked. My network also doesn't support vhosts.

---

### Post by user1397 on 2010-01-20
you could always just make a new one.

---

### Post by YeOK on 2010-01-20
You can also rent a shell host, they are cheap, about £3 per month for a basic IRC bouncer. I use [ZNC]("http://en.znc.in/wiki/ZNC"),  not sure if it work on windows.

---

### Post by CJ Master on 2010-01-20
> **ubuntuman001 said:**
> you could always just make a new one.
I don't understand. I am trying to make a new hostname.
> **YeOK said:**
> You can also rent a shell host, they are cheap, about £3 per month for a basic IRC bouncer. I use [ZNC]("http://en.znc.in/wiki/ZNC"),  not sure if it work on windows.
Is a shell host required? Does there happen to be any way to get a free one?

---

### Post by Grenage on 2010-01-20
Your hostname is where you connection is coming from, you can only have a different one by proxying with a bouncer or shell account.  I'm not aware of any free providers.

You do mean hostname, not user name, right?

---

### Post by CJ Master on 2010-01-20
> **Grenage said:**
> Your hostname is where you connection is coming from, you can only have a different one by proxying with a bouncer or shell account.  I'm not aware of any free providers.

You do mean hostname, not user name, right?

Yes. For example, this is one I saw.

Person has connected (~Person@SHAM.WOW)

Something like that.. Just my own personal hostname like that SHAM.WOW one. Did he have to pay to do that?

---

### Post by YeOK on 2010-01-20
> **CJ Master said:**
> Yes. For example, this is one I saw.

Person has connected (~Person@SHAM.WOW)

Something like that.. Just my own personal hostname like that SHAM.WOW one. Did he have to pay to do that?

Depends, some IRC networks offer a Vhost service (free). If your ISP allows, you can sometimes set a reverse DNS, I doubt you can do this however. The other option is to rent a shell and use a bouncer. I don't know of any free services. Make sure if you do rent one, it allows you to set a custom hostname (rDNS).

---

### Post by CJ Master on 2010-01-20
I found a free shell account hosting service on SDF. How do I set rDNS? And after that, how do I use a bouncer on it?

---

### Post by YeOK on 2010-01-20
> **CJ Master said:**
> I found a free shell account hosting service on SDF. How do I set rDNS? And after that, how do I use a bouncer on it?

I don't know, usually rDNS is setup via an admin panel. Ask your host. As for a BNC, depends on the shell host, some will have easy to use menus, others will expect you to install it (./configure, make).

---

### Post by Dayofswords on 2010-01-20
> **CJ Master said:**
> Person has connected (~Person@SHAM.WOW)
underneath, there's your mildew

---

### Post by CJ Master on 2010-01-20
Ug. Turns out the shell host I found doesn't have support for BNC. Does anyone know of a free one that does, that doesn't require you to send in a postcard or something ridiculous like that?

---

