---
title: "Strange network problems with VirtualBox 2.1"
date: 2009-02-10
forum: Server Platforms
---

### Post by Noccy on 2009-02-10
I've got a nice Ubuntu 8.10 setup running VirtualBox 2.1. Inside VirtualBox runs a setup of Windows 2000 (for IIS, until all the sites are migrated to ASP) which runs quite fine in interactive mode. 

However, attempting to start it as a service fails. The box starts up, and I can access it via RDP to the linux system. Logging on shows me that it has a proper IP assigned (same as the DNS entry for it). So;

Base system: Ubuntu 8.10 with dynamic ip (host1)
Virtual: Windows 2000 with dynamic ip (host2)

Both system get the IP from the providers DHCP servers, and work fine. 

However, when the virtual machine is started with my init.d script (providing -type vrdp), even though the IP is properly assigned to the virtual machine, it's not accessible from the outside. The pings drop and no services are available. If I fire it up using the VirtualBox GUI however, everything is working fine.

Has anyone got a solution to this problem before I go bald here? :)

**Edit:** Now the virtual machine isn't even available in interactive mode for some reason. Only changes I've made is enabling IPv4 forwarding and setting eth0 in promiscuous mode.


Best regards,
Chris

---

