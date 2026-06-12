---
title: "[SOLVED] Samba DC setup with possibility to join domain trough VPN"
date: 2008-12-17
forum: Server Platforms
---

### Post by sami83 on 2008-12-17
How would I go about creating a Samba Domain Controller with the possibility to join computers remotely to the domain trough VPN tunnel, is extra configuration needed for DNS or other systems? I am familiar with Samba DC and have all that configuration sorted out just wondered about the remote workstation domain joining. Any advice is welcome.

---

### Post by sami83 on 2008-12-19
Did some more research and testing and you need this in the DNS: _ldap._tcp.dc._msdcs.example.com SRV 0 5 389 server.example.com

allso you need to make sure that in the vpn client it uses the correct nameserver.

---

