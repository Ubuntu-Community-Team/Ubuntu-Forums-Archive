---
title: "Unpredictable response time"
date: 2009-07-19
forum: Server Platforms
---

### Post by Sitix on 2009-07-19
Hello,

I happen to have a rather strange problem. I run a server that hosts my mother's company's website. However, for some reason it has incredibly unpredictable response times. In fact, sometimes it just takes a fraction of a second to load a page, and another time it takes up to 5 or 10 seconds. At digital rush-hour, only about 25 people are on the website. It is a simple website, the MySQL queries aren't all that complicated, the only thing that I think might slow things down a little, is a statistics system that tends to take up a lot of space. However, I empty the statistics every now and then as well.

I have been checking the load avarages, but those haven't changed in the meanwhile. The RAM is about 300 out of 1000MB, so that seems okay as well.

I'll copy the specs:
Kernel Version	2.6.24-24-generic (SMP)
Distro Name	 Ubuntu 8.04.2
Intel(R) Celeron(R) M CPU 530 @ 1.73GHz
1024MB RAM
And it doesn't use any swap.

In other words, I really don't know where to look for the problem. I run Apache2, php5... more or less a standard LAMP configuration.

Can anybody help me out?

Thanks in advance!

---

### Post by windependence on 2009-07-20
Can we take a look at the site?

How is it being hosted, DSL? Cable? T1?, and what ISP are you using?

If I know what the URL is, I can run some tools to see where the delay is, that way we can eliminate things like ISP or internet connections or possibly network problems.

-Tim

---

