---
title: "Filtering spam (Postfix, procmail)"
date: 2009-11-17
forum: Server Platforms
---

### Post by James Goode on 2009-11-17
Hi,

I've set up an email server with Postfix, Dovecot and Spamassassin.  It receives emails, and adds [***** SPAM score *****] to the subject line of spam.

Can I get it to move spam to the Trash folder automatically, possibly using .procmailrc?

Thanks,

--James.

---

### Post by prsjm3qf on 2009-11-18
Just a thought....

I achieve this by setting up a filter at the mail client level.

Both Horde and Squirrelmail will do this for you invisibly and automatically.

Don't know about non-webmail setups.

---

### Post by James Goode on 2009-11-18
I didn't look closely at Squirrelmail, because I didn't see a solution immediately.  I found this guide:

> Click on Options
Select Message Filters
You can set "What to scan" to all messages or "Only unread" messages. I recommend setting it to "Only unread" messages.
Click new
Match: Header
Contains: X-Spam-Status: Yes
Move To: INBOX.Spam

You could also scan the subject line for "[POSSIBLE SPAM]"

click on submit

I can't find a message filters button, do I need a plugin?

---

### Post by wyldfury on 2009-11-18
Dovecot has the Sieve plugin ([http://wiki.dovecot.org/LDA/Sieve](http://wiki.dovecot.org/LDA/Sieve)) for mail filtering. If you also need to allow users to upload their own sieve scripts then you could also look at Pigeonhole ([http://pigeonhole.dovecot.org/](http://pigeonhole.dovecot.org/)).

---

### Post by James Goode on 2009-11-18
I found the message filter plugin, and enabled it with SquirrelMail's conf.pl.  It should now move spamassassin-marked spam into my Trash folder.

I also have a calendar and fortunes at the top of the page!  I will look again at Sieve later, it looks quite tricky to set up.

Thanks for your help,

--James.

---

