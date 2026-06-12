---
title: "Postfix and Squirrelmail"
date: 2008-03-01
forum: Server Platforms
---

### Post by Hungry Snail on 2008-03-01
Hi,

Everything is working ok, this is more of a "where does it go" question.

I'm trying to workout where squirrelmail moves the emails to when you put them in a user created folder.

My setup is Postfix with dovecot and mysql installed on Ubuntu 6.06.

I know new emails are stored in /var/vmail/domainname/user/new if I read the email via squirrelmail the email is moved to /var/vmail/domainname/user/cur

If I move the email to a user created folder I am unable to locate the email anywhere on the server even though I am able to read it via squirrelmail, if I then move the email from the user created folder back into the inbox the email is once again visable in /var/vmail/domainname/user/cur

Any help would be appreciated :).

Regards

---

### Post by nickjqw on 2008-03-01
These should be stored in /var/vmail/domainname/user/.<FOLDERNAME>

Might also be in .INBOX.<FOLDERNAME>

Cheers,
Nick

---

### Post by Hungry Snail on 2008-03-01
Thats what I thought, but those folders are no where to be seen,not eben a 'find . -name' can locate them :(.

The contends of my /var/vmail/domainname/user/ folder are as follows.



cur
dovecot.index
dovecot.index.cache
dovecot.index.log
dovecot-uidlist
new
subscriptions
tmp

If i open subscriptions with nano it lists all the folders on Squirrelmail for that user.

Sent
Trash
Drafts
Disabled

But where the emails vanish to when I move them to the Disabled folder is a complete mystery.

Regards

---

### Post by Hungry Snail on 2008-03-01
hmmm

I did a cd /var/vmail/domain/user/.Disabled and it took me to the folder.

But for some reason this folder, and the other Squirrelmail folders are invisible and cannot be seen from /var/vmail/domain/user/
Strange.

Thanks for the .disable tip though

---

### Post by nickjqw on 2008-03-01
Files with a . are hidden by default, try using "ls -la" to see the files...

Nick

---

### Post by MJN on 2008-03-03
Note that the file/message locations are dictated by your IMAP server as opposed to Squirrelmail (it just being an IMAP client).
 
Mathew

---

