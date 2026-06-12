---
title: "CPU affinity idea"
date: 2007-07-16
forum: The Cafe
---

### Post by daverich on 2007-07-16
how about making any programs launched on desktop 2 run on cpu 2 - or at least be biased to that cpu?

seems like a pretty good idea to me?

Kind regards

Dave Rich

---

### Post by prizrak on 2007-07-16
I'm confused, are you talking mutlitple workspaces with dual core cpu's? If yes then I don't see why you would ever want to confine it to just one. The whole point is running a system that can use any CPU resources available.

---

### Post by insane_alien on 2007-07-16
seems limiting. i use workspace1 more often than workspace2 and the programs on workspace2 typically idle 99% of the time(email)

---

### Post by Tomosaur on 2007-07-16
> **daverich said:**
> how about making any programs launched on desktop 2 run on cpu 2 - or at least be biased to that cpu?

seems like a pretty good idea to me?

Kind regards

Dave Rich

The whole point of having two CPUs is that both CPUs are utilised to the spread the work out so that stuff gets done faster. Limiting the 2nd desktop to just one CPU therefore defeats the purpose, and your machine would probably run slower because of it.

In any case, most modern Linux distros will sort all of this out automatically, so you don't have to worry about it. There's no point restricting some programs to a particular CPU when everything would be so much quicker and more efficient by spreading it out and letting different CPUs handle little tiny chunks of processing.

---

### Post by ssam on 2007-07-16
as said above linux tries to share tasks across avaliable CPUs. there is a lot of work being done on schedulars currently to try and improve how resouces are shared.

there have been some recent article on [http://kerneltrap.org/](http://kerneltrap.org/) about the Completely Fair Scheduler ( [http://kerneltrap.org/taxonomy/term/239](http://kerneltrap.org/taxonomy/term/239) ). though they get quite technical

if you are having trouble with a process not getting as much cpu time as you want it to, have a look at the program ```
nice
```. maybe gnome could have a GUI for nice?

---

### Post by Turboaaa2001 on 2007-07-16
I understand what your talking about, and I think it should be an optional feature only. I use BOINC with multiple projects and run it on the fourth desktop. My settings use both cores so implementing your idea would cut into productivity.

However, it would be benificial to people who want to dedicate 1 core to a single process/process tree. I think the best way of doing that is creating a program to handle that rather than relying on desktop space. The multi-desktop environment is used instead of using several monitors.

I think it should be available to those who need it. Otherwise it should be left out of the default installation.

---

### Post by a12ctic on 2007-07-16
Itd be nice if youd want to limit cpu use on some apps, encoding comes to mind. But wouldn't it be easier just to make it so that encoding only uses one of the cpus? Instead of having the whole desktop dedicated to it? I dont know.

---

### Post by daverich on 2007-07-17
I see what you guys are saying.

Basically there's just times when i want something to use the 2nd cpu - like when I'm burning a cd or something I want to force everything else over to another cpu.

It seemed an easy way to do it.

Kind regards

Dave Rich

---

### Post by cobrn1 on 2007-07-17
if you want to prioritise a task then there should be a separate way of doing that, but forcing each desktop to only use a certain amount of the CPU is limiting the potential of the PC...

Sometimes you need more, sometimes you need less. It makes more sense to dynamically give the amount of processing power needed, instead of setting it in stone, as this will limit the performance.

---

### Post by xzero1 on 2007-08-25
This is a very interesting question. Since each core, at least for athlon x2, has its own L2 cache it should be better to resume a thread on that same core. But wait, it also depends on the type of thread -- cpu bound, io bound, sleeping etc. We would not want to tie up core just so a io bound thread can own it. Still the cpu bound, higher priority threads should probably have affinity for a certain cpu. A good os scheduler will take these ideas into account.

---

### Post by popch on 2007-08-25
I think what you're really looking for is how to dedicate one core exclusively to one process. 

That would have the advance that the process in question would become very nimble. It would have the disadvantage that the processor reserved for that process could idle quite a lot.

---

### Post by hessiess on 2007-08-25
would be totaly useless, wouldent be able to render with multiple threds, i rarly use multiple desktops

---

