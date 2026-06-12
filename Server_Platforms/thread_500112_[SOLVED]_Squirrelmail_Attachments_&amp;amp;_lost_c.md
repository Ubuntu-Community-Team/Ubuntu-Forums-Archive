---
title: "[SOLVED] Squirrelmail Attachments &amp;amp; lost connection after DATA"
date: 2007-07-13
forum: Server Platforms
---

### Post by bmathis on 2007-07-13
Hey everyone - 

I have a Postfix, Courier IMAP/POP, and Squirrelmail server going on Dapper and everything works fine except when i try and send an attachment though Squirrelmail. It sits there for a little bit and then times out. When I check the mail.log file the last entry says "lost connection after DATA"  and kills apache2. I have to restart apache for anything to work again.

Has anyone seen this or know of a fix.

Thanks

---

### Post by Mr. C. on 2007-07-13
The lost connection message indicates the client dropped the connection before the final dot.  You will have to look at what php is doing.  See:

[http://article.gmane.org/gmane.mail.squirrelmail.user/32159/match=attachment](http://article.gmane.org/gmane.mail.squirrelmail.user/32159/match=attachment)

MrC

---

### Post by bmathis on 2007-07-13
thanks Mr. C, ill check it out later tonight when I get home.

---

### Post by bmathis on 2007-07-14
i figured out the problem, it was something with the html_mail plugin. I removed, downloaded, and then installed it again and everything seems to be working fine now.

---

