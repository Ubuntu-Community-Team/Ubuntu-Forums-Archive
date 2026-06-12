---
title: "Apache, mysql. monit don't start on reboot"
date: 2013-03-06
forum: Server Platforms
---

### Post by chmac on 2013-03-06
We have 3 dedicated servers, 2 with OVH (who roll their own kernel) and one with Hetzner. They're all configured virtually identically thanks to puppet.

However, on the Hetzner machine, after a reboot, some services are not started automatically. Specifically, apache2, mysql, and monit are the ones I've noticed. I've compared the /etc/init/ and /etc/init.d/ scripts for these three programs and they're the same on all 3 servers. I've likewise checked /etc/rc2.d/ and the same links appear for all servers.

How do I debug this problem? I can't find anything pertinent in /var/log/syslog and I'm at a loss as to where else I could be looking.

---

