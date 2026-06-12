---
title: "mailserver - procmail question"
date: 2006-07-22
forum: Server Platforms
---

### Post by docko on 2006-07-22
i installed a mailserver at my home network. i used this howto [http://workaround.org/articles/ispmail-sarge/](http://workaround.org/articles/ispmail-sarge/), plus i added fetchmail to 
download messages from multiple pop3 accounts.
now i want to add procmail to this system to filter messages with ***SPAM*** in title and move them to Spam directories that are located inside every virtual account's mail folder. can anybody tell me how to configure procmail and how to tell postfix to use it?

thank you

---

### Post by docko on 2006-07-24
anyone please?

---

### Post by LordHunter317 on 2006-07-24
Install procmail.
Add/edit this line to /etc/postfix/main.cf:```
mailbox_command = procmail -a "$EXTENSION"
```
Add this file as your global /etc/procmailrc if you're using Maildirs:```
DROPPRIVS=yes
DEFAULT=/home/${USER}/Maildir/
ORGMAIL=${DEFAULT}
```And isn't required if you're using regular mail spools.  Add any rules to that file you want to run for all users (if using mailspools, add DROPPRIVS=yes at the top to make sure they're run safely).

---

### Post by docko on 2006-07-25
thanks LordHunter317
my users' mail directories are located in /home/vmail/some-virtual.domain/user/
new emails are stored in ./new, read emails in ./cur
i want to move all messages marked as Spam to ./.Spam (in every user's directory) is it possible to set this in the global /etc/procmailrc?
 or how can can i do it?

thank you

---

### Post by docko on 2006-07-26
sorry for bump, but i still didn't solve that...

---

### Post by LordHunter317 on 2006-07-26
Yes, it is.  Putting a / on the end of the place to delivery to automatically makes procmail assume it is a Maildir.  That's why I explictly did it in the example above.

Any recepies you add to the global file will be run for all users.

---

