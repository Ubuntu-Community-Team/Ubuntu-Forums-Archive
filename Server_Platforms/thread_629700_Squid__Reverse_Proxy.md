---
title: "Squid / Reverse Proxy"
date: 2007-12-02
forum: Server Platforms
---

### Post by vaximily on 2007-12-02
Ok, please bear with me as this will probably be complicated and parts may not make much sense. Feel free to ask me to clarify anything.

Keep in mind, hardware is NOT a limitation. If it's needed, I have it / can get it.

Here's my current setup:
High-speed Connection > Smoothwall Firewall box > Windows Server 2003 EE x64 w/ IIS 6.

I have multiple websites hosted (different TLD's) that IIS can filter host-headers and route to the appropriate site.

What I would like to have.

High-speed connection > Smoothwall OR Ubuntu SQUID w/ DHCP, DNS, etc > Multiple Ubuntu and Windows Servers.

I am having difficulty conceptualizing everything in my mind, but here is basically what I need:

example1.com > my public IP > Smoothwall (or other) routes ALL traffic (HTTP, FTP, remote desktop, etc) to server1 inside my network.
And I want that setup with multiple top-level domains. Each one will have it's own dedicated server, but I need something that can catch all of that traffic and forward it based on the host-header information, without me having to do a bunch of port re-mapping, but I only have ONE external IP address.

I'm sure there are pieces I'm missing so ask away, hopefully we can find a solution.

---

