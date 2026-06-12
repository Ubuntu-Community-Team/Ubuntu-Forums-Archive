---
title: "A Dual-Kernel OS?"
date: 2009-09-05
forum: The Cafe
---

### Post by chessnerd on 2009-09-05
Alright, dual- and quad-core processors are becoming more and more common every day, almost to the point that any PC you get has at least a dual-core. I started thinking about the evolution of computers towards multiple core processors when I thought of something else: Will we someday see an age of dual- and quad-kernel operating systems?

I think there could be some advantages to a dual-kernel OS, in particular with compatibility and stability. An OS with two Linux kernels might not be much better than a single Linux kernel when it comes to compatibility, but imagine being able to run Linux and BSD applications at the same time because one kernel is Linux, the other is BSD, and they each handle their own programs on one screen at the same time. This would be similar to a virtual machine, but not in that both types of applications are being run natively and neither kernel depends on the other to work. It also might help stability if the two can work individually. Let's say that a Linux/BSD hybrid was created and one kernel failed, even catastrophically. The other could still boot up the system so the user could go in and fix the problem or at least throw their files on a thumb-drive before a full reinstall.

I would never claim to be an expert in OS kernels, so I don't know if this idea is even possible or if it has been discussed a thousand times before on UF (I would doubt that I'm the first person to think of this.) I'm basically just wondering a few things:
1. Is it possible, or even practical, to create an OS with two kernels?
2. What would be the advantages with such a system? Would there be disadvantages?
3. Has a dual-kernel OS already been created?

---

### Post by HappinessNow on 2009-09-05
> **chessnerd said:**
> Alright, dual- and quad-core processors are becoming more and more common every day, almost to the point that any PC you get has at least a dual-core. I started thinking about the evolution of computers towards multiple core processors when I thought of something else: Will we someday see an age of dual- and quad-kernel operating systems?

I think there could be some advantages to a dual-kernel OS, in particular with compatibility and stability. An OS with two Linux kernels might not be much better than a single Linux kernel when it comes to compatibility, but imagine being able to run Linux and BSD applications at the same time because one kernel is Linux, the other is BSD, and they each handle their own programs on one screen at the same time. This would be similar to a virtual machine, but not in that both types of applications are being run natively and neither kernel depends on the other to work. It also might help stability if the two can work individually. Let's say that a Linux/BSD hybrid was created and one kernel failed, even catastrophically. The other could still boot up the system so the user could go in and fix the problem or at least throw their files on a thumb-drive before a full reinstall.

I would never claim to be an expert in OS kernels, so I don't know if this idea is even possible or if it has been discussed a thousand times before on UF (I would doubt that I'm the first person to think of this.) I'm basically just wondering a few things:
1. Is it possible, or even practical, to create an OS with two kernels?
2. What would be the advantages with such a system? Would there be disadvantages?
3. Has a dual-kernel OS already been created?
Sounds like an interesting idea, and one I have never heard of before it sounds like it may be helpful in development say a dual core Kernel with Linux and Haiku for example.

---

### Post by moster on 2009-09-05
I am not sure you guys understand what kernel really is. It is not like car having two instead of one engine.

---

### Post by blueturtl on 2009-09-05
1. Since the kernel is in control of hardware, running two without an abstraction layer (such as a virtual machine) simultaneously would be quite problematic. Though potentially possible, it would hardly be pragmatic.

2. Update the system core without shutting down (potentially no downtime). This could now be done by switching the hardware control to the other kernel not being replaced. This can AFAIK already be accomplished on Linux even but then again also with a single kernel (on-line patches can be applied to a running kernel).

The downside is inherently added complexity. The disadvatages would probably outweight the benefits.

3. See above.

I'm hardly a kernel level hacker myself, so take everything I write with some healthy scepticism.

---

### Post by hessiess on 2009-09-05
Look into hypervisers and virtual machines, thease alow you to run multiple OS's at the same time. In order to run two kernals at the same time, you would effectively need two completely separate computers bolted onto one board. Currently multi-core mashennes are like having multiple graphics cards in one machene, the extra cores just act as add-on prosessors shearing the same resources.

---

### Post by RabbitWho on 2009-09-05
Why not just dual boot? 
It would be nice if there were better dual boot options, I've seen screeshots of proprietary software where you can run windows in a window within Linux or apple, if this came as standard it would be wonderful and would include the advantages you mentioned.

---

### Post by chriskin on 2009-09-05
> **RabbitWho said:**
> Why not just dual boot? 
It would be nice if there were better dual boot options, I've seen screeshots of proprietary software where you can run windows in a window within Linux or apple, if this came as standard it would be wonderful and would include the advantages you mentioned.

do you mean virtual machines? virtualbox is open source (at least one of the two editions)

---

### Post by 3rdalbum on 2009-09-05
The whole thing just sounds like what you can do with a hypervisor. The hypervisor talks to the hardware, the two kernels talk to the hypervisor, the hypervisor allocates access to the screen and I/O. With a bit of hackery foo, you could have both systems running programs on the same X server with the same window manager.

---

### Post by Sporkman on 2009-09-05
You could also have code run kernel-less or "bare metal" on some cores.

---

