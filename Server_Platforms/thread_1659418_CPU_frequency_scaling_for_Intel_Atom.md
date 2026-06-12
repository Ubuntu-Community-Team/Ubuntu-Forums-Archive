---
title: "CPU frequency scaling for Intel Atom?"
date: 2011-01-04
forum: Server Platforms
---

### Post by wilco.vertegaal on 2011-01-04
I am running Ubuntu 10.10 Server on an Intel Atom D510 based mainboard. I would like to enable CPU frequency scaling to save as much power as I can, for these two reasons:

* The server is basically a file server that is idling most (99.9%) of the time. No time critical processes on it.
* The PSU fan tends to speed up easily, depending on power demand, and since the server is right next to my desk I would like it to be as quiet as possible.

However I do not seem to be able to turn on CPU power saving features. Apparently a CPU frequency scaling driver is missing. I installed cpufreqd and cpufreq-utils, and cpufreq-info gives me the following output:

```
wilco@Boromir:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.

```

I have no idea how to solve this. I tried installing powernowd instead, which didn't help, and that's as far as my knowledge goes. I could not find any clues on how to install cpu frequency scaling drivers on Ubuntu Server. I'm starting to worry that frequency scaling is disabled in Ubuntu Server.

Any help is greatly appreciated.


(I'm putting this here and not in Hardware forum because the CPU itself and the board are capable of CPU frequency scaling. I learnt this in the Netbook Remix forum: [Power Management on Intel Atom]("http://ubuntuforums.org/showthread.php?t=1431982&highlight=atom+cpufreq"). Also the CPU was perfectly capable of frequency scaling when I ran FreeNAS on it: the CPU was running at 267MHz almost 24/7.)

---

