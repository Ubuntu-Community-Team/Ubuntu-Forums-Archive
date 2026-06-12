---
title: "Cannot open `/root/.mailrc': Permission denied"
date: 2010-08-13
forum: Server Platforms
---

### Post by stek_87 on 2010-08-13
Hi!

When I mail from root shell cli with the command:
echo test | sudo -u <localusername> mail -s "Testmail" [email]name@domain.com[/email]

I get error: Cannot open `/root/.mailrc': Permission denied

I have done some time with google and also read the "man mail" but I am unable to get rid of this message.

The email gets delivered fine, but I still want to know why I have to get this error..

someone got an idea?

---

### Post by scottuss on 2010-08-13
> **stek_87 said:**
> Hi!

When I mail from root shell cli with the command:
echo test | sudo -u <localusername> mail -s "Testmail" [email]name@domain.com[/email]

I get error: Cannot open `/root/.mailrc': Permission denied

I have done some time with google and also read the "man mail" but I am unable to get rid of this message.

The email gets delivered fine, but I still want to know why I have to get this error..

someone got an idea?

Put sudo right at the front of the command

---

