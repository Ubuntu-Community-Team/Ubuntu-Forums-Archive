---
title: "Spam catching addresses"
date: 2011-07-23
forum: Server Platforms
---

### Post by narcisgarcia on 2011-07-23
Does somebody know a way to make a MTA (such as Postfix) to filter all mail that matches across various recipients?

For example:
- A monitoring recipient [email]detector@example.com[/email]
- A personal recipient [email]mike@example.com[/email]

If the MTA receives a message sent to [email]detector@example.com[/email] , it's automatically stored as a spam case. If the MTA receives THE SAME message to [email]mike@example.com[/email] , it's sure spam and can be discarded automatically.

---

