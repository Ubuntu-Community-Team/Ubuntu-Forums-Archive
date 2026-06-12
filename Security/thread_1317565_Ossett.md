---
title: "Ossett"
date: 2009-11-06
forum: Security
---

### Post by phillw on 2009-11-06
I've just received the following alerts, via email, to me.

My system is supposed to be 'locked down'

> OSSEC HIDS Notification.
2009 Nov 07 00:54:34

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:54:34 localhost udev-configure-printer: Failed to get parent



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:54:34

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:54:34 localhost udev-configure-printer: Failed to get parent



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:54:34

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:54:34 localhost udev-configure-printer: Failed to get parent



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:54:34

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:54:34 localhost udev-configure-printer: Failed to get parent



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:54:34

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:54:34 localhost udev-configure-printer: Failed to get parent



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:54:35

Received From: piglet->ossec-monitord
Rule: 502 fired (level 3) -> "Ossec server started."
Portion of the log(s):

ossec: Ossec started.



 --END OF NOTIFICATION> OSSEC HIDS Notification.
2009 Nov 07 00:56:37

Received From: localhost->/var/log/messages
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:56:36 localhost pulseaudio[2768]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:56:37

Received From: localhost->/var/log/auth.log
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:56:36 localhost gnome-keyring-daemon[2702]: Failed to unlock login on startup



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:56:37

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:56:36 localhost pulseaudio[2768]: shm.c: shm_open() failed: Read-only file system



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:56:37

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:56:36 localhost pulseaudio[2768]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.



 --END OF NOTIFICATION



OSSEC HIDS Notification.
2009 Nov 07 00:56:39

Received From: localhost->/var/log/syslog
Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Nov  7 00:56:38 localhost gnome-session[2717]: WARNING: Could not launch application 'at-spi-registryd-wrapper.desktop': Unable to start application: Failed to execute child process "/usr/lib/gnome-session/helpers/at-spi-registryd-wrapper" (No such file or directory)



 --END OF NOTIFICATION

But, along with other reports... this is the one that worries me ....

> OSSEC HIDS Notification.
2009 Nov 07 00:59:39

Received From: localhost->/var/log/auth.log
Rule: 5403 fired (level 4) -> "First time user executed sudo."
Portion of the log(s):

Nov  7 00:59:39 localhost sudo:     root : TTY=unknown ; PWD=/ ; USER=phillw ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy



 --END OF NOTIFICATION
Any help would be appreciated,

Thanks,

Phill.

---

