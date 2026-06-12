---
title: "SSH not working &quot;out of the box&quot;"
date: 2008-01-14
forum: Server Platforms
---

### Post by Jamina1 on 2008-01-14
Hi!

I've installed Ubuntu 7.10 Server onto a brand new server machine. Up and running great, I chose LAMP and Open SSH server as the only software to install with the operating system when it asked.

Once the network is configured, it has an external IP address that can be reached from port 80 across our entire network without any problems - which means apache is working great.

Problem is, none of these same computers can SSH to the new server. On my linux machines from terminal it just hangs and then times out. Putty from a windows machine gives an almost immediate "Connection Refused" Error.

I have not installed anything else but the os and have not added or modified any firewalls to the system.

From the server itself I can SSH to the external IP addres (not using localhost) but not from other computers. What's the issue here?

We are behind a router, however the router admin assures me that the settings are exactly the same as another server we have which SSH is allowed to just fine.

---

### Post by PriceChild on 2008-01-14
Could you ensure the package "openssh-server" is installed?```
sudo apt-get install openssh-server
```I'm wondering if some enter/spacebar confusion unchecked it.

---

