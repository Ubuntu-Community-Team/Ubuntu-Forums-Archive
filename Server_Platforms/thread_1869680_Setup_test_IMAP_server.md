---
title: "Setup test IMAP server"
date: 2011-10-26
forum: Server Platforms
---

### Post by raffaele181188 on 2011-10-26
I need to test a program against an IMAP mail server
I installed Ubuntu on a virtual machine and now I want some hints on how to setup a simple Dovecot server to be accessed with IMAP. Basically I need a way to populate the inbox with thousands of script-generated messages, and then retrieving it using local system users credentials from another machine (so my mail client will use something like [email]raffaele@testmail.local[/email] as username and my regular password for password). I've never configured anything like this and I hope this is a simple task, because this server is only for testing purposes

---

### Post by vasile002 on 2011-10-26
Here's a howto that explains how to do it with simple system accounts for authentication:
[http://library.linode.com/email/postfix/dovecot-system-users-ubuntu-10.10-maverick](http://library.linode.com/email/postfix/dovecot-system-users-ubuntu-10.10-maverick)

I hope it helps

---

### Post by raffaele181188 on 2011-10-26
I gave up with Dovecot and installed Citadel, but can't get it to work
I have two processes named citserver, but webcit cannot connect to server, end netstat only shows two opened ports (80 and 443). Any idea why citadel server doesn't do anything? Also, I see no log file...

---

