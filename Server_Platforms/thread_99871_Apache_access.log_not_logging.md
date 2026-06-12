---
title: "Apache access.log not logging"
date: 2005-12-06
forum: Server Platforms
---

### Post by krewemaynard on 2005-12-06
I've been having a hard time getting Apache2 to log site access. I'm not sure if there's a module I'm missing, or if my system logger (sysklogd) isn't writing quickly enough. I do have an access.log.1 file in /var/log/apache2, but there's no live logging as I had under Gentoo. 

All I have in the /etc/apache2/mods-enabled directory is cgi, php4, and userdir. There's nothing in mods-available that mentions logging.

Li'l help? :???:

---

### Post by krewemaynard on 2005-12-07
Ok, I've figured out that it's not the system logger....the vsftpd log writes in real time. Just need to fix Apache.

---

### Post by PWill on 2007-01-16
I have this same problem.
How did you fix it?

---

### Post by PurplePenguin on 2007-01-17
I have the same problem as well, and was hoping that this thread would help me figure out what to do!  The thread looks pretty dead, though, with the original post being from Dec. 2005.

If anybody reads this and knows what to do, please let us know!

---

### Post by PurplePenguin on 2007-01-17
Just a followup... everything seems to be working OK for me now.  I have WebMin installed on my server and am just getting used to it.  I went into WebMin, then into the setup for the three different Virtual Hosts that I have on the machine, pointed each of them to a different place to make their own logs, then went into the Webalizer module and entered the information so each log would get analyzed at different times during the night.

It looks like it works perfectly!  I can't believe how powerful and easy WebMin makes everything!

---

