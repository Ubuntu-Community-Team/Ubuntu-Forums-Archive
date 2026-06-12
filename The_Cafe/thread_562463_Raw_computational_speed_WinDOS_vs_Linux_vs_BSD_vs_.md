---
title: "Raw computational speed: WinDOS vs Linux vs BSD vs Solaris...?"
date: 2007-09-28
forum: The Cafe
---

### Post by Sporkman on 2007-09-28
Got a question: Is there any data/evidence comparing the raw computational speed between these kernels? I'm not talking about how snappy the desktop feels, nor server-specific tasks like packet processing, database calls, etc. I'm talking raw computational speed: integer math, floating point ops, memory reads & writes, etc.

Anybody know?

---

### Post by samjh on 2007-09-28
If you Google the keywords "windows", "linux", "benchmark", there are a lot of results which claim to measure performance differences between Windows, Linux, and even Mac OS.

But it's really hard to objectively test the performance differences between various operating systems, because so much depends on the quality of optimisation of the software that is used to do the benchmark for each operating system.  Even the choice of desktop environment (eg. Gnome, KDE) influences benchmarking data.

Having that that, there are benchmarks between Windows and Linux which shows Windows to be faster, and vice versa for Linux.  So there is really nothing conclusive.

Even if a comprehensive benchmark existed, I'd take it with a tablespoon-full of salt! :)

---

### Post by tgalati4 on 2007-09-28
You would have to conduct your own tests with code that you are familar with.

In my testing with a GPS-based tracking program, Damn Small Linux ran faster than Ubuntu Dapper.  DSL uses a 2.4.26 kernel with about 20 processes running upon fresh boot.  Ubuntu Dapper (2.6.15-28 kernel) loads about 75 processes for a lean boot.  Less process interrupts means more CPU cycles for your application.

Microsoft DOS probably runs the fastest.

The trick is your development environment.  You have to compile your code and get it to run in your environment.  In my case, I am able to compile in Ubuntu and port the binary and it runs fine--and faster on DSL.  Just another neat trick you can play in Linux.  So that may work for you as well.

You can get 7-10% increase by not running the X server.  You can run DSL in headless mode--no keyboard, mouse, or monitor and remotely log into it using ssh from another machine to port your code (using scp) and run jobs.  Can't think of a faster set up short of a cluster, multiprocessor, or super computer.

Can't speak to BSD or Solaris, though I have a powerbook that runs OSX 10 and it's running a flavor of BSD.  It has a similar processor load to Ubuntu.  Lots of stuff running in the background.

Perhaps there is a version of Linux called Damn Fast Linux.

One final note, the processor comes into play.  A Mac G4 or G5 processor has the Altivec processing extensions which are helpful for matrix math such as ray tracing, and video rendering.  Again, depending on your application, the processor will make a big impression on overall throughput.  

Cycles are meaningless, wall clock time is the real benchmark.

---

### Post by Sporkman on 2007-09-28
> **tgalati4 said:**
> You would have to conduct your own tests with code that you are familar with.


I've been thinking of that, but I have neither the spare time nor computers.

I figure on the same machine, I'd do miminal installs of each, take the same simple benchmarking C code, compile it natively on each via gcc -O3, then run & time...

Maybe one of these days.

---

### Post by happysmileman on 2007-09-28
> **Sporkman said:**
> I'd do miminal installs of each, take the same simple benchmarking C code, compile it natively on each via gcc -O3, then run & time...

It's not recommended you use anything above -O2 as it can reduce the accuracy of your program and produce wrong output, especially bad for things like floating point calculations and stuff you'd be doing.

---

### Post by Sporkman on 2007-09-28
> **happysmileman said:**
> It's not recommended you use anything above -O2 as it can reduce the accuracy of your program and produce wrong output, especially bad for things like floating point calculations and stuff you'd be doing.

:eek:

I did not know that! Why would they implement switches that produce incorrect results??

---

### Post by happysmileman on 2007-09-28
> **Sporkman said:**
> :eek:

I did not know that! Why would they implement switches that produce incorrect results??

Well that may not be true but I thinK i was ectured on it on a forum before, so maybe it needs to be verified. But I can see why they could include it

There are things it wouldn't matter for, like if you're doing 3D graphics and a red pixel is off by one pixel to the right you're fine. But if you're calculating a billion decimal places of pi you need accuracy.

I don't think it can affect the libraries it connects to, since they'd be compiled seperately, so if it's a modern GUI program with a bunch of libraries doing all the hard work then you could optimise it past there and not notice

---

### Post by bruce89 on 2007-09-28
Vista will certainly be last anyway, thanks to good old C#.

---

### Post by happysmileman on 2007-09-28
> **bruce89 said:**
> Vista will certainly be last anyway, thanks to good old C#.

True, I'd say Linux would be faster than all except the older versions of Windows, maybe XP could get through, it's horribly slow on my computer (I actually get pissed off waiting for it to reboot so I can load Linux) but no-one else I know appears to have the problems (yes I'm virus free, or else my anti-virus isn't working)

---

