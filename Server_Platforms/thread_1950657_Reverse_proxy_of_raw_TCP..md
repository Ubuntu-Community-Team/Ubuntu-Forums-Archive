---
title: "Reverse proxy of raw TCP."
date: 2012-04-01
forum: Server Platforms
---

### Post by josh.pbh on 2012-04-01
Hi there, forums.
I was planning on starting up two/more Minecraft servers in a VM, on different ports, and using another VM with a reverse proxy to determine which port to send the connection on to.
My dns has wildcard support, so I was planning to do something like:
mc_1_.example.com:**25565** > 192.168.1.1:**25565**
mc_2_.example.com:**25565** > 192.168.1.1:**2556*_6_***

I assume Apache2 won't do this, but I've heard about FProxy from somewhere. Does anyone know if that will work? I've looked but not found any examples of this anywhere!

Thanks everyone!

---

### Post by SeijiSensei on 2012-04-02
> **josh.pbh said:**
> I assume Apache2 won't do this

You assume wrong.  Read this:  [http://httpd.apache.org/docs/2.2/mod/mod_proxy.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy.html)

On the other hand, if all you want to do is forward an arbitrary pair of ports to one or more other machines, you can either write some iptables rules, or use an application-level TCP proxy.  I use an old but reliable application called [tcpproxy]("http://www.quietsche-entchen.de/cgi-bin/wiki.cgi/proxies/TcpProxy").  I normally just compile it from source, but the web page says there's a .deb package.  You might be able to install that using dpkg.

---

