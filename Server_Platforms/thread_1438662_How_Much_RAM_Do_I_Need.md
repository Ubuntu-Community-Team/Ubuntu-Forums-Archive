---
title: "How Much RAM Do I Need?"
date: 2010-03-25
forum: Server Platforms
---

### Post by cusinndzl on 2010-03-25
I have an Ubuntu Server 9.10 running LAMP, PostgreSQL Database Server, ProFTPD, and SSH. It has a 2.4GHz Pentium 4 CPU and I currently only have 512MB of RAM for it. 

How much RAM do I need? I get about 30 unique visitors a day and it's a Wordpress blog.

---

### Post by cdenley on 2010-03-25
> **cusinndzl said:**
> I have an Ubuntu Server 9.10 running LAMP, PostgreSQL Database Server, ProFTPD, and SSH. It has a 2.4GHz Pentium 4 CPU and I currently only have 512MB of RAM for it. 

How much RAM do I need? I get about 30 unique visitors a day and it's a Wordpress blog.

For 30 visitors on a blog, I think 512MB of memory is plenty for a server without a GUI.

---

### Post by KB1JWQ on 2010-03-25
Srsly.

However, RAM is cheap; if it makes you feel better, get more.

Are you currently hitting a RAM ceiling?

---

### Post by jrssystemsnet on 2010-03-25
> **cusinndzl said:**
> I have an Ubuntu Server 9.10 running LAMP, PostgreSQL Database Server, ProFTPD, and SSH. It has a 2.4GHz Pentium 4 CPU and I currently only have 512MB of RAM for it. 

How much RAM do I need? I get about 30 unique visitors a day and it's a Wordpress blog.At this level of traffic, you're probably fine.  At ten times this level of traffic, you're probably fine.

Check your swap usage to find out for sure.

```
you@box:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3962        702       3260          0        151        418
-/+ buffers/cache:        133       3829
Swap:        11609          0      11609

```In the example above, you know the box is doing OK for RAM because although it has several gigs of swap available, it isn't using any of it.

Note that this is a very primitive kind of testing: "throw it in the fire, then check it to see if it works".  Just looking at the swap usage right after you install the machine doesn't help much; what we're doing there is looking at swap usage on a machine that's already *in* production and getting normal usage.  But your machine is apparently already in normal usage, so that simple check should be helpful for you too. :)

Also note: small amounts of swap usage - say, less than 10M - don't really matter.  But once you start seeing significant amounts used, you really, really, really want more RAM if at all possible.

---

### Post by dudumomo on 2010-03-25
Yes indeed, you should try to check your swap.
But 512mb seems fine for your server.

If you want to install more services, I presume you will need 1gb instead.

---

### Post by hessiess on 2010-03-25
Its hardly worthwhile running a standalone server for a website that only gets 30 hits a day. though to answer the question, 512 meg is *plenty* for a server which has such a small amount of traffic. Assuming you are not bloating it with X11, its probably only using 100-200 meg of RAM.

For such a low traffic website, you would be better off using a shared hosting provider, then work on increasing the traffic to a decent level using search engine optimisation.

---

