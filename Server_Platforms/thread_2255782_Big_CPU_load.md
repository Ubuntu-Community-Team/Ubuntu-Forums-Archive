---
title: "Big CPU load"
date: 2014-12-07
forum: Server Platforms
---

### Post by niki85 on 2014-12-07
Hello,

I have big server cpu,
here is information, i guess need opitmize apache or ? how to do this ?
[IMG]http://s27.postimg.org/wasc3m4kj/cpu.png[/IMG]

Thanks.

---

### Post by tgalati4 on 2014-12-07
I don't see a problem.  Your apache service is only using 9% overall CPU, so technically, you could run 8 more web services.  Sometimes the load is not accurately represented.  Try performing some updates then a cold boot and check again.  Sometimes system background processes will throw the load off.  Is the web service slow?

You do have 1.5% in wait states, typically I/O-related, so check that your hard disks have good SMART status, with tied-down power connectors.

---

### Post by TheFu on 2014-12-07
Top isn't really a good way to determine server performance. A tool that can graph performance for 20-50 different things over 5 min, a day, a week, a month, 6 months would be much better. It helps to gather these stats before you need them, so when something odd happens, the graphs will show it.  Lots of tools do this stuff - munin, cacti, sysusage ... just off the top of my head.

I don't see anything terrible from the top data, but 1 point in time means nothing.

You appear to have about 10x too much RAM for the current workload - does that help?  If you are having page performance issues, time to fix the application, do smarter caching, compress the data, and use sprite-based images as needed inside the app to limit separate file downloads for buttons, etc.  If you want to profile a webapp - check out Zoompf.com - Billy is really smart and knows web performance AND web security - IRL, ask me about a live demo he did ... ;)

---

### Post by niki85 on 2014-12-08
> **TheFu said:**
> Top isn't really a good way to determine server performance. A tool that can graph performance for 20-50 different things over 5 min, a day, a week, a month, 6 months would be much better. It helps to gather these stats before you need them, so when something odd happens, the graphs will show it.  Lots of tools do this stuff - munin, cacti, sysusage ... just off the top of my head.

I don't see anything terrible from the top data, but 1 point in time means nothing.

You appear to have about 10x too much RAM for the current workload - does that help?  If you are having page performance issues, time to fix the application, do smarter caching, compress the data, and use sprite-based images as needed inside the app to limit separate file downloads for buttons, etc.  If you want to profile a webapp - check out Zoompf.com - Billy is really smart and knows web performance AND web security - IRL, ask me about a live demo he did ... ;)


Yes probably is app problem, i have before similar problem but need to be for sure this is not server problem, you suggest fix app ? can you suggest me how i can determine which file .php is problem ?

Thanks.

---

### Post by TheFu on 2014-12-08
> **niki85 said:**
> Yes probably is app problem, i have before similar problem but need to be for sure this is not server problem, you suggest fix app ? can you suggest me how i can determine which file .php is problem ?

Thanks.

You haven't stated what the issue is AND backed that up with data yet.  So - what, exactly, is the issue?  The CPU load shown is not an issue, IMHO.

---

### Post by niki85 on 2014-12-08
> **TheFu said:**
> You haven't stated what the issue is AND backed that up with data yet.  So - what, exactly, is the issue?  The CPU load shown is not an issue, IMHO.

cpu is 50% this is normal with this traffic ? before i have much more traffic and cpu not go above 20% this was other app but this is similar operation.
[http://pasteboard.co/2hC1Apc6.png](http://pasteboard.co/2hC1Apc6.png)

---

### Post by TheFu on 2014-12-08
> **niki85 said:**
> cpu is 50% this is normal with this traffic ? before i have much more traffic and cpu not go above 20% this was other app but this is similar operation.
[http://pasteboard.co/2hC1Apc6.png](http://pasteboard.co/2hC1Apc6.png)

There is nothing "normal". You are assuming that we know **anything** at all about your system, your webapp, your db, your traffic, the average size of returned data, how much is dynamic and how much is static, caching .... we don't know anything.  We don't know anything about the hardware or networking involved either ... well, except that lots of RAM seems to be available.

Can you offer any more data about the system, app, architecture?

---

### Post by nerdtron on 2014-12-08
How many pageviews does your website have? I don't think 1.34 is high enough, especially we don't even know how many cores it has.
You might wanna take a look at you apache logs on how many page views/ visit/crawlers are accessing the site. And also historical performance data might be helpful like since when did this server have a "high cpu usage"

---

### Post by niki85 on 2014-12-08
Intel Xeon E3 1225v2
4 c/ 4 t
3.2 GHz+
32 GB RAM HD 2 x 2 TB SATA

9000 views per day

---

### Post by TheFu on 2014-12-08
Application architecture?
languages, DBs, amount of data, average page side, average static data/pg, where is the DB running - same box, different box, networking, caching, reverse proxy use, HA stuff?  Can you please provide some of that data as requested before?

We really do want to help.  9k pgs is nothing in an hour for a 1CPU box even for the worst java or Ruby web app ... unless the pages are really 3 hr streaming videos. The image of 2Mbps bandwidth doesn't lead to streaming video, but I dunno. "Need the info."

Tuning a server has thousands of aspects and giving 1 thing to do isn't effective use of your time or ours.  MORE INFORMATION ABOUT THE APPLICATION, PLEASE.  This will help us point you towards the most likely, and most helpful things to research.  In the end, performance comes down to
* CPU load
* RAM utilization
* swapping (virtual memory management)
* Disk I/O
* Network I/O
* failing hardware issues
* attacks which produce DoS
and ways to make the most for each of those things within the application architecture, hardware, networking, available.  So ... I provided some performance monitoring tools earlier. Did you install 1 of those and start capturing data?  Are there any charts for the last 24 hrs yet?  

These charts are less important than providing us an overview of the application architecture. That is really what we need first.

---

