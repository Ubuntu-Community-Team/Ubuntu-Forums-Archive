---
title: "Issues when loading site."
date: 2010-04-17
forum: Server Platforms
---

### Post by kolad on 2010-04-17
Hi all,

I'm currently experiencing some "performance issues" while opening my web page from outside my network.

I have ubuntu server 9.10 x86 running an apache web server 2.2.12. Simple machines forum is installed on top of it. The server is behind my wireless router on which I've configured port forwarding from port 80 to port 80 on the server. The router WAN IP is public. When I open the web site from computer behind the router everything is fine. However when i open it from outside the network it takes ages to load and it doesn't load it all(some links without the graphics). In ports.conf file the port is set to 80. Am I missing something here?:confused: Please help.

Best Regards

---

### Post by kolad on 2010-04-17
Nevermind the problem has been resolved. It wasn't linux issue at all. "This theme's URL:" and "This theme's images URL:" contained server's private IP address 192.168.x.x. Just in case someone encounter the same problem.

---

