---
title: "Simple Samba Question"
date: 2008-11-05
forum: Server Platforms
---

### Post by TheGameAh on 2008-11-05
Hey guys.

Working on moving a bunch of shares off of an Active Directory box onto a Linux Samba server.  I'm still getting shares setup and stuff, but a question about restarting the service.

Exactly when do you have to restart the samba service?  If I add a group to the "write list" for instance, do I have to restart samba?  If I do, I assume that just for that second that samba restarts, users are cut out of their files, right?

---

### Post by HermanAB on 2008-11-05
You should not need to restart the service.

You should read the Official Howto on the Samba web site:
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

Cheers,

Herman

---

### Post by lykwydchykyn on 2008-11-05
If you change the config, you need to reload it.  This isn't quite the same as a restart.  I would have to experiment to be sure, but I don't beleive this affects running sessions.

So the command would be:
/etc/init.d/samba reload
or
invoke-rc.d samba reload
or
smbcontrol smbd reload-config

---

### Post by cdenley on 2008-11-05
You have to restart samba if you change the global configuration. You can reload it if you change the share configuration, but I think it's reloaded every minute, anyway.

---

