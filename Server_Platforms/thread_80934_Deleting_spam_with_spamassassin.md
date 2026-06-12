---
title: "Deleting spam with spamassassin"
date: 2005-10-23
forum: Server Platforms
---

### Post by Moobert on 2005-10-23
I've resently setup postfix and spamassassin up, and now after getting a good detection system in place i'd like to remove all spam before it reaches the mail box.
However this seems a little more tricky... after looking into potfixs own filtering, local procmail delivery and amavisd-new methods i'm still getting the spam develivered. So i'm wondering which of these methods are the best to use and are their any more methods to remove the spam ?

---

### Post by LordHunter317 on 2005-10-23
First off, deleting spam cold is silly, unless it has an extremely high score (min 10 or higher, realistically 15 or higher).  SA is hardly perfect.

I don't know if amavisd-new can be told to automatically delete high scoring spam.  I know MailScanner can, though.

If you want to delete high scoring spam using procmail, the reciepe would look something like:```
:0
* ^X-Spam-Level: \*\*\*\*\*\*\*\*\*\*
/dev/null
```
Where each \* adds to the minimum score required for deletion.

---

### Post by Moobert on 2005-10-23
i'll checkout MailScanner. I'll have another go with procmail, do you know of any guides about using it with postfix ?

---

### Post by LordHunter317 on 2005-10-23
No, because it's pretty simple.  Add this to your /etc/main.cf:```
mailbox_command = mailbox_command = procmail -a "$EXTENSION"
```And then if you want global Maildir delivery, add this to /etc/procmailrc:```
DROPPRIVS=YES
ORGMAIL=$HOME/Maildir/
DEFAULT=$ORGMAIL
```All mail will go through procmail at that point.  If you want any recipes to apply globally, add them to the /etc file.  Local rules go in ~/.procmailrc.

---

### Post by Moobert on 2005-10-23
thanks i'll give it a try.

---

### Post by LordHunter317 on 2005-10-23
That should be /etc/postfix/main.cf, BTW.

---

