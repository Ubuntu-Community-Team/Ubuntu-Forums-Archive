---
title: "Shutdown Log for 13.10"
date: 2013-10-24
forum: Ubuntu, Linux and OS Chat
---

### Post by mtbdrew on 2013-10-24
Every time the system is shutdown an error message scrolls across the screen too quickly for me to catch what it says. Is there a shutdown log that might be capturing this error message and if so where would I find it?

---

### Post by mtbdrew on 2013-10-28
Is this the correct forum or do I need to move this somewhere else?

---

### Post by ssam on 2013-10-28
might be in /var/log/syslog or /var/log/messages

---

### Post by Erik1984 on 2013-10-28
Interesting question I like to know this too. I don't see a file /var/log/messages here. /var/log/syslog does not contain the messages shown at shutdown on my machine.

---

### Post by bug67 on 2013-10-28
Naw, I'm getting them too.  I'm getting them when waking from suspend and during re-boots.  It says something about an Intel mismatch error.  Mine does anyhow.

I was trying to figure it out by manually suspending my machine so I could try to read the message.  But, somehow by doing so, the error logs quit showing up.  Now, I haven't re-booted since then so, I dunno about that but, it seems to have cleared up on the wake from suspend.

**_EDIT_**:

Nope.  Still getting them on re-boot.  Something about Intel pipe mismatch.  It would be nice if I could figure out exactly what it says but like the OP says, it flashes up way too fast.

---

### Post by grahammechanical on 2013-10-29
Would someone like to explain how it is possible to write a log file to disk once the operating system has shut down?

---

### Post by Bashing-om on 2013-10-29
et all;
What I have found that one can do is to pause that output to the screen;
Control+s and Control+q stop/start but you gotta be fast. :-)
or one might try:
Scroll Lock.

[INDENT][INDENT]works for me
[/INDENT][/INDENT]

---

### Post by mtbdrew on 2013-10-31
> **bug67 said:**
> Naw, I'm getting them too.  I'm getting them when waking from suspend and during re-boots.  It says something about an Intel mismatch error.  Mine does anyhow.

I was trying to figure it out by manually suspending my machine so I could try to read the message.  But, somehow by doing so, the error logs quit showing up.  Now, I haven't re-booted since then so, I dunno about that but, it seems to have cleared up on the wake from suspend.

**_EDIT_**:

Nope.  Still getting them on re-boot.  Something about Intel pipe mismatch.  It would be nice if I could figure out exactly what it says but like the OP says, it flashes up way too fast.

Not after but while the shutdown is being done. There is a a whole series of events that have to be stopped and there should be some tracking of this process to ensure the events are handled correctly.

---

