---
title: "Server Hacking"
date: 2012-07-11
forum: Server Platforms
---

### Post by Vishal Agarwal on 2012-07-11
Everyday i am getting below log report. i am unable to identify, what port is being used for this type of hacking so that I can block it ?
 



 A total of 38 sites probed the server 
      101.108.37.150
      101.224.2.249
      108.3.237.42
      109.168.209.239
      110.77.149.139

and so many. 

This report comes from syslog report.

---

### Post by SeijiSensei on 2012-07-11
If your iptables ruleset has a default DENY policy, or a catch-all REJECT at the bottom, there is nothing you need to do.

If you want more information about what's happening, add this to the bottom of the ruleset, just above any catch-all REJECT rule:

```

iptables -A INPUT -j LOG 

```

Now you'll get verbose entries in syslog with the ports being targeted.

There's nothing you can do to stop being probed other than having a robust set of firewalling rules to block the attempts.

---

