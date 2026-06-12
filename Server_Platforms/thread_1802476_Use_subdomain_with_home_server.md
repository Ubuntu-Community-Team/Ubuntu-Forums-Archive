---
title: "Use subdomain with home server"
date: 2011-07-12
forum: Server Platforms
---

### Post by ipedrolima on 2011-07-12
Hello everyone,

I've been working on a ubuntu home server for a couple of days now, and I've been able to solve most of my issues only by reading old threads here. I'm currently using Ubuntu desktop 11.04, but most of the time I'm using the command line interface through ssh on my MacBook. I was going to install Ubuntu Server, but as a complete newbie I decided to stick with the GUI for emergencies.

Anyway, I have a domain name ([www.example.com](www.example.com)) and a website hosted on a certain provider, and I'd like to use a subdomain (home.example.com) that I can use instead of my No-IP name (example.servegame.info). I've learned that I should set a A record for that subdomain to my IP. The problem is, my ISP only gives me a dynamic IP--thus, I have to use no-ip. I've tried to set the A record to my no-ip address but my provider only allows me to input numbered IPs.

What should I do?

Thanks!

---

### Post by Bachstelze on 2011-07-12
In order for a name to resolve to another name (as opposed to an IP), you need a CNAME record, not an A record.

---

### Post by ipedrolima on 2011-07-12
Okay, so I've set a CNAME record pointing to my no-ip address and I'm waiting for it to propagate.

---

### Post by ipedrolima on 2011-07-12
Worked like a charm. Thank you very much!

---

