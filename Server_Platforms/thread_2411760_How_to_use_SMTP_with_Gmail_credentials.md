---
title: "How to use SMTP with Gmail credentials"
date: 2019-02-03
forum: Server Platforms
---

### Post by programercek on 2019-02-03
Hi,

I got:[CENTER][COLOR=#333333][FONT=&quot]expected response code 250 but got code "530", with message "530 5.7.0 Must issue a STARTTLS command first. c18sm4433898wre.32 - gsmtp "

I used tutorial: [/FONT][/COLOR][/CENTER][https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp](https://easyengine.io/tutorials/linux/ubuntu-postfix-gmail-smtp)      and this works only for gmail. 
I want to use differents SMTPs from my server.
Gmail, my mail.domainname.com, and maybe another providers...

How to do this?

---

### Post by barroncm on 2019-02-04
Try this one, looks like the page you were using missed a couple steps.
[https://www.howtoforge.com/tutorial/configure-postfix-to-use-gmail-as-a-mail-relay/](https://www.howtoforge.com/tutorial/configure-postfix-to-use-gmail-as-a-mail-relay/)

You are missing a MTA(like Postfix) the above was very simple and easy to do.
Im not sure about using more than one smtp at a time though.

---

