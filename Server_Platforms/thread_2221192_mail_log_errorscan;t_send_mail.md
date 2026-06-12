---
title: "mail log errors:can;t send mail"
date: 2014-05-01
forum: Server Platforms
---

### Post by shad2 on 2014-05-01
i have set up a mail server but i can't send email to virtual users.
 here is my mail log:
```
May  1 10:29:07 babel-laptop postfix/pickup[6549]: 5D3263C0843: uid=0 from=<root>
May  1 10:29:07 babel-laptop postfix/cleanup[16442]: 5D3263C0843: message-id=<20140501142907.5D3263C0843@babel-laptop>
May  1 10:29:07 babel-laptop postfix/qmgr[6550]: 5D3263C0843: from=<root@babel-laptop.babel-laptop.localhost>, size=236, nrcpt=1 (queue active)
May  1 10:29:07 babel-laptop postfix/trivial-rewrite[16443]: warning: do not list domain babel-laptop.localhost in BOTH mydestination and virtual_mailbox_domains
May  1 10:29:07 babel-laptop postfix/local[16444]: 5D3263C0843: to=<aretab@babel-laptop.localhost>, relay=local, delay=0.34, delays=0.23/0.02/0/0.1, dsn=5.1.1, status=bounced (unknown user: "aretab")
May  1 10:29:07 babel-laptop postfix/cleanup[16442]: 957553C0ADF: message-id=<20140501142907.957553C0ADF@babel-laptop>
May  1 10:29:07 babel-laptop postfix/qmgr[6550]: 957553C0ADF: from=<>, size=2034, nrcpt=1 (queue active)
May  1 10:29:07 babel-laptop postfix/bounce[16445]: 5D3263C0843: sender non-delivery notification: 957553C0ADF
May  1 10:29:07 babel-laptop postfix/qmgr[6550]: 5D3263C0843: removed
May  1 10:29:07 babel-laptop postfix/smtp[16446]: fatal: valid hostname or network address required in server description: 0
May  1 10:29:08 babel-laptop postfix/qmgr[6550]: warning: private/smtp socket: malformed response
May  1 10:29:08 babel-laptop postfix/qmgr[6550]: warning: transport smtp failure -- see a previous warning/fatal/panic logfile record for the problem description
May  1 10:29:08 babel-laptop postfix/master[6547]: warning: process /usr/lib/postfix/smtp pid 16446 exit status 1
May  1 10:29:08 babel-laptop postfix/master[6547]: warning: /usr/lib/postfix/smtp: bad command startup -- throttling
May  1 10:29:08 babel-laptop postfix/error[16455]: 957553C0ADF: to=<root@babel-laptop.babel-laptop.localhost>, relay=none, delay=1.2, delays=0.09/1/0/0.11, dsn=4.3.0, status=deferred (unknown mail transport error)
```

what can i fix here to be able to create the user mailboxes and view the mail?

---

### Post by shad2 on 2014-05-01
from this warning ,
May  1 10:29:07 babel-laptop postfix/trivial-rewrite[16443]: warning: do not list domain babel-laptop.localhost in BOTH mydestination and virtual_mailbox_domains
I removed domain babel-laptop.localhost from mydestination tried again.

---

