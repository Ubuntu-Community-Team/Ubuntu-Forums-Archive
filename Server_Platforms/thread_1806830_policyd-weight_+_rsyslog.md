---
title: "policyd-weight + rsyslog"
date: 2011-07-18
forum: Server Platforms
---

### Post by Gatsby7 on 2011-07-18
Hi all.
I just installed policyd-weight on a 10.04 LTS Ubuntu Server distro, and it's working fine. Now i need 2 separate log messages from the postfix one, so i created a "rule"  /etc/rsyslog.d/10-test.conf writing:

:msg, contains, "policyd", /var/log/test.log
& ~

The file is correctly created but it's blank. Can u give me a hint please?

Thanks a lot

---

