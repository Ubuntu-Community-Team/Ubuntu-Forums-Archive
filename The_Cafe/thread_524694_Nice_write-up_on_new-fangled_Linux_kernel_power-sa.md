---
title: "Nice write-up on new-fangled Linux kernel power-saving features"
date: 2007-08-13
forum: The Cafe
---

### Post by Sporkman on 2007-08-13
[http://news.com.com/2102-1007_3-6192865.html?tag=st.util.print](http://news.com.com/2102-1007_3-6192865.html?tag=st.util.print)

> 
**Linux coders tackle power efficiency**

By Stephen Shankland
Story last modified Mon Jun 25 10:55:58 PDT 2007

Maybe you'd be better off if you didn't spend so much time looking at your watch.

That, loosely speaking, is the rationale behind a significant change at the heart of Linux that programmers hope will make the open-source operating system more efficient. New versions of the operating system are being endowed with a "tickless" kernel that forsakes traditional computer time-keeping in an effort to keep the processor in a somnolent, low-power state.

Power efficiency is something every operating system could use. For Linux, efficiency could make the operating system more competitive with Windows on portable computers by extending battery life, and on servers that typically run 24 hours a day, it could cut growing power costs.

The tickless kernel isn't the only effort under way. Intel released software called PowerTop in May that makes it easier to find out what software is needlessly keeping a computer's processor on high alert.

"It makes a lot of sense," Illuminata analyst Gordon Haff said of the power-saving work. "Raw, flat-out horsepower is less and less what the game's about--especially on laptops, which are becoming more common."

Some Linux developments take years to arrive, but the tickless kernel is now making its way into the Linux mainstream.

"The re-engineering has mostly been done," said Linux leader Linus Torvalds of the new kernel. And for higher-level software, PowerTop has been "invaluable, he added. "A lot of people and (Linux) distributions are actually interested in this, so the user applications do seem to be getting fixed."

There's more work to be done, but the progress has been measurable, said Arjan van de Ven, a longtime kernel programmer now working at Intel. "What we see in our lab today is that Linux on a laptop consumes 15 percent to 25 percent less power during idle than a code base of about three months ago," he said.

**Cutting chip power**

Processors, though not the only power drain in a computer, slurp a lot of electrical power--more than a 100-watt lightbulb in many cases. Worse, even more electricity is consumed by fans that blow waste heat out of a computer, and more still by air conditioning in data centers.

But in recent years, chipmakers have given microprocessors the ability to drop down into lower-power states when they don't need to run full throttle. The chip's internal frequency slows, voltage levels drop, and electrical consumption tapers down.

Obviously, processors can go into these power-saving states when a user commands a computer into standby mode. But a lot more can be done. Because gigahertz-frequency processor cycles last less than a billionth of a second, though, chips can actually enter and leave low-power states many times in the interval between two keystrokes of a fast typist.

But an operating system kernel--the core software that handles basic tasks such as scheduling processes and communicating with hardware--isn't always good at avoiding busywork. For one thing, software often needlessly prods the kernel into alertness. For another, the kernel itself can waste energy twiddling its thumbs when it could just as well be lowering its blood pressure and dozing off.

Intel's software helps uncover examples of the first problem. The tickless kernel helps with the second.

**Going tickless**

Version 2.6.21 of the Linux kernel, which Torvalds released in April, includes the tickless option. It was incorporated into Fedora 7, Red Hat's free hobbyist version of Linux.

"In terms of power, it's a huge savings," van de Ven said.

A typical Intel processor for mobile computers consumes a maximum of 1.2 watts in its deepest power-saving state, he said. "The gotcha is that if you wake up every millisecond, you hardly get past the shallow power saving mode," van de Ven said. "The end effect is that tickless gets you into the maximum power save modes, saving significant power and extending battery life."

The tickless kernel still keeps track of time, but in a different way. Instead of checking frequently for work to be done--literally 1,000 times a second in the case of Linux, with each millisecond-long tick of the kernel's clock--the kernel schedules the hardware to interrupt it when it knows a future job will require its attention.

The tickless kernel provides another indirect benefit when it comes to power efficiency: It enables better use of virtualization, technology that lets multiple operating systems run simultaneously on the same computer, by replacing numerous idle machines with fewer, more efficiently used ones.

Tickless kernels mean that the virtualization software that underlies all those operating systems isn't unduly taxed with needless interruptions. So theoretically, administrators can consolidate servers more aggressively.

"If you have a server running 50 virtualized guests, and each guest has a timer tick 1,000 times per second, that is 50 thousand ticks per second, without even doing any work yet," van de Ven said. "With tickless, you go from 1,000 to maybe 10, and suddenly it becomes manageable to do 50 guests."

Michael Larabel, editor of the Phoronix site that tests Linux hardware performance, found the tickless kernel can cut power consumption from 28 watts to 26 watts in IBM's Pentium M-based ThinkPad R52 running Fedora 7.

"A tickless kernel, in conjunction with (processor-based) power-saving technologies, can go a long way in extending the life of the battery and reducing the heat output," Larabel said.

**Peeking with PowerTop**

A tickless kernel isn't much good if higher-level software requires the kernel to schedule frequent wakeup calls. That's where PowerTop comes in.

"A typical Linux distribution has many components that wake the processor up frequently for no good reason," van de Ven said in an announcement of the software. "PowerTop will provide an indication of which...software components are the biggest offenders in slurping up your battery time."

Scrutiny with PowerTop has uncovered power-draw culprits. The Gvim text editor's blinking cursor wakes up the kernel. Evolution e-mail software needs to check for new jobs to do 10 times a second. The GAIM (now called Pidgin) instant-messaging software checks every 5 seconds to see if it should set itself as "idle."

As well as fixing these sorts of issue, the Linux kernel itself needs to be spruced up to better support its own "ticklessness."

"Even though the kernel itself now has all the fundamental timer-handling knowledge, most of the kernel subsystems use some timers for their own handling, and tuning that usage will probably go on for some time," Torvalds said.

And other frontiers need work, van de Ven said. Device drivers--the software modules that let the kernel communicate with hardware such as network cards or keyboards--need to be revamped to better handle power issues.

Another issue is developing power-related policy management software that governs a computer's behavior based on what its user is doing. And yet another thorny one is supporting laptop suspend-resume abilities better so laptop computers can hibernate gracefully.

"On the suspend/resume side there will be a lot of rearchitecting needed, especially for suspend-to-disk," van de Ven said. "It's an ongoing discussion topic in Linux."

But much of that work can take place on a newly tickless foundation. "The heavy lifting is mostly done," Torvalds said. 

---

### Post by phrostbyte on 2007-08-13
Most tests roughly show a 10% power save on laptops, and a whooping 20% on desktop machines. Combine that with millions of computers running Linux, and you are talking about an entire medium sized power plant worth of electricity being saved.

---

### Post by Polygon on 2007-08-13
interesting,

is this a option on kernel compile time, or is it something that you can turn on and off at will? Like it goes into 'tick' mode when a laptop is plugged into ac power, but goes into tickless when your running on battery?

---

### Post by Gremlinzzz on 2007-08-13
Version 2.6.21 of the Linux kernel, which Torvalds released in April, includes the tickless option. It was incorporated into Fedora 7, Red Hat's free hobbyist version of Linux. I don't see ubuntu mentioned im using feisty with 2.6.22-9-generic
But does  the  tickless option run by default or only with  Fedora 7, Red Hat'?

---

### Post by Depressed Man on 2007-08-13
Interesting..if this is in Gutsy already I'm going have to try it again on my laptop.

---

### Post by cobrn1 on 2007-08-13
Maybe a stupid question, but linux is very aggresive with cacheing, right? If you could turn that off you'd save a bit of power/cpu cycles loading stuff into the mem - also, less work on the harddrive, which is (can be) a big power drainer.

---

