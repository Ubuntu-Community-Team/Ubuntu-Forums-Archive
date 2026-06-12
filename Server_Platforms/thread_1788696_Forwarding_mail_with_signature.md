---
title: "Forwarding mail with signature"
date: 2011-06-23
forum: Server Platforms
---

### Post by absVoid on 2011-06-23
Hi!

At first I want say that I'm regular Ubuntu user, not system administrator. I have installed mail server using [Virtual Users And Domains With Postfix, Courier, MySQL And SquirrelMail (Ubuntu 11.04)]("http://www.howtoforge.com/virtual-users-and-domains-with-postfix-courier-mysql-and-squirrelmail-ubuntu-11.04"). And it's work! :)

But I have a challenge. I need to get incoming mail (from another server), zipping mail-body (as html or text) and all attachments into zip-archive, compile new mail with this new attachment (zip-archive) and (most important!) sign all this email with signature which locale in pem-file and send it to BCC-address from incoming mail.

I don't know how do it or which tutorial start to read.

Please, help![-o<

---

### Post by BkkBonanza on 2011-06-23
This sounds like something [fdm]("http://fdm.sourceforge.net/") could handle. It can fetch mail for you, call a script to process the mail, and then forward to another address.

Mind you, I haven't done that, but this seems like a good starting place. The package is in the repositories.

---

