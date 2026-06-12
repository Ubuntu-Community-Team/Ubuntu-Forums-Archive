---
title: "Ubuntu 10.04 Server + Shorewall: cannot start firewall"
date: 2011-09-01
forum: Server Platforms
---

### Post by michael_schmid on 2011-09-01
Hi folks,

I've a virtual private server that runs Ubuntu 10.04. To configure the  firewall I've installed shorewall and copied over a configuration that  is known to work on another (Debian) server. The configuration itself is  very basic at the moment: basically block everything incoming except  SSH. Please note that I *have not* changed any of the default  configuration settings in /etc/shorewall/shorewall.conf.

Now, when I try to start the firewall via /etc/init.d/shorewall start, I  get the following error log in /var/log/shorewall-init.log:

12:08:03 Compiling...
12:08:04 Loading Modules...
   ERROR: A log level other than NONE requires LOG Target in your kernel and iptables

Hope you guys can help me out on this one!

---

