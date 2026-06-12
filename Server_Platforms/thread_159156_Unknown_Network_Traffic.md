---
title: "Unknown Network Traffic"
date: 2006-04-12
forum: Server Platforms
---

### Post by WelterPelter on 2006-04-12
Every once in a while, I notice some network traffic coming and going from my ubuntu box (which is connected via ethernet to the router). I doubt anything unusual is going on, but I *do* wonder what's up. Which program is interacting with the network? 

How do I find this out? Is there a simple utility that traces the source of this traffic? 

Thanks.

---

### Post by ssalman on 2006-04-12
I'm no expert, but give "ethereal" a try. You'll need to install though.

---

### Post by fdoving on 2006-04-14
With 'lsof -i' you can see the list of connections like this:
```

COMMAND    PID     USER   FD   TYPE  DEVICE SIZE NODE NAME
ssh      16131    frode    3u  IPv4 1141026       TCP 192.168.0.100:37131->server.example.com:ssh (ESTABLISHED)

```

That would tell you what's going on, and where. For speed and such you can use 'iptraf'.


- Frode

---

