---
title: "server firewall"
date: 2011-06-10
forum: Server Platforms
---

### Post by mortified_pengiun on 2011-06-10
This may seem like a really dumb question, but I can't seem to find an answer .  

I installed ubuntu server and got it set up, and im trying to install shorewall as a firewall, but whenever i do sudo apt-get install shorewall i get a package not found error.

---

### Post by hawkmage on 2011-06-10
What do you get if you run the command:
```
apt-cache search shorewall
```

---

### Post by mortified_pengiun on 2011-06-10
After doing that it worked, thank you.

---

### Post by HermanAB on 2011-06-11
Howdy,

Bear in mind that many firewall scripts like Shorewall, are very old and contain hundreds of rules that are not needed anymore, since the IP stack has been improved over the years.

In my experience, you nowadays only need one rule in a server firewall, to protect against DOS and brute force attacks:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

All other rules seem to be quite superfluous and most of my servers - all the ones less than about 5 years old - have only that one single firewall rule.

---

### Post by Oceanwatcher on 2011-06-12
> **HermanAB said:**
> 
In my experience, you nowadays only need one rule in a server firewall, to protect against DOS and brute force attacks:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

Herman,

If I understand it correct, Ubuntu Server comes with UFW installed, but not enabled. I checked my newly installed server, and it is there.

On this page

[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

there is some information about it and I tested the dryrun example without enabling UFW. It listed a lot of rules and I am curious to where I should check if the rule you mentioned above is implemented?

What file should it go in? UFW looks like an easy tool to set the basic rules. I have a server online that will be used for streaming (flumotion) and nothing else. So I am only interested in opening the ports needed for the streaming.

Hope it is possible to get your thoughts on this.

---

### Post by spynappels on 2011-06-13
> **HermanAB said:**
> Howdy,

In my experience, you nowadays only need one rule in a server firewall, to protect against DOS and brute force attacks:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT



Should this be one of the first rules in the chain, say after a rule allowing all lo traffic? I have always inserted it as the second rule of my chains, after my allow lo traffic rule, but have yet to get a specific answer to this....

---

