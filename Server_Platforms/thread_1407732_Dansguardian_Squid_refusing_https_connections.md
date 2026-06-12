---
title: "Dansguardian Squid refusing https connections"
date: 2010-02-15
forum: Server Platforms
---

### Post by bertmanphx on 2010-02-15
Hello,
I have a computer running Ubuntu 8.10 that acts as a file server and transparent proxy using Dansguardian and Squid.

My problem, is that while the filtering seems to work perfectly for http sites, it does not filter out an https connection.  Specifically, if someone tries to use an https proxy, the non https portion such as Adverts and such are filtered, but the URL box on the site still allows them to route around my proxy.  An example of a site offering proxies is camolist.com.

If I configure FF to use the same proxy configuration for https, then I get an error "Proxy refusing connections".

Is There something I need to change in Squid, so that It filters https traffic?

TIA,

bertmanphx

---

