---
title: "Postfix - sender_acces"
date: 2009-05-03
forum: Server Platforms
---

### Post by H4ST3 on 2009-05-03
Greetings,

I am running webmin and managing my virtual servers with Virtualmin. I have been having a hell of a time getting the Postfix mail server running. 

My latest issue is:
fatal: open database /etc/postfix/sender_access.db: Invalid argument

At first I was getting a database not found error so I created this text file:
```
#sample /etc/postfix/sender_access contains frequently spoofed domains
aol.com     reject_unverified_sender
hotmail.com reject_unverified_sender
yahoo.com reject_unverified_sender
gmail.com reject_unverified_sender
bigfoot.com reject_unverified_sender
 
```

then I added .db so Postfix would recognize it. I am guessing the text formatting is wrong. How can I fix this?

I'm guessing its a simple fix, but I'm new at this and don't know how this needs to be formated, or what tools to use to create it.

Thanks in advance

---

### Post by ephmanjmm on 2009-05-04
I don't think you just add .db to the end of the file name.  You use the postmap hash:/etc/postfix/sender_access command to create the file.

---

### Post by H4ST3 on 2009-05-04
Thanks I figured there was a command that I didn't know about to get that done. I'll give it a try when I get back.

---

