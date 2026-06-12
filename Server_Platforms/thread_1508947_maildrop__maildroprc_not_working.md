---
title: "maildrop / maildroprc not working"
date: 2010-06-13
forum: Server Platforms
---

### Post by superradical on 2010-06-13
Here is my setup:
postfix w/ virtual users, maildrop is in main.cf as the command that delivers mail.   However if I enable any rules in either maildroprc or in that users directory under .mailfilters, they both seem to do nothing.  Any suggestions on where to go from here?  We also have spamassassin and amavis going.  Would it be possible they're causing problems with the maildrop filtering?
Or is it possible to explicitly filter mail from within spamassassin / amavis?

---

