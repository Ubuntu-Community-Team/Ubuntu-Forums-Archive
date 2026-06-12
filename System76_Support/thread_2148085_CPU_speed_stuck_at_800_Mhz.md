---
title: "CPU speed stuck at 800 Mhz"
date: 2013-05-23
forum: System76 Support
---

### Post by DVDFortyTwo on 2013-05-23
A couple of days ago I noticed a lot of my scripts running a fair bit slower than expected on my Serp7 with 13.04 and 3.8.0-21-generic kernel.  I think I've finally been able to determine the reason, but I have no idea how to fix it.  I did[FONT=Ubuntu Mono] sudo apt-get cpufrequtils and found out that my cpu speed seems to be stuck at 800 Mhz even with a lot of stuff running using 100% cpu when the cpu governor was set to "ondemand".  This made no sense so I forced it into "performance" by doing cpufreq-set -r -g performance, but the cpu speed still seems stuck at 800 Mhz on all the cores and things are still slow.  I don't understand this, but I'm a newbie at sysadmin stuff.  This just started happening and I don't know how to fix it.  Thanks for any help.  Here's the output of cpufreq-info showing that it's set at performance but cpu is at 800 Mhz.  This sounds like the exact same problem described here [/FONT][http://askubuntu.com/questions/296653/ubuntu-13-04-cpu-frequency-scaling-stuck-on-lowest-frequency?rq=1](http://askubuntu.com/questions/296653/ubuntu-13-04-cpu-frequency-scaling-stuck-on-lowest-frequency?rq=1) but I'm not clear how he "manually" set his frequencies.[FONT=Ubuntu Mono]
[/FONT]> cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [EMAIL="cpufreq@vger.kernel.org"]cpufreq@vger.kernel.org[/EMAIL], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:32.09%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:10.18%, 800 MHz:57.73%  (3342)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:31.17%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:10.23%, 800 MHz:58.60%  (3005)
analyzing CPU 2:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 2
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:31.82%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:14.94%, 800 MHz:53.24%  (3798)
analyzing CPU 3:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 3
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:31.11%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:8.26%, 800 MHz:60.63%  (2922)
analyzing CPU 4:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 4
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:30.78%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:7.54%, 800 MHz:61.68%  (1892)
analyzing CPU 5:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 5
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:30.33%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:10.42%, 800 MHz:59.25%  (1804)
analyzing CPU 6:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 6
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:30.33%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:8.05%, 800 MHz:61.62%  (1924)
analyzing CPU 7:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1 2 3 4 5 6 7
  CPUs which need to have their frequency coordinated by software: 7
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.50 GHz
  available frequency steps: 2.50 GHz, 2.50 GHz, 2.00 GHz, 1.80 GHz, 1.60 GHz, 1.40 GHz, 1.20 GHz, 1000 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 2.50 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz (asserted by call to hardware).
  cpufreq stats: 2.50 GHz:30.65%, 2.50 GHz:0.00%, 2.00 GHz:0.00%, 1.80 GHz:0.00%, 1.60 GHz:0.00%, 1.40 GHz:0.00%, 1.20 GHz:0.00%, 1000 MHz:14.12%, 800 MHz:55.23%  (2121)


---

### Post by ohnonot on 2013-05-24
well firstly you have to set things like that with root privileges (sudo) but it still might not work.
how and when did the problem start?
i'm very bad at reading long output (what you posted), but it seems your governor is set to performance and the system somehow doesn't like that?
what about the computer getting hot, noise from the fan? consider cleaning the fan.
then, you'd have to find out from which config file the governor is set during boot and maybe change sth there.

ps: greetings to florida! i recently became a fan of carl hiaasens books, so i developed an affinity to florida...

---

### Post by DVDFortyTwo on 2013-05-24
> **ohnonot said:**
> well firstly you have to set things like that with root privileges (sudo) but it still might not work.
how and when did the problem start?
i'm very bad at reading long output (what you posted), but it seems your governor is set to performance and the system somehow doesn't like that?
what about the computer getting hot, noise from the fan? consider cleaning the fan.
then, you'd have to find out from which config file the governor is set during boot and maybe change sth there.

ps: greetings to florida! i recently became a fan of carl hiaasens books, so i developed an affinity to florida...
Thanks.  Sorry about the long output, but I didn't know how else to show that it was messed up, at least based my limited understanding of how it's supposed to work.  At any rate, after some further research it appears as though I'm experiencing something extremely similar to this bug.  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1174169](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1174169).  I think what happened for me is that a few days ago, there was lightning in the area so I took the laptop off AC power and ran it on battery for a while.  When the storm passed, I plugged it back into AC power, and I think that's when the trouble began.  A reboot or shutdown didn't seem to have any affect.

EDIT:  OK, I just updated to 3.8.0-22 generic kernel and rebooted, and the problem still seemed to be there.  However, on a random whim, I went onto battery power from AC for a few seconds and then plugged it back into AC, and now it seems to be functioning normally again!  I think there's a bug somewhere along the line, but at least I don't think it's my physical hardware breaking so that makes me happier.  I work in the sciences and do a lot of scientific computing, but sysadmin stuff gives me a headache.

I run sudo stress -c 8 in a terminal window while doing watch grep \"cpu MHz\" /proc/cpuinfo in order to verify that it's cycling up CPU speed correctly.  It's going up to 2.50 GHz like I'd expect it to now with stress, whereas before it rarely ever made it past 1.0 Ghz.

---

### Post by ohnonot on 2013-05-24
curious.
i hope it stays ok.

---

### Post by RizSilverthorn on 2013-06-07
> **DVDFortyTwo said:**
> ... However, on a random whim, I went onto battery power from AC for a few seconds and then plugged it back into AC, and now it seems to be functioning normally again!...

Just wanted to say I have exactly the same issue. I tried the "pull out PSU and re-insert" trick and that works! My battery is completely fubar - lasts <2 mins from full charge so didn't think about running from it for a couple of seconds. I'm guessing it's a BIOS thing as I didn't have the mains power turned on when switching on the laptop, so it booted using the battery.

---

