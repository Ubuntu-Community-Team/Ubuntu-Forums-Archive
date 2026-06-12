---
title: "OS wars! ;) Benchmark"
date: 2011-03-08
forum: The Cafe
---

### Post by Ben Page on 2011-03-08
Hey Ubuntuers!

Have you ever had that talk...Linux sucks, Windows Rules, Macs are the fastest and magical computers? LOLz!

Check out these Geekbench results, they are all done on the same hardware, nothing except the OS is changed. All benches are run in 32-bit OSs. 

Never seen this kind of direct comparison, I think Ubuntu is on it's way to pawn the arrogant competition ;)

---

### Post by Kirboosy on 2011-03-08
Do you want us to upload screenshots of direct comparisons of the different OS on our systems too? Or can we just upload a single benchmark from one OS?


~Caboose 

PS. Sorry if its a dumb question...

---

### Post by 3Miro on 2011-03-08
> **Ben Page said:**
> 
Have you ever had that talk...Linux sucks, Windows Rules, Macs are the fastest and magical computers? LOLz!


This shows that Linux is at least as fast as the other two.

[http://www.top500.org/stats/list/36/osfam](http://www.top500.org/stats/list/36/osfam)

Pull something similar about the bank servers and you have covered the security aspect too.

The only thing left is the difference in commercial programs available.

---

### Post by Ben Page on 2011-03-08
> **Caboose885 said:**
> Do you want us to upload screenshots of direct comparisons of the different OS on our systems too? Or can we just upload a single benchmark from one OS?


~Caboose 

PS. Sorry if its a dumb question...

You can upload what ever you have, maybe different cross platform benchmarks.
I just wanted to upload these so people have something to rub on their argument opponents face :D And I thought it's interesting.

---

### Post by Ben Page on 2011-03-08
> **3Miro said:**
> This shows that Linux is at least as fast as the other two.

[http://www.top500.org/stats/list/36/osfam](http://www.top500.org/stats/list/36/osfam)

Pull something similar about the bank servers and you have covered the security aspect too.

The only thing left is the difference in commercial programs available.

Yes, this concerns me the most! If there was CS5 Master Collection and MS Office 2010 for Ubuntu, I would ditch the other two in this instant. I'm aware of alternatives, but that's not an option in my case.

---

### Post by NightwishFan on 2011-03-08
I do not put much stock in any benchmarks. Does this one simulate some random artificial workload?

---

### Post by Ben Page on 2011-03-08
> **NightwishFan said:**
> I do not put much stock in any benchmarks. Does this one simulate some random artificial workload?

Yes, benchmarks are too "synthetic" and they are not necessarily representative when it comes to real life use cases, but Geekbench examines all spheres of computer hardware and runs pretty relevant tests. More info about Geekbench here: [http://www.primatelabs.ca/geekbench/](http://www.primatelabs.ca/geekbench/)

---

### Post by NightwishFan on 2011-03-08
Thanks for the link. I will check it out. :)

---

### Post by GWBouge on 2011-03-08
Yup.  What should be noted running a 32-bit test on 64-bit OS's, though?  Especially whereas most software on the Windows side is still 32-bit (most of the large programs I use, that is, such as games), but on the Ubuntu side is 64-bit?

---

### Post by Kirboosy on 2011-03-08
Here you go. Everything is 64 Bit but the program only ran in 32 bit cause its the trial version (dumb)

My netbook is a Dell Duo and my Desktop is a homebuilt computer.

---

### Post by Lucradia on 2011-03-08
> **Caboose885 said:**
> Everything is 64 Bit but the program only ran in 32 bit cause its the trial version (dumb)

And this is why I won't test.

---

### Post by Spr0k3t on 2011-03-09
Would be nice to see the 64bit results.

[http://browse.geekbench.ca/geekbench2/view?id=375079](http://browse.geekbench.ca/geekbench2/view?id=375079)

---

### Post by handy on 2011-03-09
Comparisons don't mean squat.

The bottom line is, is a user (company) content with the efficiency/efficacy of their hardware/OS/application solution(s) & the professional support available for them?

Some tasks require huge amounts of hardware to satisfy a user's requirement(s). 

The choice of OS is unimportant. What is important is running the specialised software required for the task at hand. Inefficiency in any quarter costs time, money & credibility. Credibility can be the most costly variable of all.

If this software is available on a stable & free OS; well then that is a plus. 

If it is not, then more money must be spent buying the OS (so what?).

Whether money is saved or lost by using a free OS is debatable, due to the range of variables involved that include system support, hardware compatibility & professional standard application availability.

---

### Post by 3Miro on 2011-03-09
> **handy said:**
> 
The choice of OS is unimportant. What is important is running the specialised software required for the task at hand. Inefficiency in any quarter costs time, money & credibility. Credibility can be the most costly variable of all.


Not entirely true. A few years ago I had MATLAB on both Linux and Windows. A computation that takes several hours would run under Linux, but would crash Windows XP. Do you think Vista can run on 100% CPU and 80% Memory for one week straight? Ubuntu has no trouble with it. The choice of OS does matter.

---

### Post by Lucradia on 2011-03-09
> **3Miro said:**
> Not entirely true. A few years ago I had MATLAB on both Linux and Windows. A computation that takes several hours would run under Linux, but would crash Windows XP. Do you think Vista can run on 100% CPU and 80% Memory for one week straight? Ubuntu has no trouble with it. The choice of OS does matter.

AMD can run under 100% CPU easier than Intel to be honest. Try using the betas of Folding@Home using the 64-bit optimized ones. They can tax your CPU to almost un-usability, but won't crash your system, it'll just make it act really slow (Linux will still allow you to use the mouse easily; but not Windows.)

A very simple test though is to use a timer and then execute a fork bomb on each system. (Make sure to disable advanced firewalls such as COMODO; as they will try to stop a buffer overflow.)

---

### Post by 3Miro on 2011-03-09
> **Lucradia said:**
> AMD can run under 100% CPU easier than Intel to be honest. Try using the betas of Folding@Home using the 64-bit optimized ones. They can tax your CPU to almost un-usability, but won't crash your system, it'll just make it act really slow (Linux will still allow you to use the mouse easily; but not Windows.)

A very simple test though is to use a timer and then execute a fork bomb on each system. (Make sure to disable advanced firewalls such as COMODO; as they will try to stop a buffer overflow.)

The mouse issue is probably related to the memory. The biggest hit on performance is when you fill all of memory and then have to go on swap. In the case of a supercomputer, the OS makes huge difference. Win7 uses about a gig of RAM just for itself, suppose you have 1000 machines that is a terabyte of RAM. A out-of-the-box Ubuntu would cut that by a factor of 4. Optimized Linux can go below 100MB per node and I would imagine Windows server would do better than Win7.

Bottom line is, the OS does matter.

---

### Post by chucky chuckaluck on 2011-03-09
I'd be curious to see how the Win7 and Ubuntu compare to Snow Leopard on a iMac. And, I guess you could put Mac OS X x86 in there, too.

---

### Post by handy on 2011-03-10
> **3Miro said:**
> Not entirely true. A few years ago I had MATLAB on both Linux and Windows. A computation that takes several hours would run under Linux, but would crash Windows XP. Do you think Vista can run on 100% CPU and 80% Memory for one week straight? Ubuntu has no trouble with it. The choice of OS does matter.

There are always exceptions. :)

---

### Post by Khakilang on 2011-03-10
To me I am not so concern about performance since its only a small difference. But I am more concern on other issue like virus and spyware. Bit its good to know.

---

### Post by Lucradia on 2011-03-10
> **Khakilang said:**
> To me I am not so concern about performance since its only a small difference. But I am more concern on other issue like virus and spyware. Bit its good to know.

viruses and malware aren't really an issue with Linux; most have all been patched immediately after they've been found. However; no matter the system, a trojan will always succeed.

---

