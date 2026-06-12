---
title: "So much memory is lost... or maybe not?"
date: 2010-08-10
forum: The Cafe
---

### Post by der_hede on 2010-08-10
You don't believe the "free" command? It says: your system (without Buffer/Cache) is consuming more than a gig?

You run some "ps aux"/"ps -eF"/… and can't believe all those tiny pits are "more than a gig"? There's only firefox with >100mb, this is not plausible?

Test it:
sum=0; for i in $(ps -eo rss); do sum=$[$sum+$i]; done; echo $sum

I didn't believe either. I summed up (mental arithmetic) the bigger ones... ~200mb. free said: 700MB... wow...
But this way I know now: Yes. 700MB is indeed plausible. And without shared libs it would be "more than a gig" :-P

---

### Post by RiceMonster on 2010-08-10
ok.

---

### Post by regala on 2010-08-10
> **der_hede said:**
> You don't believe the "free" command? It says: your system (without Buffer/Cache) is consuming more than a gig?

You run some "ps aux"/"ps -eF"/… and can't believe all those tiny pits are "more than a gig"? There's only firefox with >100mb, this is not plausible?



the amount of "free" memory is given by total - (buffers + cache + apps); so this is  normal because your sum does only sum apps contributed memory. buffer and disk caches are seldomly evicted as it is sure people prefer to preserve small access disk than memory consumption.  (memory serves to be consumed, not to be checked for useless emptiness).

-- 
Mathieu

---

### Post by Mahngiel on 2010-08-10
> **regala said:**
> memory serves to be consumed, not to be checked for useless emptiness.

I like this quote.  Too many people are concerned with having "free" memory, when there really is no point for it.  Free ram is not on par meaning-wise with free disk space.

---

### Post by der_hede on 2010-08-11
Is my english that bad? I've written "without Buffer/Cache".

Linux - like every other modern system (yes, even Windows) - tries to use all available memory. Windows even swaps out apps if there's much more ram used by cache/buffers than linux does. That's a fact most people know.

But with the free command there's some "-/+ buffers/cache"-line. There you can see the used mem _without_ buffers+cache. That's what I meant.

Second: My Ubuntu AMD64 system uses >500MB right after boot while other systems, like a debian one, uses only a little more than 100MB. So I searched _why_ this is the case. I took a look into all those RSS values from "ps aux" and mentally summed them up. And I couldn't believe that all those small values are that much all in all / collectively.
The thing is: It seemed for me this is not plausible, because there's no RSS value above 100MB right after boot but there's >500MB used.
I don't know how to call it in englisch, in german it would be "die Masse machts". Maybe an english translation would be something like "losses add up". I mean: there are so many 1MB processes, in sum these are consuming much more ram as I assumed at first view.

I started this thread for all those people having the same worries...


Btw: the sum-up of RSS can be smaller _and_ bigger than "-/+ buffers/cache" used ram from the free-command (i.e. the RAM used by Apps).
RSS doubles shared libs for every process. So this sum-up can be bigger. On the other hand not every ram used by a process is counted in RSS (Wikipedia is wrong here, e.g. page-table and task_struct is missing). Finally kernel space counts in "-/+ buffers/cache" used ram but is not summed up with rss. So this sum-up can also be smaller.
So even if this sum and used ram is on paar, this means your system already benefits from shared libs :-).

---

### Post by K.Mandla on 2010-08-11
This python script might be of interest to you.

[http://kmandla.wordpress.com/2009/08/29/looking-close-at-memory-usage/](http://kmandla.wordpress.com/2009/08/29/looking-close-at-memory-usage/)

For my own part, regardless of the consensus on whether or not memory should be in use or free, a program or an operating system that sits heavily in memory suggests bloat. But that is by no means the only answer.

---

### Post by ubunterooster on 2010-08-11
> **regala said:**
> memory serves to be consumed, not to be checked for useless emptiness
Mathieu

Agreed
```
ubunterooser@ubunterooster-server:~$ free
             total       used       free     shared    buffers     cached
Mem:       7674836    6482028    1192808          0     209100    4590728
-/+ buffers/cache:    1682200    5992636
Swap:            0          0          0
ubunterooser@ubunterooster-server:~$ 
```

---

### Post by der_hede on 2010-08-11
> **K.Mandla said:**
> [http://kmandla.wordpress.com/2009/08/29/looking-close-at-memory-usage/](http://kmandla.wordpress.com/2009/08/29/looking-close-at-memory-usage/)

Thanks. A fine little piece of software. :-)

---

### Post by conundrumx on 2010-08-11
Free memory is wasted memory.

---

### Post by der_hede on 2010-08-11
> **conundrumx said:**
> Free memory is wasted memory.
That's right. But this is a different topic.
free mem vs. cache != used-(buffers+cache) vs. summed up RSS

---

