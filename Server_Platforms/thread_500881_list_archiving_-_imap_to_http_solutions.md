---
title: "list archiving - imap to http solutions?"
date: 2007-07-14
forum: Server Platforms
---

### Post by awry on 2007-07-14
Hi everyone,

I'm trying to help a client improve their mail archives.  The MLM is Mailman, and they're currently using pipermail.  They have some legit gripes with pipermail, and want it out of the picture.

We've been pursuing a [mod_mbox]("http://httpd.apache.org/mod_mbox/") strategy, but the code doesn't seem very mature nor very actively maintained.  Attachment handling is broken, and there is no functional search implementation.

Lurker and MHonArc are more mature, but are not substantial improvements over pipermail for my client.  They're both pretty fugly, and Lurker has an especially funky interface.

Is there any common list archiving software that we're overlooking?  I like the gmane threaded interface, but weaver/loom seems unworkable.

I really like the idea of offering an anonymous, read-only IMAP archive, perhaps served up by dbmail.  But a web interface of some kind is also essential.  Does anyone know of an http imap reader designed for anonymously browsing an imap archive?  Or an easy way to easily strip-down/customize a popular webmail client (squirrel, imp) to suit such a purpose?  Threading and search features are a must, of course.

Help me brainstorm, guys... there has to be something better out there!

---

