---
title: "rsh from bash script problem"
date: 2010-05-03
forum: Security
---

### Post by daniele75 on 2010-05-03
Hello all.

I've this problem, I need to run a remote command from an ubuntu server to another, so I launch this command via bash script.

The command launched from terminal line works greatly.

When it's invoked by bash script it doesn't work; adding some redirection I can see that error is

Host key verification failed.

Command that I execute is

/usr/bin/rsh -i /home/nagios/.ssh/id_rsa root@192.168.1.16 /usr/local/bin/test >> /var/log/test 2>&1

I've tried to use also "/home/nagios/.ssh/id_rsa" and '/home/nagios/.ssh/id_rsa', with no results.

Until one month ago script worked greatly, I suppose that problem is arise when I've run apt-get upgrade last time, that has upgraded ssh.

Any help will be appreciated.

Daniele

---

