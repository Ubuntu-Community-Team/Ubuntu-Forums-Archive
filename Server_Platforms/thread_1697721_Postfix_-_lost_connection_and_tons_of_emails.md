---
title: "Postfix - lost connection and tons of emails"
date: 2011-03-01
forum: Server Platforms
---

### Post by januzi on 2011-03-01
Hi

I have got a strange problem with postfix. It is sending emails to all the people, but one person keeps complaining about number of emails. I checked it and I got:

> 
Mar  1 12:51:18  to=<xxxx, relay=xxxxx:25, delay=340648, delays=340648/0.01/0.23/ 0.13, dsn=4.4.2, status=deferred (lost connection with xxxx while sending end of data -- message may be sent more than once) 


So, the connection was lost, but the recipient got the email. Unfortunately postfix tries to send the email once more, and again, and again, till it reaches the queue lifetime. 

Is there a way to check what is wrong with postfix/recipient's server ? Or maybe I could disable deferring in that one case - lost connection at the end of data ?

---

