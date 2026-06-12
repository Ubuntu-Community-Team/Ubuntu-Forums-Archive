---
title: "Can I safely delete /etc/mysql?"
date: 2019-02-03
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2019-02-03
I'm migrating most of my services into containers. I just moved my mariadb server into a container then did  ```
apt --purge autoremove mariadb-server
``` on my host. However it left behind the /etc/mysql folder. If I don't need it, I'd like to dump it but I'm afraid of losing something. The only services on the host that use sql in any form is Kodi. Can I safely delete this folder to keep things tidy and cleaned up?

*EDIT* Marking as solved. I came up with a way to troubleshoot and eliminate it myself. Kodi being the only thing relying on SQL I simply moved the /etc/mysql folder to /etc/mysql.orig and restarted Kodi. Testing all database functions and everything is working fine. Have eliminated the folder. System is clean.

---

### Post by TheFu on 2019-02-03
If you aren't positive, just move the directory to a .old name and wait a month.  You can even setup an 'at' job to delete it automatically in the future.

---

### Post by Tadaen_Sylvermane on 2019-02-03
I thank you much. I just had the same idea. Moved it to mysql.orig and restarted Kodi. Kodi being the only DB based software on my host, tested and all is well. I'm glad you confirmed the thought. It is now gone and cleaned out.

Side note. Why wasn't that folder cleared on a purge?

---

