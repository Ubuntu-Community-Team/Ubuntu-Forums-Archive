---
title: "MAILER-DAEMON problem"
date: 2007-08-29
forum: Server Platforms
---

### Post by guttdude on 2007-08-29
I got this mail in pine after I use smtp to retrieve mails.

```
From:    Mail System Internal Data 
Subject:    DON'T DELETE THIS MESSAGE -- FOLDER INTERNAL DATA

This text is part of the internal format of your mail folder, and is not
a real message. It is created automatically by the mail system software.
If deleted, important folder data will be lost, and it will be re-created
with the data reset to initial values.
```

How to set exim4 not to mail this message to users.

---

### Post by MJN on 2007-08-29
As it says, it's not a 'real' message (just looks like one) hence it is not being sent by anyone/anything. Rather, it is used by Pine (4) and IMAP servers wihch use the mbox format.
 
See [http://www.ucs.ed.ac.uk/fmd/unix/docs/mail/pine4.10.html#pseudo-msgs](http://www.ucs.ed.ac.uk/fmd/unix/docs/mail/pine4.10.html#pseudo-msgs) for further details.
 
Mathew

---

