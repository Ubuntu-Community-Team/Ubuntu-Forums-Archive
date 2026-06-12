---
title: "clock_gettime skips ahead now and then..."
date: 2009-03-25
forum: Server Platforms
---

### Post by FreedomFromWindows on 2009-03-25
Hi,

I have a weird problem with the high resolution clock.

When I wait on an external events, specifically packets arriving on a pcap Ethernet interface at precisely 5mS intervals, every 1.6 seconds there is at least one additional delay of exactly 1mS.  (Sometimes there is more than one, and in that case, one succeeding time will be under-reported by 1mS, but the net effect is that exactly 1mS disappears around 1.6 seconds.)  I am able to check with an external analyzer that the delay is on reception/processing in the server box, not with the device originating the packets.

I have tried various ways around it, including installing the real-time kernel, and putting the thread on its own processor with taskset (and blocking the OS and all other threads/processes from using that processor).  But while the reported jitter goes down with these improvements, all the way down to about +/-2uS, the 1mS jump keeps appearing.

I am running server 8.04, 8.10, and 9.04 (alpha 6 right now).  The behaviour is similar on all of them (with variations in the amount of jitter).

The best results have been with clock_gettime() using CLOCK_MONOTONIC.  CLOCK_REALTIME is no better.

However, because CLOCK_MONOTONIC is guaranteed never to go backward, and is guaranteed consistent across cores in one machine, I believe the OS must occasionally nudge one processor's clock forward to catch up with whatever the fastest one is, or something like that.

There is not AFAIK any guarantee that CLOCK_MONOTONIC won't skip ahead, only that it won't go backward.

One more interesting twist is that I believe this problem may be more severe on a server with Core 2 Duo processor than it is with another machine with an AMD Phenom Quad (though it is running desktop, but while there is more jitter than with server edition, there are no 1mS jumps in time).  It could be the luck of which core the thread is assigned to being either the fastest on the processor (in the case of the AMD?) or the slowest (in the case of the Intel)?

I'm tearing my hair out over this - I'm getting really good accuracy on the timestamping of these incoming messages, except for this periodic and repeatable problem.

Does anyone know if the theory on the OS causing clocks to skip ahead happens to be true?

Are there any other calls I could use instead?  

Because I can isolate the thread to one core and lock it there, I could use the equivalent of a hardware performance counter on the core but that doesn't seem much supported under Linux just yet.  I also tried using the CPU_TIME type clocks, but I think there is some other uncertainty with them because even though the thread is the only thing on the core, and it is running flat out in a hard loop, the CPU time does not increment as fast as real time IIRC.

Also though this is a 'server' question there might be some other forum to do with timing or something that might be better - if you know of one I'd really appreciate the pointer.

Thanks for any and all suggestions!

---

