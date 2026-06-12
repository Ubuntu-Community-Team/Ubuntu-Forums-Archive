---
title: "exec: 3: /usr/lib/update-notifier/update-motd-cpu-checker: not found"
date: 2010-06-19
forum: Server Platforms
---

### Post by Pitou on 2010-06-19
Hello,

I got this this morning when loging in my ubuntu server system:

Last login: Sat Jun 19 08:01:00 EDT 2010 on ttyS0
exec: 3: /usr/lib/update-notifier/update-motd-cpu-checker: not found
run-parts: /etc/update-motd.d/20-cpu-checker exited with return code 2
run-parts: failed to stat component /etc/update-motd.d/50-landscape-sysinfo: No such file or directory
exec: 3: /usr/lib/update-notifier/update-motd-updates-available: not found
run-parts: /etc/update-motd.d/90-updates-available exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-reboot-required: not found
run-parts: /etc/update-motd.d/98-reboot-required exited with return code 2


Any idea what happened?

Thank you.

Pitou!

---

### Post by techathy on 2010-10-23
Had this this morning after updating my HTPC install.
```
sudo apt-get install update-notifier-common
```
which installed 2 packages in total & now everything is back to how it was. I assume that some changes to do with which packages provide various files has broken things with people using non-existant/minimal desktop server installs.

---

