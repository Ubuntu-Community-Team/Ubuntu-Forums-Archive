---
title: "Headless Server Hangs on Reboot"
date: 2010-12-19
forum: Server Platforms
---

### Post by MrWES on 2010-12-19
At times, say when I have a power outage and there may be disk errors; when my server reboots it hangs on a check disk prompt. How to I set it so that it automatically checks the disk(s) for error without asking me.

Bill

---

### Post by clrg on 2010-12-19
Add the following line to /etc/rc.local
```
touch /forcefsck
```

And your server will run a filesystem check every time it reboots.

---

### Post by MrWES on 2010-12-19
I don't necessarily want a filesystem check everytime, however, when it does run I don't want it to be interactive. It's a headless server, so I want the check to run without prompts from me.

Bill

---

### Post by CharlesA on 2010-12-19
As far as I know, it is unable to repair errors automatically. You'd have to run fsck manually for it to do that.

Also, if you are running into power problems, why not get a UPS, so the machine can be shutdown safely in the event of a power failure.

---

