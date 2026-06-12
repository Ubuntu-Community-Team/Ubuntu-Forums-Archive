---
title: "Ubuntu 8.04 -- udevd process goes nuts, eats CPU"
date: 2008-07-14
forum: Server Platforms
---

### Post by danilche on 2008-07-14
Hi all,

I have recently upgraded one of our servers to ubuntu 8.04, and the performance of that server's main application (a PHP CRM) dropped through the floor. In investigating the problem, i noticed something weird. The udevd process seems to take up about 65% of the CPU time when idle; less when other stuff is running, but still a lot. I wonder if this behavior could be related to the 

I did shut MySQL server down, and that didn't help.

My server has 2GB of RAM and 3GB swap. There is no funny hardware or software installed.

Does anyone have any idea why udevd would be eating up so many CPU cycles?

Thanks in advance.

---

### Post by kauschovar on 2008-08-26
I have a similar (or maybe the same) problem.  The one detail you didn't mention in your post that is affecting me is that udevd is also consuming all of my memory.  Do you have the same problem?

I searched the forums for an hour or two, and this thread is the closest to the problem I'm experiencing.  My server had been running fine for about two years.  The server's uptime was almost a year when the problem started.  I've regularly updated the software.

I rebooted the server yesterday, and today it is sluggish again.  Investigating the issue, I found that udevd is consuming 150% of my memory (all my physical memory plus some of the swap).  The only thing being hosted from this server is Trac and Subversion, and I'm the only user.  Below is the output from free and top.

free -m
```

             total       used       free     shared    buffers     cached
Mem:           250        247          3          0          0          5
-/+ buffers/cache:        241          8
Swap:          972        212        760
```

top
```

top - 12:26:31 up 1 day, 53 min,  1 user,  load average: 4.33, 4.32, 3.08
Tasks:  55 total,   3 running,  52 sleeping,   0 stopped,   0 zombie
Cpu(s): 71.8%us,  6.3%sy,  0.0%ni,  0.0%id, 21.6%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:    256288k total,   252372k used,     3916k free,        0k buffers
Swap:   996020k total,   186936k used,   809084k free,     3064k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
27512 root      17  -2  134m 132m  336 S  0.7 52.8   0:00.02 udevd
 2245 root      17  -4  134m 132m  272 R 72.4 52.8   1384:30 udevd
27513 root      18  -2  134m 131m  116 R  0.0 52.7   0:00.00 udevd
```

Does anyone have any idea what could cause this or how to fix it?  Any help would be greatly appreciated.

---

### Post by roboa1983 on 2008-08-27
I tried to solve this problem some months ago when I had ubuntu 7.10 for a 64-bit distribution. 
Although this should be taken with a grain of salt since my problem was solved months ago (i.e. perhaps check if someone had the same solution), what I did was just purge udevd. Afterwards, things got back to normal.
Hope this at least gives you some direction.

---

### Post by cmeckhardt on 2008-08-28
I've been seeing this problem too, on a brand-new hardy install.

A friend pointed me at [http://codepoets.co.uk/upgrade-ubuntu-gutsy-emvs-and-udevd-100-cpu-usage-aka-udevd-going-nuts](http://codepoets.co.uk/upgrade-ubuntu-gutsy-emvs-and-udevd-100-cpu-usage-aka-udevd-going-nuts) last time this happened and I followed the instructions there, which alleviated the problem at that time.

[COLOR="Red"]EDIT: DON'T DO THIS or remove udevd if you're using gnome, as much of gnome seems to depend on it.[/COLOR]  You might be cleverer and have guessed not to do it to a desktop box since this thread appears in "Server Platforms", but I am not that clever and I just hosed myself.

However, today it cropped up again.  A quick perusal of the udevd and udevadm man pages suggested that ```
udevadm control --stop_exec_queue
``` (as root) would cause the process to stop trying to execute kernel events, and it seemed to work if you don't want to purge udevd.  But this is only a temporary workaround and if anyone else knows what's really going on here I'd love to hear it.

---

