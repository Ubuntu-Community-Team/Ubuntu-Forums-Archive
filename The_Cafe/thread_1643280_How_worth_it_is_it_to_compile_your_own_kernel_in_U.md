---
title: "How worth it is it to compile your own kernel in Ubuntu?"
date: 2010-12-11
forum: The Cafe
---

### Post by user1397 on 2010-12-11
To the people that do this, do you see any significant improvements/advantages to compiling your own kernel in Ubuntu? I also want to know if you compile your own kernel, do you just keep that kernel basically forever until you recompile or something? You never update it correct?

Also what is the best guide for this?

---

### Post by NightwishFan on 2010-12-11
There is no significant advantage unless you already know what you need. For example, I like to play around with different options such as enabling full preemption, disabling some options such as cgroups.

The generic Ubuntu kernel will work fine for you.

---

### Post by Spice Weasel on 2010-12-11
It's only really needed/worth it if some firmware you need is disabled by default.

---

### Post by 3Miro on 2010-12-11
I do heavy computations on my machine and I did recompile the Ubuntu kernel for 9.10 giving it a server flavor and optimizing it for my CPU. It resulted in about 8% improvement in performance, however, this is dependent on what you do, how you do it and exactly what your hardware is. Unless you are doing something very heavy, you should stick with the generic one.

As for the updates, I would simple recompile the kernel every time I see an update to the generic Ubuntu kernel (and I have some free time).

On the other hand, if you want to learn more about Ubuntu and Linux in general, compiling your own kernel is a good first step.

---

### Post by bwhite82 on 2010-12-11
This task isn't for the faint of heart. I've tried and failed several times to compile my own kernel. You'd think it would be somewhat easy...you can list your hardware in a terminal and then find all of it in a nice graphical kernel compilation tool..and be on your way. NOPE.

It either failed to compile or failed to boot (more the latter).

Advantage: You can feel good about compiling your own kernel, totally suited to your machine

Disadvantage: You go through a bottle of aspirin.

---

### Post by 3Miro on 2010-12-11
> **Soldierboy said:**
> This task isn't for the faint of heart. I've tried and failed several times to compile my own kernel. You'd think it would be somewhat easy...you can list your hardware in a terminal and then find all of it in a nice graphical kernel compilation tool..and be on your way. NOPE.

It either failed to compile or failed to boot (more the latter).

Advantage: You can feel good about compiling your own kernel, totally suited to your machine

Disadvantage: You go through a bottle of aspirin.

Depends on what exactly you are doing. It took me 5 attempts to manage to boot Gentoo properly, but then I was going for the bare minimum, I wanted to compile only what I would use. Ubuntu gave me trouble only once and it was because I had removed some random things and had no clue what I was doing. If you take the existing Ubuntu generic kernel and tweak only the options for the CPU type and preemption, then there is no reason why it wouldn't compile and boot just fine.

---

### Post by NightwishFan on 2010-12-11
I have a tutorial for compiling a kernel with the CK patches. Follow these steps except skipping the CK patching part to do is easily:
[http://ubuntuforums.org/showthread.php?t=1637004](http://ubuntuforums.org/showthread.php?t=1637004)

I really do not much recommend using CK any more. It does not help my workloads (nor hurt it).

---

### Post by bwhite82 on 2010-12-11
> **3Miro said:**
> Depends on what exactly you are doing. It took me 5 attempts to manage to boot Gentoo properly, but then I was going for the bare minimum, I wanted to compile only what I would use. Ubuntu gave me trouble only once and it was because I had removed some random things **and had no clue what I was doing.** If you take the existing Ubuntu generic kernel and tweak only the options for the CPU type and preemption, then there is no reason why it wouldn't compile and boot just fine.

Yeah this was probably my problem. You really need to know what you are doing if you want a successful compile and boot. Because of this thread, I *may*, just may, try my hand again...

---

