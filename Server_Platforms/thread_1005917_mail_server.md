---
title: "mail server"
date: 2008-12-08
forum: Server Platforms
---

### Post by brocky102 on 2008-12-08
does anyone know how to configure fetchmail to collect a catch-all email account and then deliver it to local accounts? 

I have asked this question before but was wanting to do it a different way and got no real answer. 

Now all it has to do is get the mail from the remote mail server then deliver it to my local mail server running on the same machine which is postfix/dovecot. 

Any help would be greatly appreciated.

---

### Post by albinootje on 2008-12-08
Take a look at getmail, an interesting alternative for fetchmail.
[http://pyropus.ca/software/getmail/faq.html#faq-how-filter](http://pyropus.ca/software/getmail/faq.html#faq-how-filter)

---

### Post by brocky102 on 2008-12-11
Ok i have got this almost working.

I had this working fine on my test domain but as soon as i put it on our live domain it stopped working. I checked the log and this is what i am finding in my procmail.log

```

From glenn@eresources.com.au  Fri Dec 12 11:11:54 2008
 Subject: test3
  Folder: /usr/sbin/sendmail -oi test3@dmdiesel.com.au                     5497
From MAILER-DAEMON  Fri Dec 12 11:11:55 2008
 Subject: Undelivered Mail Returned to Sender
  Folder: /home/catchall/mail/new/1229040716.4817_0.mail                   7600

```


and here is my procmail filter

```

DEFAULT=$HOME/mail/
MAILDIR=$HOME/mail
PMDIR=$HOME/.procmail
LOGFILE=$HOME/procmail.log
SHELL=/bin/sh

:0
* ^Delivered-To: test3@dmdiesel\.com\.au
! test3@dmdiesel.com.au

```

It never used to do this. Does anyone have any idea why this is happening

---

### Post by brocky102 on 2008-12-23
Solved. See [http://www.experts-exchange.com/OS/Linux/Q_23978681.html]("http://www.experts-exchange.com/OS/Linux/Q_23978681.html") for the full resolution

---

