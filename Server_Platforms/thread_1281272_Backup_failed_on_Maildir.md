---
title: "Backup failed on Maildir"
date: 2009-10-03
forum: Server Platforms
---

### Post by sunstriker on 2009-10-03
Hi,

We have a postfix/dovecot server handling our mail at the office. I've configured daily backup on tape using webmin. This solution did the job until some days ago: I've added the always_bcc option in my postfix config (to send a copy of each mail to an archive). Since then I get following error in my mailbox every day:
...

tar: Removing leading `/' from member names
tar: /home/archive/Maildir/new: file changed as we read it
tar: Removing leading `/' from hard link targets
...
Backup failed!

I can't imagine that this Maidir changes every time my system starts backing up. When I turn off "always_bcc" the problem is gone. But I really need this option.

Any ideas?

---

