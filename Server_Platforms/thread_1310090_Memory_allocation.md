---
title: "Memory allocation"
date: 2009-11-01
forum: Server Platforms
---

### Post by adman4054 on 2009-11-01
I'm manipulating images via Graphicmagick. I'm receiving an error; Unable to read image data (/tmp/gmvvytDd) [Cannot allocate memory]. I'm hoping to get some help resolving this issue, how do I increase the allocation? Should I? If so, how do I do it. Using Hardy Heron, **Thanks!**

Here is the info
```


 **free** 
            total       used       free     shared    buffers     cached
Mem:       3116016     437728    2678288          0      12148     163824
-/+ buffers/cache:     261756    2854260
Swap:      7245272     250032    6995240
**ulimit -a**
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 24575
max locked memory       (kbytes, -l) 32
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 24575
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited

```

---

