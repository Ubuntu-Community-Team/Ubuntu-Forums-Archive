---
title: "Why swap partition is not used?"
date: 2022-02-04
forum: Ubuntu, Linux and OS Chat
---

### Post by flyingosprey on 2022-02-04
My old machine has Ubuntu 20 LTS installed. It only has 16G memory. It has 32G swap partition. I am building a large project on it.

This is what the "top" command shows:

top - 00:24:48 up 1 day, 48 min,  2 users,  load average: 1.01, 1.05, 1.06
Tasks: 243 total,   3 running, 240 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.2 us,  1.3 sy, 11.3 ni, 87.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :  15960.8 total,    **179.0 **free,    434.1 used,  15347.6 buff/cache
MiB Swap:  30517.0 total,  **30305.1 **free,    211.9 used.  15198.9 avail Mem


The physical memory is almost all used. But swap space is almost unused.

My understanding is: when physical memory are all used, swap space  will be used as the backup memory. So it should be used. Is that correct?

---

### Post by KBar on 2022-02-04
Both [Wikipedia]("https://en.wikipedia.org/wiki/Memory_paging#Unix_and_Unix-like_systems") and [Ubuntu Community Help Wiki]("https://help.ubuntu.com/community/SwapFaq") have great articles on memory paging and swapping in particular. In it, there is a paragraph dedicated to your question.

There are potentially two answers to your main question:

[LIST=1]
[*]Swap is not being used simply because it's not needed. 16G is plenty and maybe the kernel feels like it's enough and prefers not to resort to swapping, which leads to another factor; 
[*]and that is swappiness. Although it's set to 60—which is quite aggressive—on most Ubuntu Desktop installations, you might have changed it at some point or your specific installation is a bit atypical. To find out its current value, execute one of the two, sorted in order of preference: 
[/LIST]
 ```
sysctl vm.swappiness
``````
 cat /proc/sys/vm/swappiness
```[This]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F") section explains how it can be configured, temporarily or permanently.

---

### Post by The Cog on 2022-02-04
In your output above, there is 434.1 used for applications (they have asked to be allocated memory) and 15347.6 being used as disk cache. This disk cache is used to store what has recently been written/read in to save time waiting for the disk in case the info is asked for again. There is no point in leaving that memory unused.  If an application asks for more memory to be allocated to it, some of the disk cache will be used/re-purposed. I'm not sure if Windows doesn't use spare RAM, or if it simply reports it unused even though it is being used for cacheing, but the difference in reporting does sometimes cause confusion. 

It really makes no sense to start saving the disk cache to the swap partition. That's why swap is not used at the moment.

This is a common enough question that someone has made a web page about it: [https://www.linuxatemyram.com/](https://www.linuxatemyram.com/)

Edit: Ninja'd by KBar, and with much better links too.

---

