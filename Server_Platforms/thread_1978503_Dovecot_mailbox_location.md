---
title: "Dovecot mailbox location"
date: 2012-05-11
forum: Server Platforms
---

### Post by jrop on 2012-05-11
Hello all, I (finally) got Postfix and Dovecot playing nicely together, but I had a question about something that seemed sort of sketchy:

My directory structure is as follows:
/home/vmail/[domain]/[user mbox file]

However, when using:
    user:password
in my passwd-file, and
    mail_location = mbox:/home/vmail/%d:INBOX=/home/vmail/%d/%u
in /etc/dovecot/dovecot.conf, I get this error:
    IMAP(user@domain.com): Namespace '': maildir: Home directory not set for user. Can't expand ~/ for mail root dir in: ~/Maildir

However, if I override the location in the userdb file, and set it to:
    user:passwd:vmail:vmail::::userdb_mail=mbox:/home/vmail/[domain]:INBOX=/home/vmail/[domain]/user

Then everything works...???  What's wrong with this?

Also, as a side question, how do I turn sendmail off permanently in Ubuntu 10.04?  I figured out how to stop it (sudo service sendmail stop).

---

