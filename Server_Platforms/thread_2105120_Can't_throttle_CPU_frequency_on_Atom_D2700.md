---
title: "Can't throttle CPU frequency on Atom D2700"
date: 2013-01-15
forum: Server Platforms
---

### Post by Jack Kelly on 2013-01-15
Hi there,

I'm trying to throttle the CPU speed on my [Intel Atom D2700]("http://ark.intel.com/products/59683/Intel-Atom-Processor-D2700-1M-Cache-2_13-GHz") (Cedarview 32nm) on an [Intel Desktop Board D2700MUD]("http://ark.intel.com/products/56457/Intel-Desktop-Board-D2700MUD").  I'm running Ubuntu Server 12.10 64-bit.  I have the latest motherboard BIOS installed (0074).

I have installed [FONT=Courier New]cpufrequtils[/FONT].  When [FONT=Courier New]cpufrequtils[/FONT] was installed, I noticed these worrying messages:

```

Setting up libcpufreq0 (008-1) ...
Setting up cpufrequtils (008-1) ...
 * Loading cpufreq kernel modules...  [fail] 
 * CPUFreq Utilities: Setting ondemand CPUFreq governor... * disabled, governor not available... [ OK ] 

```Then, when I run[FONT=Courier New] cpufreq-info[/FONT], I get this error:

```

jack@logger:~$ cpufreq-info
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 2:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.
analyzing CPU 3:
  no or unknown cpufreq driver is active on this CPU
  maximum transition latency: 4294.55 ms.

```Also: I don't have a [FONT=Courier New]cpufreq[/FONT] directory in [FONT=Courier New]/sys/devices/system/cpu/cpu?/[/FONT]

Incidentally, I understand that Intel provide very little Linux support for the graphics processor integrated onto the D2700 (because this specific GMA core is based on PowerVR).  I wonder if Intel have also failed to provide adequate Linux support for the frequency throttling on this CPU?

**UPDATE**:
I've found [a more appropriate place]("http://ubuntuforums.org/showthread.php?p=12456390#post12456390") to post this question.  Please can we delete this question?  Sorry for the inconvenience.

---

