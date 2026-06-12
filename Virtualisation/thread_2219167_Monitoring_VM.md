---
title: "Monitoring VM"
date: 2014-04-23
forum: Virtualisation
---

### Post by ivana2 on 2014-04-23
Hi,

As a part of my master thesis, my mentor wants me to measure energy  consumption of different monitoring tools for a single virtual machine,  so I have Ubuntu 12.04 running on VMware Player on Windows 7 host OS.  Since I'm a total newbie in this field, I googled tools like nagios,  groundwork, solarwinds, but it looks quite complex just for measuring  single VM and then measuring its own consumption. I hope somebody have  some other suggestion.

---

### Post by heiko_s on 2014-04-23
The only thing I trust is a digital watt meter. But that would only measure the power consumption of the entire PC. Running your VMware player on a Windows host is probably not the best starting point, as Windows does weird things and in unpredictable times. Essentially you would have to disable tons of "features" that can kick in anytime (for example when it feels that it's been running idle for a while, it might start some "housekeeping" tasks or run "indexing" or "updates", just take a guess).

If you had a Linux host, you could more easily control the housekeeping tasks if there are any. Even though I run an ordinary desktop edition with tons of applications as well as some ssh server and other essentials, I don't notice any power consumption variations when running idle.

So one possible way would be to:
1. Measure the power consumption of the host while idle over some time.
2. Start the VM, let it settle in, and measure the power consumption over some time.
3. Start the application inside the VM, let it settle and measure the power consumption, again over some time.

Always note the average and lowest values.

Hope I haven't missed the point here.

Frankly, I can't see how tools like nagios, groundwork, etc. can measure energy consumption without a measuring device. Of course, they could estimate (relative) power consumption based on CPU load (%), Vcore voltage, etc. that could be read out from the m/b monitoring chips or the CPU. I'm not familiar with any of these monitoring tools, though I've seen a few in the past.

---

