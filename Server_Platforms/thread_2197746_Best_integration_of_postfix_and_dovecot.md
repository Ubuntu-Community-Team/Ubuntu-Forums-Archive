---
title: "Best integration of postfix and dovecot"
date: 2014-01-05
forum: Server Platforms
---

### Post by pft42 on 2014-01-05
Hi,

I have a mail server (12.04LTS) running with fetchmail, postfix, dovecot and amavis. For some users procmail is activation via a pipe in ".forward"

Currently the "integration" is done just by telling postfix the storage location in main.cf: "home_mailbox = Maildir/"

Planning some changes in dovecot configuration (multiple IPs) I browsed through the documentation and found some hints for different ways of integration, like calling the local delivery program of dovecot of even starting a respective daemon in postfix's master.cf.

What is the "recommended" approach with only a dozen users, no virtual mailboxes, pure passwd user "database" and moderate traffic?

Any description of approaches with pros or cons welcome

Thx
Thomas

---

