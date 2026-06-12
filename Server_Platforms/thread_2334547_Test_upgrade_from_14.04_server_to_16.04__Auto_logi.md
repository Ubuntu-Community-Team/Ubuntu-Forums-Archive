---
title: "Test upgrade from 14.04 server to 16.04:  Auto login fails"
date: 2016-08-20
forum: Server Platforms
---

### Post by DigiAngel on 2016-08-20
Currently I modified /etc/init/tty1.conf as shown running on 14.04 Server:
```
#exec /sbin/getty -8 38400 tty1
exec /bin/login -f mysername < /dev/tty1 > /dev/tty1 2>&1

```

After a test upgrade on a VM this no longer works.  Is there something else I need to accomplish for an autologin to console with 16.04?  Thank you.

---

### Post by DigiAngel on 2016-08-21
Because #systemd:

[http://forums.debian.net/viewtopic.php?f=16&t=123694]("http://forums.debian.net/viewtopic.php?f=16&t=123694")

Edit the file at /etc/systemd/system/getty.target.wants/getty@tty1.service and change the "ExecStart=" line in the "[Service]" to: 
```
ExecStart=-/sbin/agetty -a <user name> %I $TERM
```

---

