---
title: "port 25 and 587 no connection"
date: 2011-07-30
forum: Server Platforms
---

### Post by gypsumwolf on 2011-07-30
When I telnet my mail server with port 25 and 587 with my mail.domainname.com (or even domainname.com) it does not connect. When I try it with my IP address on my internal network it works fine. My router is forwarding both of those ports to the server.

My problem is I cant recieve e-mail. I do have a PTR record set up and A and MX record.

Is there a way to check if my ISP is blocking those ports?

---

### Post by ian dobson on 2011-07-31
Hi,

Sounds as if your ISP is blocking the ports or your router doesn't allow connections from inside the network to the wan ip of the router.

Try opening a non-standard port (2011) forwarding it to you server and see if that port gets through. If you PM me with your domain name/ip address I'll try connecting from my IP and let you know if I get through/if you ISP is blocking.

Regards
Ian Dobson

---

