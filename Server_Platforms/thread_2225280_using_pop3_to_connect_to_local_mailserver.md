---
title: "using pop3 to connect to local mailserver"
date: 2014-05-20
forum: Server Platforms
---

### Post by shad2 on 2014-05-20
how can i manage to connect to my local email server from the php .
I can send emails to users in the database on the terminal,but when i try from browser i get the following error:
Connecting to localhost ...
S +OK Dovecot ready.
Connected to the POP3 server "localhost". C USER aretab
S +OK
C PASS getin1234
S -ERR Authentication failed.
**Error: Password error: Authentication failed.**

I know that this is the password for this user.
in my auth log file I have this:
May 21 00:39:02 bal-lop CRON[18907]: pam_unix(cron:session): session opened for user root by (uid=0)
May 21 00:39:02 bal-lop CRON[18907]: pam_unix(cron:session): session closed for user root

and in my mail log I have this:
May 21 00:43:09 bal-lop postfix/qmgr[1717]: E99073C06A7: from=<>, size=2415, nrcpt=1 (queue active)
May 21 00:43:10 bal-lop postfix/smtp[32146]: fatal: valid hostname or network address required in server description: 0
May 21 00:43:11 bal-lop postfix/qmgr[1717]: warning: private/smtp socket: malformed response
May 21 00:43:11 bal-lop  postfix/qmgr[1717]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem description
May 21 00:43:11 bal-lop postfix/master[1708]: warning: process /usr/lib/postfix/smtp pid 32146 exit status 1
May 21 00:43:11 bal-lop  postfix/master[1708]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
May 21 00:43:12 bal-lop  postfix/error[32201]: E99073C06A7: to=<root@bal-lop .bal-lop .localhost>, relay=none, delay=53437, delays=53435/2.6/0/0.17, dsn=4.3.0, status=deferred (unknown mail transport error)

What can i do to fix this isuue?

---

