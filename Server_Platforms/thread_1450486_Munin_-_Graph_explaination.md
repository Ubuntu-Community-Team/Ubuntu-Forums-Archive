---
title: "Munin - Graph explaination"
date: 2010-04-09
forum: Server Platforms
---

### Post by dudumomo on 2010-04-09
Hi everyone !
I've just installed munin on my self hosted server.
Everything seems to work, but in fact I don't really know which graph is important and most of all I don't even know what some graph means.

I would like to create a page with some major graph to check everyday.

May be you can explain me what are these graph, what should I use and what can be an acceptable value for some of them:
1) Apache Process
2) Inode usage
3) IOstat (If I understood correctly this one, it is the input and output of my hard-drive, the lowest the best to insure the well flowing of my system
4) MySQL throughput (Is it better to check the MySQL queries instead ?)
5) Fork rate
6) VMstat (seems to be linked to the system load)
7) Available entropy
8) Load average (I know what is it, but do have any idea about a good value ? <2.5 ?)
9) File table usage
10) Inode table usage
11) Swap in/out (Should be 0 right ? or not very high ? I have a pic with this one to 1.2)
12) NTP timing statistics for system peer

Also, I saw my Memory usage quite high on my server, but in fact I have 1gb cached, so the graph tell me that my Memory usage is high, but in fact it's not...(Well I guess), any solution ? (Well I don't really mind to watch this graph in such a way, but still..)

And I guess monitoring my server by using daily and weekly graph is enough no ? Monthly graph will not really help me I guess except for seeing a large historic.

I know I'm asking a lot ;) but thanks for answering me !

---

### Post by minaev on 2010-04-09
> **dudumomo said:**
> I would like to create a page with some major graph to check everyday.
My usual daily peek at Munin reports normally stays on disk usage, MySQL connections, queries and slow queries, Nginx requests per second (mostly for the reasons of vanity), CPU usage (here I ponder for a little longer), load average and memory usage. All other things attract my attention only when there's a strange irregularity there.
> 3) IOstat (If I understood correctly this one, it is the input and output of my hard-drive, the lowest the best to insure the well flowing of my system
Depends on what the system is used for. Zero value isn't normal either :)
> 4) MySQL throughput (Is it better to check the MySQL queries instead ?)
I'd say yes, queries tell me more.
> 6) VMstat (seems to be linked to the system load)
Number of processes currently running and waiting for I/O to finish. Not too informative unless it hits the roof.
> 8) Load average (I know what is it, but do have any idea about a good value ? <2.5 ?)
Normally, LA should not exceed the number of CPUs. But it's much more convenient when it's significantly less than 2.
> Also, I saw my Memory usage quite high on my server, but in fact I have 1gb cached, so the graph tell me that my Memory usage is high, but in fact it's not...(Well I guess), any solution ?
How do you know it's high? Areas marked 'Unused' and 'Cache' are free memory.
> And I guess monitoring my server by using daily and weekly graph is enough no ? Monthly graph will not really help me I guess except for seeing a large historic.
There are situations when things change slowly and seen only on a monthly graph.

If you have more than one server, create an overview page that would show all servers on one graph. My 'Totals' page shows disk usage on root partitions of all servers, LAs, MySQL connections, Nginx RAM usage and number of processes.

---

### Post by dudumomo on 2010-04-09
Thank you so much for your explaination !
It's much clearer now !

About Ram, I misunderstood the graph. Actually I got a large amount of cached and unused memory.

And for my CPU it even shows the nice part (As I'm doing network computing for science, ie BOINC)

Hmm..last question, is it possible to separate the network graph by Upload and Download ?
Because as I am on an ADSL connection, my UP is 1MB and my DL 22MB, so now, the top of the graph (Upload part) is quite small and difficult to see clearly.
The download is not really a problem then.

So, I'll go with Disk usage, IO Stat, MySQL queries, eth0 traffic, CPU Usage, load average and memory usage.
Daily and weekly graph on 1 page should be good.

Thank you !

---

### Post by minaev on 2010-04-09
Have you been on [Munin Exchange]("http://muninexchange.projects.linpro.no/")? There's a number of readymade plugins for Munin, and there's a chance that one of them will do what you want.

---

### Post by dudumomo on 2010-04-09
Wow seems nice !
I will try to see how it works !
But there are a lot of great graph !

Thank you !

---

