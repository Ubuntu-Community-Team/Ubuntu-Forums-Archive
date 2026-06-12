---
title: "Where is maildirmake?"
date: 2006-09-04
forum: Server Platforms
---

### Post by Milambar on 2006-09-04
Having kicked mandriva off my server, Im rather disappointed to find that ubuntu doesn't use Mail dirs. It uses mailboxes. No biggie, its an easy reconfiguration...

Usually.

Not in this case.

Ubuntu doesn't appear to supply the maildirmake command for me to generate the appropriate directory structures. Its not installed, nor is it in any of the repositories that I can find.

```
root@crydee:/etc# locate maildirmake
root@crydee:/etc# apt-cache search maildirmake
root@crydee:/etc# 
```

As you can see.. Nothing happening. So, my question is... How do I install maildirmake and where do I get it from? I really do prefer mail directories to mailboxes.

Milambar
irc.sorcery.net #nebula

---

### Post by Glut on 2006-09-05
maildir make is found in the maildrop packages (I'm fairly sure, haven't checked recently) but you may not need it.

Mail delivery format depends on your MTA. You haven't specified what you're using and I can't remember what the default is.
Postfix and Exim will happily create maildir directories on delivering the first email.
procmail (sendmail's default deliverer) will not.

---

### Post by StickyStyle on 2006-09-05
You will find maildirmake in several packages, notably IMAP server packages and maildrop as mentioned...
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=maildirmake&searchmode=searchword&case=insensitive&version=dapper&arch=i386](http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=maildirmake&searchmode=searchword&case=insensitive&version=dapper&arch=i386)


> 
Postfix and Exim will happily create maildir directories on delivering the first email.
procmail (sendmail's default deliverer) will not.


Procmail will gladly deliver, and create Maildir folders. 
If you are using postfix set mailbox_command = /usr/bin/procmail in your /etc/postfix/main.cf

set MAILDIR=/where/ever/you/want/mail/ (notice the trailing slash) in your /etc/procmailrc, and make sure users that use .procmailrc files add a trailing slash to to there destination folders. Such as the following...

:0:
* ^X-CRM114-Status: SPAM.*
.Junk/

---

### Post by Milambar on 2006-09-07
Thanks guys.

:)

---

