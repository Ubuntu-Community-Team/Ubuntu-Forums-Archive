---
title: "Dovecot maildir + postfix/procmail = no go!"
date: 2009-08-03
forum: Server Platforms
---

### Post by artheus on 2009-08-03
Hi!

I've now set up my mail server, finally working quite great. There is just one small detail left now.. My dovecot IMAP server won't show incoming messages.

In dovecot.conf I've set up my mail_location to be
**mail_location = maildir:/home/%u/Maildir**

I then searched all over to find a solution of my postfix smtp problem. The problem was that the incoming mail got put in "/var/mail/$USER".. So I found a place where they said to make a "/etc/procmailrc" where I write in

```

DROPPRIVS=YES
ORGMAIL=${HOME}/Maildir/
DEFAULT=${ORGMAIL}

```

And sure.. the smtp now puts all the incoming mail into the "${HOME}/Maildir/". But when I connect to the IMAP server using Thunderbird, I can't see the messages...
The mail appears in the format "1249304981.4402_0.username".

Something gives me the feeling that this (in covecot.conf) might be the problem :

```

namespace private {
   separator = .
   prefix = INBOX.
   inbox = no
   hidden = no
}

```

I would not like that to be the problem, as that is exactly the way I want my IMAP to appear in Thunderbird :
```

INBOX
|
|-Sent
|-Trash
|-Drafts
|-Other folder
|  -Subfolder
|  -And another
|-Important stuff

```


Please help me!

Cheers,
Artheus

---

### Post by artheus on 2009-08-04
Hello? *bump*   *bump*

---

### Post by IDtheTarget on 2009-08-28
I found your post on Google while trying to fix this very same problem.

Turns out that you need to make a change in /etc/dovecot/dovecot.conf

You need to add the following line:

mail_location = maildir:~/Maildir

This tells dovecot (your IMAP server) where the mail is being stored.

Then you have to restart dovecot by typing:

invoke-rc.d dovecot restart

Hope this helps!

---

