---
title: "Postfix and Gmail/Hotmail from Outlook"
date: 2011-04-07
forum: Server Platforms
---

### Post by Hioushi on 2011-04-07
Hello,

Following [this guide]("http://library.linode.com/email/postfix/dovecot-mysql-ubuntu-10.04-lucid"), I have postfix+dovecot+mysql running on Ubuntu Server 10.4 serving virtual domains and so far so good. I managed to solve a few problems with SMTP, but a few others remain.

This one is quite strange (at least for me, maybe for some of you might be obvious or trivial). Whenever I send mail one of the following happens with Gmail and Hotmail:

1. Send mail through telnet to: Gmail receives it Ok, Hotmail marks it as Spam.
2. Send mail through webmail (squirrelmail) to: Gmail marks it as spam, Hotmail throws a connection time out.
3. Send mail through email client (Outlook/Thunderbird): Same as Webmail.

What appears odd to me is that sending mail through telnet works. 

Here's my main.cfg
[http://pastebin.com/45n6ANWb](http://pastebin.com/45n6ANWb)

Any help will be greatly appreciated.

---

### Post by elico on 2011-04-08
i dont understand.
what is 1? send mail to gmail from your host? or from gmail to your host?
recommend to try:> smtpd_use_tls = no
for testing
and an actual log file output (edit what you need)
can be more helpful.

---

### Post by Hioushi on 2011-04-08
Sorry, I forgot to clarify, the problem is sending from my server to both hotmail and gmail on each scenario I listed.

Disabling TSL solved the problem, at least I know what to troubleshoot, I was at lost before. Great advice, thank you.

---

