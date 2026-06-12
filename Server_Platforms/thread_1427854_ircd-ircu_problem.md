---
title: "ircd-ircu problem"
date: 2010-03-12
forum: Server Platforms
---

### Post by m3bik on 2010-03-12
I'm trying to set up a private irc server. I install ircd-ircu, modify the configuration file, restart the daemon, and everything works great. After the next server reboot, the server shows the daemon is running, but I can no longer connect to the server from my irc client. I've tried restarting the daemon with no luck. I can then uninstall and reinstall it with the same outcome. Everything works initially, but after rebooting, the irc client can't connect... Is there something I'm missing or overlooking?

---

### Post by tors on 2010-09-21
```

root@host# mkdir /var/run/ircd
root@host# chown irc:irc /var/run/ircd
root@host# /etc/init.d/ircd-ircu restart

```

---

