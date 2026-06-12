---
title: "Services do not start after a reboot (none of them); what happened?"
date: 2014-07-24
forum: Server Platforms
---

### Post by a03-6eo-chg on 2014-07-24
Hello!

I have an Ubuntu 12.04.4 LTS server that is hosted with mediaTemple. They performed "routine" maintenance this morning and the server never came back online after they performed a "hard reboot" (I could tell it was a hard reboot from the syslog; there was no evidence of a proper shutdown).

The first thing I tried was to reboot the VM instance again. But it appeared to be "frozen" at the container-level. I had to call mediaTemple and have a support rep get directly at the console and reboot the instance.

The instance booted, but not a single service started. The entire OS was only using 7MB of RAM. The rep tried to start the sshd service manually and stated that it failed because the /var/run/sshd directory did not exist. So, he created the directory manually and then sshd started correctly.

Am I mistaken in that the sshd init script should **create** that directory if it doesn't exist? Isn't that one of the core functions of an init script, to create any directories, PID lock files, etc. that are necessary for the service to run? My understanding is that /var/run is ephemeral; it is wiped on boot, intentionally. So, why on Earth would sshd fail to start because /var/run/sshd doesn't exist?

Once I had SSH access again, I began looking around for a reason for which none of the normal services (mysql, nginx, postfix, postgrey, dovecot, bind, etc.) started after boot-up was complete. The natural go-to was the syslog. Well, as it turns-out, sysklogd hadn't even started, so there were no log entries from the moment that mediaTemple killed the power on the VM instance.

Has anybody ever seen this happen? My obvious concern is that if this VM is ever restarted for any reason, the same thing will occur.

How can I find the root-cause for this? I mean, a VM should be able to be hard-rebooted and bounce-back with no major repercussions. The case here was anything but.

Thanks for any help.

---

### Post by TheFu on 2014-07-25
Can you compare all the changed files from the prior day backups to see what is missing, changed, added?

---

