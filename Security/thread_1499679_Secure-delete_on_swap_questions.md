---
title: "Secure-delete on swap questions"
date: 2010-06-02
forum: Security
---

### Post by Troll 10.04 on 2010-06-02
I would like to know on what conditions does Ubuntu write to swap?  

I am obviously an end-user only and I have been playing with sswap on secure-delete.  I would like to know if before I read a sensitive document, for example, I turn off swap, and then turn it on once I am finished, is there any reason for there to be an account of the document in swap?  Does RAM write to swap?  Under what conditions?  

Thanks,

---

### Post by Bachstelze on 2010-06-02
> **Troll 10.04 said:**
> I would like to know on what conditions does Ubuntu write to swap?  

I am obviously an end-user only and I have been playing with sswap on secure-delete.  I would like to know if before I read a sensitive document, for example, I turn off swap, and then turn it on once I am finished, is there any reason for there to be an account of the document in swap?  Does RAM write to swap?  Under what conditions?  

Thanks,

AFAIK there is no precise reason that defines when the OS writes in swap and when it doesn't, so if you're really that concerned, you should always assume your document did get written in swap.

If you don't want traces of your document to remain, you can for example make a simple shell script that will physically erase all data in the swap partition (since swap partitions are generally small, this shouldn't take too much time), and have it run either as a cron job or manually (or both).

---

### Post by bodhi.zazen on 2010-06-02
Here is a nice discussion on swap ":

[http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space](http://www.linux.com/news/software/applications/8208-all-about-linux-swap-space)

You will get a lot of opinions on swap, and really the answer is to monitor your swap use, if any.

IMO, on the vast majority of desktops, assuming you have 2 Gb RAM, you can almost always turn swap off entirely, which is what I would advise.

Many people have 3-4 Gb RAM.

So:

1. How much RAM do you have?

2. Are you even using Swap ?

Use free -m to see your RAM use.

[http://www.cyberciti.biz/faq/linux-check-memory-usage/](http://www.cyberciti.biz/faq/linux-check-memory-usage/)

Ste line +/- buffers is the most important for RAM, and the swap line for swap.

If you are not using swap, you can probably turn it off (do not mount the swap partition) an /or decrease the swappiness (to 0 - 10).

If you are not using swap, you do not need to worry about it.

---

### Post by Troll 10.04 on 2010-06-03
> **Bachstelze said:**
> AFAIK there is no precise reason that defines when the OS writes in swap and when it doesn't, so if you're really that concerned, you should always assume your document did get written in swap.

We are talking about a computer.  A computer is incapable of doing anything random.  There must be conditions upon which the OS writes to swap.

---

### Post by HermanAB on 2010-06-03
Encrypt your swap.  Read the 'swapon' man page.

---

