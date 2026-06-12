---
title: "Using POSTFIX for a multi domain server"
date: 2008-01-22
forum: Server Platforms
---

### Post by csurlee on 2008-01-22
Hello, 
I have a question... 
i want to make a mail server and now i use qmail as mail server  on a slack... its good i use 5 domains on this but i want to change the operations system to a ubuntu server. My question is ... can i use postfix like qmail for 5 or for ex.: 100 domain ...to have seperate mail accounts for every domain name i host
Thanks alot.  :guitar:

---

### Post by MJN on 2008-01-22
Of course, see [http://www.postfix.org/VIRTUAL_README.html](http://www.postfix.org/VIRTUAL_README.html) for a good overview.
 
Note the various options available depending on exactly how you want it structured. For example, whether you want each 'mail user' to also have a 'system user' account, whether 'mail users' are just that - mail only etc etc.
 
Note that the best approach for 5 domains with a handful of users will likely differ to that for 100 domains and thousands of users hence it will pay dividends to consider your exact requirements before venturing down one particular path.
 
Mathew

---

### Post by csurlee on 2008-01-22
thanks man you where very helpfool :D :popcorn:

---

