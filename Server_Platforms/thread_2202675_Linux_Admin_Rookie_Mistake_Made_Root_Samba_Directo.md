---
title: "Linux Admin Rookie Mistake: Made Root Samba Directory Owned by Root Group"
date: 2014-01-30
forum: Server Platforms
---

### Post by mckelvey-andy on 2014-01-30
So, now no one can access shares and I'm even unable to cd into the directory at all unless I first sudo bash.

I need to know how to undo this and make the /srv/samba folder have the default permissions a fresh install would have.

Thanks, appreciate it.

-Andrew

---

### Post by bab1 on 2014-01-30
> **mckelvey-andy said:**
> So, now no one can access shares and I'm even unable to cd into the directory at all unless I first sudo bash.

I need to know how to undo this and make the /srv/samba folder have the default permissions a fresh install would have.

Thanks, appreciate it.

-Andrew

You use ***chown *** change the group ownership like this```
sudo chown root:users /srv/samba
```...or you can use ***chgrp ***like this```
sudo chgrp users /srv/samba
```

[COLOR="#0000FF"]Edit: The root user is always the owner and group owner of /srv.  You always have to use sudo to create a directory below /srv initially.[/COLOR]

---

