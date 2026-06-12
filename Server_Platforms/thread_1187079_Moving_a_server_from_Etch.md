---
title: "Moving a server from Etch"
date: 2009-06-14
forum: Server Platforms
---

### Post by comandrei on 2009-06-14
I have and old box running Debian Etch at work that's doing a lot of things (mail server, router, proxy), and I'd like to move the whole server to a new box with Jaunty Server.
My main problem is the mail server. It's running  Postfix for SMTP and Dovecot for IMAP.
Does anyone know how to move the e-mail users have on the old server to the new machine? Do I only need to move their home directories ( Dovecot uses Maildir ) or do I need to move other files (like /var/spool/mail) ?

---

