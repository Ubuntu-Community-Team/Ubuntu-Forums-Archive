---
title: "Continuation of DenyHosts"
date: 2014-05-18
forum: Security
---

### Post by thnewguy on 2014-05-18
DenyHosts is a useful security tool for blocking brute-force attacks against OpenSSH servers. As many of you may already know, the DenyHosts package was dropped from Ubuntu 14.04. The package was dropped because the upstream project was no longer being maintained.

The DenyHosts project has been forked is is now maintained at [http://denyhost.sf.net](http://denyhost.sf.net) People hoping to set up protection against brute-force attacks can find an update version of the software from the project's new website.

---

### Post by bashiergui on 2014-05-20
Cool. Thanks for sharing. 8)

---

### Post by HiImTye on 2014-05-21
[fail2ban](http://packages.ubuntu.com/trusty/fail2ban) is still in the repos

---

### Post by unspawn on 2014-05-23
> **thnewguy said:**
> DenyHosts is a useful security tool for blocking brute-force attacks against OpenSSH servers. ...but fail2ban still is "more useful": it doesn't rely on tcp_wrappers (aka service level connections), uses iptables by default, can use ipset, can handle multiple services and is still maintained to name just five reasons.

---

### Post by thnewguy on 2014-05-23
> **unspawn said:**
> ...but fail2ban still is "more useful": it doesn't rely on tcp_wrappers (aka service level connections), uses iptables by default, can use ipset, can handle multiple services and is still maintained to name just five reasons.

Those are exactly the reasons why I do _not_ use fail2ban. DenyHosts does not mess with the firewall, is more cross-platform, is smaller and more simplified. I don't want a Swiss Army knife to monitor multiple services and alter my firewall, I want one simple tool which I can install that will guard one service. Plus, as I just pointed out above, DenyHosts is maintained.

---

### Post by ant2ne on 2014-05-23
i fail to see the value of denyhosts or fail2ban when iptables can do it all. And it gives you one place to troubleshoot when something doesn't work as it should.

If your iptables are set up properly, and ssh is only allowed from a certain IP (my workstation) then that brute fore attack has to be coming from my workstation. If my workstation (or its IP) is compromised, there is no additional security resisting that brute force if using any other or additional technology.

---

### Post by unspawn on 2014-05-24
> **thnewguy said:**
> DenyHosts does not mess with the firewall, is more cross-platform, is smaller and more simplified.  DenyHosts by default relies on tcp_wrappers. Apart from tcp_wrappers itself being susceptible to spoofing attacks (OK, in theory), the method *requires* a remote connection to a service as the service *itself* must make the decision. As would be obvious anything based on Netfilter won't suffer from that as any connection request will be dropped long before it reaches the application layer. On top of that the performance of iptables rules (or rather *an ipset*) and ease of rule or set maintenance are better as they reside in memory completely. And, this may be more like personal preference, somehow "it just doesn't seem right". It's like using /etc/hosts to block ads: a previous millennium leftover, crude and only partially effective way of doing things.    > **thnewguy said:**
> Plus, as I just pointed out above, DenyHosts is maintained. That's good to know because I just read OpenSSH will apparently be dropping tcp_wrappers: [http://permalink.gmane.org/gmane.comp.security.denyhosts.user/1040](http://permalink.gmane.org/gmane.comp.security.denyhosts.user/1040) ...

---

### Post by thnewguy on 2014-05-24
> **ant2ne said:**
> i fail to see the value of denyhosts or fail2ban when iptables can do it all. And it gives you one place to troubleshoot when something doesn't work as it should.

If your iptables are set up properly, and ssh is only allowed from a certain IP (my workstation) then that brute fore attack has to be coming from my workstation. If my workstation (or its IP) is compromised, there is no additional security resisting that brute force if using any other or additional technology.

That would be fine if your server is on the same LAN as your workstation and the IP of your workstation does not change. But what about if you want to access your server from another address or from outside the local network? Firewall rules are very limited this way. Most of the servers I maintain are on another network and are often accessed from the road, this makes firewall based rules completely unsuited for the situation.

---

### Post by ant2ne on 2014-05-27
> **thnewguy said:**
> That would be fine if your server is on the same LAN as your workstation and the IP of your workstation does not change. But what about if you want to access your server from another address or from outside the local network? Firewall rules are very limited this way. Most of the servers I maintain are on another network and are often accessed from the road, this makes firewall based rules completely unsuited for the situation.How so? I doubt your server is internet facing with its own private IP. Probably, it resides behind and firewall/router and then certain ports are forwarded to the server. possibly using iptables, like I do. At the firewall/router you can specify rules including connection limits. And at the server's ssh config (or OS policies) you can set log on limits and lockout thresholds etc. 

I'm all for multiple layers of security, but it seems like this layer can be easily replace with other tried existing technologies.

---

### Post by thnewguy on 2014-05-27
> **ant2ne said:**
> How so? I doubt your server is internet facing with its own private IP. 

Well, then you would be completely wrong. Most of the servers I manage are Internet facing with their own private IP address. A few are behind firewalls and, obviously, have less need for security software like DenyHosts. However, the majority of the servers are public-facing and therefore it makes a lot of sense to have some sort of filtering in place.

Look, not everyone's situation is exactly like yours and therefore some of us use different tools.

---

### Post by ant2ne on 2014-05-28
> How so? I doubt your server is internet facing with its own private IP. Sorry, I meant pubic IP.

---

### Post by thnewguy on 2014-06-12
A new version of DenyHost has been published at [http://denyhost.sf.net](http://denyhost.sf.net)
The new version includes support for Linux iptables, meaning it is no longer reliant on tcp_wrappers,  There are a number of minor bug fixes in there too along with some new documentation and command line flags for purging old entries.

---

