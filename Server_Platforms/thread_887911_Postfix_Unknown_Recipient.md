---
title: "Postfix Unknown Recipient"
date: 2008-08-12
forum: Server Platforms
---

### Post by chrisdeeley on 2008-08-12
Is it possible to stop postfix rejecting messages sent to [email]invalid-user@domain.com[/email]? Or customize the message which is returned when the user does not exist?

At the moment, my server is returning the error 

550 5.1.1 <invalid-user@domain.com>: Recipient address rejected: User 
unknown in virtual mailbox table

(because I'm using virtual user maps)

If possible I would like to return a customized message.

Thanks

---

### Post by chrisdeeley on 2008-08-12
I think i've just answered part of my own question. Adding
smtpd_reject_unlisted_recipient = no
to main.cf seems to work in accepting these messages, then my server sends a non-delivery report, so hopefully I should be able to use bounce_template_file to create a customized report.

How would I configure it to accept the messages but just delete them rather than sending a non-delivery report?

---

### Post by MJN on 2008-08-12
> **chrisdeeley said:**
> I think i've just answered part of my own question. Adding
smtpd_reject_unlisted_recipient = no
to main.cf seems to work in accepting these messages, then my server sends a non-delivery report,Think very carefully about adopting this strategy as you are now having to deal with wrongly-addressed mail *after* the SMTP dialogue hence any non-delivery report will be sent to the the address listed in the From: field.... In the case of spam sent to random addresses this From: field will of course will be some poor sucker's address which will then get your non-delivery report...  ...even though they never sent the message.

> How would I configure it to accept the messages but just delete them rather than sending a non-delivery report?Are you sure you want to do this also? Sure, it may stop the backscatter mentioned above but it also means that legitimate senders who accidentally misspell your (and your users') e-mail addresses will be none the wiser that their message has been binned.

I hope this doesn't sound too negative but I thought it wise to offer it as food for thought in case you hadn't considered these issues.

Mathew

---

### Post by chrisdeeley on 2008-08-13
Thanks for the advice Mathew.

If i leave the smtpd_reject_unlisted_recipient = yes, is there any way of changing the error message that is returned to something of my choice. So that as opposed to saying *user unknown in virtual user table*, could it just say that the *user is unknown*.

Also is there a way to feed messages for virtual users into spamassassin before they are delivered to the virtual mailboxes? I can only find ways of doing this for local users, not virtual users.

Thank you for your help

---

### Post by MJN on 2008-08-13
> **chrisdeeley said:**
> If i leave the smtpd_reject_unlisted_recipient = yes, is there any way of changing the error message that is returned to something of my choice. So that as opposed to saying *user unknown in virtual user table*, could it just say that the *user is unknown*.

To be honest I don't know. I'm sure there must be a way though... although I do wonder if it really is worth it. The vast majority of 'user unknown' bounces must surely be the result of spammers hence they won't be reading what you've got to say, and for what is surely a small minority of genuine mis-addressed mail I would've thought the default error is sufficient - even to the most non-computer-savvy they would realise it didn't work out. Besides which, I'm sure the subtlety of your desired change would be lost on practically everyone!

> Also is there a way to feed messages for virtual users into spamassassin before they are delivered to the virtual mailboxes? I can only find ways of doing this for local users, not virtual users.

How are you invoking SA? Via a content_filter? It might be worth posting your config so we can walk through it...

Mathew

---

### Post by chrisdeeley on 2008-08-13
At the moment i'm using 
mailbox_command = /usr/bin/procmail
to filter messages using procmail which feeds them into spamassassin.

But, as I found out, this only works for local delivery not virtual delivery.

I haven't got a clue on how to use the content_filter. I've been to loads of websites and none of them seem to explain in plain english, how to use content_filter. The only examples I can find use content_filter to feed messages into clam AntiVirus.

---

