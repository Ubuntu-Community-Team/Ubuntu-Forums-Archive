---
title: "Postfix SMTP invalid address rejection"
date: 2009-06-17
forum: Server Platforms
---

### Post by Jonie on 2009-06-17
What's the option to control the Postfix behaviour when the message has multiple recipient addresses and one or more of them are invalid? There are two kinds of action to be taken:
- to abort SMTP transaction when the invalid address is being contacted, leaving email client with the mailing list partly undelivered
- to accept message for delivery and return failure notice about the problems encountered, delivering mail to all valid addresses

ISPs usually follow either way, but sometimes the second action is more preferred, though potentially less secure. Per account control would be perfect solution, but probably hard to implement.

---

