---
title: "Local mail server for testing purpose"
date: 2010-12-10
forum: Server Platforms
---

### Post by kuanjian on 2010-12-10
Hi there,
I'm relatively new to Linux and I'm still learning. Right now, I'm trying to figure out how to setup a local mail server for internal testing on my php development work. For example if I sent an email using php script to [email]someone@localhost.com[/email]. I should be able to check the mailbox of 'someone' either in Outlook or SquirrelMail.

I have done some reading about this. All I know is that I need Postfix with Courier. But I just don't know to get it working.

Any help please?

---

### Post by garryconn on 2010-12-11
Have you read the Postfix section on the Ubuntu Server Guide? 

-- [https://help.ubuntu.com/10.10/serverguide/C/postfix.html](https://help.ubuntu.com/10.10/serverguide/C/postfix.html)

---

### Post by HermanAB on 2010-12-11
It takes about 20 minutes to install Citadel, using the Easy Install script:
[http://citadel.org](http://citadel.org)

Unlike Postfix, it Just Works (TM).

---

### Post by kuanjian on 2010-12-11
I have been following the documentation at [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) but I'm getting no way.

I try to do it from fresh installation again and see how it goes first.

Thanks garryconn and HermanAB for replying.

---

