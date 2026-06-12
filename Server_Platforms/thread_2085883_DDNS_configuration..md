---
title: "DDNS configuration."
date: 2012-11-19
forum: Server Platforms
---

### Post by OmegaHarvest on 2012-11-19
Hi Guys

I'm currently in the process of teaching myself Ubuntu server (currently running 12.04). 

I've successfully configured DNS with BIND9 and ISC-DHCP, both of which are working beautifully. 

I'm now hoping to configure dynamic DNS so that DHCP automatically updates the host records in the DNS zone databases I have configured.

Just wondered if anyone has any experience of this and how easy it is? I've tried the following guides (which I'll link below) but found that when I added a new VM to my test domain no new A records appeared in my Zone database. 

I used [http://www.kirya.net/articles/running-a-secure-ddns-service-with-bind/](http://www.kirya.net/articles/running-a-secure-ddns-service-with-bind/) for configuring DDNS and [http://www.webhostingskills.com/articles/configuring_a_dhcp_server_to_update_a_bind_name_server](http://www.webhostingskills.com/articles/configuring_a_dhcp_server_to_update_a_bind_name_server) for DHCP.

I've since reverted to a previous snapshot of my server and reverted the changes, but I will try again a little later.

Just wondered if anyone knew of any caveats to be aware of as this looks like it should be relatively simple to configure. 

I'm assuming DDNS works in Linux as you would expect where new A records are created, or does it just update existing records in BIND?

Many thanks, hope this makes sense.

---

