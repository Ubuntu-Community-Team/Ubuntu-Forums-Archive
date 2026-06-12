---
title: "Ubuntu 10.04"
date: 2010-03-24
forum: Server Platforms
---

### Post by Windows_ on 2010-03-24
Ubuntu server 10.04 64 bit eats too much RAM!!!

```

# free 

            total      used      free       shared      buffers   cached
Mem:       2057136     644932    1412204    0           6276      27508

-/+ buffers/cache:     611148    1445988
Swap:      3903752          0    3903752

```

It is on my Xeon server. It's after mini install without any programs - no dns, no apache, no php etc... 

640 mb for what? It is too much !!! I'm going to try debian instead on my production server.

---

### Post by jrssystemsnet on 2010-03-24
"Used" includes filesystem cache.  You're upset over nothing.

You are by no means the first user to badly misunderstand how memory usage works; see [http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html) and [http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html](http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html) for two of the first decently written answers I could find to this question.

This kind of thing gets asked a LOT, but the short answer is "free RAM is wasted RAM, that's why so much of yours is used."

---

### Post by KB1JWQ on 2010-03-24
Once again jrssystemsnet is spot on.

I've got 8 gigs on this laptop.  free here says:

             total       used       free     shared    buffers     cached
Mem:       8053916    1737812    6316104          0      62540     726264
-/+ buffers/cache:     949008    7104908
Swap:      6385796          0    6385796

Two firefox windows and a pair of terminals don't take up almost 2 gigs, I promise. :-)

---

### Post by Windows_ on 2010-03-24
> **jrssystemsnet said:**
> "Used" includes filesystem cache.  You're upset over nothing.

You are by no means the first user to badly misunderstand how memory usage works; see [http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html) and [http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html](http://sourcefrog.net/weblog/software/linux-kernel/free-mem.html) for two of the first decently written answers I could find to this question.

This kind of thing gets asked a LOT, but the short answer is "free RAM is wasted RAM, that's why so much of yours is used."

Ok, thank you very much for your links.

---

### Post by Slim Odds on 2010-03-24
> **Windows_ said:**
> Ok, thank you very much for your links.

It's so darned funny that this topic comes up with all operating systems.

[http://www.osnews.com/story/22896/Windows_7_Memory_Usage_FUD_Explained](http://www.osnews.com/story/22896/Windows_7_Memory_Usage_FUD_Explained)

It's not really funny. It's a huge waste of time and space to explain it over and over again.

---

### Post by jrssystemsnet on 2010-03-24
I actually first saw this coming up MANY years ago when Linux fans (who have, for reasons which escape me, always liked to claim "BSD is dying!") derided FreeBSD for "using all the free RAM".

At the time, Linux didn't do filesystem caching very well (maybe even not at all?  I forget), while FreeBSD did much, much more aggressive filesystem caching, so a FreeBSD system which had been up for a while would have much less "free" RAM showing up than an otherwise similar Linux system.

Of course, on the gripping hand, there really *are* differences between the amount of code and the efficiency of memory usage between different operating systems... it's just not as easy to analyze it as people think. :popcorn:

---

### Post by KB1JWQ on 2010-03-24
I'm not entirely clear as to the root cause, but lately there've been a spate of questions like this cropping up all over the place, culminating in [http://tech.slashdot.org/story/10/02/18/0429258/86-of-Windows-7-PCs-Maxing-Out-Memory?art_pos=3](http://tech.slashdot.org/story/10/02/18/0429258/86-of-Windows-7-PCs-Maxing-Out-Memory?art_pos=3) (which was then debunked in [http://news.slashdot.org/story/10/02/21/2329249/Windows-7-Memory-Usage-Critic-Outed-As-Fraud](http://news.slashdot.org/story/10/02/21/2329249/Windows-7-Memory-Usage-Critic-Outed-As-Fraud))

---

