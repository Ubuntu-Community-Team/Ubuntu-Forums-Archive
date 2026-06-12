---
title: "logcheck rules"
date: 2007-06-07
forum: Server Platforms
---

### Post by sickdude on 2007-06-07
Hi all,

Ok i was advised to use logcheck to monitor my system. So i installed it last night, this morning my mailbox was full of logcheck e-mails. So i'm trying to figure out what rules i should write, and of course what the syntax should be :-P

so i was wondering, if you are using logcheck, what rules do you guys have and why?

Lets call this the logcheck rules thread :-P

---

### Post by Mr. C. on 2007-06-07
The good news is that you are receiving the reports you want.

The bad news is that you are going to have to start the learning process of what is important *to you* and what is not.  The rules are already written

Each service (http, ssh, etc.) will have its own log entries; you will have to start to become familiar with those if you are security conscious.

There is no single, simple answer to your question.  Start your learning here:

[INDENT]   [http://logcheck.org/](http://logcheck.org/)
   [http://logcheck.org/docs/](http://logcheck.org/docs/)[/INDENT]

MrC

---

### Post by sickdude on 2007-06-07
Ok well im not all that good in regular expressions so this is kinda hard.

And i think that the documentation isnt all that good. 

And there should be some default rules that you could use, these are my 2 cents on logcheck.

So anyway if somebady has some tips on making these rules please let me know so it isnt going to cost me a year to learn it. :-P

---

