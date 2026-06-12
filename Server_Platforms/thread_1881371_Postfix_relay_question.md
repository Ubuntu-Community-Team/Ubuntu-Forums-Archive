---
title: "Postfix relay question"
date: 2011-11-15
forum: Server Platforms
---

### Post by vanio on 2011-11-15
Hi, I have the following situation (not my idea, but I'm the one who has to solve it :S):
Postfix + Dovecot server for staff mail and Exchange server for students mail, with two different domain names, but the task given to me is that all mail must be addressed to the linux server and if the account doesn't exist the mail must be relayed to the Exchange server. And I have no access to the exchange server. I know that it is possible with sendmail, but can I do it with postfix?

---

### Post by smtp on 2011-11-28
Hello,

I think yes it would be possible to have that with postfix as well
However it appears that the task is not correct, because "Dovecot server for staff mail and Exchange server for students mail".
Thus I think that all student's smtp addresses will be hosted on Exchange, right?
If yes you could route all messages addressed to student domain to Exchange.

---

