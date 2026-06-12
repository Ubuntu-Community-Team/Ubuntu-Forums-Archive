---
title: "SSH Tunneling &amp; Nginx not showing visitor IP"
date: 2018-11-09
forum: Server Platforms
---

### Post by sunrex on 2018-11-09
I'm using the following command for tunneling 443 traffic to the web server:

ssh -L 127.0.0.3:443:127.0.0.2:443 user@127.0.0.2 -p 22

This command works, users are able to browse the website through the proxy server... however, it shows their IP as 127.0.0.3.

Is it even possible to restore the original visitor IP using this method and if not what alternatives are available? IPTables would work, but I'd like the traffic to be encrypted between the proxy and web server for privacy reasons.

---

### Post by slickymaster on 2018-11-09
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2018-11-10
Use OpenVPN to set up a [static tunnel]("https://openvpn.net/static.html") between a host on the local network and the remote. Route traffic to the remote over the tunnel. IP addresses should be preserved.

---

