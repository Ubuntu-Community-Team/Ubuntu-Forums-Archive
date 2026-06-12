---
title: "How can I force certain users to use webmail only?"
date: 2009-02-27
forum: Server Platforms
---

### Post by phudgee on 2009-02-27
Heres my current setup:

Ubuntu 8.04
Postfix 2.5.1
Dovecot 1.0.10

Using Virtual users, MailDir format, WITHOUT a MySQL database.
Setup by this document: [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

I have about 30 domains being serviced by this box, and it works great!

However, I have a couple domains I'd like to add to give people FREE email addresses. I've got the domains added, and everything works good, however I'd now like to prevent them from using POP/IMAP clients to use this free account. I've installed RoundCube webmail, and would like them to have to use this exclusively to utilize the free account.

I still want the people with paid email to continue to use POP/IMAP.

I'm not sure if this is something I can do in Postfix or Dovecot, or in Ubuntu itself.

Ive Google this for the past 2 days, and am coming up empty-handed.

Does anyone have a clue as to how I can do this? Or can point me to some documentation I can read on it?

Can I block traffic at the OS level on a per-user basis?
Can I prevent certain users from connecting POP/IMAP from a server other than localhost?
Do I need to set up some obscurely named, and non-standard ported mailserver for the free accounts, so only the technically savvy can figure out the settings?
Im just not sure where to do this...

Thanks!

---

### Post by martien on 2009-02-27
> **phudgee said:**
> Heres my current setup:

Ubuntu 8.04
Postfix 2.5.1
Dovecot 1.0.10

Using Virtual users, MailDir format, WITHOUT a MySQL database.
Setup by this document: [https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

I have about 30 domains being serviced by this box, and it works great!

However, I have a couple domains I'd like to add to give people FREE email addresses. I've got the domains added, and everything works good, however I'd now like to prevent them from using POP/IMAP clients to use this free account. I've installed RoundCube webmail, and would like them to have to use this exclusively to utilize the free account.

I still want the people with paid email to continue to use POP/IMAP.

I'm not sure if this is something I can do in Postfix or Dovecot, or in Ubuntu itself.

Ive Google this for the past 2 days, and am coming up empty-handed.

Does anyone have a clue as to how I can do this? Or can point me to some documentation I can read on it?

Can I block traffic at the OS level on a per-user basis?
Can I prevent certain users from connecting POP/IMAP from a server other than localhost?
Do I need to set up some obscurely named, and non-standard ported mailserver for the free accounts, so only the technically savvy can figure out the settings?
Im just not sure where to do this...

Thanks!
Im not exactly sure how to do what you want, but im sure that can be done with database for example. Dovecot must have something like that (option to prevent imap access). But, wait... hmm, roundcube/squirrelmail and the other webmail clients are using imap to manage the mailboxes. I still think there is a right decision, but like i said im not sure about it. Another way is to change the default pop3/imap ports and give them only to your paid members, but its a temporary solution.

---

### Post by phudgee on 2009-02-27
Thanks for the reply, but I'd rather not switch over to a database backend at this moment.

I have thought about the port change, but a simple port scan and telnet will give you the right ports quickly.

And yes, roundcube uses IMAP that's why I was wondering if there was a way to prevent non-localhost IMAP/POP logins on a per-user basis.... as Roundcube would be connecting from localhost, whereas Thunderbird client on the users machine would not be.

---

### Post by martien on 2009-02-27
> **phudgee said:**
> Thanks for the reply, but I'd rather not switch over to a database backend at this moment.

I have thought about the port change, but a simple port scan and telnet will give you the right ports quickly.

And yes, roundcube uses IMAP that's why I was wondering if there was a way to prevent non-localhost IMAP/POP logins on a per-user basis.... as Roundcube would be connecting from localhost, whereas Thunderbird client on the users machine would not be.
I didn't mean database in its directly translation. Whatever is done with a database server can be done with text files as well.
Im sure there are mail servers using such a configuration, but im not sure if they are using dovecot. Try to search the same thing for courier and if you find the thing just migrate from dovecot to courier.

---

### Post by phudgee on 2009-02-27
I'd rather setup a different server for the free email or change ports than migrate my existing system.... its running so good :)

---

### Post by phudgee on 2009-02-28
Ok, I think I've found a solution, but I can't seem to get it working. It is "allow_nets"....

I've posted the following to the Dovecot Mailing list as well, in hopes that someone can help me out - anyone here got any ideas?

--------------------------------

I have added:

allow_nets=10.1.10.1 to the end of a specific users entry in the users file.

When that user tries to login, I get the following in the logs:

dovecot: 2009-02-28 09:06:59 Error: IMAP(bob@mydomain.com): Ambiguous mail location setting, don't know what to do with it: allow_nets=10.1.10.1 (try prefixing it with mbox: or maildir:)
dovecot: 2009-02-28 09:06:59 Error: IMAP(boo@mydomain.com): Mail storage creation failed with mail_location: allow_nets=10.1.10.1
dovecot: 2009-02-28 09:06:59 Error: child 4174 (imap) returned error 89

here is the line from my users file:

[email]bob@mydomain.com::5000:5000::/home/vmail/mydomain.com[/email]/:/bin/false::allow_nets=10.1.10.1

here is the corresponding line from the passwd file:

[email]bob@mydomain.com[/email]:$1$evcHgrbC$BuyQRCspMzTpD8zkphxo0/


My goal is, that I want to allow this user to check email ONLY from the IP specified (i.e. 10.1.10.1)

I just can't seem to get this working...
Am I going about something the wrong way?

Thanks!

---

### Post by phudgee on 2009-02-28
I was correct that it was the allow_nets extra field that needed to be used.

Per this page here:

[http://wiki.dovecot.org/PasswordDatabase/ExtraFields](http://wiki.dovecot.org/PasswordDatabase/ExtraFields)

I have added the field to my passwd file, and now the specific user can only log into webmail, by specifying the web server as the only IP he is allowed to log in from.

Thanks!

---

