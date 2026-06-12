---
title: "Slow performance in Site"
date: 2014-07-20
forum: Server Platforms
---

### Post by Ri_CatB_Support on 2014-07-20
Hi,

We have the business website, nowadays users are complaining that there was slow perfomance in a site.

This application is hosted in ubuntu in below configuration:

Ubuntu version: 10.04LTS
Database: Postgresql

While analysing the issue, we found there are many incoming connections are coming when the issue occurs.

Using the command: netstat -plan|grep :80|wc -l

When this values are getting reduced then performance of the site is working fine as expected, but often we are facing this slow performance issue.

We have tried increasing the maxclient value in prefork worker module to 350 as below, but there is no use.

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          350
    MaxRequestsPerChild   0
</IfModule>

Current running Apache version:
Server version: Apache/2.2.14 (Ubuntu)

Could you plaese anyone help me how to overcome from this issue, what action required to increase the perfomance.

Why there are many incoming connections are falling during that point of time only. 
Your help on this regards will be highly appreciable one.

Thanks in advance!

Regards,
Prakash

---

### Post by deadflowr on 2014-07-20
Thread moved to Server Platforms

---

### Post by TheFu on 2014-07-20
There is no way for us to know why inbound connections occur to a random server on the internet from here.  It is especially hard without any data about the sort of app involved, tools involved, overall system architecture, etc.

Could it be a DoS attack? Or perhaps the website has been featured on a blog or weekly podcast?

I would throw new, bigger, faster, hardware at the problem - especially if the server is 4 yrs old.  Newer servers are MUCH more capable and will need less power, less cooling, and less physical space to do the same job.  I'd split the DB server off and put that on different hardware.

Do you have any long term system performance monitors running that can pinpoint the root cause?  CPU, memory, network I/O, disk I/O?  Looking over the data for the last year would provide insight into the issue. Was it a gradual increase?

Also - do the log files show any issues besides more connections?  Failing hardware, disk access problems, anything else?

Do you redirect bogus connections using firewall rules or block abusive users completely or does everyone in the world automatically get a full connection to the webapp? How hard would a website redesign be to prevent excess DB transactions for unimportant people? Can a proxy server run a micro-cache to reduce DB hits for simple browsing before any transactions are needed?  nginx has a micro-cache facility.

Finally my last remaining 10.04 server is being migrated to new hardware and 14.04 in the next few months, before 10.04 support ends in early 2015.  It is time to put that into your budget NOW if there will be a delay until 2015 on your side.

Hope this was helpful in some way.  It is hard to diagnose issues from 5 sentences. I'm sure you understand.

---

### Post by CharlesA on 2014-07-20
+1 to offloading the db if you can.

I think TheFu covered most of what can be done.

Are you running a caching server or CDN or anything like that in addition to Apache? Are you hosting mostly static content or is the site dynamic?

---

### Post by SeijiSensei on 2014-07-21
Have you checked that all queries have proper indexes?  SELECTs that use joined tables will often need custom indexes to execute quickly.

Use the ANALYZE and EXPLAIN commands in PostgreSQL to evaluate the queries in the application.

Have you looked into tuning the performance of PostgreSQL?  See these:

[https://wiki.postgresql.org/wiki/Performance_Optimization](https://wiki.postgresql.org/wiki/Performance_Optimization)
[https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server](https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server)
[http://www.postgresql.org/docs/9.2/static/performance-tips.html](http://www.postgresql.org/docs/9.2/static/performance-tips.html)

---

