---
title: "Complex CPU Affinity"
date: 2009-09-19
forum: Server Platforms
---

### Post by RIFGenesis on 2009-09-19
Hi,

I would like to assign a running process exclusively to a CPU core on one of my Ubuntu servers. I am aware of the taskset command and how to use it but I would like for only this 1 process to use the given core and for no other processes to naturally use it as they switch between cores.

I had a look at the man page for taskset and noticed that there is a --cpu-list option which allows specifying multiple CPUs. I was thinking of writing a script which assigns the exclusive process to a particular core and then assigns all other pids to the remaining 7 cores using the --cpu-list option. This script could be run in cron periodically.

Will this work, and is there a better way of doing this?

---

### Post by scorp123 on 2009-09-19
> **RIFGenesis said:**
>  Will this work, and is there a better way of doing this? The big question is: Why would you want to do this? Linux was specifically designed so that you don't have to bother about such things, e.g. tasks will switch between whichever CPU's that don't have too much to do.

If you think you need better performance then I'd recommend you look into changing your Linux I/O scheduler.

The default for Ubuntu desktop is the "Completely Fair Queuing" scheduler (CFQ). But depending on what a system is supposed to do it may also be worth to try the "deadline" scheduler.

Please read here:
[http://www.redhat.com/magazine/008jun05/features/schedulers/](http://www.redhat.com/magazine/008jun05/features/schedulers/)

What they write about Red Hat Linux also applies to any other Linux distribution.

For servers I have had good experience with the "Deadline" scheduler. From above Link:
>  " ... The Deadline elevator uses a deadline algorithm to minimize I/O latency for a given I/O request. The scheduler provides near real-time behavior and uses a round robin policy to attempt to be fair among multiple I/O requests and to avoid process starvation. Using five I/O queues, this scheduler will aggressively re-order requests to improve I/O performance. ... "

IMHO it may be worth to benchmark your system after booting witch each scheduler.

Messing with CPU affinity however is something I'd definitely not recommend. It should not be necessary to do this. In my opinion you'd only cripple your system and actually slow things down.

Using the right scheduler is the way to go, IMHO.

---

### Post by RIFGenesis on 2009-09-20
> **scorp123 said:**
> The big question is: Why would you want to do this? Linux was specifically designed so that you don't have to bother about such things, e.g. tasks will switch between whichever CPU's that don't have too much to do.

The processes in question are game servers and I want to do this because a customer will be paying for a dedicated core. This is not about being fair to other processes.

My I/O scheduler is already set to deadline as it appears this is the default for the server platform.

---

### Post by tgalati4 on 2009-09-20
Hogging one processor may have undesirable effects.  Perhaps you could set a payscale tied to the "nice" value of the process.

man nice

---

### Post by scorp123 on 2009-09-21
> **RIFGenesis said:**
> The processes in question are game servers and I want to do this because a customer will be paying for a dedicated core.  In that case using a virtual machine would be the better option. I'd recommend Xen. Xen VM's run at nearly the native speed of the host OS and for virtualizing Linux-on-Linux it's ideal. You'd configure the Xen VM so it gets to only see one single core. So the customer gets what they paid for. The real task-handling would still remain with your host OS (invisible to the customer) and the many cores it has at its disposal. The other advantage would be that with Xen VM's you can fine-tune how much memory and CPU% resources they may consume at max. With this you could make sure that your hosting server remains up and running and responsive even if that customer would happen to do strange things to his server processes inside the Xen VM.

---

### Post by Vegan on 2009-09-21
OP: I can see no reason at all for mucking with the CPU. The defaults are fine. Keep in mind the kernel will deal with heavy loads fine. So this is an area that you should never need to worry about.

---

