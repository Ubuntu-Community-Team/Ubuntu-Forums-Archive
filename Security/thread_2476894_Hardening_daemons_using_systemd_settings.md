---
title: "Hardening daemons using systemd settings"
date: 2022-07-11
forum: Security
---

### Post by ceterum on 2022-07-11
Systemd service files allow for restricting the access rights of the daemon it starts. Take for instance cupsd; it runs as root but access to the filesystem can be limited by adding these lines to the unit file:[INDENT]
ReadOnlyPaths=/
ReadWritePaths=/var/cache/cups /etc/cups /run/cups /var/log/cups
[/INDENT]
 
A lot more restrictions can be added; see systemd.exec(5).

I maintain my patched unit files in */usr/local/lib/systemd/system* where they don't get overwritten when I update the system.

Now my question: Has anybody done a similar thing? Anything on github?

---

### Post by vbgf3 on 2022-07-25
I hope your locking of cups is successful. Have a look at /etc/apparmor.d/usr.sbin.cupsd. It lists various things that cups uses. That file made me cringe. I did 'apt remove cups', I rarely print anything.

---

### Post by ceterum on 2022-07-26
Thanks for the fast reply!

Yes, the cups AppArmor profile looks like a security nightmare. I'd better stick to AppArmor.

BTW, I hadn't thought about the PDF driver needing write access to the entire home directory.

---

