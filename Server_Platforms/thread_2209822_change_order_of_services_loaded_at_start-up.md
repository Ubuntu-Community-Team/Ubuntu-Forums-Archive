---
title: "change order of services loaded at start-up"
date: 2014-03-07
forum: Server Platforms
---

### Post by sir-marky on 2014-03-07
I have a problem on my server where Varnish isn't allowing Apache to load properly. It's probably just a config problem but the present solution is simply to stop Varnish, restart Apache and then restart Varnish.

Is there an easy way to tell Ubuntu to load Varnish AFTER Apache on system boot until I have time to go back and look at this?

---

### Post by Wise1 on 2014-03-07
I have not looked into this on Ubuntu as I use centos for servers.  However if Ubuntu uses chkconfig then it has a priority setting so you can control the order.

chkconfig [--level <levels>] [--type <type>] <name> <on|off|reset|resetpriorities>

---

### Post by DJ_Max on 2014-03-07
You can start here [https://help.ubuntu.com/community/UpstartHowto](https://help.ubuntu.com/community/UpstartHowto)

---

