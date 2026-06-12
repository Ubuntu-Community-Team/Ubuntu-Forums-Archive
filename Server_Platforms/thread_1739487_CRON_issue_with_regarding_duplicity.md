---
title: "CRON issue with regarding duplicity"
date: 2011-04-26
forum: Server Platforms
---

### Post by hawk2010 on 2011-04-26
Hi all,

I'm on Ubuntu 10.04 server .
I have added the following duplicity command to a shell script and moved it to /usr/bin

duplicity full --no-encryption --ssh-options="-oProtocol=2 -oIdentityFile=/home/user/.ssh/kow" --verbosity=9 /home/user/Desktop/testdup scp://kowalski@192.168.2.68//home/kowalski/testdup2

I have added the following line at /etc/crontab

45 10 * * * root sh /usr/bin/backupk.sh >/dev/null 2>&1

I logged in as root and executed the script and it works. But when its on cron it doesn't. I do not see any entries in the remote server.

My cron.log shows the following : 

Apr 26 10:45:01 user CRON[5629]: (root) CMD (sh /usr/bin/backupk.sh >/dev/null 2>&1)

Any idea why this is happening?

---

### Post by zerocooly2kde on 2011-05-08
Hi,

what did you do to fix the problem?
I have the same one and can't figure out what's wrong.

thx

---

