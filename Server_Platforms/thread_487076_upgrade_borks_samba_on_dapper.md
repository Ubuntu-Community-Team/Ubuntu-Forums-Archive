---
title: "upgrade borks samba on dapper"
date: 2007-06-28
forum: Server Platforms
---

### Post by sgla1 on 2007-06-28
the recent upgrade to samba 3.0.22-1ubuntu3.3 appears to bork the startup links for samba (i.e. /etc/rcx.d/S20samba).  I found that smbd and or nmbd was not started on reboot.  The kill links for samba are still present, though, which will cause ```
update-rc.d samba defaults
``` to fail.

The quick fix I found was to delete the kill scripts ```
update-rc.d -f samba remove
``` and then recreate them as above.  Reboot or start samba manually, then **verify** what is actually running.  You should see the following: ```
root      8694  0.0  0.1   6784  1612 ?        Ss   13:38   0:00 /usr/sbin/nmbd -D
root      8695  0.0  0.0   6632   492 ?        S    13:38   0:00 /usr/sbin/nmbd -D
root      8697  0.0  0.2   9552  2392 ?        Ss   13:38   0:00 /usr/sbin/smbd -D
root      8699  0.0  0.1   9552  1228 ?        S    13:38   0:00 /usr/sbin/smbd -D
```

Cheers

---

