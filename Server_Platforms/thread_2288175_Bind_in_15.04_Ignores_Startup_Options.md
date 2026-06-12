---
title: "Bind in 15.04 Ignores Startup Options"
date: 2015-07-24
forum: Server Platforms
---

### Post by snowy16 on 2015-07-24
It appears Bind in Ubuntu 15.04 doesn't acknowledge startup options in /etc/default/bind9.  I noticed in syslog that bind was trying to resolve ipv6 addresses even with -4 added to Options="-u bind -4" in /etc/default/bind9.  When I run sudo systemctl status bind9 it shows the service running /usr/sbin/named -f -u bind with no mention of -4.

I stopped Bind and tried firing bind manually with sudo named -f -u bind -4 and Bind no longer attempts to resolve ipv6 addresses so I don't believe the issue lies with Bind itself.  Has anyone run into this issue or have any workarounds?

---

