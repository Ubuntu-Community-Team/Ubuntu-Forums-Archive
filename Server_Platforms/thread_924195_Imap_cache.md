---
title: "Imap cache"
date: 2008-09-19
forum: Server Platforms
---

### Post by ub007 on 2008-09-19
Hi,

I have written a test script to laod test my imap server.Inspite of running 500 threads in a very short interval,the server response is very good...as if there is hardly any load on it.I was just wondering whether IMAP is caching the previous requests,if so the subsequent requests wouldnt put any load on the server.Could anyone guide me on this.Does IMAP employ a cache and if so how do i disable it?I'm running courier-imap

Cheers
David

---

### Post by MJN on 2008-09-19
This will likely depend on exactly what your script is doing, and therefore what it is ultimately trying to measure.
 
I would recommend having a look at [http://www.courier-mta.org/mbox-vs-maildir/](http://www.courier-mta.org/mbox-vs-maildir/) where you will find some test scripts that perform a variety of IMAP message manipulations (including searches) with which to form a basis of benchmarking whatever aspect of system performance you are trying to measure.
 
Might you be underestimating the performance of modern hardware for such tasks? Or were the results seemingly too good to be true?
 
Margew

---

### Post by ub007 on 2008-09-20
--------------------------------------------------------------------------------

> This will likely depend on exactly what your script is doing, and therefore what it is ultimately trying to measure.

I am trying to measure the mail retrieval time.Each thread downloads mail selected at random.So by starting a huge number of them,i'm hoping to stress the server to a point of crashing.
The graphs i got show interesting results.To begin with i had sent 2000 mails to the inbox using a script.Within 3 minutes of starting the test ,the retrieval time & overall response time increased drastically.After 2 more minutes,the times reduced and it was back to normal.At this point i noticed from my thunderbird interface that most of the mails were in a 'read' state.So is i assume the load was high when there were unread mails...so may be IMAP is caching the mail requests....
The graph i get is exactly an inverted 'V' shape.

---

