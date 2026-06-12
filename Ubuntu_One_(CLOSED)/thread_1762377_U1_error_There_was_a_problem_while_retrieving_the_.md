---
title: "U1 error: There was a problem while retrieving the credentials."
date: 2011-05-19
forum: Ubuntu One (CLOSED)
---

### Post by arpit22x on 2011-05-19
Hi all,


Plz help me to connect to u1.
u1sdtool -s gives

State: READY
    connection: Not User With Network
    description: ready to connect
    is_connected: False
    is_error: False
    is_online: False
    queues: IDLE

~/.cache/ubuntuone/log/syncdaemon-exceptions.log gives:


2011-05-19 14:16:44,732 - twisted - ERROR - Unhandled error in Deferred:
2011-05-19 14:16:44,732 - twisted - ERROR - Unhandled Error
Traceback (most recent call last):
Failure: ubuntuone.platform.linux.dbus_interface.NoAccessToken: CredentialsNotFound

I have tried with two different accounts but it gives the same error. Plz help. I have already posted it here-
[http://ubuntuforums.org/showthread.php?t=1738894](http://ubuntuforums.org/showthread.php?t=1738894)

---

