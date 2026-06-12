---
title: "save iptable rules?"
date: 2009-06-23
forum: Security
---

### Post by firsttimeuser on 2009-06-23
Does iptable provide some sort of save under init.d feature?

I manually created the iptable rules and want the rule sets to be loaded every time the system boot.

thanks

---

### Post by Bachstelze on 2009-06-23
To save your rules:

```
iptables-save > rules.txt
```

To restore them:

```
iptables-restore < rules.txt
```

To have them restored at boot, you can for example set a [font="monospace"]@reboot[/font] cron job for root.

---

