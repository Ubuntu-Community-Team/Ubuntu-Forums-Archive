---
title: "Excessive Memory Usage on Merb Processes"
date: 2008-12-22
forum: Server Platforms
---

### Post by ubuser_7 on 2008-12-22
Hi Everyone

We are running Ubuntu Server 8.04 on an AMD machine with a gig of RAM.

We are running merb servers for public websites, and some thin websites for our internal websites. We had migrated to this hardware very recently from our original Debian server on an older machine.

Now the problem is that ever since we moved out to this new machine, we have been having memory trouble. The merb processes ( 10 processes) start with a big memory foot print and then just keep getting bigger.

They start with a resident memory size of ~50 MB (earlier they started with 30 and stabelized in 30-35). They just keep getting bigger occupying like 70-90 memory (varies greatly). 

Free has the following output:
```

             total       used       free     shared    buffers     cached
Mem:           941        604        337          0          7         35
-/+ buffers/cache:        561        379
Swap:         2823        330       2493

```

the used goes up to like 800+ (in both memory and buffer). I understand the buffering thing in Linux but the buffer/cache used itself is 800-900MB. 

As a result, we have to restart the merb processes and apache like every two-three days. The whole machine starts becoming slow and pages take a long time to be served. Interesting thing is we did a very similar migration on another machine (Debian to Ubuntu Server, although its just a LAMP server) and it works fine. While it still occupies the whole memory, but free shows that its mostly cache, unlike this machine. 

I also installed memstat, but the output varies greatly. I just restarted the servers, so will post the output from memstat, when the memory usage goes up. 

Can some one please suggest some tools that can help diagnose these problems or make any other suggestions?

Thanks!

---

### Post by CrucifiedEgo on 2008-12-22
which used line are you looking at?  the second number (561) is the one that counts in this case.

---

### Post by ubuser_7 on 2008-12-22
Yes, 561 is when i just restart the merb processes. This used to be like 300 in original machine. This goes till 800-900 (sometimes even 900+). I will put actual output from free in a few hours, because I just restarted the merb processes before writing the post.

---

### Post by ubuser_7 on 2008-12-22
Ok, now that we are back to high memory consumption, here are some outputs:

```

$sudo memstat

...
  11656k: PID 10205 (/lib/libnss_dns-2.7.so)
...
  80020k: PID  4961 (/usr/lib/ruby/1.8/x86_64-linux/digest/sha1.so)
  80168k: PID  4966 (/usr/lib/ruby/1.8/x86_64-linux/digest/sha1.so)
  79664k: PID  4971 (/usr/lib/ruby/1.8/x86_64-linux/digest/sha1.so)
  33256k: PID  4979 (/usr/lib/ruby/1.8/x86_64-linux/iconv.so)
  33260k: PID  4984 (/usr/bin/ruby1.8)
  33240k: PID  4989 (/usr/lib/ruby/1.8/x86_64-linux/iconv.so)
...
 73508k: PID 14539 (/usr/lib/libdb-4.6.so)
  69752k: PID 14541 (/usr/lib/libdb-4.6.so)
  68068k: PID 14543 (/usr/lib/libdb-4.6.so)
  68636k: PID 14545 (/usr/lib/libdb-4.6.so)
  66956k: PID 14547 (/usr/lib/libdb-4.6.so)
  81428k: PID 14549 (/usr/lib/libdb-4.6.so)
  66036k: PID 14551 (/usr/lib/libdb-4.6.so)
  72036k: PID 14553 (/usr/lib/libdb-4.6.so)
  71688k: PID 14555 (/usr/lib/libdb-4.6.so)
  67184k: PID 14557 (/usr/lib/libdb-4.6.so)
...
--------
1461896k

```

Showing only those entries that take up a large amount of memory. Can put up the whole thing, but would avoid.

```

free -m
             total       used       free     shared    buffers     cached
Mem:           941        878         63          0          3         29
-/+ buffers/cache:        844         97
Swap:         2823        391       2432

```

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                       
 4966 www-data  20   0  162m  67m 1796 S  0.0  7.2   5:43.03 thin                                                                                          
 4971 www-data  20   0  161m  65m 1784 S  0.0  7.0   6:12.66 thin                                                                                          
14539 www-data  20   0  192m  65m 3276 S  0.3  6.9   0:26.91 merb                                                                                          
 4961 www-data  20   0  162m  63m 1992 S  0.0  6.7   4:43.05 thin                                                                                          
14555 www-data  20   0  190m  62m 3276 S  0.0  6.6   0:23.79 merb                                                                                          
14549 www-data  20   0  190m  61m 3276 S  0.0  6.5   0:26.01 merb                                                                                          
14553 www-data  20   0  191m  61m 3272 S  0.0  6.5   0:24.25 merb                                                                                          
14543 www-data  20   0  187m  60m 3276 S  0.0  6.4   0:20.68 merb                                                                                          
14557 www-data  20   0  186m  59m 3272 S  0.0  6.3   0:25.20 merb                                                                                          
14547 www-data  20   0  186m  59m 3272 S  0.0  6.3   0:20.99 merb                                                                                          
14545 www-data  20   0  187m  59m 3272 S  0.0  6.3   0:23.02 merb                                                                                          
14551 www-data  20   0  185m  58m 3276 S  0.0  6.2   0:21.82 merb                                                                                          
14541 www-data  20   0  184m  57m 3272 S  0.0  6.1   0:19.84 merb               

```

Btw, thin usually is not consuming that much memory. mostly it has a low memory footprint and even if does go up (as it is now, it comes down fast)  Things get worse. While free output remains more or less the same, the top shows that merb processes go up till like 800+

Any suggestions?

---

### Post by ubuser_7 on 2008-12-29
Bump

---

