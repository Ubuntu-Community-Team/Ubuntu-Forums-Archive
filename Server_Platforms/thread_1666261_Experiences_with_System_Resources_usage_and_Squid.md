---
title: "Experiences with System Resources usage and Squid"
date: 2011-01-13
forum: Server Platforms
---

### Post by R.Bucky on 2011-01-13
I implemented squid as a caching proxy on my local network for a couple of test users. Squid is temporarily installed on my HTTP server; wondering about potential slow downs for pushing the HTTP content. What experiences do users have with the allotment of system resources for a user base of 20 using squid?

---

### Post by chrislynch8 on 2011-01-14
Hi,

I have Squid installed on a Server that is also acting as a webserver (220 user CRM), DHCP, DNS, Router/Gateway, Samba, NFS, VPN, to about another 25 Servers. 

On this Main server I have over 50 users and all web traffic is redirected through squid. 

THe Server itself has a Xeon processor and 4GB of RAM nothing super special, and it running like a charm. No issues with system resources. 

From webmin I can see that squid is the most memory intensive service running but it normally seems to use about 50Mb of RAM.

---

### Post by SeijiSensei on 2011-01-14
I have Squid running as a transparent proxy with a lot of ACLs for a network of about 200 workstations.  It's on a P4 with 512MB of memory.  It's load average hardly ever exceeds 0.1.

---

### Post by R.Bucky on 2011-01-14
This box is an i7 - 850 with only 6 low traffic HTTP sites, a couple of admin Samba shares, and then squid. I think you folks summed it up. Thanks for contributing.

~Mark

---

