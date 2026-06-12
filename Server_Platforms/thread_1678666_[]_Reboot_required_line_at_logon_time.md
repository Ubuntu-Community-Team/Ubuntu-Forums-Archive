---
title: "[?] Reboot required line at logon time"
date: 2011-01-30
forum: Server Platforms
---

### Post by Kooothor on 2011-01-30
Hello,

When I log onto my 10.04 server via ssh, there is the /etc/motd displayed.
This motd is made up each time by the files in /etc/update/motd.d/.
There is this one file : update-motd-reboot-required
The content is 
exec /usr/lib/update-notifier/update-mot-reboot-required
and the content of this one is :
if the file /var/run/reboot-required exists, print it.

[B]
But who is making this file and why ??[/B]

we know who it is: it's pam_motd.. but why would I reboot ??!?


editt2 : nvmd
[http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd](http://serverfault.com/questions/92932/how-does-ubuntu-keep-track-of-the-system-restart-required-flag-in-motd)

---

### Post by doogy2004 on 2011-01-30
That file was created by a package that was updated and the system needs to be restarted for the update to take effect.  Updates such as kernel upgrades require a system reboot to take effect.

---

