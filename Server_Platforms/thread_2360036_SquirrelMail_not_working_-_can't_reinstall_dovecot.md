---
title: "SquirrelMail not working - can't reinstall dovecot etc..."
date: 2017-05-01
forum: Server Platforms
---

### Post by dchurch24 on 2017-05-01
Hi all,

I have an Ubuntu 14.04 LTS install on my server.

Until recently, everything was working fine. Suddenly, I couldn't install anything through apt-get, so I googled around a bit and one site in particular said to uninstall dovecot - which I did.

Of course, then all my email stuff stopped working (squirrelmail error: ERROR: Connection dropped by IMAP server.).

I went to reinstall dovercot-core and I get the following error:

Errors were encountered while processing:
 libpam-systemd:i386
 dovecot-core
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am stumped. I can do a apt-get update and that all works fine.

Please help - my wife is extremely annoyed at me for breaking her email, and I am currently getting it in the neck from her! :p

EDIT: The result of uname -a is: Linux xxxxxxxx.co.uk 2.6.32.65-kvm-i386-20150205-hg4accef0bb82b #1 SMP

---

### Post by howefield on 2017-05-01
Thread moved to the "*Server Platforms*" forum for a better fit.

---

