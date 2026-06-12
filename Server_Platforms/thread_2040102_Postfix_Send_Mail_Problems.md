---
title: "Postfix Send Mail Problems"
date: 2012-08-10
forum: Server Platforms
---

### Post by nycterfin on 2012-08-10
Hello there.  I recently did a clean install of ubuntu following one of those perfect server guides with ispconfig and everything went smoothly.  However, postfix is exhibiting some peculiar behaviour.

I have postfix configured to send mail out on port 587 via smtp because I'm on comcast and that's what they require.  I can receive mail fine.  I can log into my accounts via thunderbird and receive my mail through that program.  However, I cannot send mail via thunderbird but I can send mail via webmail (squirrelmail).  When I attempt to send mail via thunderbird I get this error:
```
Sending of message failed.
The message could not be sent because the connection to SMTP server <snip> was lost in the middle of the transaction. Try again or contact your network administrator.
```

In /var/log/mail.log I see a report that no authentication attempt was made.

How can I resolve this issue?

---

