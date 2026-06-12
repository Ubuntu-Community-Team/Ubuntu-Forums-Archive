---
title: "Redirecting apache2 traffic from a different network"
date: 2012-12-12
forum: Server Platforms
---

### Post by SoCalChris on 2012-12-12
I've got a server running apache2 on my local network. It's running several web applications that I want available to all machines on my local network. However, I want one of them to be available to the local network, AND connections from the internet. Each application is listening on a different port.

Is there a way that I can redirect all web traffic from non-local clients, except for traffic destined for that port?

For example, I want the following to be available only to machines on the local network:
[http://myserver:8080](http://myserver:8080)
[http://myserver:8081](http://myserver:8081)
[http://myserver:5050](http://myserver:5050)

But I also want [http://myserver:5050](http://myserver:5050) to be available to traffic coming from the internet. Any other traffic I want to simply redirect to a different web address.

I would think that this wouldn't be too difficult, but I'm not finding anything.

Any suggestions on how to do this, or where to start?

Thanks

---

### Post by SeijiSensei on 2012-12-12
Is this machine directly on the Internet, or is it behind a router?  If the latter, the simplest solution is to forward port 5050 on the router back to the server.  Then external users can only see that port and its associated web site.

If the server has two network cards and sits between the public Internet and your LAN, you can bind the internal sites to the LAN-facing IP address and bind the external site to the Internet-facing address.

---

