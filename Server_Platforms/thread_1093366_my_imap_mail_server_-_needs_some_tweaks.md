---
title: "my imap mail server - needs some tweaks"
date: 2009-03-11
forum: Server Platforms
---

### Post by d2a on 2009-03-11
i'm running dovecot as an IMAP mail server on my home server, which i connect to with my phone and several other machines to check my mail etc.

i use getmail to collect mail from my various pop accounts. getmail filters the mail using spamassassin via a Filter_external, before delivering it to my Maildir on the home server.

Then when I connect to the home server from my various machines, IMAP manages the status of all the mail, so unread messages are common etc.

All works very nicely. However I'd like to fix a minor annoyance...

...Spamassassin marks mail as SPAM but the mail client must move it to the Junk folder. I'd like the mail to be filtered on the home server on receipt.

Is there a way of moving mail to the Junk folder based on the spamassassin headers? Perhaps a small perl script added as another getmail filter_external?

Or am I just making things really complicated for myself? Is there a simpler setup for what I'm trying to do?

Thanks for any ideas...

---

