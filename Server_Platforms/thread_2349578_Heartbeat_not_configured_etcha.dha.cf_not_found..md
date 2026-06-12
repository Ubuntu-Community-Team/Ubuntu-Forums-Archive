---
title: "Heartbeat not configured: /etc/ha.d/ha.cf not found."
date: 2017-01-16
forum: Server Platforms
---

### Post by doctorwho12 on 2017-01-16
Hi, I have looked on Google and I can't find a solution to this particular problem. Any help is much apreciated!

I have been following [https://tipstricks.itmatrix.eu/configuring-heartbeat/](https://tipstricks.itmatrix.eu/configuring-heartbeat/) tutorial on how to set up heartbeat. I have coppied it exactly, except changed the IP's and hostnames.
When I try to start Heartbeat, I get the following error:

```
Jan 16 03:10:27 webha1 systemd[1]: Starting LSB: High-availability services....
Jan 16 03:10:27 webha1 heartbeat[6181]: Heartbeat not configured: /etc/ha.d/ha.cf not found. Heartbeat failure [rc=1]
Jan 16 03:10:27 webha1 systemd[1]: heartbeat.service: PID file /var/run/heartbeat.pid not readable (yet?) after start
Jan 16 03:10:27 webha1 systemd[1]: Failed to start LSB: High-availability services..
Jan 16 03:10:27 webha1 systemd[1]: heartbeat.service: Unit entered failed state.
Jan 16 03:10:27 webha1 systemd[1]: heartbeat.service: Failed with result 'resources'.
```

I have tried CHMOD 755, and this makes no difference. All files in the directory are owned by root.

Thanks in advance!

---

