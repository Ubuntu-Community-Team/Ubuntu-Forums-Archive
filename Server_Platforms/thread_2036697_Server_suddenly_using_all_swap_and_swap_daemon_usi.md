---
title: "Server suddenly using all swap and swap daemon using upto 50% CPU time"
date: 2012-08-02
forum: Server Platforms
---

### Post by phillw on 2012-08-02
Hi Guys,

puzzled at this..

```

top - 17:46:13 up 9 days, 18:54,  1 user,  load average: 3.25, 3.22, 3.05
Tasks: 5947 total,   1 running, 5946 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.8%us, 31.4%sy,  0.0%ni,  0.0%id, 66.8%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1019544k total,   938564k used,    80980k free,       68k buffers
Swap:  1045500k total,   962500k used,    83000k free,     1816k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   22 root      20   0     0    0    0 D 23.4  0.0 155:44.89 kswapd0            
 2511 timelord  20   0 21916 4964   24 R  3.0  0.5   0:01.06 top                
 2231 znc       20   0  353m 109m  836 D  2.1 11.0 117:19.42 znc           

```

```

 free -m
             total       used       free     shared    buffers     cached
Mem:           995        916         78          0          0          5
-/+ buffers/cache:        911         84
Swap:         1020        933         87

```

Any ideas? It's been running quite happily until today.

Thanks,
Phill.

---

### Post by SeijiSensei on 2012-08-02
I'd start with this myself:

2231 znc       20   0  **353m 109m**  836 D  2.1 11.0 117:19.42 znc

What if you reboot?  Does the problem disappear then grow over time?  Perhaps znc (whatever it is) has a "memory leak."  

If this is a server, I might add another GB of swap by creating a swap file on the hard drive.  But first I'd figure out why znc is using up a third of your memory.

---

### Post by phillw on 2012-08-02
> **SeijiSensei said:**
> I'd start with this myself:

2231 znc       20   0  **353m 109m**  836 D  2.1 11.0 117:19.42 znc

What if you reboot?  Does the problem disappear then grow over time?  Perhaps znc (whatever it is) has a "memory leak."  

If this is a server, I might add another GB of swap by creating a swap file on the hard drive.  But first I'd figure out why znc is using up a third of your memory.

It is my suspicion that ZNC may have a memory leak, but for it to go from 300Mb free memory to using all that & all the swap in about 24 hours is problematical. The server is a dedicated znc server, so it should be the only process that uses any 'really serious' cpu time,

As it is a VM I'm hosting on behalf of someone else, the guy who 'looks after' znc for ubuntu repos; I do feel somewhat powerless to intervene without his permission to do a boot. I can, in the mean time add some swap to it.

Now to look this up for ubuntu-server, I'm CentOS server trained... same idea, just slightly different instructions :P 

Additional 1GB swap added.

Thanks,

Phill.

---

### Post by phillw on 2012-08-02
The swap has been added, but the swap daemon is still really working hard...

```

top - 19:32:33 up 9 days, 20:41,  1 user,  load average: 3.02, 2.99, 3.00
Tasks: 5949 total,   1 running, 5948 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us, 44.5%sy,  0.0%ni,  0.0%id, 54.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1019544k total,   937156k used,    82388k free,       68k buffers
Swap:  2094072k total,   994236k used,  1099836k free,     4504k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   22 root      20   0     0    0    0 D 36.7  0.0 190:50.71 kswapd0            
 2231 znc       20   0  353m 103m  360 D  5.8 10.4 122:19.42 znc         

```

I'll await for the VM owner to come on-line, in the meantime I'll add the 2nd 1GB swap area to fstab so it is permanent for when the reboot happens. 

thanks for your help & suggestions.

Phill.

---

### Post by teward on 2012-08-02
ZNC isnt designed to use swap.  I typically, when I run VMs, don't request swap for that reason.  If znc's using swap, its a bad thing.

I'm the VM owner, and its quite possible it was DDoS related, we'll see if additional iptables blocking rules stem the flow of data in/out.  But I have no idea whether ZNC was taking up all that swap or not...

---

### Post by phillw on 2012-08-02
Reboot has happened,

We are hopeful, at is does seem to stink of a DDoS. 

time will tell.

Thanks,

Phill.

---

