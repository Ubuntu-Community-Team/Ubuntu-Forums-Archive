---
title: "Squirrelmail 404 on Compose"
date: 2007-08-27
forum: Server Platforms
---

### Post by viniosity on 2007-08-27
Just did a dist-upgrade which gave me Squirrelmail 1.4.10a.  Things appear to work as normal but when I go to compose a message I now get a 404.  I tried changing themes to the default theme but that didn't seem to have any affect.  Logs are also of no help unfortunately..

Anyone have any ideas?

---

### Post by viniosity on 2007-08-27
Well, I downloaded 1.5.1 which doesn't work (there's a bug where you can't login.. using a few common PHP versions).  Ended up going back to Squirrelmail 1.4.9 and everything is fine.  Looks like the URLs are adding an extra /src/ for some reason.  So in 1.4.10a you get:

[http://foo.com/src/src/compose.php?mailbox=INBOX&startMessage=1](http://foo.com/src/src/compose.php?mailbox=INBOX&startMessage=1)

nstead of:

[http://foo.com/src/compose.php?mailbox=INBOX&startMessage=1](http://foo.com/src/compose.php?mailbox=INBOX&startMessage=1)

---

