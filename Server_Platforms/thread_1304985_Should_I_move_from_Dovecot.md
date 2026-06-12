---
title: "Should I move from Dovecot?"
date: 2009-10-29
forum: Server Platforms
---

### Post by StrangeWill on 2009-10-29
I'm working for a small business, we're currently running dovecot virtual users, it's working pretty decently, at least with outlook (kinda, deleted messages are not moved to trash... must be purged on folder change... lame), web based mail have been *slooooooow* though. Squirrelmail and SugarCRM>

I've heard of Cyrus, and am almost being tempted to use this as our IMAP agent, should I? What are the major benefits over Dovecot? Will I be able to easily move over our e-mail system in about an hour or so of work? Will I get a noticeable performance increase (we seem to have having some bad IMAP lagging with Dovecot),


All mail is stored in /var/vmail/{domain}/{user}
Virtual users are handled by MySQL via postfixAdmin.

---

### Post by Lars Noodén on 2009-10-30
In addition to Cyrus there are other open source MTAs to look at:

simta
    [http://rsug.itd.umich.edu/software/simta/](http://rsug.itd.umich.edu/software/simta/)
Postfix
    [http://www.postfix.org/](http://www.postfix.org/)
Exim
    [http://www.exim.org/](http://www.exim.org/)
Sendmail
    [http://www.sendmail.org/](http://www.sendmail.org/)

---

### Post by StrangeWill on 2009-11-01
Well those only serve up SMTP though right? I'm having issues with IMAP being slow as all hell.

That or Apache.

---

### Post by mbaas on 2009-11-01
At the moment i'm using [Courier]("http://www.courier-mta.org/") as pop3 / imap server with roundcube as webmail. Seems to work fast enough.

---

