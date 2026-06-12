---
title: "Showing security update details"
date: 2020-09-01
forum: Security
---

### Post by sean02 on 2020-09-01
How can we see the details of pending security updates?

```

root@ubuntuhost:~# apt list --upgradable | grep security

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

linux-generic/focal-updates,focal-security 5.4.0.45.49 amd64 [upgradable from: 5.4.0.42.46]
linux-headers-generic/focal-updates,focal-security 5.4.0.45.49 amd64 [upgradable from: 5.4.0.42.46]
linux-headers-virtual/focal-updates,focal-security 5.4.0.45.49 amd64 [upgradable from: 5.4.0.42.46]
linux-image-generic/focal-updates,focal-security 5.4.0.45.49 amd64 [upgradable from: 5.4.0.42.46]
linux-image-virtual/focal-updates,focal-security 5.4.0.45.49 amd64 [upgradable from: 5.4.0.42.46]
linux-libc-dev/focal-updates,focal-security 5.4.0-45.49 amd64 [upgradable from: 5.4.0-42.46]
linux-virtual/focal-updates,focal-security 5.4.0.45.49 amd64 [upgradable from: 5.4.0.42.46]
```


I don't see any mention of the security issues in apt changelog. How can I find out what security issues are addressed by an update?

---

### Post by scorp123 on 2020-09-01
> **sean02 said:**
> How can I find out what security issues are addressed by an update?

Security notices (explaining what and why something is getting fixed) can be found here:
[https://ubuntu.com/security/notices]("https://ubuntu.com/security/notices")

You can also check the sources and the commit logs of the developers, e.g. for the Linux kernel.

Example for the Linux kernel packages in Ubuntu 20.04... their git repository is here:
[https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/focal]("https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/focal")

The last "git commit" from about 6 days ago for the kernel 5.4.0-45.49 shows these entries:
[https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/focal/log/?h=Ubuntu-5.4.0-45.49]("https://git.launchpad.net/~ubuntu-kernel/ubuntu/+source/linux/+git/focal/log/?h=Ubuntu-5.4.0-45.49")

You can click on every entry there and read why something was pushed or removed which ultimately lead to the new kernel package being released and then pushed to us end-users.

Dito for the upstream Linux kernel project. Their logs are here:
[https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/log/")

---

### Post by sean02 on 2020-09-03
Thanks, this is basically what I've been doing: Searching for  announcements about packages that I see pending updates for. I was hoping  there was some way that I could get a concise description of why  something is in the security updates channel from the shell.

---

