---
title: "[ask] why result from mailgraph and pflogsumm different?"
date: 2011-06-07
forum: Server Platforms
---

### Post by venol on 2011-06-07
helo, I have installed postfix with amavisd, spamassassin, and clamav on ubuntu 10.04 server, all works as well. But, when I test to send 2 messages from outside to my server, the report from mailgraph and pflogsumm is different. To avoid pflogsumm count twice from amavis, I have combine pflogsumm with preflog. And the result like this .

> 

root@mail:/home/venol# /usr/sbin/prepflog.pl -d today /var/log/mail.log | pflogsumm | more

Grand Totals
------------
messages

      2   received
      2   delivered

Host/Domain Summary: Message Delivery 
--------------------------------------
 sent cnt  bytes   defers   avg dly max dly host/domain
 -------- -------  -------  ------- ------- -----------
      2     1226        0     0.8 s    0.8 s  dodol.com

Host/Domain Summary: Messages Received 
---------------------------------------
 msg cnt   bytes   host/domain
 -------- -------  -----------
      2     1226   suhernak.com

Senders by message count
------------------------
      2   [email]root@suhernak.com[/email]

Recipients by message count
---------------------------
      2   [email]venol@dodol.com[/email]

Senders by message size
-----------------------
   1226   [email]root@suhernak.com[/email]

Recipients by message size
--------------------------
   1226   [email]venol@dodol.com[/email]

. . . ..



and I have setting on mailgraph with "ignore_localhost" in /etc/default/mailgraph to "true" to avoid mailgraph count twice from amavisd-new. But, I'm waiting until 10 minute, the graph not increase, what is problem??

[IMG]http://dl.dropbox.com/u/21180631/ru.jpg[/IMG]

somebody can help me please, :(

---

### Post by venol on 2011-06-10
somebody can help me please. n_n

---

### Post by venol on 2011-06-15
help! 
: (

---

