---
title: "Server Polkitd in Auth.Log"
date: 2012-01-07
forum: Security
---

### Post by freshtoast on 2012-01-07
Hello all,

I was recently checking the auth.log file on my ubuntu ssh server and I saw something I've never seen before:

```
Jan  2 07:03:08 server polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session1 (system bus name :1.22 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8)
Jan  2 07:03:09 server dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=1000 pid=1184 comm="nautilus ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=669 comm="/usr/sbin/console-kit-daemon --no-daemon "))
Jan  2 07:03:11 server dbus-daemon: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.29" (uid=1000 pid=1355 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply=0 destination=":1.9" (uid=0 pid=669 comm="/usr/sbin/console-kit-daemon --no-daemon "))

```

Is this normal, or something I should be worried about?

Many thanks in advance for any help

---

