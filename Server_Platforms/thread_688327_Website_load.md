---
title: "Website load"
date: 2008-02-05
forum: Server Platforms
---

### Post by jonabyte on 2008-02-05
Hello,

I am about to start hosting a live site using Ubuntu Server 6.04.

The site will probably have 2,000 visits a month, maybe a bit more.

I am running this on a older computer 900mhz, 512mb ram.

The only thing I am not sure about is whether the site will hold up, are there any kind of testing that I can do ahead of time to see how well it does.

TIA

---

### Post by perfecttao on 2008-02-05
[http://www.opensourcetesting.org/performance.php](http://www.opensourcetesting.org/performance.php)

:)

---

### Post by KyleAnderson on 2008-02-05
Is 2000/month really accurate ? If so you should have no problem with that hardware. 
Even if that is 2000 visitors clicking on multiple things, a server with those specis have no problem serving even with dynamic pages. (67/day?)

---

### Post by Sporkman on 2008-02-05
You'll be fine. It will basically be idle all the time.

---

### Post by jonabyte on 2008-02-06
I assumed as much, but when you break down the stats to what actually might happen such as;

most visitors will come monday to friday 9am to 5pm, you are looking at 100 hits in 8 hours or 12 hits/hour.

I am more interested in learning the max that this server can handle, who knows maybe the site will take off and have more hits.

---

### Post by perfecttao on 2008-02-06
As mentioned on the performance tests site above, you could check

[http://jakarta.apache.org/jmeter/](http://jakarta.apache.org/jmeter/)

or 

[http://hammerhead.sourceforge.net/](http://hammerhead.sourceforge.net/)

:)

---

### Post by Sporkman on 2008-02-06
> **jonabyte said:**
> I assumed as much, but when you break down the stats to what actually might happen such as;

most visitors will come monday to friday 9am to 5pm, you are looking at 100 hits in 8 hours or 12 hits/hour.

I am more interested in learning the max that this server can handle, who knows maybe the site will take off and have more hits.

If you think about it, servers don't require a lot of power... Even if you grant a very generous second of computation time per page hit, there's 86,400 seconds per 24 hr period...

---

