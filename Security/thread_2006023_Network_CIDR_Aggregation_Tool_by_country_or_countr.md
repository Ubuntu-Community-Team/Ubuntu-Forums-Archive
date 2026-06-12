---
title: "Network CIDR Aggregation Tool by country or countries"
date: 2012-06-18
forum: Security
---

### Post by CIPB on 2012-06-18
We have been working on a variety of network aggregation tools to help produce smaller Access Control Lists for our members and non-members. Members select a country or group of countries and a tool consolidates the data.

Our initial scripts focused on simply aggregating contiguous networks into larger network ranges with starting and ending IPs to represent the network blocks. This resulted in much smaller ACLs, but not all firewalls or security systems could handle data in this format.

WE responded to this by creating code that would allow us to output our data into legal CIDR networks (we can of course convert the data into Netmask, Cisco or other formats). Basically we are joining contiguous networks as we did in our original scripts and then converting the blocks into CIDR.

We would appreciate any feedback you have to offer on this tool. You can try it at [https://www.countryipblocks.net/ip_aggregation_beta.php]("https://www.countryipblocks.net/ip_aggregation_beta.php").

Testing this with a variety of country combinations we are seeing ACL size reductions of 17-80%. Is this significant enough to make a positive impact on .htaccess, web.config or hardware firewalls like Cisco? Any feedback you can provide would be greatly appreciated.

---

