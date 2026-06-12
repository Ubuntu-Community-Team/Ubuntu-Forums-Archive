---
title: "Boot message logging"
date: 2007-01-16
forum: Server Platforms
---

### Post by kitman420 on 2007-01-16
I have an ubuntu server 6.06 system where I do not have access to the console. So when the machine reboots, I can't see the startup messages that say which process is started.  If a process doesn't start, the errors don't show up in the logs. How can I enable boot message logging?

I did some searching and I found a [_spec_]("https://blueprints.launchpad.net/ubuntu/+spec/boot-message-logging") for exactly what I need but it's not implemented on my system. Is there a patch/package I can download or somehow enable this with syslog?

Thanks,
D

---

### Post by kitman420 on 2007-01-16
It turns out that bootlogd isn't turned on by default in ubuntu server 6.06. How dumb. This should be turned on by default in any server.

Had to edit /etc/default/bootlogd and set it to yes
also had to update-rc.d -f bootlogd defaults

---

