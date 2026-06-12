---
title: "Postfix + Pgsql = duplicate emails (?)"
date: 2006-02-20
forum: Server Platforms
---

### Post by agillesp on 2006-02-20
I setup Postfix with SSL / TLS and auth-pgsql.  Everything I send out creates two copies of the email.  I have two different email addresses (foo & bar) + one virtual email address (zed).  [email]zed@example.com[/email] is mapped to [email]foo@example.com[/email].  [email]bar@example.com[/email] has no other virtual mappings.

Email originating from either foo or bar results in two emails.  Here is a relevant mail.log snippet:

Feb 20 13:46:05 localhost postfix/cleanup[12736]: 678974C1A4: message-id=<43FA0E87.2080504@example.com>
Feb 20 13:46:05 localhost postfix/qmgr[12019]: 678974C1A4: from=<foo@example.com>, size=702, nrcpt=1 (queue active)
Feb 20 13:46:05 localhost postfix/smtpd[12729]: disconnect from unknown[192.168.1.100]
Feb 20 13:46:05 localhost imapd-ssl: Connection, ip=[::ffff:192.168.1.100]
Feb 20 13:46:05 localhost imapd-ssl: LOGIN, user=foo, ip=[::ffff:192.168.1.100], protocol=IMAP
Feb 20 13:46:05 localhost postfix/pickup[12018]: E39784C1D5: uid=65534 from=<foo>
Feb 20 13:46:05 localhost postfix/cleanup[12736]: E39784C1D5: message-id=<43FA0E87.2080504@example.com>
Feb 20 13:46:05 localhost postfix/qmgr[12019]: E39784C1D5: from=<foo@example.com>, size=562, nrcpt=1 (queue active)
Feb 20 13:46:06 localhost postfix/smtp[12738]: 678974C1A4: to=<test@gmail.com>, relay=mail.gmail.com[216.239.63.83], delay=1, status=sent (250 G340m7A2 Message accepted for delivery.)
Feb 20 13:46:06 localhost postfix/qmgr[12019]: 678974C1A4: removed
Feb 20 13:46:06 localhost postfix/smtp[12745]: E39784C1D5: to=<test@gmail.com>, relay=mail.gmail.com[216.239.63.83], delay=1, status=sent (250 S340y7A2 Message accepted for delivery.)
Feb 20 13:46:06 localhost postfix/qmgr[12019]: E39784C1D5: removed


Anybody have any ideas?

Thanks.
-Abe

---

### Post by rich on 2006-02-21
erm,

The postfix lists have several duplicate mail threads. Most of them boil down to problems with other parts of the mail process (procmail etc) or the mappings. 

Are the messages actually the same ? There seems to be a difference in size between them. Do the headers within the mail itself offer any clues ?

Rich

---

### Post by agillesp on 2006-03-08
Yep, looking at the headers revealed the dupes were coming from a different UID.  My users look-up table was using the UID "noboby" for everyone.  For some reason this wasn't jiving with *real* users on the Linux box.  I changed the UID to the actual UID of the user and it seemed to work.

Now I just gotta figure out why Horde email interface is sending its own dupe from user www-data.

Thanks for the help!
-Abe

---

