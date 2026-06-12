---
title: "rsync and lastlog"
date: 2007-03-14
forum: Server Platforms
---

### Post by jonbuys on 2007-03-14
Hello,

I've got a confusing question about rsync, ssh, and the lastlog file.  I've got an Ubuntu 6.06 server setup with a restricted user shell (rbash) that can only access rsync.  When I rsync to this server, the server does not update the lastlog file with the connection information.  It seems that lastlog is only updated when I actually log in with ssh or via the terminal.  

I'd really like to be able to track rsync logins, to make sure my automated backups are working.  Any ideas?

Thanks

---

