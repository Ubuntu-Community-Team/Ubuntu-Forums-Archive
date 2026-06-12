---
title: "UFW not blocking IP range"
date: 2020-11-18
forum: Security
---

### Post by dookster on 2020-11-18
I am running an Ubuntu box on digital ocean droplet with Nginx.
I have set up a block for an IP range xxx.xxx.xxx.0/24
This deny rule is set as rule #1 in UFW.

Even though not necessary I have reloaded UFW, checked the status, config seems correct.
However, IP addresses from that range are still hitting the website.

I know the order of rules in UFW is important so for good measure I added the above deny rule as #1.

So, what is wrong here? Why are those IP addresses not being blocked by UFW?

---

### Post by EuclideanCoffee on 2020-11-18
What's the rule? It should something like this.

ufw deny proto tcp from 202.54.1.0/24 to any port 22

---

