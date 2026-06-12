---
title: "email forwarding question?"
date: 2010-02-18
forum: Server Platforms
---

### Post by matthinckley on 2010-02-18
Hi,

I currently have a linux machine running SMTP and Dovecot for an email server.

I'm looking at replacing this server with an Ubuntu/Zimbra machine.

I have the Ubuntu/Zimbra machine all configured for the same domain as the original mail server.

Is there a way that I can set my original mail server to relay only a specific address to the new server for testing?

i.e. [email]user1@domain.com[/email] mx record points to server1.domain.com.  can I have server1.domain.com relay messages for user1 to newzimbra.domain.com while not relaying all of the other mail for domain.com?


Thanks in advance,

Matt

---

### Post by mbehamin on 2010-02-19
you can forward an email address to other address just by adding .forward in user home directory. 
therefor if you use different temporary address for your new mail server you can forward the mails toward the new mail server. 
im not sure but i think it is impossible to use rely based on the users.
if you find some solution let us know

---

### Post by ephmanjmm on 2010-02-19
You might try this:

[http://www.postfix.org/rewrite.html#canonical](http://www.postfix.org/rewrite.html#canonical)

---

### Post by matthinckley on 2010-02-23
thanks for the responses.

I don't know what I was thinking.. putting both servers as the same domain won't work for testing for me because I cant send mail from the zimbra server to the main server as the zimbra server thinks everything for its domain should be internal to that server.. 

I'm going to use a test domain for the testing on the zimbra server and use the .forward file on the main server to copy mail over there..

I did find out that in the .forward file you can escape the same email address to keep it from recursively looping

ie for mail account [email]user1@mainserver.com[/email] .forward would contain

```
\user1
user1@testserver.com
```

this keeps it from reading the .forward file the second time around :)

---

