---
title: "need help with performance rails, apache"
date: 2007-06-03
forum: Server Platforms
---

### Post by nephish on 2007-06-03
hello there all,

we are using a dell poweredge server. has 4 processors, 8 gig ram, and 6 hard drives in raid 5.

Now, our site really slows down a lot when there are more than about 30 folk connected at a time ( as shown in gkrellm). However, the processors are not bogged down, the network is not bogged down, and we are only using half of the RAM. My question is, where should i look for another bottleneck ? 

We are using rails in production mode, apache server,  and mysql. ubuntu 6.10

any ideas?

thanks

---

### Post by Brazen on 2007-06-03
> **nephish said:**
> hello there all,

we are using a dell poweredge server. has 4 processors, 8 gig ram, and 6 hard drives in raid 5.

Now, our site really slows down a lot when there are more than about 30 folk connected at a time ( as shown in gkrellm). However, the processors are not bogged down, the network is not bogged down, and we are only using half of the RAM. My question is, where should i look for another bottleneck ? 

We are using rails in production mode, apache server,  and mysql. ubuntu 6.10

any ideas?

thanks

Did you set up rails to use mod_fcgid?

Also, in a production environment, you really should keep your database server on it's own server.  This is true for Oracle, MS-SQL, Postgresql, and MySQL.

Do you have the 2nd edition of the Pragmatic Programmer's Agile Web Development on Rails?  Their is a section in there about Production deployments which talks about things to do and to avoid in regards to performance.  And many of those things have changed since the first edition of the book.  That is probably going to be the most accurate information for you.  However if you have not set up rails to use mod_fcgid, then it is expected that you would have performance problems running on Apache, so just fixing that could be all you need.

PPAWDoR actually says to stay away from running rails on Apache and instead use Apache to proxy to a Mongrel or Lighttpd server.  Personally, I'm not sure I agree with that (and that is even a reversal from the first edition).  I've been using rails with Apache and fcgid with no problems

---

### Post by nephish on 2007-06-03
ok, i will get the second book. i have the first edition now. 
we do have rails and mysql on the same server.
we are using fcgid

my employer will not like the seperate machine advice. But, suppose i can sell him on it, should the more powerfull server be the MySQL server or the Apache server ?

thanks

---

### Post by Brazen on 2007-06-03
> **nephish said:**
> ok, i will get the second book. i have the first edition now. 
we do have rails and mysql on the same server.
we are using fcgid

my employer will not like the seperate machine advice. But, suppose i can sell him on it, should the more powerfull server be the MySQL server or the Apache server ?

thanks

usually the sql server needs to be more powerful, but this is HIGHLY dependant on your application.

---

### Post by elst on 2007-06-04
To clarify, you don't necessarily need separate machines for "light" workloads (which actually covers many applications), especially with such a high spec server. One important resource is disk I/O, moving a busy database off to a dedicated machine definitely helps if that becomes a bottleneck. DBs can also hit a CPU hard when an  intensive query comes up.

I've had less luck with Rails and Apache/FastCGI, although it's been a few months now since I tried it. I get the impression that the code in this area isn't very actively developed or maintained.

---

