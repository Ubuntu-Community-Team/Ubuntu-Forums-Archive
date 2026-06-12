---
title: "How do I set up my computer to send mail in php?"
date: 2006-01-12
forum: Server Platforms
---

### Post by stroopwafel on 2006-01-12
I am new to PHP and MySQL. I've installed it on my laptop (P2 366 MHz, **X**ubuntu Breezy) and it's working fine. 

QUESTION 1: What are the minimum requirements to make the php mail function work on my laptop running Apache 2? 

QUESTION 2: I heard some warnings about using Apache-2 with php: Should I remove it and install Apache-1? (if so, how do I install Apache-1, I tried "sudo apt-get install apache1", but that didn't work, so I just installed apache 2)

---

### Post by i_am_socket on 2006-01-13
I have had no problems with Apache2 and php.  As long as you have your php set up properly (ie, point it at the proper SMTP server) it'll send mail just fine; not to mention that it really has nothing to do with Apache2 anyway.

---

### Post by fakey1223 on 2006-04-26
To get the php mail() function working, I installed the sendmail package (doing so removed postfix).

---

