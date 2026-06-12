---
title: "Secure email portal"
date: 2016-12-09
forum: Server Platforms
---

### Post by johncroc on 2016-12-09
We currently use Symantec's PGP Universal Server as our secure email portal*, implemented as a standalone "web" server in our DMZ.  It's time to renew support and I'm looking for a way to replace it with something from the open source world, that would run in a Debian environment (Ubuntu, etc.).  The solution needs to enable mail recipient/users to create their own accounts and to view their email with ZERO intervention from IT personnel.

I've spent a little time Googling and not finding anything but cloud solutions.  I think the word "portal" is throwing Google off, but if I take that word out, all I get are returns that specify basic Linux email servers (POP3, IMAP, SMTP, etc.), without the portal functionality.

Anyone have any ideas about what packages I should be looking at to replace the Symantec PGP Universal server?

JC


*Our primary email system is Exchange 2010.  When one of our internal users sends an email to a recipient domain that doesn't have TLS enabled, Exchange sends the email to our secure portal.  The secure portal then notifies the recipient to use their browser to log in and view the email via HTTPS.

---

