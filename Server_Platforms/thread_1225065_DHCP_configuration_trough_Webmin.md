---
title: "DHCP configuration trough Webmin"
date: 2009-07-28
forum: Server Platforms
---

### Post by sikandarnoori on 2009-07-28
hi all,
i install and configured DHCP in Ubuntu 9.04 server by using Webmin, all my dhcp clients can get IP automaticaly and there is no problm with communicate with each other and server but the problem is they dont have access to internet altough the server can access internet, can any one help me what should i do to fix the problem? i'm sure i must do some thing with linux firewall, network configuration and . . . , nut how? i need your help,
regards,

---

### Post by Serangan on 2009-07-28
You would need a setting in iptables?

Something to do with IP Masquerading

have a look at this;
[https://help.ubuntu.com/9.04/serverguide/C/firewall.html](https://help.ubuntu.com/9.04/serverguide/C/firewall.html)

There's a section about IP Masquerading. It should help you fix your problem i think

Also, im running webmin, and it's easier to do masquerading via ssh.

---

