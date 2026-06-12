---
title: "Help I do not know where to start problem postfix-mysql dovecot-mysql"
date: 2017-05-18
forum: Server Platforms
---

### Post by pablitoo on 2017-05-18
My log is as follows

```
 May 17 18:57:01 corpocar postfix/smtpd[4316]: connect from mail-yb0-f196.google.com[209.85.213.196]
 May 17 18:57:02 corpocar postfix/smtpd[4316]: 15E681A00B9B: client=mail-yb0-f196.google.com[209.85.213.196]
 May 17 18:57:02 corpocar postfix/cleanup[4320]: 15E681A00B9B: message-id=<CA+DdPwZ9=ygAdg4YtneLOdNLL9Pro7sSOX19LeHcrBtE9ZFDfQ@mail.gmail.com>
 May 17 18:57:02 corpocar postfix/qmgr[4313]: 15E681A00B9B: from=<maugerijuan@gmail.com>, size=2437, nrcpt=1 (queue active)
 May 17 18:57:02 corpocar postfix/qmgr[4313]: warning: connect to transport private/virtuales: No such file or directory
 May 17 18:57:02 corpocar postfix/error[4321]: 15E681A00B9B: to=<pablo@corpocar.com>, relay=none, delay=0.53, delays=0.47/0.01/0/0.06, dsn=4.3.0, status=deferred (mail$
 May 17 18:57:02 corpocar postfix/smtpd[4316]: disconnect from mail-yb0-f196.google.com[209.85.213.196] ehlo=1 mail=1 rcpt=1 data=1 quit=1 commands=5
 May 17 19:00:22 corpocar postfix/anvil[4318]: statistics: max connection rate 1/60s for (smtp:209.85.213.196) at 
 May 17 18:57:01May 17 19:00:22 corpocar postfix/anvil[4318]: statistics: max connection count 1 for (smtp:209.85.213.196) at 
 May 17 18:57:01May 17 19:00:22 corpocar postfix/anvil[4318]: statistics: max cache size 1 at May 17 18:57:01 
```

The email arrives at the manager and does not find the table to deposit it but I do not know where I have the error in if to change it can be the transport table? ... I put this on the transport table


create table transport ( 
domain varchar(128) not null primary key unique, 
transport varchar(128) not null default 'virtuales:' )

---

### Post by howefield on 2017-05-18
Hello and welcome to the forums.

The "*Forum Feedback & Help*" sub forum is for problems with the forums themselves, so thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by pablitoo on 2017-05-18
[COLOR=#212121][FONT=arial]Sorry .. did not know .. can be deleted so I pass the other forum?
[/FONT][/COLOR]
[COLOR=#212121][FONT=arial]
Sorry .. did not know .. can be deleted so I pass the other forum?[/FONT][/COLOR]

---

### Post by howefield on 2017-05-18
> **pablitoo said:**
> Sorry .. did not know .. can be deleted so I pass the other forum?

Don't worry, it's not a problem, your thread is now in the right sub forum so just hang on for someone who can help you.

---

