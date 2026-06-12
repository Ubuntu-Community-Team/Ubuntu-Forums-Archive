---
title: "Mail Server sending problems"
date: 2010-09-11
forum: Server Platforms
---

### Post by head-desk on 2010-09-11
Hi all,

I am having a hair-ripping moment where I cannot get my mail server to send any mail. It keeps asking for authentication even when I give it a username and password.

The server consists of Dovecot - Postfix - PostgreSQL - saslauthd - ubu10.04

There are no real users only virtual ones in the database. I can authenticate fine via imap and receive emails without a hitch. The problem is only on sending.

I followed these tutorials:
[http://wiki2.dovecot.org/HowTo/DovecotPostgresql](http://wiki2.dovecot.org/HowTo/DovecotPostgresql)
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

Anyone out there done a postgres dovecot setup?

- HeadDesk (the painful kind) :p

---

### Post by hictio on 2010-09-11
Are you sending the emails directly from that server, or are you using a SMART HOST?
Is this a specific problem with the outgoing emails of the "Mail Server" portion of that server, I mean, does any type of email -that has to be send from that box- actually been sent at all? For instance, Logwatch emails.

---

### Post by head-desk on 2010-09-11
> **hictio said:**
> Are you sending the emails directly from that server, or are you using a SMART HOST?
Is this a specific problem with the outgoing emails of the "Mail Server" portion of that server, I mean, does any type of email -that has to be send from that box- actually been sent at all? For instance, Logwatch emails.


Through a remote mail client, I think so yes.

I am using the Windows Live Mail client to access the mailbox over imap and smtp(sending). The mail I assume when I click send goes through the server giving me my mail. When I click send it asks for authentication constantly and never accepts the password that is being used to receive mail.

-HeadDesk

---

### Post by head-desk on 2010-09-12
Having a look in the logs I get this every time I try to authenticate via the mail client for sending.
> 
SASL LOGIN authentication failed: authentication failure

Password is definately correct.

---

### Post by HermanAB on 2010-09-12
> Password is definately correct.

No, the error messages are always correct, though they may sometimes be a little misleading...

Your best bet is to go to the Postfix project web site and start reading.

---

### Post by head-desk on 2010-09-16
> **HermanAB said:**
> No, the error messages are always correct, though they may sometimes be a little misleading...

Your best bet is to go to the Postfix project web site and start reading.

Done some digging and only partly solved the problem.

If I have a plain text password in the database and the pam_pgsql.conf file set "pw_type = plain" then everything works fine.

If I encrypt it with for example md5 and set "pw_type=md5" it won't work. 

Any ideas? I am loosing hair :p

---

