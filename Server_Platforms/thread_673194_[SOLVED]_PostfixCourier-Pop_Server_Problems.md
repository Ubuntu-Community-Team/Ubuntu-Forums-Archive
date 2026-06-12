---
title: "[SOLVED] Postfix/Courier-Pop Server Problems"
date: 2008-01-20
forum: Server Platforms
---

### Post by fromp on 2008-01-20
So I have an Gutsy Gibbon running on an old Dell Dimension 2100 with a Linksys WMP54G. The internet is working fine, surprisingly for that card.

My internet setup is:
Internet
|
Router - - (IP passthrough) - - Server
|
Family Computer (Windows XP)

I have no-ip installed and working so IP renewal is not a problem.

I was using [http://www.flurdy.com/docs/postfix/](http://www.flurdy.com/docs/postfix/) to configure Postfix and Courier for virtual users, intending to follow the rest of the tutorial if postfix and courier worked out.

I had tried setting up shorewall once, but couldn't get version 4.x installed, only 3.4.4. It wasn't working, so i un-installed it, planning to install that after I got my courier problem solved.

I can telnet into, or connect using evolution to both Postfix and Courier from anywhere and send mail to any address. My Problem lies with receiving mail. If i send mail from myself to myself, it is received. If I send an email from my gmail account, i never get it. But I also do not get a return error email in gmail.

I think the problem lies with filtering, but i have very little knowledge of courier or postfix.

Any help is greatly appreciated.

---

### Post by fromp on 2008-01-20
it is fixed now.
i installed shorewall 4.0.7 from tar.bz2, configured that, and it worked.
i guess shorewall 3.4.4 had left incorrect entries before it was removed.

---

