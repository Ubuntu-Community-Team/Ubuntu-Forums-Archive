---
title: "When to reboot after update on server?"
date: 2007-09-01
forum: Server Platforms
---

### Post by ariek on 2007-09-01
Hi all,

Is there a way to find out when a server needs a reboot? After my last update (just now) I received kernel update linux-image-2.6.20-16-generic 2.6.20-16.31, while uname -r tells me it is using 2.6.20-16-generic. I would be nice if there's an easy way to tell by, let's say a log entry, or an email.

Thanks for any replies,

Arie

---

### Post by southernman on 2007-09-01
Any kernel update = reboot

Most software updates = restart those specific services

---

### Post by rich.bradshaw on 2007-09-01
Yeah, you have to restart for any kernel.

Any software can just be restarted.

---

### Post by az on 2007-09-01
From /usr/share/doc/update-notifier/HOOKS

"Another example is the reboot notification. Packages like the kernel,
glibc, dbus and hal require a reboot. To simplify things
update-notifier installs a helper script in

/usr/share/update-notifier/notify-reboot-required"


cat /usr/share/update-notifier/notify-reboot-required 

#!/bin/sh

# Wake the applet up
if mountpoint -q /var/run; then
        touch /var/run/reboot-required
fi



So, if /var/run/reboot-required is there, a reboot is required.  I guess there is currently no method for Ubuntu-server to send you an email or something like that...

---

### Post by NewbieNik on 2007-09-01
I tend to reboot after any major update. Its a bit like swinging the wall to hit the hammer, but its effextive and saves confusion

---

