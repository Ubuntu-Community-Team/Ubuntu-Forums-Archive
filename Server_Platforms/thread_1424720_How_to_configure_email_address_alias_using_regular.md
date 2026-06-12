---
title: "How to configure email address alias using regular expression in postfix"
date: 2010-03-08
forum: Server Platforms
---

### Post by stevenfoong on 2010-03-08
Hi , I am newbie in postfix , been try to search around but didnt manage to get an answer for my question, help anyone who know the answer, please help me. Thank you.

I am trying to configure virtual alias using regular expression.
For example :

Email send to [email]user.1@example.com[/email] and [email]user.2@example.com[/email] will deliver to user mailbox.

Email send to [email]user2.1@example.com[/email] and [email]user2.2@example.com[/email] will deliver to user2 mailbox.

And the numbers or alphabet in between user name and the domain will be vary , I can't just do a normal alias.

I been try to play around with main.cf and the virtual alias table but still not able to get work. So I am not sure is the main.cf didnt configure correctly or the regular expression is not working.

If anyone know how to solve this issue, please share with me.

Thank you.

---

