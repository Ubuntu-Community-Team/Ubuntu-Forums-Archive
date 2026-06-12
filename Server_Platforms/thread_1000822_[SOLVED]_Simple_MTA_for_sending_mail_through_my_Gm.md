---
title: "[SOLVED] Simple MTA for sending mail through my Gmail account"
date: 2008-12-03
forum: Server Platforms
---

### Post by tnek on 2008-12-03
Hi,

I am looking for a simple MTA, preferably much simpler than procmail but still being sendmail compatible, for sending mails from my Gmail account. I'll use it to send mails from PHP (more specifically from Drupal 6.x).

I've read about Nullmailer but I can't get the configuration right as they want TLS authentication. Something where I won't have to read manuals for hours just to send some mail would be best. ;)

---

### Post by Wayne_V on 2008-12-03
Can you just enable imap on your gmail account and use that?

[http://www.devarticles.com/c/a/PHP/Create-Your-Own-Mail-Script-With-PHP-and-IMAP/](http://www.devarticles.com/c/a/PHP/Create-Your-Own-Mail-Script-With-PHP-and-IMAP/)

---

### Post by tnek on 2008-12-03
Thank you for answering. But even if I enable IMAP (which I already have) I'm still sending messages through their SMTP-server. I don't understand how enabling IMAP will help me, please go into more detail if this is an actual solution.

---

### Post by Wayne_V on 2008-12-03
So you want to run your own MTA?   A lot of sendmail setup issues there, masquerading, smarthost, dns names, etc.   Here's a good guide:  [http://www.redhat.com/support/resources/howto/RH-sendmail-HOWTO/book1.html](http://www.redhat.com/support/resources/howto/RH-sendmail-HOWTO/book1.html)
I use sendmail - takes a bit to learn and configure properly but it works well.

I haven't used exim but a lot of people like it:  [http://ubuntuforums.org/showthread.php?t=196112](http://ubuntuforums.org/showthread.php?t=196112)

---

### Post by hictio on 2008-12-03
tnek, I don't fully understand your request :D
You want to:

> 
I am looking for a simple MTA, preferably much simpler than procmail but still being sendmail compatible, for sending mails from my Gmail account.


but then, you say:

> 
But even if I enable IMAP (which I already have) I'm still sending messages through their SMTP-server


Therefore, not sure if this is what you want or not :D :
[sSMTP: A simple alternative to Sendmail](http://www.linux.com/feature/132006)
[Sending Email From Your System with sSMTP](http://tombuntu.com/index.php/2008/10/21/sending-email-from-your-system-with-ssmtp/)

---

### Post by tnek on 2008-12-03
Wayne_V: I only want to send some mails, and I've got it working now using ssmtp. When I need the power of sendmail or exim I'll take some time to learn one of them. But at the moment I'm satisfied just relaying my mail sending to the SMTP-server of Gmail using ssmtp. But thanks for answering and trying to help me!

hictio: You figured out what I wanted. I now use ssmtp to send mails from cron jobs, PHP etc through my Gmail account. It works like a charm and took me 15 minutes to set up. :-) A big thank you!

---

