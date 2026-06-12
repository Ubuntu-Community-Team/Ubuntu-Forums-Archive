---
title: "local lan"
date: 2009-05-02
forum: Server Platforms
---

### Post by johnh10000 on 2009-05-02
I posted in here last week.... I have now got the lan working-ish:

Ping works
Ftp works anon wise

good.

Trying to get apache to work.  It works off the server box no else on the lan :(
Again telnet and ssh work on server box.

Any ideas on how to let services see the lan

using intripid

---

### Post by freebeer on 2009-05-02
Just so I understand... from the computer that is running Apache, you can bring up the web page(s) from a browser, but you can't bring up the pages from the other computers on the LAN?

What are you typing in the URL  box of the browser to access the server?

---

### Post by Iowan on 2009-05-02
At least part of your answer may be [here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

### Post by johnh10000 on 2009-05-09
> **freebeer said:**
> Just so I understand... from the computer that is running Apache, you can bring up the web page(s) from a browser, but you can't bring up the pages from the other computers on the LAN?

What are you typing in the URL  box of the browser to access the server?

Sorry gang I posted this in linux questions too.  Found out what was wrong.  My firewall at the linux end wasn't right, got lokit, configured it, and everthing works!!

Any ideas on how to run x apps on a windows box?  Someone surgested cygwin. I have this now telned over fine.  Only just installed it, and I'm tired so don't know yet.

---