### Post by Tachyon_ on 2007-09-28
Interesting performance comprasion that has Linux and BSD, Linux owned and FreeBSD was really good too:
[http://bulk.fefe.de/scalability/]("http://bulk.fefe.de/scalability/")

Look at the supercomputer list, which I think is the most descriptive (performance is really crucial and expensive):
Linux 77.80 % 
Windows 0.40 % 
Unix 12.00 % 
BSD Based  0.80 %  	
[http://www.top500.org/stats/list/29/osfam]("http://www.top500.org/stats/list/29/osfam")

> **tgalati4 said:**
> You would have to conduct your own tests with code that you are familar with.

In my testing with a GPS-based tracking program, Damn Small Linux ran faster than Ubuntu Dapper.  DSL uses a 2.4.26 kernel with about 20 processes running upon fresh boot.  Ubuntu Dapper (2.6.15-28 kernel) loads about 75 processes for a lean boot.  Less process interrupts means more CPU cycles for your application.

Microsoft DOS probably runs the fastest.

The trick is your development environment.  You have to compile your code and get it to run in your environment.  In my case, I am able to compile in Ubuntu and port the binary and it runs fine--and faster on DSL.  Just another neat trick you can play in Linux.  So that may work for you as well.

You can get 7-10% increase by not running the X server.  You can run DSL in headless mode--no keyboard, mouse, or monitor and remotely log into it using ssh from another machine to port your code (using scp) and run jobs.  Can't think of a faster set up short of a cluster, multiprocessor, or super computer.

Can't speak to BSD or Solaris, though I have a powerbook that runs OSX 10 and it's running a flavor of BSD.  It has a similar processor load to Ubuntu.  Lots of stuff running in the background.

Perhaps there is a version of Linux called Damn Fast Linux.

One final note, the processor comes into play.  A Mac G4 or G5 processor has the Altivec processing extensions which are helpful for matrix math such as ray tracing, and video rendering.  Again, depending on your application, the processor will make a big impression on overall throughput.  

Cycles are meaningless, wall clock time is the real benchmark.
2.6 has better performance than 2.4 in almost all cases. First is the difference in the running programs, that in your case seems to be the most effective. But, when you get these out of the way, run 20 process in 2.4 or 2.6, 2.6 pwns. To get equal measurements, you should recompile kernel with things that are only needed. Ubuntu ships with lots of stuff inside the kernel too. This is my hypothesis that the first link seems to prove.
You claimed the DOS is fastest. However, the kernel of the DOS can not take the advantage of modern processors (processor matters much as you said, but kernel has to support these things). I would argue that any *nix kernel is better on modern machines, especially when we need to run more programs or one program that links to libaries or has threads. I don't see the supercomputers running DOS.
FreeBSD and UNIX (solaris) have a really good performance, much better than Linux had way back (2.4) then. Now things are mostly equal I would say.

---

### Post by Sporkman on 2007-09-28
> **happysmileman said:**
> There are things it wouldn't matter for, like if you're doing 3D graphics and a red pixel is off by one pixel to the right you're fine. But if you're calculating a billion decimal places of pi you need accuracy.


Any wrong calculation is bad, regardless of the application. A wrong calculation can result in mis-indexing of arrays, wrong forking in a program's control flow, etc.

My employee scheduling app (invoked from my website in my sig) is compiled via -O3... I'd better recompile to -O2, though execution speed is very important for this app (a modest scheduling task can take it 20 mins, to run, for example, on ubuntu server).

---

### Post by samjh on 2007-09-28
> **Sporkman said:**
> :eek:

I did not know that! Why would they implement switches that produce incorrect results??

The -O3 switch itself doesn't produce incorrect results.  Rather, code that has been designed without considering the effects of -O3 may produce incorrect results.  It's like modifying your car: hard-core performance mods might make it go faster, but it might become heavier and less reliable if you don't modify other aspects of the car to compensate for the differences.

If you want to use -O3, you need to design your source code so that the optimisation will work well, otherwise the result might not be what you expect.  I don't know the specifics of GCC's behaviour with -O3.  Consult GCC's documentation for that information.

It is generally accepted that -O2 provides the best balance between reliability and speed for production release builds.

---

### Post by HermanAB on 2007-09-28
Hmm, it depends on what you do on the machine. When you optimize for speed you have to determine whether it is Disk I/O, Network I/O, Computations, Scheduling or Memory that is the limiting factor, then look for an appropriate solution.  On a desktop computer, things are usually disk drive and network bound and the only way to mitigate is by adding more RAM.

---

### Post by Sporkman on 2007-09-28
> **Tachyon_ said:**
> Interesting performance comprasion that has Linux and BSD, Linux owned and FreeBSD was really good too:
[http://bulk.fefe.de/scalability/]("http://bulk.fefe.de/scalability/")

Look at the supercomputer list, which I think is the most descriptive (performance is really crucial and expensive):
Linux 77.80 % 
Windows 0.40 % 
Unix 12.00 % 
BSD Based  0.80 %  	
[http://www.top500.org/stats/list/29/osfam]("http://www.top500.org/stats/list/29/osfam")


2.6 has better performance than 2.4 in almost all cases. First is the difference in the running programs, that in your case seems to be the most effective. But, when you get these out of the way, run 20 process in 2.4 or 2.6, 2.6 pwns. To get equal measurements, you should recompile kernel with things that are only needed. Ubuntu ships with lots of stuff inside the kernel too. This is my hypothesis that the first link seems to prove.
You claimed the DOS is fastest. However, the kernel of the DOS can not take the advantage of modern processors (processor matters much as you said, but kernel has to support these things). I would argue that any *nix kernel is better on modern machines, especially when we need to run more programs or one program that links to libaries or has threads. I don't see the supercomputers running DOS.
FreeBSD and UNIX (solaris) have a really good performance, much better than Linux had way back (2.4) then. Now things are mostly equal I would say.

Thanks, very interesting.

---

