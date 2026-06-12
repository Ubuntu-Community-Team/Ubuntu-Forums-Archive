---
title: "Why is Apache running so many processes? Excessive RAM here?"
date: 2011-05-14
forum: Server Platforms
---

### Post by rainleader on 2011-05-14
I notice Apache is running multiple processes on my LAMP server (ubuntu 10.10). I'm just running a Wordpress site with MySQL as a database. It seems like www-data is running apache2 more than it should (using too much memory too), am I correct:

 ```
   ID        Owner        Size        Command   
    31200     www-data     251236 kB     /usr/sbin/apache2 -k start
    20678     www-data     250948 kB     /usr/sbin/apache2 -k start
    25781     www-data     248888 kB     /usr/sbin/apache2 -k start
    31045     www-data     248844 kB     /usr/sbin/apache2 -k start
    19926     www-data     246480 kB     /usr/sbin/apache2 -k start
    20749     www-data     239380 kB     /usr/sbin/apache2 -k start
    32616     www-data     238632 kB     /usr/sbin/apache2 -k start
    8846     mysql     238128 kB     /usr/sbin/mysqld
    24178     www-data     234228 kB     /usr/sbin/apache2 -k start
    32618     www-data     232344 kB     /usr/sbin/apache2 -k start
    32615     www-data     232204 kB     /usr/sbin/apache2 -k start
    19805     root     208156 kB     /usr/sbin/apache2 -k start
```

---

### Post by SeijiSensei on 2011-05-14
The number of concurrent listeners is controlled by various directives in the httpd.conf file.  Take a look at things like "StartServers".

That said, the listeners largely use shared memory components.  Each individual child process doesn't use much unique memory of its own.

---

### Post by Lars Noodén on 2011-05-14
Take a look at [StartServers](http://httpd.apache.org/docs/2.2/mod/mpm_common.html#startservers), [MaxSpareServers](http://httpd.apache.org/docs/2.2/mod/prefork.html#maxspareservers) and [MinSpareServers](http://httpd.apache.org/docs/2.2/mod/prefork.html#minspareservers).  By changing those, you can adjust the number of processes Apache uses.

---

### Post by rainleader on 2011-05-14
Hmm... thanks. I'll try tweaking those settings -- I'm worried about running out of memory.

---

### Post by dtfinch on 2011-05-14
Some of that memory is shared (that one running as root forks itself to create the other www-data processes, but the actual memory isn't copied unless modified), so it's overreported, but I'm used to seeing it report about 25mb per process, rather than 250mb.

I do have doubts that webmin is reporting to correct size. If you run "ps -A v", the RSS column should have the amount of memory (in kb) actually being used (though still not subtracting shared memory). If webmin is reporting the DRS size instead, that would inflate the results considerably.

Edit/Add:
Yeah, it appears to be misreported. I don't have webmin installed to test, but looking at sysv-lib.pl in webmin's "Running Processes" module, it's using the "VSZ" output from ps, which is comparable to the "DRS". To give an example of how off that is, on my own system with 4gb total, 3gb free, and no swap used, RSS from all processes adds up to 980mb, while VSZ from all processes adds up to over 13gb.

---

### Post by rainleader on 2011-05-14
> **dtfinch said:**
> Some of that memory is shared (that one running as root forks itself to create the other www-data processes, but the actual memory isn't copied unless modified), so it's overreported, but I'm used to seeing it report about 25mb per process, rather than 250mb.

I do have doubts that webmin is reporting to correct size. If you run "ps -A v", the RSS column should have the amount of memory (in kb) actually being used (though still not subtracting shared memory). If webmin is reporting the DRS size instead, that would inflate the results considerably.

Edit/Add:
Yeah, it appears to be misreported. I don't have webmin installed to test, but looking at sysv-lib.pl in webmin's "Running Processes" module, it's using the "VSZ" output from ps, which is comparable to the "DRS". To give an example of how off that is, on my own system with 4gb total, 3gb free, and no swap used, RSS from all processes adds up to 980mb, while VSZ from all processes adds up to over 13gb.

Wow! Thanks for looking into that and providing such a detailed response. I was worried about massive memory overallocation to Apache but you've solved that. Very interesting to hear the difference between the two outputs -- I could definitely see others being confused by this as well.

Thanks again, have a great weekend!

---

