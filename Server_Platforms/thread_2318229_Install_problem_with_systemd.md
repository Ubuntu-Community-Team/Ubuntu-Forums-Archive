---
title: "Install problem with systemd"
date: 2016-03-24
forum: Server Platforms
---

### Post by kaiv on 2016-03-24
Hi there,

something seems to be broken with my package management. I couldn't install any new packages. I tried to solve it myself with the help of Google and came so far as to take away the entry for systemd in /var/lib/dpkg/status to then run:
-> sudo apt-get -f install
(Reading database ... 314324 files and directories currently installed.)
Preparing to unpack .../systemd_225-1ubuntu9.1_amd64.deb ...
dpkg: error processing archive /var/cache/apt/archives/systemd_225-1ubuntu9.1_amd64.deb (--unpack):
** triggers ci file contains unknown directive syntax**
Errors were encountered while processing:
 /var/cache/apt/archives/systemd_225-1ubuntu9.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

but this seems to open another problem. Any ideas?

---

### Post by nerdtron on 2016-03-26
What did you installed before this happened?

---

