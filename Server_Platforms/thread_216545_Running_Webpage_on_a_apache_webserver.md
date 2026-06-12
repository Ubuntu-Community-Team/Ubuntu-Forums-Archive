---
title: "Running Webpage on a apache webserver"
date: 2006-07-15
forum: Server Platforms
---

### Post by tiger99 on 2006-07-15
Hi All
I am trying to setup a webserver to run my own webpage on my machine. I've read the server guide. It explained how to configure the apache2 webserver but it doesn't say anything about how to run a web page. 
Can someone please explain to me the process of running a webpage on a webserver? 
Where can I get a domain name for my webpage? Can I generate a new domain name from my webserver or do I still need to purchase one?

I am new in the server setup stuff. So, any detailed explaination/input will be really appreciated

Thanks

---

### Post by Randomskk on 2006-07-15
Some info..
1) You'll need to buy a domain, at a registrar such as GoDaddy
2) You'll need to run a name server, such as "bind9" (in the repos) to manage this domain name

Basically, buy your domain, and point it to your IP (you'll need a static IP!), setup BIND (check the server guide) and make sure router ports are forwarded (BIND needs 53 TCP and UDP) and you should be set.

---

### Post by az on 2006-07-15
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

From your home, you would use dynamic dns and then put your web pages in /var/www/

---

### Post by uncleclinto on 2006-07-16
I haven't even set up my server yet, but I do know from my WAMP server that DYNDNS.org is the place to go.  I also read a fabulous tutorial that I will try to find for you in the next 12 hours.  It explained dynamic dns services etc.  

GoDaddy is popular, but DYNDNS offers additional free services, such as port forwarding (in case your ISP blocks port 80 for non-business subscribers).  

Good luck!  More later.

ps: the folks in these groups are super-knowledgable and super helpful.  I'm just breaking into this Linux thing, and I have found tons of friendly prompt help.  :-D

---

### Post by mmcclure79 on 2006-07-28
Do you need DDNS if you are already running a webserver but with just the ip instead of a name? It's from home, but the ISP doesn't block port 80 or much of anything really.

---

