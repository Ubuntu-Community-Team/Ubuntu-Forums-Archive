---
title: "Strange TXT record in bind"
date: 2009-05-06
forum: Server Platforms
---

### Post by lykwydchykyn on 2009-05-06
I have set up a BIND server with dynamic DNS using DHCP3 server.

It's working fine, and we have a Windows 2003 server pulling the zone back as a slave.  The network admin noticed today that there are a lot of TXT records for the dynamic hosts that are just long random hex strings.  

I did some looking at the logs and it seems to have something to do with rrset, but I'm not clear on what this means.  Is this normal or is something misconfigured on our server?

It seems to be working fine, I think the network admin would feel better about using this setup if he knew what this record was about.

---

