---
title: "[SOLVED] make squid serve as gateway without transparent"
date: 2007-09-05
forum: Server Platforms
---

### Post by xyrer on 2007-09-05
Hi, I would like some computers in our network to pass thru squid as a gateway without squid being transparent, I need people on my network to authenticate before browsing internet, but there are a few exceptions, I need a couple of computers to have a direct connection to the internet, I was thinking about rules for squid so it lets them go without authentication, but all my searches have gone bad, I don't really know what I have to look for, either way, every web I've seen says the answer is a transparent proxy, but I can't allow that as I need most the people to type login and password, it's only a couple exceptions.

Please someone tell me how to do it in squid, if it's not possible, then what would be a work-around, thanks for your time.

---

### Post by KCPokes on 2007-09-05
Squid, I believe, by default is not transparent.  Gives you the option of setting specific machines to access the internet via the proxy, while others would go directly via the default route.  Of course the problem with that is if people are smart they change their browser settings and they bypass it as well.  

Is there a reason that you choose Squid (for caching) or is it simply to control access?  If its purely for access, you may be disappointed in Squid.  For example, you can restrict http traffic, but instant messenger traffic is not considered HTTP, thus it'll continue to go through.  At least this was the case when I last had a standalone Squid proxy in place.  If you are simply wanting to use something for control you consider more of a firewall solution and block people based on IPtables rules; the rules are in place at specific times to block access, down at times to allow access.  That is the heart of most "gateways"; the proxy is simply to control/block some content and to cache common content.

---

### Post by xyrer on 2007-09-05
Hi, thanks for the quick response, I chose squid for both, caching and authentication, we had wingate but it's unstable and substle to viruses, we have a separate firewall so I don't mind about restrictions.
The authentication is very good, when the user wants to navigate it asks for login and password, so the control is based on username and not on ip, wich is what I want as users can use another person machine.
The only problem now is with those users having to connect with windows-only vpn software.

I thought of acl rules but haven't found documentation for a particular case like the one I have.

---

### Post by erwall on 2007-09-05
> **xyrer said:**
> Hi, thanks for the quick response, I chose squid for both, caching and authentication, we had wingate but it's unstable and substle to viruses, we have a separate firewall so I don't mind about restrictions.
The authentication is very good, when the user wants to navigate it asks for login and password, so the control is based on username and not on ip, wich is what I want as users can use another person machine.
The only problem now is with those users having to connect with windows-only vpn software.

I thought of acl rules but haven't found documentation for a particular case like the one I have.

[http://wiki.squid-cache.org/SquidFaq/ProxyAuthentication](http://wiki.squid-cache.org/SquidFaq/ProxyAuthentication)

---

### Post by xyrer on 2007-09-18
I'm sorry but couldn't find a way to do this, if anyone could help me either with iptables or something, every documentation about iptables i have found assumes you already know how to use it.

---

### Post by xyrer on 2007-10-22
Finally iptables solved this issue, there's a way to do this by identifying the software that tries to connect but it's harder than forwarding by iptables.
Thanks to all, anyway.

---

