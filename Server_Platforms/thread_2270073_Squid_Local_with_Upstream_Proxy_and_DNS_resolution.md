---
title: "Squid Local with Upstream Proxy and DNS resolution"
date: 2015-03-20
forum: Server Platforms
---

### Post by Nick_Robinson on 2015-03-20
Hi Everyone!

 I am working on a proxy solution for public schools here in Western Australia working within the confines of Department of Educations (DOE) network and have run into an issue in regard to DNS resolution for forcing Google searches through the safe seach IP 216.239.38.120 (forcesafesearch.google.com).

 All public schools in Western Australia must run all internet traffic through an upstream proxy that is provided by DOE. DOE will not allow modification of DNS on their network to support an authoritative zone for google.com.au and google.com so that all google queries resolve to the safe search IP.

I thought that the solution would be to install Ubuntu onto suitable hardware and install Squid and BIND9. Then configure the local DNS server to have authoritative zones for google.com and google.com.au and point squid to the upstream proxy. The idea was that this would result in squid being passed the safe search IP address when the query was resolved.

What I have found in testing this however was that even thought doing an Nslookup for example to [www.google.com.au](www.google.com.au) on the Ubuntu system resulted in the correct IP for safe search, Squid still returned the non-safe search results from google.

My question is then is there any way to force squid to do a DNS lookup locally before passing the request to the upstream proxy? Or is the upstream proxy the problem (i.e. is the upstream proxy doing DNS resolution as a result of the pass through from the local squid instance)?

Any help on a workaround / fix for this is very appreciated.

---

