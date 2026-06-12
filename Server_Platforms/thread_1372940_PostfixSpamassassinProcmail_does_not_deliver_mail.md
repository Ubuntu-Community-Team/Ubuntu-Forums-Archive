---
title: "Postfix/Spamassassin/Procmail does not deliver mail"
date: 2010-01-05
forum: Server Platforms
---

### Post by storwalle on 2010-01-05
I have followed tutorials on how to get my working Postfix/Dovecot/Spamassassin installation to send emails marked as spam into dev/null instead of being delivered to the IMAP inbox with an altered X-Spam header.

I get everything working according to the tutorials except the fact that ham gets delivered to /var/mail/mailbox_user_name and never get picked up by my email client which uses IMAP over SSL to retrieve emails. 

Local delivery of emails are in Postfix configured to be delivered to ~/Maildir and they get there as long as I am not using Procmail. As soon as I use Procmail they get delivered to var/mail/mailbox_user_name.

The script I am using for Procmail is found here:
[http://wiki.apache.org/spamassassin/DeletingAllMailsMarkedSpam](http://wiki.apache.org/spamassassin/DeletingAllMailsMarkedSpam)

What is wrong? It feels like Procmail not delivering ham to the correct place, but where do I control the delivery after Procmail has done it stuff?

Kind regards
Michael  :confused:

---

