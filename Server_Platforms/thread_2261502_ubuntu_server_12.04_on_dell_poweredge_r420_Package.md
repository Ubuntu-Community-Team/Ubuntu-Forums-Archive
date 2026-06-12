---
title: "ubuntu server 12.04 on dell poweredge r420 Package temperature above threshold"
date: 2015-01-19
forum: Server Platforms
---

### Post by tback on 2015-01-19
I've got a two dell poweredge r420 in use as webservers. They run 12.04 (see kernel version below). When they're stressed both of them fill their syslog with temperature warnings:

```
Jan 17 23:26:48 www-1 kernel: [7039978.004640] CPU0: Core temperature above threshold, cpu clock throttled (total events = 122611642)
Jan 17 23:26:48 www-1 kernel: [7039978.004644] CPU6: Core temperature above threshold, cpu clock throttled (total events = 122612238)
Jan 17 23:26:48 www-1 kernel: [7039978.006663] CPU6: Core temperature/speed normal
Jan 17 23:26:48 www-1 kernel: [7039978.029701] CPU0: Core temperature/speed normal
```

Both machine are colocated in a decent datacenter and breathe reasonably clean and cool air. 
Bios Settings are set to maximum performance.
I checked with the datacenter: air temperature is always below 20 degrees Celsius.
I inquired with Dell: They gave me the unsupported OS talk but said it was normal.
I went to the datacenter and checked the fans: they're clean.

What is left to investigate? What did I miss? Or is this in fact normal?

Thanks a lot for your assistance.

```
# uname -a
Linux tfw-www-1 3.2.0-70-generic #105-Ubuntu SMP Wed Sep 24 19:49:16 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by lukeiamyourfather on 2015-01-19
Intel says their TDP is the average load over time in a "real world" setting. In their world servers apparently have lots of idle time... AMD says their TDP is the maximum possible load under any circumstance which is how processors should be rated in my opinion because running at a full load for extended period of time is a fairly common thing.

This average load type of TDP makes it a little fuzzy when selecting processors and cooling for a Intel machine. Take for example an Intel machine with a processor rated at 90W TDP and a machine capable of cooling 90W TDP. Under a continuous load of 100% the average could be more like 135W or higher which is beyond what the cooling can handle so the processor will get throttled to reduce the load (in this case load being heat, not the Linux CPU load).

I wouldn't exactly call it "normal" because they simply sold a machine with more processor power than it can cool when under continuous load but it's par for the course with 1U servers where there's almost no wiggle room for TDP and itty bitty heatsinks. If there will be 100% load on the processor for extended periods of time it's smarter to configure a 1U machine with lower wattage processors so the actual load doesn't exceed the TDP of the cooling. Buying the faster and more expensive processor with a higher TDP that just gets throttled under continuous load in that form factor is a waste of money unless the workload is latency sensitive and isn't continuous.

If the higher TDP processors are needed performance wise and the load will be continuous it would make sense to use a form factor that can accommodate larger heatsinks and larger fans to provide more cooling capacity (like 2U, 3U, 4U, pedestal, etc.). At the end of the day it might not matter much if the throttling doesn't happen often but if it happens all the time it was a poor choice of hardware for the workload.

---

### Post by tgalati4 on 2015-01-19
I would be curious to know if you ran an "approved" operating system, such as Red Hat if the temperatures will still hit throttling with your workload.

As a 1 RU, energy efficient, rack server, compromises have been made.  Obviously running at maximum performance with your workload causes it to overheat.

How often does it overheat if you turn off "Maximum Performance"?  I agree with luke that it's difficult to achieve decent cooling in a 1 RU server because there is very little room to stuff everything that is needed for a high-performance server.

I have a feeling you are not the only one with this problem.  Perhaps it is a poor design.

What is the trigger temperature that causes throttling?  Can you change the temperature in the BIOS?  How long are the warranties on these machines?  It's possible the trigger temperatures were set lower to reduce warranty claims.

---

### Post by lukeiamyourfather on 2015-01-20
> **tgalati4 said:**
> I would be curious to know if you ran an "approved" operating system, such as Red Hat if the temperatures will still hit throttling with your workload.

The only Dell supported operating system on the R420 is Windows. They say other operating systems are supported but they push support to the developer of that operating system, in this case Canonical.

[http://linux.dell.com/files/supportmatrix/Ubuntu_Support_Matrix.pdf](http://linux.dell.com/files/supportmatrix/Ubuntu_Support_Matrix.pdf)
[http://www.ubuntu.com/certification/hardware/201211-12067/](http://www.ubuntu.com/certification/hardware/201211-12067/)

It sounds like a physical limitation of the machine rather than a software issue. I'm pretty sure the same would happen on any other operating system given the same computing load (RHEL, Windows, FreeBSD, take your pick).

One more thing to add to what I posted previously. While the data center might say everything is always a certain temperature there are going to be hot spots and cool spots in most data centers. Measure the ambient temperature of the intake right in front of the server yourself to know for sure.

---

### Post by MAFoElffen on 2015-01-20
Just an idea... I had this on one with a 1U Xeon. What I did was pulled it,. Cleaned off the cpu heat sink paste that was dried up... Used the silver heat sink paste... Was lower temps after that.

The silver type doesn't dry out and harden like the white type does. So if moved, especially on 1U's, the case will sometimes flex... and that flex will break the contact on the heatsink paste (if hardened). The silver type, since it stays a paste...  seems to keep that contact.

A retired Sys Admin friend of mine had suggested this to me when I was having problems.

Someone had mentioned both Intel and AMD. I notice that comparably between the two, Xeons seem to run hotter. Anyone else notice this?

---

### Post by tback on 2015-01-22
[[COLOR=#000000]@lukeiamyourfather[/COLOR]]("http://ubuntuforums.org/member.php?u=774656"):
> Intel says their TDP is the average load over time in a "real world"  setting. In their world servers apparently have lots of idle time... AMD  says their TDP is the maximum possible load under any circumstance  which is how processors should be rated in my opinion because running at  a full load for extended period of time is a fairly common thing.

This average load type of TDP makes it a little fuzzy when selecting  processors and cooling for a Intel machine. Take for example an Intel  machine with a processor rated at 90W TDP and a machine capable of  cooling 90W TDP. Under a continuous load of 100% the average could be  more like 135W or higher which is beyond what the cooling can handle so  the processor will get throttled to reduce the load (in this case load  being heat, not the Linux CPU load).
Very interesting. For the record: The processor is xeon e5-2440 with a TDP of 95W.

To maintain proper etiquette:
Intel & Dell: I am dissapoint. 

/proc/cpuinfo model name:
Intel(R) Xeon(R) CPU E5-2440 0 @ 2.40GHz

---

### Post by tback on 2015-01-22
[[COLOR=#000000]@lukeiamyourfather[/COLOR]]("http://ubuntuforums.org/member.php?u=774656"):
> While the data center might say everything is always a certain  temperature there are going to be hot spots and cool spots in most data  centers. Measure the ambient temperature of the intake right in front of  the server yourself to know for sure.

Thanks for the advice to measure air temperature myself. I'll bring a thermometer next time I visit the datacenter.

---

