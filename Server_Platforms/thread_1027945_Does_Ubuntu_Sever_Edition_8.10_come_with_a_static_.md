---
title: "Does Ubuntu Sever Edition 8.10 come with a static IP?"
date: 2009-01-01
forum: Server Platforms
---

### Post by full of questions on 2009-01-01
Does Ubuntu Sever Edition 8.10 come with a static IP?

I am trying to host my own site and want to know if Ubuntu server Edition 8.10 comes with a free static IP instead of the normal dynamic IP.  Or do I need to buy one from my ISP?

---

### Post by Iowan on 2009-01-01
The server will attempt to set itself up with DHCP address.  You can give it a static address on your LAN, but that will be a private IP address - not viewable from internet.  For that, you will need to buy one from your ISP, or  you might be able to use a service like no-ip or dyndns.  Some ISP's (like mine) prohibit servers, and may block "standard" ports.

---

### Post by redmk2 on 2009-01-02
> **full of questions said:**
> Does Ubuntu Sever Edition 8.10 come with a static IP?

Ubuntu does not come with any IP address.  Whether it is static or dynamic, private or public.  You as the administrator assign an address to the host, either manually (static config) or dynamically (via DHCP). 
> 

I am trying to host my own site and want to know if Ubuntu server Edition 8.10 comes with a free static IP instead of the normal dynamic IP.  Or do I need to buy one from my ISP?

Your ISP assigns the IP address to the public side of your modem (router).  If you need a static IP you should contact the ISP.  This static IP usually costs more than a dynamically assigned address.  Once again this is on the public facing interface.  Depending upon how you set up your network your inside facing interface may or may not be an ISP assigned IP address.

If you use private IP addressing, then NAT must be employed and you will need forward the port assignment to host running the web server.

---

