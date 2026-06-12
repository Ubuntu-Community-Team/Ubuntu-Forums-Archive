---
title: "Number of LTSP Clients possible?"
date: 2010-06-02
forum: Server Platforms
---

### Post by meadmarc on 2010-06-02
Good morning!

I am setting up my first LTSP server, and presently have it running with about 13 clients.

From what I have read, the key to making this work well is RAM, and the ratio is about 100 MB RAM per client.

I am running a Dell Poweredge server with two dual-core 2.4GHZ CPU's, and 2.5 GB RAM (I will upgrade to 4 within a week, which is the server's limit).

As I watch the system monitor, the RAM seems to be doing fine, but the CPU's just fly up to the high 90's for all four, and stay there for the most part.

I replaced Gnome with LXDE as the default desktop environment, and that helped some, but we're still seeing extremely high CPU utilization.

Our target for this installation is 40 cleints; our RAM should support that.  

But is this normal for the CPU's?  Can this server handle 40 clients running LXDE?

I did order a pair of matched intel 2.8GHZ's off ebay that should plug in, that's all the server can do.

---

### Post by meadmarc on 2010-06-03
Does anyone know this?

---

### Post by jeight on 2010-09-08
You will see a high CPU usage when using a standalone LTSP server. If you start clustering your ltsp servers with loadbalacing you will see that go down tremendously. Chances are with a standalone server you won't see much of a change in CPU usage between 10 - 40 thin clients because most of the applications that are using that CPU are already running and so it shouldn't change much.

---

