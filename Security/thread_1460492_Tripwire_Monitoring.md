---
title: "Tripwire Monitoring"
date: 2010-04-22
forum: Security
---

### Post by Ravernomina on 2010-04-22
Hello all. I just installed and Configured Tripwire. This is just a simple question so i hope it can be answered quickly.Say for example i reboot my computer, Will i need to run tripwire in terminal to have it monitor my disks again? or will it start up automatically when my computer turns on/ When i got in? anyone have any idea? Thanks!

---

### Post by Ravernomina on 2010-04-23
Bump

---

### Post by cdenley on 2010-04-23
It does not constantly run in the background. It is run daily.
```

ls /etc/cron.daily/tripwire

```

---

