---
title: "What are the benefits of a realtime kernel?"
date: 2009-12-07
forum: Ubuntu Studio
---

### Post by JohneG on 2009-12-07
I don't know what benefits having a realtime kernel for audio gives the user. Could someone explain it to me? I've heard it's better but i don't know why. Also how would i go about setting it up and how would it affect the rest of my system?

---

### Post by wkulecz on 2009-12-07
It should greatly reduce the worst case latency response to hardware interrupts.  This should insure you sound card doesn't drop data or "glitch" the audio.

It should have no impact on the rest of your system.  If it does, file a bug report.

OTOH, if you are happy with your current audio performance there is no reason to change to the real-time kernel.  Its mostly audio recording and complex multi-channel ouptput that benefits most.

I run the real-time kernel on 6.06 where I have an image processing application.  While I can't say exactly where it happened as the real-time kernel has been updated, situations where I drop frames (dual frame grabbers) have been greatly reduced with no changes to my code.  Initally I could only use BT8x8 based cards that have 8-frame buffer depths in hardware, now I can use SAA713x based cards that only have 3-frame hardware buffer depths.

--wally.

---

### Post by RaumTrug on 2009-12-07
the main (and probably only) benefit is lowering input/output latency without getting dropouts. that means you will be able to record some sound from the input, process it in realtime and listen to the processed sound while it is coming through, hopefully without noticing any delay with your ears! also, if you use synthesizers with a midi keyboard to play/record "live", sound will respond much quicker when you press a key, giving a direct feel.

for other stuff it's pretty useless I guess, it will just make the realtime audio and soundcard i/o stuff "untouchable" by other stuff and responding quicker (higher priority & frequency). downside is that overall performance can drop, and also energy consumption by the cpu!

for setting up look here:

[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

and this might prove very useful for getting latency even lower:

[http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=50adaa1f88479db1986a19297dc552dd](http://wiki.linuxmusicians.com/doku.php?id=system_configuration&DokuWiki=50adaa1f88479db1986a19297dc552dd)

expecially this:

[http://tapas.affenbande.org/wordpress/?page_id=40](http://tapas.affenbande.org/wordpress/?page_id=40)

have fun!

---

### Post by DerickX on 2009-12-08
> **wkulecz said:**
> 
I run the real-time kernel on 6.06 where I have an image processing application.  .
Dapper Drake Wow!

---

### Post by thorgal on 2009-12-08
the RT patched kernel offers an environment very close to hard realtime processing, i.e. a completely deterministic duration for a given process.

This means that if some audio data from your soundcard or some app MUST be delivered to somewhere after a given, well defined amount of time, the RT kernel will ensure that is done, regardless of whatever other processes (like network activity, graphical refresh, etc) are requesting CPU interrupts. 

That's in fact the goal of the RT kernel: ensure complete determinism in process duration. That's where the concept of preemption kicks in: if you allow audio to be treated that way, the audio process threads must preempt some other stuff to maintain full processing priority. A lot of the kernel code has been made fully preemptable. But there are still areas where this is not fully guaranteed.  
 
The vanilla kernel (not fully preemptable) is doing very good nowadays because lots of the work from the RT patch guys has made it into the mainline kernel. That's what I use personally and it's doing great with my hardware at all latencies. YMMV :)

---

