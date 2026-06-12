---
title: "Nohup question"
date: 2013-03-15
forum: Server Platforms
---

### Post by carp3di3m on 2013-03-15
I run a script via nohup and during day time I stop it some times.

Once I killed the process and then later try to start the process i get the message that the process is still running.

I checked and the process is defiantly not running.

I have to reboot to get the sh running again.

---

### Post by LHammonds on 2013-03-15
That sounds odd.  I guess the process you killed was a child process or if you killed the parent process, it did not kill the child process.

Does it have this problem when you run it without nohup and just press CTRL+C to stop the script?

If it doesn't and you don't want to modify your script to handle interrupts, consider using "screen" to start the script.  Then detach from that screen session and let it continue.  If you want it to stop, re-attach the screen session and press CTRL+C to stop it.

LHammonds

---

