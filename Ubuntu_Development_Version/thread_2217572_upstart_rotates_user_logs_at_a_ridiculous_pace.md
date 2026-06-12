---
title: "upstart rotates user logs at a ridiculous pace"
date: 2014-04-17
forum: Ubuntu Development Version
---

### Post by mc4man on 2014-04-17
It seems to be set to do so hourly.
My ~/.cache/upstart/ was emptied early this morning & I haven't been online that much today. 
(a few hrs. this moring, for a moment this afternoon, a couple of hrs. tonight. 
At this point I'm up to the 6th rotate on some of the more active logs like gnome-session & dbus.

I've reason here to limit writes whenever possible so as a matter of course set the user upstart  logs rotate to monthly & until needed make some of the very 'active' logs read only, otherwise don't think the space used matters much
Maybe this was done intentionally to mitigate some logs almost continuously printing useless info?, Guess I'll see at some point - 
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1309271](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/1309271)

---

### Post by QDR06VV9 on 2014-04-18
Yep same here, Dont know if it matters but I have apport disabled.
From testing haven't re-enabled yet. seen a few crash logs not many.

---

### Post by cariboo on 2014-04-18
I'm not seeing that here, mind I'm running a new system, and the only log that has rotated do far are syslog.

---

### Post by zika on 2014-04-18
```
-rw-r-----   1 some_user some_user    2272 Apr 18 10:36 dbus.log-rw-r-----   1 some_user some_user    3609 Apr 18 10:19 gnome-settings-daemon.log
-rw-r-----   1 some_user some_user     218 Apr 18 10:17 unity-panel-service.log
-rw-r-----   1 some_user some_user 2197110 Apr 18 10:09 gnome-session.log
drwx------   2 some_user some_user   20480 Apr 18 09:42 .
-rw-r-----   1 some_user some_user    2884 Apr 18 09:14 indicator-sound.log
-rw-r-----   1 some_user some_user     240 Apr 18 09:14 indicator-session.log
-rw-r-----   1 some_user some_user  188022 Apr 18 09:13 gnome-session.log.1.gz
-rw-r-----   1 some_user some_user    1514 Apr 18 09:13 dbus.log.1.gz
-rw-r-----   1 some_user some_user     908 Apr 18 09:13 gnome-settings-daemon.log.1.gz
-rw-r-----   1 some_user some_user     358 Apr 18 09:12 indicator-sound.log.1.gz
-rw-r-----   1 some_user some_user     156 Apr 18 09:12 indicator-sync.log.1.gz
-rw-r-----   1 some_user some_user     170 Apr 18 09:12 indicator-bluetooth.log.1.gz
-rw-r-----   1 some_user some_user     108 Apr 18 09:12 indicator-power.log.1.gz
-rw-r-----   1 some_user some_user     109 Apr 18 09:12 window-stack-bridge.log.1.gz
-rw-r-----   1 some_user some_user     373 Apr 18 09:12 at-spi2-registryd.log.1.gz
-rw-r-----   1 some_user some_user      95 Apr 18 09:12 unity7.log.1.gz
-rw-r-----   1 some_user some_user      91 Apr 18 09:12 click-user-hooks.log.1.gz
-rw-r-----   1 some_user some_user     134 Apr 18 09:12 update-notifier-crash-_var_crash_libebml4.0.crash.log.1.gz
-rw-r-----   1 some_user some_user      77 Apr 18 09:12 im-config.log.1.gz
-rw-r-----   1 some_user some_user      85 Apr 18 09:12 update-notifier-release.log.1.gz
-rw-r--r--   1 some_user some_user      60 Apr 18 09:12 dbus-session
-rw-r-----   1 some_user some_user      69 Apr 18 09:12 ssh-agent.log.1.gz
-rw-r-----   1 some_user some_user     209 Apr 18 09:11 hud.log.1.gz
-rw-r-----   1 some_user some_user     210 Apr 18 09:11 unity-panel-service.log.1.gz
-rw-r-----   1 some_user some_user     213 Apr 18 09:08 indicator-session.log.1.gz
-rw-r-----   1 some_user some_user      90 Apr 18 08:20 unicast-local-avahi.log.1.gz
-rw-r-----   1 some_user some_user   97216 Apr 18 08:03 gnome-session.log.2.gz
-rw-r-----   1 some_user some_user    1052 Apr 18 08:03 dbus.log.2.gz
-rw-r-----   1 some_user some_user    1028 Apr 18 08:03 gnome-settings-daemon.log.2.gz
-rw-r-----   1 some_user some_user     459 Apr 18 08:03 indicator-sound.log.2.gz
-rw-r-----   1 some_user some_user     157 Apr 18 08:03 indicator-bluetooth.log.2.gz
-rw-r-----   1 some_user some_user      99 Apr 18 08:03 indicator-power.log.2.gz
-rw-r-----   1 some_user some_user     101 Apr 18 08:03 window-stack-bridge.log.2.gz
-rw-r-----   1 some_user some_user     373 Apr 18 08:03 at-spi2-registryd.log.2.gz
-rw-r-----   1 some_user some_user      86 Apr 18 08:03 unity7.log.2.gz
-rw-r-----   1 some_user some_user      82 Apr 18 08:03 click-user-hooks.log.2.gz
-rw-r-----   1 some_user some_user     121 Apr 18 08:03 update-notifier-crash-_var_crash_libebml4.0.crash.log.2.gz
-rw-r-----   1 some_user some_user      74 Apr 18 08:03 im-config.log.2.gz
-rw-r-----   1 some_user some_user      73 Apr 18 08:03 update-notifier-release.log.2.gz
-rw-r-----   1 some_user some_user      60 Apr 18 08:02 ssh-agent.log.2.gz
```
As I recall there was reboot due to new 999 in the meantime...

---

### Post by mc4man on 2014-04-18
here's ex. on here after a little less than a day, it is keeping the size small on active one
> ~/.cache/upstart$ ls -la |grep gnome
-rw-r-----  1 doug doug  5633 Apr 18 06:24 gnome-session-Unity.log
-rw-r-----  1 doug doug  2647 Apr 18 06:08 gnome-session-Unity.log.1.gz
-rw-r-----  1 doug doug  8150 Apr 17 22:18 gnome-session-Unity.log.2.gz
-rw-r-----  1 doug doug  2491 Apr 17 19:13 gnome-session-Unity.log.3.gz
-rw-r-----  1 doug doug  3162 Apr 17 14:13 gnome-session-Unity.log.4.gz
-rw-r-----  1 doug doug  7281 Apr 17 11:26 gnome-session-Unity.log.5.gz
-rw-r-----  1 doug doug  2610 Apr 17 08:25 gnome-session-Unity.log.6.gz


---

### Post by zika on 2014-04-18
> **mc4man said:**
> here's ex. on here after a little less than a day, it is keeping the size small on active onePointing finger in the dark: GDM with Unity?

---

