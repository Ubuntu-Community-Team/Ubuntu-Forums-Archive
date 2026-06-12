---
title: "Which reverse-proxy or load balancer do you use?"
date: 2019-03-12
forum: Ubuntu, Linux and OS Chat
---

### Post by TheFu on 2019-03-12
Over the years, I've used a few different load balancers from hardware, DNS-round-robin, and software. They each have different uses.
At our small business, I've been using nginx the last decade since pound didn't support HTTPS.  Running about 20 different websites - a mix of static, RoR, php, and Perl webapps.

I know the world uses many others, like ha-proxy. Sorta fell into nginx since we were using it already as a web-server for the performance. Like having all external requests go through 1 "front-end" that has the different protections and terminates the SSL in a single place.

I don't think there are any wrong answers, just better answers for specific situations.
This article, [https://geekflare.com/open-source-load-balancer/](https://geekflare.com/open-source-load-balancer/) , 
has this list:
[LIST]
[*]    Seesaw
[*]    LoadMaster by KEMP
[*]    HAProxy
[*]    ZEVENET
[*]    Neutrino
[*]    Balance
[*]    Pen
[*]    Nginx
[*]    Traefik
[*]    Gobetween
[/LIST]

Nginx handed 200+ requests/sec from a RoR web-app here during performance tests with 99% handled in less than 1 sec.  Pound was handling less than 60 req/sec. I did enable micro-caching, just 1 sec makes a huge difference for performance and read-only requests don't really need to hit the DB.

So, what do you use?

---

