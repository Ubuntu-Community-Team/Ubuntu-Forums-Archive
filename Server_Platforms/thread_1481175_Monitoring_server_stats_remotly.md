---
title: "Monitoring server stats remotly"
date: 2010-05-12
forum: Server Platforms
---

### Post by xkaliburx on 2010-05-12
I didn't setup our old system but that server has since been retired due to hardware failure, but we have some new webervers, and a new postgtres database server in place which I need monitoring.

Some items include database size, transactions per second, io stats, memory monitoring, or as the DBA put "anything I can get".  We had used CACTI in the past for these items, but I didn't do the setup and sondering if that is what is recommended, or something else.  I am looking at groundwork open source which include nagios, etc. but figured I would consult the uforums since all these servers are running userver 9.x and 10.x

Thanks for any and all suggestions.

---

### Post by arrrghhh on 2010-05-12
Nagios is probably going to be my recommendation, just because it's so extesnible and configurable, you can probably get everything your DBA wants and then some.

---

### Post by xkaliburx on 2010-05-12
Yea, groundwork uses the built-in nagios engine but I remember a while back the config was not user friendly at all!  I got the zenoss link from the Ubunutu server page so doing some reading on that as well.

Thanks.

---

### Post by arrrghhh on 2010-05-12
Nagios... isn't so friendly.  But very powerful, if you do take the time to learn it...  That's the tradeoff.  There's some packages you can buy, but then you're trading your hard-earned cash for time.

---

