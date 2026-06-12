---
title: "how can I get users to be autosubscribed to a mailbox in squirrelmail?"
date: 2011-01-27
forum: Server Platforms
---

### Post by guest_user on 2011-01-27
running squirrelmail, postfix and dovecot, I filter out mails which are spam into a spambox and non-spam into the inbox but by default, the user is not subscribed to the spambox and therefore, the spambox is not visible to the user, how can I make it such that each time a user is created he or she is automatically subscribed to the spambox?

---

### Post by SeijiSensei on 2011-01-27
Are you not delivering each user's spam to a private folder in his or her account?  That has some serious privacy implications since misclassified legitimate messages will be visible to every user.

I recommend using procmail to filter each person's spam to /home/user/mail/spam.  You can do this with separate .procmailrc files in each user's home directory, or use a recipe like this in /etc/procmailrc:

```

:0
* ^Subject:.*spam
$HOME/mail/spam

```

(I use MailScanner which puts a "{Spam?}" tag in the subject line.) 

This recipe puts every spam-tagged message into the user's personal spam folder.

You can specify $HOME/mail in /etc/dovecot.conf as the folder location like this:

```
mail_location = mbox:~/mail:INBOX=/var/spool/mail/%u
```

I use the mbox format; if you're using Maildir replace "mbox" with "maildir".

---

### Post by guest_user on 2011-01-28
all users have their own personal spambox, just that they aren't subscribed to it by default, I'm trying to get them autosubscribed each time I add in a new user.

using virtual domains and users btw, so I dun store their mails in their home folder

---

### Post by SeijiSensei on 2011-01-28
It appears that dovecot maintains its subscription list in the root of the mail folder, e.g., /home/user/mail/.subscriptions.  You can force a particular subscription list, or any other default configuration, for new users by editing /etc/skel.  

First, create a template list of subscriptions and stash it somewhere like /etc/dovecot-subscriptions.  Then in /etc/skel, use mkdir to create the mail directory and copy the subscription list into it as .subscriptions.  New users will then start with the correct list.

---

### Post by Vegan on 2011-01-28
I am not sure if its still being maintained, but majordomo is another mailing list manager.

---

### Post by guest_user on 2011-01-28
> **SeijiSensei said:**
> It appears that dovecot maintains its subscription list in the root of the mail folder, e.g., /home/user/mail/.subscriptions.  You can force a particular subscription list, or any other default configuration, for new users by editing /etc/skel.  

First, create a template list of subscriptions and stash it somewhere like /etc/dovecot-subscriptions.  Then in /etc/skel, use mkdir to create the mail directory and copy the subscription list into it as .subscriptions.  New users will then start with the correct list.

I'm using virtual users stored in a mysql database, so the users of the mail server do not correspond to system users and hence do not have a home directory...

---

### Post by SeijiSensei on 2011-01-29
So none of them have a .subscriptions file anywhere?  Dovecot talks about this file being in the "root of the mail folder."  Where's that spam folder located?  Is there a .subscriptions file there?

---

