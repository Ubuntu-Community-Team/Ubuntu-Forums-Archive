---
title: "Syslog-ng on a remote switch"
date: 2013-08-15
forum: Server Platforms
---

### Post by sosytee on 2013-08-15
I have set up a syslog-ng server which logs well internally, however , when i disable internal logging and activate external logging(by commenting on the s_src and removing comments from s_net) on the destinations part, i changed from 
```
source(s_net)
``` where there was ```
(s_src)
``` the rest of the /etc/syslog-ng/syslog-ng.conf file remained as it were. i then configured the switch but i am not getting any logs. i am checking for the logs from the switch from /var/log/syslog.

---

