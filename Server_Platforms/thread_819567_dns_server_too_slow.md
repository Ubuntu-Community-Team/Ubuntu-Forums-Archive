---
title: "dns server too slow"
date: 2008-06-05
forum: Server Platforms
---

### Post by jsvidyad on 2008-06-05
Hi!!

   I have set up a Hardy(server version - 64 bit) machine to act as a DHCP and DNS server. The problem is that name resolution is  very slow for all machines on the local network except for the router itself(which does not use the local DNS server). I am sure that the fault lies with the DNS server, for when I enter the IP instead of hostname in the address bar, the page loads up fast. I was using a fedora machine for DHCP & DNS earlier. That machine did not have any problems. 

Thank you in advance for your help.

---

### Post by HermanAB on 2008-06-05
Run a proxy DNS on the router, or on your server, then point everything to that.  A proxy (slave) DNS is very simple to set up and zero maintenance.

---

