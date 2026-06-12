---
title: "Mail server on Ubuntu"
date: 2010-04-24
forum: Server Platforms
---

### Post by halvors on 2010-04-24
Hi!

I cant get my email server work, here is my log:

```
Apr 24 22:42:31 ss1 dovecot: Killed with signal 15 (by pid=10791 uid=0 code=kill)
Apr 24 22:42:52 ss1 dovecot: Killed with signal 15 (by pid=10829 uid=0 code=kill)
Apr 24 22:43:09 ss1 dovecot: Killed with signal 15 (by pid=10869 uid=0 code=kill)
Apr 24 22:44:16 ss1 dovecot: Killed with signal 15 (by pid=11091 uid=0 code=kill)
Apr 24 22:44:51 ss1 postfix/postmap[11672]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:44:54 ss1 postfix/postqueue[12001]: warning: Mail system is down -- accessing queue directly
Apr 24 22:46:33 ss1 postfix/postmap[12924]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:46:33 ss1 postfix/postmap[12961]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:46:34 ss1 postfix/postmap[12962]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:46:34 ss1 postfix/postmap[12963]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:46:34 ss1 postfix/postmap[12964]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:46:34 ss1 postfix/postmap[12965]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:47:07 ss1 postfix/postmap[13061]: warning: /etc/aliases, line 2: record is in "key: value" format; is this an alias file?
Apr 24 22:48:24 ss1 dovecot: IMAP(ss1): mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/ss1
Apr 24 22:48:24 ss1 dovecot: IMAP(ss1): Fatal: Namespace initialization failed
Apr 24 22:53:13 ss1 dovecot: IMAP(ss1): mail_location not set and autodetection failed: Mail storage autodetection failed with home=/home/ss1
Apr 24 22:53:13 ss1 dovecot: IMAP(ss1): Fatal: Namespace initialization failed
Apr 24 22:53:18 ss1 dovecot: dovecot: Killed with signal 15 (by pid=1774 uid=0 code=kill)
Apr 24 22:53:19 ss1 dovecot: Killed with signal 15 (by pid=1794 uid=0 code=kill)
Apr 24 22:54:02 ss1 dovecot: Killed with signal 15 (by pid=1873 uid=0 code=kill)

```Halvor.

---

### Post by speedygarth on 2010-05-11
why dont you try re installing the application by using apt-get or aptitude.
use the ubuntu server documentation on [https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by Scstrade123 on 2010-05-11
What is mail server ?

---

### Post by TheFuturian on 2010-05-11
> **speedygarth said:**
> why dont you try re installing the application by using apt-get or aptitude.
use the ubuntu server documentation on [https://help.ubuntu.com/](https://help.ubuntu.com/)

I agree that the Server Documentation is probably going to be your best source of information.

[https://help.ubuntu.com/10.04/serverguide/C/email-services.html]("https://help.ubuntu.com/10.04/serverguide/C/email-services.html")

Some Prudent Questions:-
[LIST]
[*]Which distro are you using (i.e. 10.04)?
[*]Has your e-mail server ever worked successfully?
[*]Is it inbound or outbound traffic you are having problems with?
[*]Which Packages are you using for your e-mail server?
[*]Have you configured SSL?
[/LIST]

---

