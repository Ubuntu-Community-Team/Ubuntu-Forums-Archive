---
title: "MS10 Workstation vs Linux"
date: 2017-06-05
forum: Ubuntu, Linux and OS Chat
---

### Post by mayagrafix on 2017-06-05
An article about Win10 for Workstation says that it can handle more than one CPU (up to 4). Does Linux have this capability? (each CPU can have x amount of cores)

[https://www.theverge.com/2017/6/5/15739192/microsoft-windows-10-pro-for-workstations-advanced-pcs-features]("https://www.theverge.com/2017/6/5/15739192/microsoft-windows-10-pro-for-workstations-advanced-pcs-features")

---

### Post by TheFu on 2017-06-05
> **mayagrafix said:**
> An article about Win10 for Workstation says that it can handle more than one CPU (up to 4). Does Linux have this capability? (each CPU can have x amount of cores)

$ $ grep NR_CPUS /boot/config-`uname -r`
CONFIG_NR_CPUS=512

This is on a 16.04 box - so 512.
On a 14.04 box, it was only 256.

$zero license costs for an installed OS. The installer may support fewer cores (8 I think).  Of course, all of these things are just kernel settings that can be changed and you can recompile the kernel for your requirements with whatever number you like.  I little google-fu will find more details than you can probably stand.

On large scale systems, the CPUs will have direct access to a subset of the total system RAM for performance needs.  How that works is dependent on the motherboard architecture. This has been common for 20+ yrs in the Unix world.

"24TB of memory and 768 logical CPU cores" for RHEL v7.

---

### Post by mayagrafix on 2017-06-05
But can the OS split up chores among CPU's?

I remember when two CPU mobos were a thing, and then the big secret was that whatever OS you had, the gains were minimal because task could not be split. One CPU was hard at work while the other was at idle

---

### Post by TheFu on 2017-06-06
Beware of Microsoft's marketing engine.  The Windows limit of 2 CPUs was put in place purely to force companies to purchase "server" licenses.  It has never been anything more than a profit-creating decision.  Without that artificial pricing barrier, nobody would have cared.  That article doesn't say anything meaningful to make any Linux user worried.

Unix OSes have handled using multiple CPUs the last 40 yrs.

I don't know what a "chore" is, but processes and threads are split between CPUs.  If a programmer doesn't create multi-process and/or multi-threaded programs, then that program is single-threaded and run on a single core. There is no way for the OS to magically know how to split up a single-threaded computer.

On Windows, a process has huge overhead, so spinning up another is a big deal.  On Unix, processes have very little overhead, so we've split up things into separate processes and created method to communicate between them for decades prior to MS-Windows existing.  Separate processes have run on different CPUs for a very long time. It has been automatic for longer.  Multi-threaded code really became popular due to the limitation from MS-Windows. It was the only effective way for Windows programs to use multiple CPUs.

At work and when at Uni, I've had access to multi-CPU systems since the mid-1980s. Started writing multi-threaded code in 1989 for work. In 1999, I was able to purchase my own multi-CPU x86 computer for home use.  Compiled a multi-threaded program that estimated the value of pi, using as many threads as specified.  Then I watched the CPU use get pegged on BOTH CPUs.  I changed all my Makefiles to use -j2 so each build of my software took advantage of the 2 CPUs.  It was an exciting moment that a normal person could afford a computer with multiple CPUs.  Because Linux had been running on non-x86 systems with lots of CPUs even back then, it was already multi-processor capable.

If you want to learn more, wikipedia has lots of articles on OS design.

Ask yourself this too.  Why would 498/500 the worlds supercomputers run Linux if Windows was better at processing at huge scale?  

Windows was required at a time when home computers had to cost $1500 or less and Unix didn't run well on the available hardware at that price point.  As Unix workstation hardware got cheaper and x86 hardware became more capable at the "known" price point, Unix became very possible to run on home computers.  The reason that OS/2 wasn't a huge commercial success was that it needed 8MB of RAM to run well, but 90% of the home computers only had 4MB of RAM at the time.  Microsoft was smart.  They created an OS that worked fast enough on the average hardware purchased.  I probably have the $650 8MB of RAM I purchased to make OS/2 run well around here somewhere. ;)

Unfortunately for OS/2, power users really wanted Unix and by 1995, Linux was doing everything our $20K-$200K Unix workstations did at work. After I loaded Linux at home, I didn't need OS/2 anymore. Back then, Windows used 1 CPU and "cooperative multi-tasking".  OS/2 and Unix always used "pre-emptive multi-tasking". Wikipedia has articles explaining both of those terms if you care.

---

