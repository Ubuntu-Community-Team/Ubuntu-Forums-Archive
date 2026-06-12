---
title: "Start-stop-daemon question."
date: 2007-10-30
forum: Server Platforms
---

### Post by MianoSM on 2007-10-30
I recently attempted to remove squid.

I then had second thoughts and re-installed it. After doing so I set all of my configurations, and attempted to start the server and it keeps on telling me:

start-stop-daemon: Unable to set gid to 0 (Operation not permitted)
                                                                                                                                                      [fail]

Any ideas on this?

---

### Post by MJN on 2007-10-30
Are you doing it as root? (prefix with **sudo**)

Mathew

---

### Post by MianoSM on 2007-10-31
I did attempt to do it as root as well and nothing happend.

I wound up running it from /usr/sbin/squid -NCd1 instead, and it works from that location instead of from /etc/init.rd/squid

Now to start reading up on the ACL and its modification/configuration! : )

---

### Post by MJN on 2007-10-31
init.**r**d? I'm not sure I understand.... but if you're up-and-running that's all that matters.
 
If you meant init.d I guess the startup script must be borked. I would've thought you'd want it fixing, particularly for bringing Squid up at boot?
 
Mathew

---

