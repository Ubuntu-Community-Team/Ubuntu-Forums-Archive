---
title: "Small DNS caching server for home use."
date: 2007-11-03
forum: Server Platforms
---

### Post by kuzmaster on 2007-11-03
What would be the best way to implement a small dns server for caching with minimal setup and fuss, all running on a home network.

I would also like to have it possible to redirect network addresses such as router.foo to 192.168.1.100, and the like for the rest of the computers on the network.

After doing some googling, i found this [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

Would this be a good solution?

Also, gui/web-ui is favored, but i don't mind using command-line.

---

### Post by koenn on 2007-11-03
yep, dnsmasq. small but effective.

---

### Post by kuzmaster on 2007-11-03
Yep, ive implemented that, so now how can i get router.foo to send me to 192.168.1.100 and the like for the rest of my computers?

---

### Post by koenn on 2007-11-03
> **kuzmaster said:**
> Yep, ive implemented that, so now how can i get router.foo to send me to 192.168.1.100 and the like for the rest of my computers?
You need a so-called "zone file" that lists all computers on your netwrok + their addresses. It's just a text file - dnsmasq uses the /etc/hosts file on the system it's running on by default, but you can alter that or add additional files in the dnsmasq.conf file (somewhere in /etc).
While you're at it, check what dnsmasq uses for 'forwarders" - i.e. for names / addresses outside your network (i.e.) on the internet. I probably uses the name server in /etc/resolf.conf to do that. 
Lastly, tell your computers they need to use the address of your dnsmasq computer as DNS server. 
You can automate most of this by letting dnsmasq offer dhcp service as well. It's explained in the article * you * linked to ...

---

