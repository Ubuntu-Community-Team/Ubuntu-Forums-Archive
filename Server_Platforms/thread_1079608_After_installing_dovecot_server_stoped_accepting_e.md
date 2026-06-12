---
title: "After installing dovecot server stoped accepting e-mails"
date: 2009-02-24
forum: Server Platforms
---

### Post by darek_dade on 2009-02-24
Hi

Before installing Dovecot everything was alright. Postfix was able to send and receive e-mails no problem. 

Now, when I try to send an e-mail to one of the users I get a bounce back message (almost immediately). This is what I get: 

```
I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                  The mail system

<mendax@findevent.com>: Command died with status 127: "procmail -a
   "$EXTENSION"". Command output: sh: procmail: not found

Final-Recipient: rfc822; [email]mendax@findevent.com[/email]
Original-Recipient: rfc822;mendax@findevent.com
Action: failed
Status: 5.3.0
Diagnostic-Code: x-unix; sh: procmail: not found
```

On the other hand I can send e-mails from the server without any issues.

Postfix is listening to the smtp port (which is not blocked), however, I noticed that no one is listening to 110. 

Any help greatly appreciated!

---

### Post by darek_dade on 2009-02-25
Noone has idea what's going on?

---

### Post by drzolo on 2009-02-25
install procmail

---

