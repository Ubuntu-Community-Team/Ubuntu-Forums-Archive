---
title: "Dovecot for local users"
date: 2006-08-05
forum: Server Platforms
---

### Post by lionsnob on 2006-08-05
Hello,

I'm trying to get Dovecot to work with local unix users and passwords.  For example, if there's a user on my system named bob, then a mail to [email]bob@my.syst[/email]em should go to bob's mail box.  I tried to set the options in webmin "standard unix database" and "unix passwd file," but got this error:

Starting mail server: dovecotError: Error in configuration file /etc/dovecot/dovecot.conf line 645: Unknown setting: userdb

This thread seemed to have similar issues:
[Link]("http://ubuntuforums.org/showthread.php?t=216658&highlight=dovecot+userdb")

Thanks.

---

### Post by chrisfay on 2006-08-05
This is how that section of my dovecot.conf looks:

auth default {
  # Space separated list of wanted authentication mechanisms:
  #   plain digest-md5 cram-md5 apop anonymous gssapi
  mechanisms = plain
    
  # userdb = /etc/passwd
  # passdb = /etc/passwd


I'm not sure why it rejects the userdb and passdb settings but it works if you comment out that portion.

---

### Post by mannheim on 2006-08-06
I think that a default install of Dovecot sets it up to use local unix users and passwords for IMAP or POP (as in chrisfay's post).

> if there's a user on my system named bob, then a mail to [email]bob@my.syst[/email]em should go to bob's mail box

This makes it sound like you are trying to configure mail **delivery** (which is the job of something like postfix or sendmail etc). Dovecot is all about mail **retrieval** by users.

Assuming you have postfix or sendmail working locally, then a mail to "bob@localhost" is probably being put in /var/mail/bob. You need to configure Dovecot to recognize "/var/mail/bob" as the location of bob's inbox. This is done by setting the environment variable default_mail_env in dovecot.conf.

---

### Post by chrisfay on 2006-08-06
> This makes it sound like you are trying to configure mail delivery (which is the job of something like postfix or sendmail etc). Dovecot is all about mail retrieval by users.

I had assumed he already had that running but after re-reading the post it did sound like he was trying to actually deliver the mail with doevecot. 

OP....Do you have an MTA or some kind of delivery agent? If not, you need to download something like Postfix, Qmail or sendmail and configure it to deliver your mail to your unix users. Then configure Dovecot to retrieve the mail from thier /var/mail boxes. 

> I think that a default install of Dovecot sets it up to use local unix users and passwords for IMAP or POP (as in chrisfay's post).

The configuration I posted earlier actually was not the default. I had to comment out the lines pertaining to the userdb and passwedb to get it to use /etc/psswd for authentication. It kept giving me an error code on those lines just like the OP had until I did that. Works perfect now.

---

### Post by lionsnob on 2006-08-11
Thanks for replying both of you.  Just got back from vacation and am at work now.  I think you may be right that I am confused about terminology.  I'll take a look when I get home again.

To clarify:

Software such as Dovecot lets a user log on remotely and retrieve their mail, while tools like Postfix let users receive mail from other networks to the server and send mail from the server to other networks.  Is this correct?

Thanks!

---

### Post by mannheim on 2006-08-11
Yes. For example, if we simplified the picture by imagining that the only Mail-related programs/packages out there were

(a) Thunderbird
(b) Dovecot
(c) Postfix

then Thunderbird would talk to Dovecot while the end-user was downloading mail (POP or IMAP), reading mail, deleting IMAP mail, moving mail between IMAP the user's IMAP mailboxes and so on. **Everything** else would be handled by Postfix. Just like a neighborhood post office, Postfix moves mail in both directions: it has the job of sending local mail off on its way to the outside world, and also the job of delivering incoming mail to the user's inbox.

---

### Post by lionsnob on 2006-08-11
Cool, thanks!  Everyone is so helpful :)

---

### Post by lionsnob on 2006-08-12
I reran through the install guide slower this time :) and got it up and running.  Thanks everyone!

---

