---
title: "Connecting with E-mail Clients"
date: 2009-12-12
forum: Server Platforms
---

### Post by guessswh0 on 2009-12-12
Hello,

Here is my question.  I have setup postfix with courier on my server.  I also installed squirrelmail.  Squirrelmail works perfect to receive and send any e-mail.  No issues there.

I am also able to connect to the server via pop3 (with outlook and thunderbird) and i can download my e-mails.  However, when I try to send an e-mail with my client, it always prompts me for my password.  I have even changed my password to see if that would work to a very basic one, and it is not working.  Squirrelmail works fine, but any e-mail client, it is messing up saying my smtp server needs a pass, and it won't accept what it is.

Any ideas?  I could use the help.

Thanks

---

### Post by shairozan on 2009-12-12
Hey there, 

I assume you're using SASL with courier, am I correct? If so, have you made sure that saslauthd is started. We run a similar setup where I work, and everytime we have to start the server, it's something we have to make sure gets started. Without it, courier doesn't make the connection to PAM and actually check the local password. 

```
/etc/init.d/saslauthd start
```

should make sure it's started.

---

