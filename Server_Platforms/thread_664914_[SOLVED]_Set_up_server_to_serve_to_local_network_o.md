---
title: "[SOLVED] Set up server to serve to local network only"
date: 2008-01-11
forum: Server Platforms
---

### Post by linlover on 2008-01-11
I have a Linksys g router and my ISP does not want me to have a server. So I was wondering is there any thing I have to do to make the server unreachable form the out side of my network, or is it unreachable by default?

---

### Post by mmichalik on 2008-01-11
If the server is behind the router and you let the router run DHCP to assign the IP addresses (or for that matter, even if you assign it a static IP address that the router understands, something like 192.168.x.xxx), it should be unreachable by default.

If the server is in front of the router, you would more then likely have to have a static IP from the ISP and then it would be reachable from the outside world.

---

### Post by linlover on 2008-01-12
Thank you, I wanted to make sure that I wasn't violating my ISP's TOS.

---

