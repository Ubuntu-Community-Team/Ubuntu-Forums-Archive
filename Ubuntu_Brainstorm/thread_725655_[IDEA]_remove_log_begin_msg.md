---
title: "[IDEA] remove log_begin_msg"
date: 2008-03-15
forum: Ubuntu Brainstorm
---

### Post by rforub on 2008-03-15
Hi,

In /etc/init.d files have log_begin_msg and log_end_msg.
These only print a message to the console.

They are not needed because you can check that a daemon
has loaded using the ps command or looking at the logs.

They also slow the bootup process.

They also do not work well with the cron scripts.
 
Rob.

---

### Post by chrisccoulson on 2008-03-16
Where is the evidence that they slow the boot process? And they're useful for debugging startup problems anyway.

---

### Post by rforub on 2008-03-16
A second solution would be to allow the user to choose if console
messages were displayed.

This could be done putting the log_begin_msg code into
start-stop-daemon. Then add a parameter say -msg 0 which
selects if messages are displayed.

This could be extended further by using /etc/default/start-stop-daemon
to select the parameters.

Rob.

---

