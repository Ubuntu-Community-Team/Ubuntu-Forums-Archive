---
title: "Clarifications on hierarchies of configurations in Fail2Ban"
date: 2019-07-09
forum: Security
---

### Post by WhiteTigerIT on 2019-07-09
I'm new with Fail2ban and I'm studying a configuration already active on a server, but I can't understand the configuration hierarchy.


For example:
in jail.conf there is:
```
[Ssh]
enabled = false
filter = sshd
action = iptables [name = SSH, port = ssh, protocol = tcp]
logpath = /var/log/auth.log
maxretry = 5

```

In jail.local there is:
```
[Ssh]
enabled = true

```

In jail.d / custom.conf instead there is no reference to ssh.


But if I go to the management panel I see that the Jail is active with the jail.conf configuration


I had understood that the jail.local goes to replace the jail.conf, so instead it seems to me that it integrates it and replaces it exclusively in the "enabled = true" entry, while the configuration remains that of jail.conf.

How does the configuration hierarchy work?


On my server I copied jail.conf to jail.local and was making changes to this, while new jail inserted them into a file under jail.d.
However, if what is present in jail.conf is still interpreted by fail2ban, I am afraid it will be very confusing.

---

