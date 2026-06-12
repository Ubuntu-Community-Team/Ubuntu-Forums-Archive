---
title: "How can I filter out dbus-daemon: Rejected send message from logcheck, it's spaming"
date: 2009-04-25
forum: Server Platforms
---

### Post by MechaMechanism on 2009-04-25
SOLVED

Logcheck is getting spamed with messages from dbus-daemon.  How can I filter out this log spam.

```
dbus-daemon: Rejected send message, 1 matched rules; type="method_call", sender=":1.36" (uid=1000 pid=3804 comm="/usr/lib/indicator-applet/indicator-applet --oaf-a") interface="org.freedesktop.DBus.Properties" member="Get" error name="(unset)" requested_reply=0 destination=":1.61" (uid=0 pid=7219 comm="/USR/SBIN/CRON "))
```

---

### Post by mingtien on 2009-04-26
I found this on LaunchPad -- and thought it might do the trick:

[https://bugs.launchpad.net/indicator-applet/+bug/346513](https://bugs.launchpad.net/indicator-applet/+bug/346513)

Actually what it did was hose dbus, which will freeze the keyboard and mouse upon the next boot.  <blush>

---

### Post by MechaMechanism on 2009-04-26
> **mingtien said:**
> I found this on LaunchPad -- and thought it might do the trick:

[https://bugs.launchpad.net/indicator-applet/+bug/346513](https://bugs.launchpad.net/indicator-applet/+bug/346513)

Actually what it did was hose dbus, which will freeze the keyboard and mouse upon the next boot.  <blush>Thank you.  I am now filtering out the spam.  I made a rule in ignore.d.server.

---

### Post by satyap on 2009-06-13
And what rule did you use? I used this:

^\w{3} [ :0-9]{11} [._[:alnum:]-]+ dbus-daemon: Rejected send message, 1 matched rules; type="method_call".*/USR/BIN/CRON.*$

Yeah, it's probably too permissive or whatever.

---

### Post by MechaMechanism on 2009-06-13
The filter wound up not working and I didn't want to put any more effort into it.  Any way there are many more than just cron messages, so I decided to wait for proper fix now.

---

