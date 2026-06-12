---
title: "cannot receive mail?"
date: 2012-01-25
forum: Server Platforms
---

### Post by gdtw on 2012-01-25
can someone help me with the mail problem? i use ubuntu with postfix.

starting 5 days ago, I cannot receive emails, while I can still send mails. when i try to send in an email, it bounces.

I look in the mail.info file in /var/log and see a lot of message like "connect to mx2.maine.edu... network is unreachable.."

what do i have to do with maine.edu? 

I grep in /usr/lib for maine and found some in libcgraph.so.4

is my computer hacked?

how do i fix this?

thanks

---

### Post by lisati on 2012-01-25
*Thread moved to **Server Platforms**.*

When you see a message like "connect to mx2.maine.edu... network is unreachable.." it usually relates to outgoing mail that your server cannot deliver for some reason.

As for incoming mail, a couple of possibilities come to mind. Is your ISP blocking port 25? Are the MX records for your mail server pointing to the correct address?

---

### Post by SeijiSensei on 2012-01-26
> **lisati said:**
> When you see a message like "connect to mx2.maine.edu... network is unreachable.." it usually relates to outgoing mail that your server cannot deliver for some reason.

I just checked that server ("telnet mx2.maine.edu 25"), and it's definitely reachable from here.  lisati's suggestion that the ISP is blocking you makes the most sense.  Maybe they just started blocking port 25 recently, and you're seeing the effects now?

---

