---
title: "printer problems in 10.04"
date: 2011-01-21
forum: Server Platforms
---

### Post by raymondvillain on 2011-01-21
Recently upgraded Ubuntu Server to version 10.04 (32 bit) and now I can't print.

If I open a browser window for localhost:631 and try to print a test page, I get a window asking for authentication.  I enter my username and password and the box disappears, then comes back, over and over.  Can't get past it.

I modified (slightly) the /etc/cupsd.conf file and then tried to restart cups with the command

/etc/init.d/cupsys restart

but that doesn't work now.

Any suggestions?

If I boot to recovery mode and then select "resume normal boot", one of the messages that appears on the screen reads:

starting common unix printing system: cupsd       [failed]

Is this an indication of something important?

---

