---
title: "Shorewall not starting on boot 14.04 LTS"
date: 2014-04-27
forum: Server Platforms
---

### Post by zeroburn on 2014-04-27
After I realized shorewall wasn't starting on boot, I tried to check/add it manually and I found this:

```

update-rc.d shorewall enable
update-rc.d: warning:  start runlevel arguments (none) do not match shorewall Default-Start values (S)
update-rc.d: warning:  stop runlevel arguments (none) do not match shorewall Default-Stop values (0 6)
Argument "S" isn't numeric in array element at /usr/sbin/update-rc.d line 232.
 Enabling system startup links for /etc/init.d/shorewall ...
 Removing any system startup links for /etc/init.d/shorewall ...
   /etc/rc0.d/K89shorewall
   /etc/rc6.d/K89shorewall
   /etc/rcS.d/S40shorewall
 Adding system startup for /etc/init.d/shorewall ...
   /etc/rc0.d/K89shorewall -> ../init.d/shorewall
   /etc/rc6.d/K89shorewall -> ../init.d/shorewall
   /etc/rc0.d/S40shorewall -> ../init.d/shorewall

```

Any idea how to fix this? I have the proper startup config set in /etc/default/shorewall and shorewall.conf

EDIT:
Adding shorewall to defaults doesn't remove the warning, but seems to fix the boot issue. Should a bug be reported about this?

```

update-rc.d -f shorewall remove
update-rc.d shorewall defaults

```

---

