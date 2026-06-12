---
title: "Server updates"
date: 2006-01-13
forum: Server Platforms
---

### Post by ned.b on 2006-01-13
Is there a mechanism by which a server installation updates itself?  To clarify further, if you are running straight Ubuntu desktop then you get notified of updates and have the opportunity to install them, does this happen on either of the server installs?

---

### Post by nocturn on 2006-01-13
[QUOTE=ned.b]Is there a mechanism by which a server installation updates itself?  To clarify further, if you are running straight Ubuntu desktop then you get notified of updates and have the opportunity to install them, does this happen on either of the server installs?[/QUOTE]

No, it doesn't.

I run an ubuntu server and I subscribe to the security mailing list (only notifications).  When the mails come  in, I run aptitude update && aptitude upgrade to get it updated.

---

### Post by Peter76 on 2006-01-13
It shouldn't be difficult to make a cron job out of that...

---

### Post by ned.b on 2006-01-13
Thanks for the info! :)

---

### Post by imagine on 2006-01-13
[unattended-upgrades](https://launchpad.net/distros/ubuntu/+spec/unattended-package-upgrades), in development.
[http://packages.ubuntu.com/dapper/admin/unattended-upgrades](http://packages.ubuntu.com/dapper/admin/unattended-upgrades)

At the moment you have to resort to a bash script and cron jobs: [https://wiki.ubuntu.com/AutoWeeklyUpdateHowTo](https://wiki.ubuntu.com/AutoWeeklyUpdateHowTo)

---

