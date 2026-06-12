---
title: "Courier IMAP &amp; FAM problem, timeouts"
date: 2008-08-25
forum: Server Platforms
---

### Post by synergy_ek on 2008-08-25
I have Ubuntu 7.04 Server installed and bundled Courier IMAP. IMAP server give timeouts for connections when active users (about 10) opens multiple connections to mailboxes (about 6-7 for each users). I googled for a problem and found, that problem is FAM daemon - it can opens no more than 50 sockets. When client receive a timeout from IMAP server, command
```
netstat -n | grep fam | wc -l
``` always gives 50.
Enchanced IDLE is off in /etc/courier/imapd
How can I disable FAM without recompiling Courier?

---

