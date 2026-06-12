---
title: "Squirrel Mail and Mailman"
date: 2007-09-26
forum: Server Platforms
---

### Post by DavidRussellCA on 2007-09-26
Hi There,

I've just set up a server following the community docs here: [https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

I'm hoping to run both Mailman as well as a mail server for users using Squirrel mail if possible.  Unfortunately, I'm running into some trouble.  All of the steps in the docs seemed to work - and the telnet tests work fine.

I can access the web interface of mailman and squirrelmail - and can login and send mail from squirrel mail fine.  I can also login to mailman fine, and if I create a new list / subscribe myself to a list I get that email.  So SMTP seems to be working fine.  There appears to be a problem receiving mail, though.

Mail sent to the mailman address is getting rejected flat out.  Mail sent to a local account is being recieved - but not shown in Squirrel Mail.  In the shell I see "You have new mail" and if I view the mail file the emails are there - but SM is showing no new messages.  

I know very little about this - but I'm assuming it's something my my transport file.  

Any help would be appreciated.  I'm using Ubuntu Server 7.04

---

### Post by DavidRussellCA on 2007-09-27
Update - I've managed to fix mailman such that it's sending and receiving mail fine now.  I had forgotten to set up the aliases file.  Still having trouble with SquirrelMail, though.

I can send mail out from SquirrelMail no problem.  Sending mail to the server (apart from the Mailman addresses) results in this:

> This is the mail system at host xxx.xxx.xxx.ca.

I'm sorry to have to inform you that your message could not
be delivered to one or more recipients. It's attached below.

For further assistance, please send mail to postmaster.

If you do so, please include this problem report. You can
delete your own text from the attached returned message.

                   The mail system

<mesmail@xxx.xxx.xxx.ca>: user unknown

Previously I was getting "You have new mail" in Linux - but nothing in SquirrelMail.  Now I'm not getting that.

Alias File:

> 
# Added by installer for initial user
root:   mesmail
clamav: root
amavis: root

## mailman mailing list
mailman:              "|/var/lib/mailman/mail/mailman post mailman"
mailman-admin:        "|/var/lib/mailman/mail/mailman admin mailman"
mailman-bounces:      "|/var/lib/mailman/mail/mailman bounces mailman"
mailman-confirm:      "|/var/lib/mailman/mail/mailman confirm mailman"
mailman-join:         "|/var/lib/mailman/mail/mailman join mailman"
mailman-leave:        "|/var/lib/mailman/mail/mailman leave mailman"
mailman-owner:        "|/var/lib/mailman/mail/mailman owner mailman"
mailman-request:      "|/var/lib/mailman/mail/mailman request mailman"
mailman-subscribe:    "|/var/lib/mailman/mail/mailman subscribe mailman"
mailman-unsubscribe:  "|/var/lib/mailman/mail/mailman unsubscribe mailman"

## meslink mailing list
meslink:              "|/var/lib/mailman/mail/mailman post meslink"
meslink-admin:        "|/var/lib/mailman/mail/mailman admin meslink"
meslink-bounces:      "|/var/lib/mailman/mail/mailman bounces meslink"
meslink-confirm:      "|/var/lib/mailman/mail/mailman confirm meslink"
meslink-join:         "|/var/lib/mailman/mail/mailman join meslink"
meslink-leave:        "|/var/lib/mailman/mail/mailman leave meslink"
meslink-owner:        "|/var/lib/mailman/mail/mailman owner meslink"
meslink-request:      "|/var/lib/mailman/mail/mailman request meslink"
meslink-subscribe:    "|/var/lib/mailman/mail/mailman subscribe meslink"
meslink-unsubscribe:  "|/var/lib/mailman/mail/mailman unsubscribe meslink"

Transport File:
> xxx.xxx.xxx.ca mailman:

I'm guessing it's something with everything going to Mailman now - but I'm not sure how to deal with it.  Please help! :)

---

### Post by DavidRussellCA on 2007-09-28
Okay - getting closer now.

Sending mail to the server doesn't send back any failure notices.  I get the notification that there is new mail in /var/mail/mesmail in the terminal.  It's just not showing up on SquirrelMail / if I set up an IMAP account in my mail software.  IMAP is doing something though, setting it up through OS X's "Mail" the Sent folder contains the right things - as does SquirrelMail.  It seems to just be the Inbox that isn't synchronizing with the mail file.

Thanks for any tips you can give me.

---

