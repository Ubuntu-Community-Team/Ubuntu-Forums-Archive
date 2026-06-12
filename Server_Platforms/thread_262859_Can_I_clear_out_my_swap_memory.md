---
title: "Can I clear out my swap memory?"
date: 2006-09-22
forum: Server Platforms
---

### Post by CzarAlex on 2006-09-22
Greetings, is there a way to refresh or clear out my swap memory?

```
top - 09:18:27 up 4 days, 16:16,  1 user,  load average: 0.00, 0.00, 0.00
Tasks:  86 total,   1 running,  85 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.7% us,  0.3% sy,  0.0% ni, 99.0% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    386876k total,   302956k used,    83920k free,    69136k buffers
Swap:   377488k total,    68864k used,   308624k free,   104828k cached
```

now, im not too familiar with swap, but if I have 83920K free, why is 68864K of swap being used? Id rather not restart the server to achieve this. is there a command i can run?
Thanks

---

### Post by kidders on 2006-09-22
Hi there,

Unless you're trying to do this for security reasons, I wouldn't recommend trying. Why does the amount of free swap make a difference to you?

---

### Post by CzarAlex on 2006-09-22
> **kidders said:**
> Hi there,

Unless you're trying to do this for security reasons, I wouldn't recommend trying. Why does the amount of free swap make a difference to you?

Well, and im not sure this matters much as I'm new to the whole server thing. But I'm serving MOOs (text based RPGs..like MUDs) and they run constantly in memory, saving to the hard disk every hour. I was hoping to be able to serve more on this box. Perhaps I need not worry?

---

### Post by kidders on 2006-09-22
Oh, I think I see where you're coming from. You're wondering whether, seeing as the amount of allocated real/virtual RAM is so high, you can afford to serve more stuff without condemning your server to endless paging.

The short answer is that you're looking in the wrong place for this info.

Linux kernels tend not to waste time unnecessarily deallocating unused memory, unless they actually *need* it for something. As such, situations commonly arise where you have hundreds of megs of free RAM, but the OS still looks like it's paging lots of data. In actual fact, all that really means is that, at some point in time, you needed all that extra memory ... just not any more. This is usually interpreted as a _feature_ of the Linux kernel, rather than a problem of some kind.

So, to answer your question, I ***think*** "top" is a better indicator of how much memory something is using, and where that memory is. Also, I know there is a way for you to distinguish between paged data that's just sitting there and paged data that's hopping in and out (ie it's in use). I just don't recall what it is!

**Edit:** This may be a little over-technical, but you can use the files in /proc/sys/vm to control Linux's swap-related behavior ... be very, very careful though!

**Edit:** I forgot to actually say that the way to "refresh" your pagefile is simply to turn it off, and back on again. For example **swapoff /dev/sda2; swapon /dev/sda2** Doing this would very adversely affect performance however, as the kernel undoes the damage you caused to its nice, efficient memory model.

---

### Post by CzarAlex on 2006-09-22
I thank you for the info, and I shall just leave everything as is :) Thanks again though!

---

