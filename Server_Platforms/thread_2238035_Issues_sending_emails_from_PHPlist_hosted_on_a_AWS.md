---
title: "Issues sending emails from PHPlist hosted on a AWS server"
date: 2014-08-05
forum: Server Platforms
---

### Post by joshua-aarond on 2014-08-05
Hello! I have some experience working with a linux server, but I am new enough that I could have made a terrible newbie mistake.

I have set up an email server using Ubuntu 14.04, a LAMP stack, and PHPlist. Everything seems to be fine when I send out one or two emails, but if I try and send a lot the emails only go out a few at a time (about 200 an hour). I need the server to be able to handle our company's newsletters and autoresponders, which could be as much as 10,000 or more emails at a time.

I was able to see that the messages were in the Queue for Postfix, and I have tried to tweak some of the settings of postfix to see if I could increase the performance. So far it's a no go.

I have Postfix set up to send through Mandrill's STMP, which works fine for any of my test messages.

If anyone could give me any tips or pointers, or an idea of where I should be looking, that would be awesome.

---

