---
title: "Rsync Troubles"
date: 2008-11-07
forum: Server Platforms
---

### Post by baudday on 2008-11-07
```
@ERROR: auth failed on module usernamebackup
rsync error: error starting client-server protocol (code 5) at
/home/lapo/packaging/rsync-3.0.4-1/src/rsync-3.0.4/main.c(1504) [sender=3.0.4]
```

Replacing username with my actual username, this is the error I get whenever I try to backup my windows PC to rsync on the server. Does anyone know what the problem could be?

---

### Post by windependence on 2008-11-08
Code 5 usually indicates a bad password. Make sure your caps lock is OFF.

-Tim

---

