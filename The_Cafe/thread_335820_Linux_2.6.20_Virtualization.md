---
title: "Linux 2.6.20 Virtualization"
date: 2007-01-10
forum: The Cafe
---

### Post by darkhatter on 2007-01-10
anyone else looking forward to this :mrgreen: 

Links:

Virtualization begins to materialize in the Linux kernel
[http://specialreports.linux.com/article.pl?sid=06/12/19/053225&tid=136&tid=91](http://specialreports.linux.com/article.pl?sid=06/12/19/053225&tid=136&tid=91)

Linux KVM Virtualization Performance
[http://www.phoronix.com/scan.php?page=article&item=623&num=1](http://www.phoronix.com/scan.php?page=article&item=623&num=1)

I hope I can run Mac OS X, and Windows with this

---

### Post by G Morgan on 2007-01-10
No VT extensions unfortunately. TBH VMware is good enough for now, until we can get full 3D Accel and other hardware use through a hypervisor I see little point in full hardware virtualisation. Don't get me wrong it will be great when they get that but until then VMwares consistent platform wins for me.

---

### Post by Polygon on 2007-01-10
doesnt mac os x check to see if a certain chip is present on your computer, or else it wont install? which is why the reason you almost never see any mac operating systems on non mac official computers?

so you may not be able to run mac, but surely other operating systems...

---

### Post by darkhatter on 2007-01-10
there is ways around apples crap......

I guess no one is excited about hardware virtualization....:(

---

### Post by maniacmusician on 2007-01-10
I am! I actually wasn't even aware that it wasn't available for us. Good thing too, I was just about to upgrade to a virtualization-capabale processor and it's nice to know I'll be able to take full advantage of it. Sweet stuff.

---

### Post by The Noble on 2007-01-11
The article is long and a little over my head (plus it's finals week), so maybe you guys could answer my questions. This is basically vmware through the kernel, and gives the other operating systems full run of the hardware while running (thus better performance), right? From my understading, this is really cool, as there is no need for "emulation" and the overhead would be really minimal. The one sad thing is that, from what I saw, only newer chipsets support this (the Core line, and the AM2 line mainly), but that's ok, as it wouldn't be worth running virtualization through a P4. Maybe you guys could help me understand this a little better with a brief overview, as I don't have the time to scan the article right now. 

Maybe by friday I'll revise this and answer my own questions as well as some others... Thanks for the articles, by the way!

---

### Post by G Morgan on 2007-01-11
Essentially the x86 series of procs work on the basis of privilege rings. Ring 0 is where the OS runs and ring 3 is where applications run (rings 1 and 2 do squat). Of course any sort of virtualisation tries to run an OS in ring 3 when it needs ring 0. 

Traditional emulation handles this by mangling the code being run and emulating the results of various ring 0 calls. 

Virtualisation works by hacking into the kernel to get limited ring 0 access and by writing specifically optimised sections of code to make the most of its kernel access, this is quite complex to pull off.

Para-virtualisation works by modifying the kernel of the guest OS to allow it to run as a ring 3 process. This works quite well but requires a modified kernel so is also a lot of work.

Hardware supported virtualisation works by setting up another ring where virtualised ring 0 calls are passed and handled by the hardware. This has the advantage of allowing a virtualisation system to be written very simply without any need for mangling ISA calls, writing optimised code or fiddling the kernel to make it run as an application. It makes the process much easier and in the end will be faster. It also may allow full 3D Accel and other hardware support in the long term.

---

### Post by maniacmusician on 2007-01-11
how come rings 1 and 2 do nothing? would it be more efficient to use them? or move applications down closer to ring 0? It is all pretty confusing.

---

### Post by G Morgan on 2007-01-11
> **maniacmusician said:**
> how come rings 1 and 2 do nothing? would it be more efficient to use them? or move applications down closer to ring 0? It is all pretty confusing.

PC hardware is riddled with things that were put there originally for expansion but have never been used. You'd be amazed how many hardware quirks there are altogether. The rings are just used to enforce different privilege levels, the most efficient system would be to run everything in ring 0 but there would be practically no security then, this is how MS-DOS used to run. Most systems are happy with a two tiered system in terms of security.

Ring 0 basically allows direct access to memory outside of a processes own segment. Ring 3 processes can only directly access their own memory segment and must use interrupts and system calls to access more memory.

---

