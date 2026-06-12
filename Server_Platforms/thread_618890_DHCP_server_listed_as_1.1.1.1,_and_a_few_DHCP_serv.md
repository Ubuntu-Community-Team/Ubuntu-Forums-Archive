---
title: "DHCP server listed as 1.1.1.1, and a few DHCP server questions.."
date: 2007-11-20
forum: Server Platforms
---

### Post by Fat Man on 2007-11-20
I'm pretty new to Linux, I apologize in advance if necessary..

I installed Ubuntu 7.10 server on a HP blade server. I configured it with a static IP address in a 10.30.x.x subnet, and then configured it to be a DHCP server and issue IP addresses in that subnet as well. 

It issues addresses just fine, but when I check on a client for IP lease information, the DHCP server IP address on the client is listed as 1.1.1.1. I don't see this as a show stopper, but would like it to be accurate. Any ideas on how to fix this?

I also have 3 questions about using this as a DHCP server.

1. I want a way to determine how many of the available IP addresses it has leased out so far. Is there a way to monitor this with a client or GUI? I did not install any GUI on the server.

2. Can the DHCP server be configured to ping an address before offering it? Windows DHCP servers do that. 

3. Will restarting the DHCP service potentially cause duplicate leases? My lease time is 8 hours. 

Thank you in advance,
Dan

---

