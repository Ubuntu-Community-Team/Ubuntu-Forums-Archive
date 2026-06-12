---
title: "Stop CPU downclock on ubuntu-server"
date: 2011-04-09
forum: Server Platforms
---

### Post by teuneboon on 2011-04-09
For some reason my Ubuntu server 10.10 installation decided to downclock my 2.8GHz duo-core CPU to 800MHz. Now I know this is a feature in Ubuntu Desktop edition, and I know how to disable it there(not by commandline though). But now I want to disable it on my server(should always be in "performance mode". How do I do that(please note: I only have commmandline, already had answers of people telling me to do stuff in GNOME :P)

---

### Post by disabledaccount on 2011-04-09
I know only 2 reasons why it could be nacessary to force constant CPU frequency:
- avoid TSC errors in some multi-threaded programs
- derived from above - ensure constant timings in programs that cooperate with some specialised external hardware, like LPT programming interfaces.

If this is not the case, then it's only waste of energy. It is more reasonable to tune scaling governor for more aggressive or more conservative behaviour - so it will better fit real load conditions.

google for cpufreq and read this (one of hundreds similar web pages):
[http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html](http://www.pantz.org/software/cpufreq/usingcpufreqonlinux.html)

---

### Post by psusi on 2011-04-09
+1

Disabling frequency scaling is just a waste of power and heat ( which will wear out the hardware faster ).  It only drops the frequency when the cpu is idle so it's not like you are loosing any performance.

---

### Post by Vegan on 2011-04-09
The automatic power features do not have a material amount of effect on performance.

I use an on demand profile which is ideal for a web appliance

---

### Post by teuneboon on 2011-04-10
Ok, so when I need the CPU in many short bursts it's not slower?(because it has to switch to a higher clock everytime). Cause that's my main concern about this.

---

### Post by disabledaccount on 2011-04-10
It will be - if load is too low or load peak is too short to trigger frequency switching. But as I said before - You can tune the scaling governor to fit Your needs. You can set it to rise the frequency immediately to max, maintain it for longer period and slowly lower it by one level at each period - this way only first load peak will be a bit slower and You wont lose power saving functionality.
Conservative governor is probably what You need - it can be tuned very precisely to fit the load profile:
[http://www.ibm.com/developerworks/linux/library/l-cpufreq-2/index.html](http://www.ibm.com/developerworks/linux/library/l-cpufreq-2/index.html)

edit:
Just for curiosity: what type of load peaks do You have? If this is load from network queries or services then single microseconds of delay are meaningless.

---

### Post by kiddfroster on 2011-04-10
As stated above, it's not a big deal, because it's just saving power when there isn't a load. I would still tweak the scaling governor as mentioned above to make sure that you're getting the optimal performance for your particular situation.

---

### Post by psusi on 2011-04-11
> **teuneboon said:**
> Ok, so when I need the CPU in many short bursts it's not slower?(because it has to switch to a higher clock everytime). Cause that's my main concern about this.

Theoretically yes, but practically no.  The time it takes to switch is usually measured in microseconds so even measuring it with a synthetic benchmark is not easy.  If you aren't specifically looking hard for the tiny difference, you won't notice it.

---

