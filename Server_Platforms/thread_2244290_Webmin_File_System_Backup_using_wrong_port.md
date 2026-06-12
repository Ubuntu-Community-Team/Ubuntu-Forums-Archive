---
title: "Webmin File System Backup using wrong port"
date: 2014-09-15
forum: Server Platforms
---

### Post by michael-lentz on 2014-09-15
WebMin File System Backup to a remote server uses Port 22. 
My target server does not use port 22. 
How do I tell WebMin to use a different port when RSH or SSH to the remote server ?

---

### Post by TheFu on 2014-09-15
Any tool using ssh should honor the settings in the ~/.ssh/config file.  

```
host remote-system-alias1 spirulina
  user thefu
   hostname www.example.com
   port 30122

```

Simple?
BTW I've never used webmin.

---

