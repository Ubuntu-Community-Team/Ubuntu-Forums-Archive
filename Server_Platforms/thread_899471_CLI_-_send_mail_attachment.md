---
title: "CLI - send mail attachment"
date: 2008-08-24
forum: Server Platforms
---

### Post by ngmachado on 2008-08-24
Hi,

How can attach a file to an email?

I've Postfix installed and I'm using the **sendmail** command (Postfix to Sendmail compatibility interface) to send mails, so I would like to use it.

(I've mutt installed but since I don't have the need to read email, I will end up removing it.)

Your help is really appreciated. Thanks.

---

### Post by HalPomeranz on 2008-08-24
This may be of some help to you:

[http://www.samag.com/documents/s=9171/sam0406d/0406d.htm](http://www.samag.com/documents/s=9171/sam0406d/0406d.htm)

It's about doing an auto-responder with procmail that sends emails with attachments.  But you could extract the "formail ... | sendmail ..." bit from the procmail recipe and use that to send your attachments.

---

