---
title: "What's the default &quot;Mail Server&quot; configuration in Ubuntu Server?"
date: 2011-09-28
forum: Server Platforms
---

### Post by apotrope on 2011-09-28
Hello,

I'm still finding my feet with Ubuntu Server 11.04. One of the things that I need is a functioning email server that can send and receive email. One of the options I selected during installation was the "Mail Server" option. Could someone please explain what packages this prompts Ubuntu to install and how the system configures them? I would greatly appreciate it.

---

### Post by ktmom on 2011-09-29
if it's anything like 10.04

tasksel --task-packages mail-server

dovecot-imapd
procmail
dovecot-common
postfix
libpth20
libmysqlclient16
libgpgme11
mutt
libpq5
dovecot-pop3d
bsd-mailx
ssl-cert
mysql-common

I've never installed a mail server this way, but I have to believe that it's not really configured  (did it step you through a series of questions?)  You may find a guide like [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) of one from the help.ubuntu.com/community helpful if you are starting out.

---

