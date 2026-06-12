---
title: "View incoming ssh and sftp connections"
date: 2008-07-14
forum: Security
---

### Post by futileissue on 2008-07-14
Sorry in advance if this is posted elsewhere, I did numerous searches and couldn't find anything relevant.  Also checked manpages for answers and found nothing.

I'm running an openssh server on my Ubuntu 8.04 machine.  (just for easy access to my files elsewhere).  Is there an easy way to view all currently active ssh/sftp connections?  I would like to see who's logged on, and if possible details about their actions.

Thank you.

---

### Post by Vivaldi Gloria on 2008-07-14
> **futileissue said:**
> Sorry in advance if this is posted elsewhere, I did numerous searches and couldn't find anything relevant.  Also checked manpages for answers and found nothing.

I'm running an openssh server on my Ubuntu 8.04 machine.  (just for easy access to my files elsewhere).  Is there an easy way to view all currently active ssh/sftp connections?  I would like to see who's logged on, and if possible details about their actions.

Thank you.

See /var/log/auth.log and try the command "netstat". Read

```
man netstat
```

These will show you login attempts and active connections. I don't know how you can log their actions.

---

### Post by futileissue on 2008-07-14
Thanks.  I think after some research I've discovered that sftp with openssh simply does not support any realistic way to accurately log actions.

---

### Post by daleus on 2008-07-14
you can try "watch who" in a terminal, which will show you who is logged in (from where, IP etc, or if they're local with their tty) it updates every 2 seconds, I use it to keep SSH alive (SSH keepalive doesn't work against corporate firewall used here)

---

### Post by IanUK on 2013-03-11
Try - 

grep sshd:session /var/log/auth.log | tail -1 | awk '{print $8}'

Will return "opened" or "closed" or nothing if no sessions ever used.

---

### Post by oldos2er on 2013-03-11
Old thread closed, please don't bump old threads.

---

