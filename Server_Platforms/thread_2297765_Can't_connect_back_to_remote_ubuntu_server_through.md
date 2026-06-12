---
title: "Can't connect back to remote ubuntu server through telnet after connection is lost"
date: 2015-10-06
forum: Server Platforms
---

### Post by JAZ1976 on 2015-10-06
[FONT=Helvetica Neue]I have an Ubuntu 14.04 server that runs an old mainframe system that our employees connect to remotely using Telnet. If a remote user loses their connection while they are working in the system they can't get back in unless we change the users ip address that they are getting. This happens when there are power outages or work being done on the providers lines. We have a failover setup that pushes user traffic from our MPLS network provider to our cable provider. We think the difference in network hops is causing the issue but when I clear the arp table using [/FONT]sudo ip -s -s neigh flush all[FONT=Helvetica Neue] nothing happens. How can I prevent users not being able to get back in from the ip address that they already have? This also happens to ssh connections, so it's not just telnet.[/FONT]

---

