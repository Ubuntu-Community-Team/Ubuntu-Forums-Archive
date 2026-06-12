---
title: "Darwin Kernel vs Linux Kernel"
date: 2010-05-22
forum: The Cafe
---

### Post by Ravernomina on 2010-05-22
Alright, So i have been Digging a lot lately into OpenDarwin, Mac OS X, and the Lovely Tux Linux :D. I was looking at kernel architectures for Both... and it Seems Mac OS X/DarwinOS has the Upper hand in Kernel Tech. Being Able to have the Properties of a MicroKernel and a Monolithic.

**_XNU/MACH(Darwin)_**:
-threads
-processes
-pre-emptive multitasking
-message-passing (used in inter-process communication) 
-protected memory
-virtual memory management
-soft real-time support
-kernel debugging support
-console I/O
-K32 (ability to boot in a full 32bit System)
-K64 (ability to boot into full 64bit System)
-Full BSD Base
-I/O Kit Divice Framework Based on Objective - C++
-Ability to run in a Fully Sandbox System
-Ability to Run 2 OS's at Once (reduces Speed of course :P)[MACH ability]

An thats all i really seen so far

Source: [http://en.wikipedia.org/wiki/XNU]("http://en.wikipedia.org/wiki/XNU")

What do you think?

---

### Post by 3rdalbum on 2010-05-22
Most of that, Linux already has. Linux is a hybrid kernel, not truly monolythic anyway.

Darwin development is all done at Apple anyway... The open-source people found that their contributions were not really welcome.

I would be suspicious of Darwin's security design. It's well-known that Mac OS X works-around and subverts its own security system. maybe some of this happens at kernel level.

---

### Post by Ravernomina on 2010-05-22
> **3rdalbum said:**
> Most of that, Linux already has. Linux is a hybrid kernel, not truly monolythic anyway.

Darwin development is all done at Apple anyway... The open-source people found that their contributions were not really welcome.

I would be suspicious of Darwin's security design. It's well-known that Mac OS X works-around and subverts its own security system. maybe some of this happens at kernel level.

It Does... The Full system sand boxing :P

---

### Post by Xbehave on 2010-05-22
-threads (How is this even a point?)
-processes (How is this even a point?)
-pre-emptive multitasking (Yep, oh and if you don't want it you can have non-preemptive kernel or if you want a compromise there is volentary premption)
-message-passing (used in inter-process communication) (
-protected memory (How is this even a point?)
-virtual memory management (How is this even a point?)
-soft real-time support (See above)
-kernel debugging support (How is this even a point?)
-console I/O (How is this even a point?)
-K32 (ability to boot in a full 32bit System) (How is this even a point?)
-K64 (ability to boot into full 64bit System) (How is this even a point?)
-Full BSD Base (BSD vs GNU but i wouldn't say this is an upperhand)
-I/O Kit Divice Framework Based on Objective - C++ (Not seeing how this is a point either way)
-Ability to run in a Fully Sandbox System (jails/slices are nice)
-Ability to Run 2 OS's at Once (reduces Speed of course :P)[MACH ability] (Parallels is a hypervisor, linux does has a kernel level visualisation which actually provides this feature, along with KSM (to reduce shared memory usage))

in favor of linux we have:
multiple, full MAC systems
many more architectures
many more filesystems (full ntfs r/w support)
many more drivers

---

### Post by Ravernomina on 2010-05-23
> **Xbehave said:**
> -threads (How is this even a point?)
-processes (How is this even a point?)
-pre-emptive multitasking (Yep, oh and if you don't want it you can have non-preemptive kernel or if you want a compromise there is volentary premption)
-message-passing (used in inter-process communication) (
-protected memory (How is this even a point?)
-virtual memory management (How is this even a point?)
-soft real-time support (See above)
-kernel debugging support (How is this even a point?)
-console I/O (How is this even a point?)
-K32 (ability to boot in a full 32bit System) (How is this even a point?)
-K64 (ability to boot into full 64bit System) (How is this even a point?)
-Full BSD Base (BSD vs GNU but i wouldn't say this is an upperhand)
-I/O Kit Divice Framework Based on Objective - C++ (Not seeing how this is a point either way)
-Ability to run in a Fully Sandbox System (jails/slices are nice)
-Ability to Run 2 OS's at Once (reduces Speed of course :P)[MACH ability] (Parallels is a hypervisor, linux does has a kernel level visualisation which actually provides this feature, along with KSM (to reduce shared memory usage))

in favor of linux we have:
multiple, full MAC systems
many more architectures
many more filesystems (full ntfs r/w support)
many more drivers
How is this even a point?

---

### Post by jerenept on 2010-05-23
What, exactly is the meaning of this thread? None of these things means anything to me. BTW, I think it would be better to virtualize an o/s in a program rather than the kernel, for stability reasons.

+1000 on the openness and freedom of the Linux kernel. This makes it superior to any Darwin/Apple kernel!

---

### Post by adeypoop on 2010-05-23
Ravernomina, sorry but xbehave was spot on with his analysis.

:guitar:

---

### Post by Xbehave on 2010-05-23
> **Ravernomina said:**
> How is this even a point?
well most of your points are so basic that anything above a games console OS has them.

> BTW, I think it would be better to virtualize an o/s in a program rather than the kernel, for stability reasons.
xen/parallels are hypervirtulisers that means
1) It has nothing to do with darwin vs linux
2) It runs everything virtualised even when your only running one os

---

### Post by Ravernomina on 2010-05-24
> **Xbehave said:**
> well most of your points are so basic that anything above a games console OS has them.


xen/parallels are hypervirtulisers that means
1) It has nothing to do with darwin vs linux
2) It runs everything virtualised even when your only running one os

How is this even a Point?

---

### Post by Shining Arcanine on 2010-05-24
> **Ravernomina said:**
> How is this even a Point?

It is a point because if you were to say what you said in the original post in the computer science department of any serious academic institution, you would be laughed off campus. Almost everything you said were things that are common to both kernels and the microkernel versus monolithic kernel debate is one that ended when people found that they had trouble writing microkernels that performed as well as monolithic kernels, with most kernel development going the hybrid route. Both Linux and Mac OS X's kernel are hybrid kernels. Then there is also the fact that Linux has much more development, far more support and many more features than the Mac OS X kernel, which is only used within Apple's small little world. You will not find the Mac OS X kernel controlling industrial lasers with nanosecond precision or running on equipment on Mars.

---

### Post by Frak on 2010-05-24
90% of the stuff in that list are basic features of a modern kernel. Some of the only things Darwin has over Linux would be what it doesn't include as opposed to most stock Desktop Linux kernels that include the entire kitchen sink.

---

### Post by baxzius on 2011-08-01
> **Shining Arcanine said:**
> It is a point because if you were to say what you said in the original post in the computer science department of any serious academic institution, you would be laughed off campus. Almost everything you said were things that are common to both kernels and the microkernel versus monolithic kernel debate is one that ended when people found that they had trouble writing microkernels that performed as well as monolithic kernels, with most kernel development going the hybrid route. Both Linux and Mac OS X's kernel are hybrid kernels. Then there is also the fact that Linux has much more development, far more support and many more features than the Mac OS X kernel, which is only used within Apple's small little world. You will not find the Mac OS X kernel controlling industrial lasers with nanosecond precision or running on equipment on Mars.
i admire your reply.

---

### Post by Bachstelze on 2011-08-01
> **baxzius said:**
> i admire your reply.

How is that even a point?

---

### Post by Paqman on 2011-08-01
> **Shining Arcanine said:**
> You will not find the Mac OS X kernel controlling industrial lasers with nanosecond precision or running on equipment on Mars.

I don't think you'll find Linux on Mars either. All the rovers run on VxWorks.

Apart from that, I agree 100% with your post.

[/nitpicking git]

---

### Post by Iowan on 2011-08-01
From the Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

