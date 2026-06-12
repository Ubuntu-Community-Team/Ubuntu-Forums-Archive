---
title: "Kerio-like security using Linux firewall tools?"
date: 2007-11-10
forum: Server Platforms
---

### Post by robertbub on 2007-11-10
'Though I've been using Linux for 12 years, one thing I liked about Windows and the Kerio firewall in particular was the ability to control the network connections for a specific application.

I don't expect Linux to have this rich functionality, but I would like to explore whether it would be possible to at least limit access to the HTTP protocol.  Because I like browsing the web, it is insufficient to just shut off ports 80 and port 443.  But, if I could create a fake network interface, then I could create a proxy server which only listens and sends from that fake network interface.  (With this method, I would not have to have another separate computer available to proxy through.)

[LIST]
[*]Is there a way to create such a fake network interface?
[*]Would a proxy server such as Squid support listening and sending only a particular network interface?  If not Squid, is there another proxy server which does support this notion?
[/LIST]

---

### Post by HermanAB on 2007-11-10
Read the Advanced Routing Howto and the Firewall Howtos at tldp.org

Cheers,

H.

---

### Post by robertbub on 2007-11-17
> **HermanAB said:**
> Read the Advanced Routing Howto and the Firewall Howtos at tldp.orgThanks.  These howtos are too complex.  However, on [http://www.faqs.org/docs/linux_network/x-087-2-iface.interface.html#X-087-2-IFACE.INTERFACE.ALIAS](http://www.faqs.org/docs/linux_network/x-087-2-iface.interface.html#X-087-2-IFACE.INTERFACE.ALIAS) , there is a description how to create an IP Alias for the loopback device.  This seems to be a way to make a fake network interface.

Now, the hard part -- setting up the proxies and firewall rules.

Thanks.

---

### Post by update_manager on 2007-11-17
> **robertbub said:**
> 'Though I've been using Linux for 12 years, one thing I liked about Windows and the Kerio firewall in particular was the ability to control the network connections for a specific application.

I don't expect Linux to have this rich functionality, but I would like to explore whether it would be possible to at least limit access to the HTTP protocol.  Because I like browsing the web, it is insufficient to just shut off ports 80 and port 443.  But, if I could create a fake network interface, then I could create a proxy server which only listens and sends from that fake network interface.  (With this method, I would not have to have another separate computer available to proxy through.)

[LIST]
[*]Is there a way to create such a fake network interface?
[*]Would a proxy server such as Squid support listening and sending only a particular network interface?  If not Squid, is there another proxy server which does support this notion?
[/LIST]

Application Firewall programs:
[http://www.nufw.org/-English-.html](http://www.nufw.org/-English-.html)
[http://www.shorewall.net/](http://www.shorewall.net/) (partial user-limit support)
[http://fireflier.sourceforge.net/](http://fireflier.sourceforge.net/) (no longer supported)

To make a new network interface, you can add it to /etc/network/interfaces like:
auto eth0:1
iface eth0:1 inet static
  address <ip>
  netmask <subnet>
  gateway <ip>
  
Any of these proxies can be told to listen on a specific interface:
[http://freshmeat.net/projects/ffproxy/](http://freshmeat.net/projects/ffproxy/) (also has http/https filtering)
[http://www.pps.jussieu.fr/~jch/software/polipo/](http://www.pps.jussieu.fr/~jch/software/polipo/)
[http://www.squid-cache.org/](http://www.squid-cache.org/)

---

### Post by robertbub on 2007-11-17
OK, did this.  I am using Privoxy as my http proxy, but it didn't support a bind-from address for my new fake (ip alias) network interface.  So, I downloaded the source and hardcoded the address (192.168.2.51) in the code.  (Maybe I'll generalize it some day...)

---

