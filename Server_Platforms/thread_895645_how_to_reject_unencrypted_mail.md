---
title: "how to reject unencrypted mail"
date: 2008-08-20
forum: Server Platforms
---

### Post by waster on 2008-08-20
Please could someone let me know how I can set up a mail server to reject unencrypted emails? I don't mean the connection, I mean the email contents, encrypted by PGP.

I don't mind what mail server, although I'm currently using the zimbra server packages.

Thanks.

---

### Post by Ximbiot on 2008-08-20
I use postfix and have installed all sorts of spam filters, mailing list handlers, and such for it.  The configuration is extremely complicated, but it has tons of support for filters from simple, built-in comparisons of regular expressions to mail headers to passing the entire mail to external processes and checking the result.  See [Postfix Content Inspection]("http://www.postfix.org/CONTENT_INSPECTION_README.html") for more, or try googling "postfix content filters".

---

