---
title: "Sudo bug ?"
date: 2004-11-22
forum: Server Platforms
---

### Post by troutrou on 2004-11-22
I don't quite understand this 'sudo" thing. Is it like a proper root terminal except that you must call sudo for each and every command you want to run as root ?

I was expecting sudo to therefore ask me for my password each and everytime, but it doesn't...

For example I typed "sudo /etc/init.d/./cron stop", and it asked me the PW.
Then a second later I stopped another service/daemon in the same way, but this time it did NOT ask me my PW ! :-O

Is this a bug ? Must be, it's scary !


Vince, very concerned... :-/

---

### Post by WW on 2004-11-22
Try this:
```
 $ man sudo
``` and read the first paragraph.  You'll see this:
> Once a user has been authenticated, a timestamp is updated and the user may then use sudo without a password for a short period of time (15 minutes unless overridden in sudoers).

---

### Post by troutrou on 2004-11-23
Ah, thanks, I understand much better now, I can stop worrying, sudo is working, no bug :-)

---

