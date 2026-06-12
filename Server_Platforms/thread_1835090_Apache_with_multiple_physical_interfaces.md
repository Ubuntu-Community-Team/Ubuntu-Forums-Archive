---
title: "Apache with multiple physical interfaces"
date: 2011-08-28
forum: Server Platforms
---

### Post by Shatan on 2011-08-28
Hey all, I'm trying to run a config where i have multiple interfaces in my server.

eth0 10.200.0.30
eth1 10.200.0.31

I currently have apache configured as defaults, with two sites created under sites-available:

site1.domain.com
site2.domain.com

site1.domain.com's config file looks like this
<VirtualHost 10.200.0.30>
    ...
    ServerName site1.domain.com
</VirtualHost>


site2.domain.com's config file looks like this
<VirtualHost 10.200.0.31>
    ...
    ServerName site2.domain.com
</VirtualHost>

Now, I'm behind an ASA5505, and the ASA can see both IP's, 30 and 31, but they are assigned the same MAC.  It appears that the ubuntu server is sending out the packets from eth0, and not sending anything out eth1.  A look at the output from ifconfig confirms this, traffic enters both interfaces, but only leaves eth0.  So, while on the local broadcast domain it works, I can't access the server over our site to site VPN.

How can I get Apache(or Ubuntu) to send out responses to requests from eth0(.30) out eth0, and similarly, from eth1(.31) out eth1?

---

### Post by SeijiSensei on 2011-08-28
This is difficult to do since both interfaces are in the same subnet.  If you can configure static routes on your router, try setting up point-to-point routes to the two server IP addresses.

The easier solution by far would be to assign the two interfaces to two different IP subnets and configure routing appropriately.

---

