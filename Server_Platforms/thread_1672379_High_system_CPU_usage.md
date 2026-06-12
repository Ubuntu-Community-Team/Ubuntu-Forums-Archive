---
title: "High system CPU usage"
date: 2011-01-20
forum: Server Platforms
---

### Post by Blacklite on 2011-01-20
[IMG]http://i.imgur.com/4q1us.png[/IMG]

I am getting these random spikes where htop shows MASSIVE amounts of "red" CPU usage, for which there is no explanation in htop's process list. All the processes are 1% cpu or less, except Apache and my game server, at about 20% and 10% respectively. I checked iostat at the same time and it showed this:

```

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          12.70    0.00   64.00   11.48    0.00   11.83

Device:            tps   Blk_read/s   Blk_wrtn/s   Blk_read   Blk_wrtn
sda             118.50         0.00      3384.00          0       6768
sdb             115.00         0.00      3384.00          0       6768
md0             454.50         0.00      3388.00          0       6776

```

**Specs:** Xeon E5504, 8gb ram, 2x1tb SATA w/ hardware raid 1

**Webmin:** CPU usage: 13% user, 46% kernel, 32% IO, 9% idle

**uptime:** 21:39:20 up 1 day,  6:20,  2 users,  load average: 251.28, 248.00, 203.86

Just thought I should also mention that my PHP mail() function takes AGES, and doesn't deliver the mail sometimes...

If anyone can help I'd be very grateful...

Cheers

---

### Post by hawk2010 on 2011-01-21
Can you check whether there is no dust covered in fans of the system? This may overheat the CPU.

---

### Post by disabledaccount on 2011-01-21
Blacklite:
In htop go to setup->display options->uncheck "hide kernel threads"

---

### Post by Blacklite on 2011-01-21
> **hawk2010 said:**
> Can you check whether there is no dust covered in fans of the system? This may overheat the CPU.

It's a brand new server.

> **tomazzi said:**
> Blacklite:
In htop go to setup->display options->uncheck "hide kernel threads"

Did that, but still can't see any kernel threads using a lot of CPU...

I also turned off Apache when it was happening, and it didn't affect the CPU usage.

---

### Post by disabledaccount on 2011-01-21
Can you observe same behaviour in different monitoring tools like top?
Have you tried to increase/decrease update frequency?

One thing to know about "CPU load" is that it's a fake - really. CPU load means: how much time in given period was used by monitored processes/threads -> so it highly depends on update period length.
In other words: every process loads CPU at 100% during execution.

---

### Post by Blacklite on 2011-01-21
During the spikes, top shows:

```
Cpu(s): 27.8%us, 53.4%sy,  0.0%ni, 11.9%id,  5.4%wa,  0.0%hi,  1.4%si,  0.0%st
```

---

### Post by disabledaccount on 2011-01-21
I suppose You can see differences...

If Yor system has power saving functions enabled, try to run 'cpufreq -f' together with top/htop - short 90% load spike won't trigger CPU governor to increase frequency (by default)

---

