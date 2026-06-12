---
title: "Service Reroute"
date: 2009-01-21
forum: Server Platforms
---

### Post by Nikmaster0 on 2009-01-21
I am trying to link two Ubuntu 8.10 servers together using 2 ethernet cables, a Linksys WRT54G wireless router, and Webmin. When the domain is requested using port 80, I want it to go to the web server at 192.168.1.4 (Master Server), but when SSH is requested, I want it the request to be rerouted to 192.168.1.5 (File Server). Can I do this through the Wireless Router and how, or do I have to do it through Webmin and how. Thanks.

---

### Post by ejschaefer on 2009-01-21
Hello, 

Do you mean when these services are requested from external sources? If so, then that would all be configured in your router's interface in the "port forwarding" section.

If you're not talking about directing external clients to the appropriate servers, can you be a little more specific of what exactly you're trying to accomplish?

HTTP Port Forwarding:
[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/HTTP.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/HTTP.htm)

SSH Port Forwarding:
[http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/SSH.htm](http://portforward.com/english/routers/port_forwarding/Linksys/WRT54G/SSH.htm)





Edward Schaefer
Support Supervisor
[http://www.hostmysite.com/?utm_source=bb](http://www.hostmysite.com/?utm_source=bb)

---

