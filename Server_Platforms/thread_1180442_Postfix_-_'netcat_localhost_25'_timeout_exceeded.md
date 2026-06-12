---
title: "Postfix - 'netcat localhost 25' timeout exceeded"
date: 2009-06-06
forum: Server Platforms
---

### Post by opus_az on 2009-06-06
8.04 Server, updated and upgraded. Following [this guide for postfix]("https://help.ubuntu.com/community/PostfixBasicSetupHowto")

installed postfix ;followed all defaults
installed mailx

When I do a netcat localhost 25, I get:
220 myhostname.localdomain ESMTP Postfix (Ubuntu). 

Then it times out with:
421 4.4.2 myhostname.localdomain Error: timeout exceeded

Any suggestions? (Might be missing something obvious. This is my first attempt at anything Postfix.)

---

### Post by gombadi on 2009-06-07
My first question would be - What are you expecting it to do?

> 
220 myhostname.localdomain ESMTP Postfix (Ubuntu). 


You have connected to postfix and it has identified itself. Now it is waiting for a command from you - Are you sending it anything?

If you don't send it anything then it will timeout and drop the connection.

> 
421 4.4.2 myhostname.localdomain Error: timeout exceeded


---

### Post by opus_az on 2009-06-07
OK, I'm sorry. For some reason I was expecting some kind of prompt from the system after the 220 myhostname.localdomain ESMTP Postfix (Ubuntu).

I didn't realize that's when I begin entering the ehlo, mail from, rctp to, data, etc., lines. 

It's working fine, I just didn't realize it.

Thanks for the nudge. Appreciate it!

---

