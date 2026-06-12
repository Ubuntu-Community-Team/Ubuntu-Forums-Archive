---
title: "Ufw + nflog"
date: 2019-10-30
forum: Security
---

### Post by tomvb on 2019-10-30
Hi All,

[https://bugs.launchpad.net/ufw/+bug/1475676](https://bugs.launchpad.net/ufw/+bug/1475676)
I have some problems with UFW + NFLOG (ulogd2).

I want to replace the LOG prefix with NFLOG in UFW.
```
 $ cd /etc/ufw
 $ sudo sed 's/-j LOG --log-prefix/-j NFLOG --nflog-prefix/' -i.bak user.rules
 $ sudo sed 's/-j LOG --log-prefix/-j NFLOG --nflog-prefix/' -i.bak user6.rules
```

But this workaround is not working. With ufw disable && ufw enable it's gone.

How can I replace the LOG iptables with NFLOG in UFW?
```
### LOGGING ###
-A ufw-after-logging-input -j NFLOG --nflog-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-after-logging-forward -j NFLOG --nflog-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-I ufw-logging-deny -m conntrack --ctstate INVALID -j RETURN -m limit --limit 3/min --limit-burst 10
-A ufw-logging-deny -j NFLOG --nflog-prefix "[UFW BLOCK] " -m limit --limit 3/min --limit-burst 10
-A ufw-logging-allow -j NFLOG --nflog-prefix "[UFW ALLOW] " -m limit --limit 3/min --limit-burst 10
### END LOGGING ###


### RATE LIMITING ###
-A ufw-user-limit -m limit --limit 3/minute -j NFLOG --nflog-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT
-A ufw-user-limit-accept -j ACCEPT
### END RATE LIMITING ###

```

Unprivileged containers don't have a /dev/kmsg device and access to /proc/kmsg is blocked by the kernel.

---

