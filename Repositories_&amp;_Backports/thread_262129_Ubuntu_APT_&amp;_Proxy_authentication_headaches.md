---
title: "Ubuntu APT &amp; Proxy authentication headaches"
date: 2006-09-21
forum: Repositories &amp; Backports
---

### Post by siesa on 2006-09-21
I have just installed Ubuntu 6.06 and want to update using Synaptic PM.  I have set up the proxy, set authentication in Network Proxy Preferences, set the proxy in Synaptic PM.  When I click reload, I get this error on all repos:  [COLOR="Lime"]http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required[/COLOR].  I have tried changing to [COLOR="Lime"]username:password@proxy:port[/COLOR], but that doesn't work either.  Firefox works fine, on first start, it asks for username/password, then goes on as normal.  I have also tried [COLOR="Lime"]export http_proxy=user:passw@ipaddress:port[/COLOR] & [COLOR="Lime"]export http_proxy=user:passw@proxy:port[/COLOR].  I have check in gconf and the username & password is there.  Is there anything else I can try?

---

