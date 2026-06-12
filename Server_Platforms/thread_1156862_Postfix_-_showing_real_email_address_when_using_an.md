---
title: "Postfix - showing real email address when using an alias?"
date: 2009-05-12
forum: Server Platforms
---

### Post by Funzo on 2009-05-12
Hi all

I have what is hopefully a trivial problem. I've setup a very basic mailing list using an alias connected to a MySQL database of email addresses. The problem is when I send an email to the alias address, the alias address shows up at the recipient instead of their actual email address.

For example, if I email to [email]mailinglist@domain.com[/email], then everyone in the mailing list receiving an email has "To: [email]mailinglist@domain.com[/email]", which is not what I want.

Anyway to solve this?

---

### Post by ejschaefer on 2009-05-12
Hello, 

What you're looking for it address rewriting: 

[http://www.postfix.org/ADDRESS_REWRITING_README.html](http://www.postfix.org/ADDRESS_REWRITING_README.html)

This may require a bit of reading, but what you're looking for is possible.

---

