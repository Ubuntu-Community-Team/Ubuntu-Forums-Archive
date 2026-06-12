---
title: "Pentium G620 kworker CPU usage on all 3.x kernels so far"
date: 2011-12-29
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bobsageek on 2011-12-29
Downloaded the daily, popped it on a thumb drive and booted, and just like every 3.1 or 3.2 kernel I've tried, I get 25% or greater CPU usage at idle, makes the system intolerably sluggish. With Fedora 16 kworker only happens on wake from suspend, but in the Precise daily it happens on boot. I know it's related the assorted Intel power regression issues, but anyone have any suggestions, system is rock stable and fast under 11.10 and 11.04.

Reading on some kernel discussions I found this command to try and determine what is eating the CPU:

```
$ echo workqueue:workqueue_queue_work > /sys/kernel/debug/tracing/set_event
$ cat /sys/kernel/debug/tracing/trace_pipe > out.txt
(wait a few secs)
^C
```

But I get a permission denied on the first command.

---

### Post by dino99 on 2011-12-29
12.04 is still a "work in progress", so where is the problem as you says "rock stable and fast under 11.10 and 11.04." ?

---

### Post by bobsageek on 2011-12-29
> **dino99 said:**
> 12.04 is still a "work in progress", so where is the problem as you says "rock stable and fast under 11.10 and 11.04." ?

Isn't the point of trying a daily to help identify issues and submit bug reports?

---

