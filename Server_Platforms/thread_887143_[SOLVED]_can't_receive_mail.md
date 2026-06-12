---
title: "[SOLVED] can't receive mail"
date: 2008-08-11
forum: Server Platforms
---

### Post by baudday on 2008-08-11
I've been searching for a bit, not sure what's wrong. I'm using postfix and dovecot. I can send mail fine, but I can't receive mail at all. At first when I sent from my gmail account I would get this error, 
> The error that the other server returned was: 554 554 5.7.1 <me@example.org>: Relay access denied (state 14).
I guess I got that figured out, cause now I get no error on the sender side. The e-mail simply doesn't show up in my inbox on the server. I'm at a complete loss, any help would be great. If you need more info, just tell me and I'll put it up.

---

### Post by baudday on 2008-08-11
okay, while logging out, i noticed PuTTY said I had mail, in var/mail/me and they turned out to be all the messages I couldn't find. So I guess the problem lies, how do I get the mail from there to show up in my inbox in squirrelmail?

---

### Post by MJN on 2008-08-12
Assuming you're not using Procmail to deliver the mail then tell Postfix where to store local mail with the home_mailbox directive e.g.
 
home_mailbox = Maildir/
 
will put mail in /home/<user>/Maildir/
 
(the trailing slash indicates maildir storage format as opposed to mbox)
 
Mathew

---

### Post by baudday on 2008-08-12
actually am using procmail. Should I not?

---

### Post by MJN on 2008-08-12
That's fine, Procmail is good - it's just that as you didn't mention it I didn't want to assume. Given that you do use it, then it is actually Procmail that is choosing where to the mail is stored (not Postfix) hence it has to be configured accordingly...
 
Set the following in /etc/procmailrc to declare some system-wide defaults:
 
```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL
```(adjusting ORGMAIL to suit)
 
then make sure your mailbox_command in /etc/postfix/main.cf is set correctly:
 
```
mailbox_command = procmail -a "$EXTENSION"
```
 
Restart Postfix and you should be sorted!
 
Incidentally, do still set the home_mailbox command in main.cf just in case Procmail fails to deliver and passes the message back to Postfix - it will then fallback to putting it wherever you've told it to (or not).
 
Mathew

---

### Post by baudday on 2008-08-12
okay, now I'm sort of lost. Procmail is on, but I cannot find the file /etc/procmailrc. Do I have to create it or what?

---

### Post by MJN on 2008-08-12
Yes, sorry, I should've mentioned that if it doesn't already exist then create it.

Mathew

---

### Post by baudday on 2008-08-12
that was the problem! thank you so much for all your help!

---

### Post by MJN on 2008-08-12
You're welcome!

---

