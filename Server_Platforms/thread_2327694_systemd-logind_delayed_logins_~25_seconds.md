---
title: "systemd-logind delayed logins ~25 seconds"
date: 2016-06-13
forum: Server Platforms
---

### Post by cburns on 2016-06-13
Hello,

I am having issues that are similar to [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=770135](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=770135) but keep happening after reboot. Running "systemctl restart systemd-logind.service" fixes the issue temporarily but the issue comes back quickly.

It is also similar to the following bug report [https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1591411](https://bugs.launchpad.net/ubuntu/+source/systemd/+bug/1591411)

There is also heavy ftp usage on this server and we are seeing the following in auth.log

proftpd: pam_systemd(proftpd:session): Failed to create session: Failed to activate service 'org.freedesktop.login1': timed out

ssh user@localhost hangs for 25 seconds after password is entered.

---

### Post by ciberandy2 on 2016-08-08
Since xenial I'm having the same problem. :-(
But not on all my ubuntu machines.

And clue anyone?

Thanksin advance!

---

