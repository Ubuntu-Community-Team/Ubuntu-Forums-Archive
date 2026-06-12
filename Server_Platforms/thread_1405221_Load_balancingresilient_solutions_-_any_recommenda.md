---
title: "Load balancing/resilient solutions - any recommendations?"
date: 2010-02-12
forum: Server Platforms
---

### Post by john-boy on 2010-02-12
I have a web site running on a server and would like to implement a resilient solution. Can anyone recommend any solutions based upon their own experiences? From browsing the web, I know there are a few Linux load balancing options that could meet my needs like UltraMonkey, CrossRoads, Linux Virtual Server and BalanceNG so here is a more detailed description of my requirements:

[LIST]
[*]The client should not be aware if one web server becomes unavailable.
[*]All requests from one client should be sent to the same web server so some kind of sticky session feature would be one solution. Sending all requests from all clients to one server until it became unavailable then sending requests to a second server (so no balancing, just resilience) would actually meet my needs too, although is less sophisticated.
[*]The solution must be free so it can't be a hardware appliance and must be able to run on a relatively low spec PC e.g. Pentium 4.
[*]An identical web server will be set-up so I have two 'cluster' members serving identical content but the number of members could increase.
[*]The web servers will be Windows so the solution must be compatible with this (yes I know, Windows - boo, hiss!!).
[*]Something reasonably easy to install, configure and manage so admins with minimal Linux experience can troubleshoot. A web front end to manage the solution would be nice but not essential.
[*]There doesn't seem much benefit having more than one web server providing resilience if the solution managing this is a single point of failure. The solution should address this is possible.
[/LIST]

The last point is something I'm having trouble with because it could become more complex than I initially thought. My thought is that there might be a live network load balancing server with a standby system maintaining a heartbeat between the two that is ready to take over if the first server becomes unavailable.

And yes, I do know that Windows 2003/2008 has a Network Load Balancing feature but I'm exploring all options. I was looking for a solution that would work regardless of the web server's OS as I might migrate to Linux web servers at a later date or use the load balancing solution in another non-Windows environment if successful.

Cheers y'all.

---

### Post by Jekshadow on 2010-02-13
Apache with mod_proxy load balancing to a few backends has worked well for me. 

Here is a brief tutorial:
[http://www.markround.com/archives/33-Apache-mod_proxy-balancing-with-PHP-sticky-sessions.html](http://www.markround.com/archives/33-Apache-mod_proxy-balancing-with-PHP-sticky-sessions.html)

---

