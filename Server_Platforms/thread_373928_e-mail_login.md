---
title: "e-mail login"
date: 2007-03-01
forum: Server Platforms
---

### Post by murrellr on 2007-03-01
I somehow managed to get e-mail server running on Ubuntu server 6.10.  And by following the documentation!  I'm using Postfix and Dovecot.  I can even connect with Outlook Express and read my mail.  My question concerns logging in.  For my ISP and my old server OS (YES Linux), I used the account name in the form 'userid@domain'.  But now it requires just 'userid'.  I'd like to configure the server to require the 'userid@domain' form, so when I recreate the other user's accounts, I don't have to have them try to reconfigure their clients.

I'm not asking for hand-holding, I can read documentation.  I just need to know where to look.  Is it a Postfix or Dovecot thing?  Or somewhere else?

---

### Post by Mr. C. on 2007-03-01
Sure, you can do this.  How though depends upon how you configured postfix.

Its likely configured to use "local" accounts via /etc/passwd and /etc/aliases.

You want to change the database to use something in addition to  /etc/passwd and /etc/aliases  See:

main.cf:
local_recipient_maps = unix:passwd.byname $alias_maps

[http://www.postfix.org/LOCAL_RECIPIENT_README.html](http://www.postfix.org/LOCAL_RECIPIENT_README.html)
[http://www.postfix.org/postconf.5.html#local_recipient_maps](http://www.postfix.org/postconf.5.html#local_recipient_maps)
[http://www.postfix.org/local.8.html](http://www.postfix.org/local.8.html)

Alternatively, you can use virtual users.  In the end, postfix only cares that the email user/address can be found in a table.  Other parameters specify how to deliver.

MrC

---

### Post by murrellr on 2007-03-01
What about this?  I found this in the dovecot.conf file:

# Default MAIL environment to use when it's not set. By leaving this empty
# dovecot tries to do some automatic detection as described in
# /usr/share/doc/dovecot-common/mail-storages.txt. There are a few special 
# variables you can use, eg.:
#
#   %u - username
#   %n - user part in user@domain, same as %u if there's no domain
#   %d - domain part in user@domain, empty if there's no domain
#   %h - home directory
#
# See /usr/share/doc/dovecot-common/variables.txt for full list. Some examples:
#
#   default_mail_env = maildir:/var/mail/%1u/%u/Maildir
default_mail_env = mbox:~/mail/:INBOX=/var/mail/%u

What will happen if I change the %u to %n?

---

### Post by Mr. C. on 2007-03-01
I'm sorry, i was not thinking clearly.  I was thinking of postfix recipient validation, and my own particular setup.  That will teach me to talk and type at the same time. My apologies.

Dovecot uses various databases for the username and the password; you are specifying the storage area; don't change this without configuring postfix to deliver to that location.

Read this on Dovecot:
[http://wiki.dovecot.org/UserDatabase](http://wiki.dovecot.org/UserDatabase)

This tells you how to change the database, and hence username/password you use to login to either POP/IMAP.

Again, apologies.
MrC

---

