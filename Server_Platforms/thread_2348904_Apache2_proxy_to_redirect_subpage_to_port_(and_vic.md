---
title: "Apache2: proxy to redirect subpage to port (and vice-versa)"
date: 2017-01-09
forum: Server Platforms
---

### Post by petwri on 2017-01-09
Hello everybody,

I am trying to set up an apache2 server which I use as a proxy to redirect my incoming traffic.

Since my free DNS-service only provides 3 hostnames, which is not enough for the amount of services I want to have access to on my server, I just want to use one of the hostnames, let's say 'page.myhost.net'. All the services, running on e.g. localhost:1234, should then be accessible through page.myhost.net/myfirstservice through 443 port.

I searched everywhere, but didn't find a working solution for a vhost page configuration that does this. I found information on redirection from subdomains like 'myfirstservice.myhost.net', but nothing that does the same on a subpage-level.

Any ideas where/how to start with the configuration? The official apache2 documentation doesn't really help there.

Thanks!

---

