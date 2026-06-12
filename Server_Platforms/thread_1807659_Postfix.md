---
title: "Postfix"
date: 2011-07-19
forum: Server Platforms
---

### Post by amanda099 on 2011-07-19
I'm trying to install Postfix on my Ubuntu 10.4 using
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
 
I'm following the instruction closely. When I test my default installation using telnet localhost 25, I get the following:
 
telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
 
Please help me out ! What have I done wrong ?
 
Amanda

---

### Post by Dry Lips on 2011-07-19
I'm not sure what you're doing wrong, but here is an *excellent* 
tutorial about setting up a mail server:
 
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

PS. I've asked the mods to move this thread for you, as you are
more likely to get an answer that will solve your problem in the 
"server" section of this forum...

---

### Post by Dry Lips on 2011-07-19
> **amanda099 said:**
> I'm trying to install Postfix on my Ubuntu 10.4 using
[https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)
 
I'm following the instruction closely. When I test my default installation using telnet localhost 25, I get the following:
 
telnet localhost 25
Trying ::1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.
 
Please help me out ! What have I done wrong ?
 
Amanda

From the tutorial you used:

*(if that doesn't work, check to see if postfix is running) *
```
sudo postfix status
```Did you check if postfix is up and running?

---

### Post by amanda099 on 2011-07-19
Thanks for your response Dry Lips !
 
Yes, Postfix is running. When entering sudo postfix status, I got this: 
postfix/postfix-script: the Postfix mail system is running: PID: 1094
 
And Im reading the url you suggested
[[COLOR=#000000]http://flurdy.com/docs/postfix/[/COLOR]]("http://flurdy.com/docs/postfix/")

---

### Post by Dry Lips on 2011-07-28
So how is your mailserver coming along... Is it up and running?

---

