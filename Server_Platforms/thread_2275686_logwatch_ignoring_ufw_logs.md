---
title: "logwatch ignoring ufw logs"
date: 2015-04-27
forum: Server Platforms
---

### Post by lars10 on 2015-04-27
Hey,

today I set up logwatch on my VPS running Ubuntu 14.04.2 LTS.
It's working great with one exception: It does ignore the firewall block reports from ufw.
I'm using ufw as my firewall and it is blocking a lot of connections and logging this to syslog.
However, logwatch doesn't report a single one, although all log reports are enabled and no matter what detail setting is set.

Any ideas?

Thanks!
Lars

---

