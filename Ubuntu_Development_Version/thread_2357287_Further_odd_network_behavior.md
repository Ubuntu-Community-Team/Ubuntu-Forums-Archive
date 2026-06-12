---
title: "Further odd network behavior"
date: 2017-03-31
forum: Ubuntu Development Version
---

### Post by tajreed on 2017-03-31
17.04 connects to my password connected home network but is often slow in rendering pages, resolving host-establishing secure connection and finally connect.

17.04 will not connect to WI-FI in local coffee shops where a password is required but will connect to a city-wide network which does not require a password-very odd.

Any thoughts?

Dell XPS 13 with Ubuntu pre-installed.

---

### Post by wgarcia on 2017-04-01
I'm seeing also strange network behavior on a server that I have behind a VPN, related to DNS. I thiink it is related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1647031](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1647031)

In my case my system is unable to resolve CNAME (like mail.google.com, but it can resolve [www.google.com](www.google.com)). Very oddly, if I open a browser (Firefox), after a while it starts resolving. I think the explanation is in comment #26 of the above bug report.

---

