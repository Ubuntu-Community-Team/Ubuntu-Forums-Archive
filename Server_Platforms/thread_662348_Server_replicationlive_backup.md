---
title: "Server replication/live backup"
date: 2008-01-08
forum: Server Platforms
---

### Post by MobiusNZ on 2008-01-08
I'm going to be setting up a couple of ubuntu web servers in the next couple of weeks. They're going to have Apache, PHP, MySQL, and FTP on them, and need to be replicated between themselves so that if one goes down the other can step in.

At the moment I'm thinking that the web and ftp can easily be handled by rsync running on a 1minute cron (as they will be gigabit networked together and not that much data would change over 1min), and mysql would replicate via it's own methods (a la [http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html](http://dev.mysql.com/doc/refman/5.0/en/replication-howto.html)).

If the main server went down, I'd adjust the firewall/router to point at the other one, then service would be restored.

Does anyone have any thoughts or concerns with this methodology? Also, has anyone had any experience with automated clustering/load balancing? I understand that this might be a better way to go, except from my initial looks at LVS I'd need 4 servers (2 directors and 2 real servers), which would be a pain.

---

