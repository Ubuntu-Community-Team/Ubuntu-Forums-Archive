---
title: "Exim4 not sending out all mails"
date: 2014-12-26
forum: Server Platforms
---

### Post by ruben17 on 2014-12-26
Hi all,

I set up Exim4 using the default Ubuntu tutorial, fast and simple.
I only wan to use it to send out mails, done by a local aplication.
When i test sending a email i can receive it fine, but when i send out 10 mails i only receive 3. Can anyone help me find out why?

I am new to Exim.

---

### Post by ruben17 on 2014-12-27
Sorry for the dubble post, the other mails are hold back in queue, how can i see why?

---

### Post by nerdtron on 2014-12-29
What is the source email and destination email?
What does the /etc/log/mail.log when you send emails?

If only "some" emails are received, and others are sent, that means sending is good. Do you have a spam filter active? or email send/receive limiting?

---

