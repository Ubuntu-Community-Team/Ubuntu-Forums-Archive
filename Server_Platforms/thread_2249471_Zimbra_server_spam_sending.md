---
title: "Zimbra server spam sending"
date: 2014-10-22
forum: Server Platforms
---

### Post by Sapph1r3 on 2014-10-22
I have a Zimbra server that may, or may not be sending out spam.
I am new to Zimbra and Ubuntu both, and would like to know how I can check if an account on the Zimbra server has become compromised.
The server has been tested for Open relay and accounts are not allowed to send from different addresses.
However, each address appearing in the deferred queue is not valid on the server.
e.g. domain1.com is valid but address [email]th@domain1.com[/email] is invalid yet appearing in the queue.
Any advice would be Greatly Appreciated.

---

### Post by slickymaster on 2014-10-22
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by nerdtron on 2014-10-23
Perhaps we need to see the postfix config and the mail.log that shows the deferred mail.

---

