---
title: "What is limiting a single process to about half of physical memory?"
date: 2015-11-05
forum: Server Platforms
---

### Post by theosib on 2015-11-05
I'm running 15.10 server, and I have a huge process.  For some reason I cannot figure out, something is attempting to limit the amount of physical memory this one process is allowed to have.  So here's what I see in top:

[FONT=Courier New]top - 18:52:09 up 1 day,  2:25,  3 users,  load average: 1.64, 1.30, 1.18
Tasks: 525 total,   2 running, 523 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.3 us,  1.3 sy,  0.0 ni, 97.0 id,  1.4 wa,  0.0 hi,  0.0 si,  0.0 st
KiB Mem:  65937528 total, 37526160 used, 28411368 free,    14396 buffers
KiB Swap: 67071996 total, 67071724 used,      272 free.   104304 cached Mem

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND                                                                                                    
  363 root      20   0       0      0      0 R 100.0  0.0 324:02.98 kswapd0                                                                                                    
 6725 theosib   20   0 99.398g 0.034t   8920 D  12.0 55.1  59:08.71 common_shell_ex     [/FONT]                                                                                       

The virtual size is 99G, but it's only allowing about half of my 64G of physical memory to be used.  I've checked ulimit:

[FONT=Courier New]$ ulimit -a
core file size          (blocks, -c) 0
data seg size           (kbytes, -d) unlimited
scheduling priority             (-e) 0
file size               (blocks, -f) unlimited
pending signals                 (-i) 257447
max locked memory       (kbytes, -l) 64
max memory size         (kbytes, -m) unlimited
open files                      (-n) 1024
pipe size            (512 bytes, -p) 8
POSIX message queues     (bytes, -q) 819200
real-time priority              (-r) 0
stack size              (kbytes, -s) 8192
cpu time               (seconds, -t) unlimited
max user processes              (-u) 257447
virtual memory          (kbytes, -v) unlimited
file locks                      (-x) unlimited[/FONT]

I've set "/proc/sys/vm/swappiness" to 10.

I've looked at setrlimit, but "ulimit -Sv" says "unlimited".  I've looked into control groups, and there don't seem to be any limits being set, although I'm not totally sure how to interpret what I'm seeing; I've never set up any control groups.

So what the heck is going on that is preventing the only CPU-using process of the only user from using all available physical memory?  This thing is hammering my SSD root drive's swap partition!

Please help!

---

### Post by tgalati4 on 2015-11-06
Do you have any virtual machines set up on this server?  Perhaps set up a memory limit, say 20GB, then ramp it up to 25, 30, 35, 40, 45 and see how your system responds.  

How many cores in this server?  Because of the multi-associative handling of memory between cores, it's possible, that RAM is held in reserve for the other cores.  Run *htop* to see how the other cores are being used.

---

### Post by theosib on 2015-11-06
> **tgalati4 said:**
> Do you have any virtual machines set up on this server?  

No VMs.  Just running on bare metal.

> Perhaps set up a memory limit, say 20GB, then ramp it up to 25, 30, 35, 40, 45 and see how your system responds.  

Are you talking about one of the ulimit parameters?  Which one?  I could limit virtual memory, but the process would just die when it runs out of memory.  What we need is a limit on physical memory.  So maybe "ulimit -m"?

> How many cores in this server?  Because of the multi-associative handling of memory between cores, it's possible, that RAM is held in reserve for the other cores.

There are 24 physical cores; with HT, the system sees 48.

> Run *htop* to see how the other cores are being used.

Not sure what I'm looking for.  What I see is that cores 6 and 9 are heavily loaded.  One is running Synopsys, and the other is being used by kswapd0, although htop isn't reporting kswapd0, while top does.  Syopsys is getting only about 15% of a core, though, because it's spending so much time waiting on swap.

Any ideas about the fact that kswapd0 uses 100% CPU a lot?  I would have expected that after I turned on zswap, although I have a feeling that we can't trust what top says about which process is doing the compression.  But before I enabled zswap, shouldn't it be I/O-limited?  Moving only 20M/s (each way) from swap should hardly use any CPU time in that kernel thread.

Is it normal for the system to prefer to swap out in favor of using physical RAM?  Even if swappiness is set to a low value?


I'm a circuit designer, so there are some gaps in my knowledge of Linux system administration. Otherwise, I'd ask smarter questions.  But I'm synthesizing minor variants of the same circuit, and 15.04 behaved a hell of a lot better.  It's possible that some minor change is causing a major change in what Synopsys is doing.  (I did add one high fan-out net that didn't exist in earlier designs, but it shouldn't make that huge of a difference.)  This could be causing Synopsys to have very different memory access patterns, though.  Another possibility relates to system library versions.  To make Synopsys work with 15.10, I had to make symlinks in /usr/lib to make newer libraries look like older ones that it requires.  But they were mostly things like X11 and jpeg libraries that don't even really get used.


Thanks for the help!

---

### Post by tgalati4 on 2015-11-06
I think 24 cores is the issue.  I would bet that the kernel reserves a minimum amount of RAM for each core.  Pull some CPU's and see if there is a difference.
15.10 uses systemd, so anything is possible.  I would run 14.04 LTS server and use that as your performance benchmark.

---

