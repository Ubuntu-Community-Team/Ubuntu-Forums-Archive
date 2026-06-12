---
title: "Ubuntu has experienced an internal error"
date: 2012-06-01
forum: System76 Support
---

### Post by MoebusNet on 2012-06-01
I keep getting an error message that Ubuntu has experienced an internal error: colord has experienced a SIGSEGV in dbus_message_get_reply serial()

Launchpad has had bug reports on this going back about 6 months or so marked  "priority - low". My question is, is this something I can just ignore until Ubuntu or Debian come up with a fix, or is there something I need to do about it? There is one thread on this forum that addressed ownership of sys error logs being owned by colord, but I don't comprehend how that might apply to me.

---

### Post by 2F4U on 2012-06-01
If a bug report already exists, it is always a good idea to update the bug to let the developers know that there are more people that face the same problem.
Whether you can ignore the problem mostly depends on whether there are any consequences from the error message. Are any applications or the desktop crashing, do you experience freezes, or is it just an annoyance?

---

### Post by MoebusNet on 2012-06-01
OK, I'll look up the bug & put in my 2 cents. The error message offers to submit a bug, which I've done a few of times, mainly after updates failed to cure it.

Libre Office Spreadsheet acts wonky at times, but I haven't been able to pin it on the colord error.

---

### Post by MoebusNet on 2012-06-30
Colord still has the bug, but I don't get the error message anymore. This got rid of the error message:

[http://ubuntuforums.org/showthread.php?t=1981696&page=3](http://ubuntuforums.org/showthread.php?t=1981696&page=3)
Post #30

Marked as "SOLVED".

---

