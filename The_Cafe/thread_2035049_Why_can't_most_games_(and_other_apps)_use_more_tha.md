---
title: "Why can't most games (and other apps) use more than two processors?"
date: 2012-07-29
forum: The Cafe
---

### Post by venom104 on 2012-07-29
Okay, I'm going off a bunch of stuff I heard on the internet, so forgive me if I have things wrong.

Anyway, from what I hear, most games can't use beyond two cores of a multicore system. Why is this?

I always assumed that the ability to run more than one core dealt with threading...which is defined by wikipedia as..."A technique by which a single set of code can be used by several processors at different stages of execution."

My take on multithreading is that you basically program small segments of code into threads (which means the code actually running), then you basically place the thread on an advanced queue and wait for the operating system to actually run the thread.

If this is true, then threading is mainly handled by the operating system, and not the programmer (I'm talking about RUNNING and TERMINATING THREADS, not programming the segments of code). So why can't these gams (and other apps) use more than two cores? Is it a limit set by the operating system? What about if I turn the processes affinity to ALL my cores, does that change anything?

---

### Post by mcduck on 2012-07-29
> **venom104 said:**
> Okay, I'm going off a bunch of stuff I heard on the internet, so forgive me if I have things wrong.

Anyway, from what I hear, most games can't use beyond two cores of a multicore system. Why is this?

I always assumed that the ability to run more than one core dealt with threading...which is defined by wikipedia as..."A technique by which a single set of code can be used by several processors at different stages of execution."

My take on multithreading is that you basically program small segments of code into threads (which means the code actually running), then you basically place the thread on an advanced queue and wait for the operating system to actually run the thread.

If this is true, then threading is mainly handled by the operating system, and not the programmer (I'm talking about RUNNING and TERMINATING THREADS, not programming the segments of code). So why can't these gams (and other apps) use more than two cores? Is it a limit set by the operating system? What about if I turn the processes affinity to ALL my cores, does that change anything?
Simply becasue splitting programs (and especially games) into multiple threads isn't such an easy task most of the time. For example in case of a game the task of keeping all separate threads in sync with each other can be quite hard, the sound, AI, physics, graphics rendering and everything else has to be in sync with each other adn each part requires information from others. And more often than not things can't be broken into separate task at all (or doing that wouldn't improve performance) as doing one thing depends on the results of something else, and managing such things between separate threads can easily be more complicated and less efficient than simply running everything in one thread instead.

So yes, running threads is up to the operating system, and it definitely has no problems doing that. But designing the programs in a way that they can actually run in multiple threads is complicated task.

---

### Post by miegiel on 2012-07-29
From what I understood, is that you can multithread games, but 1 thread will do about half the work that needs to be done. I think it's the graphics thread. The other threads, of the game, the OS and other programs will be divided over the other cores.

---

### Post by venom104 on 2012-07-29
> **mcduck said:**
> Simply becasue splitting programs (and especially games) into multiple threads isn't such an easy task most of the time. For example in case of a game the task of keeping all separate threads in sync with each other can be quite hard, the sound, AI, physics, graphics rendering and everything else has to be in sync with each other adn each part requires information from others. And more often than not things can't be broken into separate task at all (or doing that wouldn't improve performance) as doing one thing depends on the results of something else, and managing such things between separate threads can easily be more complicated and less efficient than simply running everything in one thread instead.

So yes, running threads is up to the operating system, and it definitely has no problems doing that. But designing the programs in a way that they can actually run in multiple threads is complicated task.

Wow, expecting a response so fast. Thank you for answering my question! You did miss one thing though, what about the process affinity? What happens if a program only supports 2 cores, and I force the affinity to 8? Will that do anything?

---

### Post by stmiller on 2012-07-29
It depends on how the software is coded/written. Games are tough for multi-threaded but something like handbrake can max out as many cores as you've got.

Cheers,

---

### Post by venom104 on 2012-07-29
Thanks to everybody for the responses.

Thread solved.

---

### Post by mcduck on 2012-07-29
> **venom104 said:**
> Wow, expecting a response so fast. Thank you for answering my question! You did miss one thing though, what about the process affinity? What happens if a program only supports 2 cores, and I force the affinity to 8? Will that do anything?
Raising the processor affinity wouldn't do anything. A program can only run as many threads as it was programmed to use.

---

### Post by nec207 on 2012-07-29
> **venom104 said:**
> Okay, I'm going off a bunch of stuff I heard on the internet, so forgive me if I have things wrong.
 
Anyway, from what I hear, most games can't use beyond two cores of a multicore system. Why is this?
 
I always assumed that the ability to run more than one core dealt with threading...which is defined by wikipedia as..."A technique by which a single set of code can be used by several processors at different stages of execution."
 
My take on multithreading is that you basically program small segments of code into threads (which means the code actually running), then you basically place the thread on an advanced queue and wait for the operating system to actually run the thread.
 
If this is true, then threading is mainly handled by the operating system, and not the programmer (I'm talking about RUNNING and TERMINATING THREADS, not programming the segments of code). So why can't these gams (and other apps) use more than two cores? Is it a limit set by the operating system? What about if I turn the processes affinity to ALL my cores, does that change anything?
 
Hardly most software is coded for more than 2 cores.This is slowing changing with many cores now.
 
 
Also games hardly use the CPU now they mostly use video card . So 8 or 12 core CPU hardly would be faster than 2 core CPU.
 
If you into gaming get best video card out there.

---

