---
title: "Open ports?"
date: 2010-11-02
forum: Security
---

### Post by vorinoch on 2010-11-02
Hi guys, I'm somewhat new to Linux and thought I'd ask this question.   I'm running Lucid installed via Wubi.  When I nmap my local IP address, there's an open port that I'm unfamiliar with -- port 1024, kdm service.  I'm running the standard GNOME environment, and looking at my packages in Synaptic, kdm is not installed.  Is this cause for concern, or is this normal?

---

### Post by CharlesA on 2010-11-02
You will show an open port if you run a scan against localhost. You'd need to scan the machine from another one on the same network to get an accurate reading.

By default Ubuntu has no open ports.

---

### Post by NertSkull on 2010-11-02
There are lots of external websites you can use to check (at your own risk).

One I've heard of thats good is [www.canyouseeme.org](www.canyouseeme.org)

You can just put port 1024 in and see what happens.

---

