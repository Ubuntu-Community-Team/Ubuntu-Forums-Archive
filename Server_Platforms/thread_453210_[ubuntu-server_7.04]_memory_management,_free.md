---
title: "[ubuntu-server 7.04] memory management, free"
date: 2007-05-24
forum: Server Platforms
---

### Post by r-w on 2007-05-24
Hello!

About 3 weeks ago I installed Ubuntu Feisty server on a Dell PowerEdge2600.  Occasion was the necessity to change 2 hard disks against bigger ones...

I noticed since then some aspects of the productive system.  (I have about 25-30 samba-users concurrent in there.  In addition to that I have dhcpd and ntpd running.)

In the first week of the ubuntu-server life I noticed a difference in memory management (free, top) compared to the antecedent server-install (Knoppix 3.7 – see below).

While the server had 2 GB of RAM, ubuntu grabbed the most RAM for cache and finally took also about 200KB swap.
That displeased me...  As consequence I installed another 2 GB of RAM last weekend.

All went well... for about 3 days.
Then ubuntu played the same with the RAM.
In the moment free gives me the following output:

```
             total       used       free     shared    buffers     cached
Mem:       4155656    4103840      51816          0          0    3349268
-/+ buffers/cache:     754572    3401084
Swap:      4000176        120    4000056
```

Another aspect:  the buffers = 0 ?
In the first days after reboot I had a buffers value above 0.  (had always above 0 with knoppix). But now?

What do you think abut this?

Is there a possibility to manipulate the memory management on the fly, to lower the cached data and get rid of the swapped?
Ubuntu kernel prefers to hoard more and more data for an indefinite time instead of taking care to not swap!

My first server-OS was an installed Knoppix 3.7 professional from a computer journal.
During an uptime of 552 days without restarting samba I had never more than ZERO use of swap and always more than zero buffers.

Does someone have a hint?

Thank you

---

### Post by craigp84 on 2007-05-24
short answer - leave the memory management to the experts.

long answer - you're misguided.

-c

---

### Post by r-w on 2007-05-24
Thank You for answering!

Be sure I feel uncomfortable with that, but... do you have a still longer answer, so that I can draw a conclusion and consider possible implications?

It's obvious; I'm not such an expert...

---

### Post by craigp84 on 2007-05-24
The 50,000ft of it goes like:

RAM is fast, disks are slow, when there's not enough current programs / data etc. to fill RAM (i.e. there's free ram) - use the spare stuff as a cache. A cache for pretty much anything, program fragments, data (files), what the kernel thinks may be needed next etc. etc.

This way, your overall performance goes up significantly.

Some operating systems don't have this, but seem to want it eventually (OpenBSD), some do have it (Linux, Windows) and some did have it but have dropped it (Solaris).

It makes sense to me to have it, but i'm not a programmer, so i'll leave that kind of decision up to them.

So in your specific case, it's most likely that when a user requests a file over SMB, samba reads that from the disk, then sends it over the network. The kernel notices this and takes the view that someone may request this file again, and, as there's plenty free ram, it will keep it in memory. This means that when a 2nd user requests the file, it can be served from (fast) ram rather than the (slow) disk.

For the average file server, this is the difference between being able to serve 200 workstations, or 210 of them.

Obviously it's intelligent about it and will flush the least used stuff (i believe the algorithm's more complex than that, although i've never actually read the code) to make way for more important stuff as programs request more memory allocation.

As for the swapping, my understanding is that there are a lot of reasons this can occur, not just because you're out of RAM. It's also my understanding that the algorithm used in Linux for VMM is "good enough" and can be trusted to do a good job.

If you're interested in tweaking this server for ultimate performance, then it's a pretty interesting road to go down - but you'll need more than just the "free" command to make any progress :-)

Hope this helps,

-c

---

### Post by r-w on 2007-05-25
Thank you very much for the elaborate answer.

It is clear for me too; cache is very important...

My main concern was with the involvement of swap memory and the possible degradation of the performance cause that.
A cached file for samba means, that the file is faster available the next time (may be in an hour again?).
But may be a piece of code, needed 10 times (?) in the minute is on the swap...

Thank you again.

Due to personal problems I’ll be away for a few days.
I will post then another experiences with the server.

rw

---

### Post by craigp84 on 2007-05-25
> But may be a piece of code, needed 10 times (?) in the minute is on the swap...

As above, this is not the case. You have a fear of swap, but swap is not always used for what you think it is.

---

### Post by r-w on 2007-05-25
Thank you.  I am now a little bit relaxed!

All my other issues (with samba) must be postponed for about a week.
I'll post again...

Bye, rw

---

