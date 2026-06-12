---
title: "Electric energy consumption of ubuntu versus windows"
date: 2013-11-03
forum: Ubuntu, Linux and OS Chat
---

### Post by richardsdma on 2013-11-03
starting from this topic:
[http://ubuntuforums.org/showthread.php?t=2154723](http://ubuntuforums.org/showthread.php?t=2154723)
i would like to hear your opinions about power consumption of a machine powered by ubuntu versus windows. this thing would only be possible if you have dual boot. 
let me give you my results:
on windows ~22W
on ubuntu ~24W (only if i put the graphic card on "low" profile. if i use "default" i have 26W)
try to test using the same condition that the result to have any value. 
on windows a use batteryCare and in ubuntu use powertop. 

so, based on the measurements, what can we do to have the same power usage as windows?

---

### Post by cariboo on 2013-11-03
You may be seeing a difference between the different ways that Windows and Ubuntu calculate power usage, the best way to test power consumption would be to put something like [this]("http://store.greengadgets.ca/") in the power line

---

### Post by Bucky Ball on 2013-11-03
> **cariboo907 said:**
> You may be seeing a difference between the different ways that Windows and Ubuntu calculate power usage, the best way to test power consumption would be to put something like [this]("http://store.greengadgets.ca/") in the power line

+1.

---

### Post by Erik1984 on 2013-11-04
> **cariboo907 said:**
> You may be seeing a difference between the different ways that Windows and Ubuntu calculate power usage, the best way to test power consumption would be to put something like [this]("http://store.greengadgets.ca/") in the power line

Actually I would like to measure the energy consumption that way, I have such a meter. Too bad the wall socket is very inconveniently located (under the desk and in the corner).

---

### Post by richardsdma on 2013-11-04
it would be very nice to do such a test. i can't wait for the results.

---

### Post by mastablasta on 2013-11-04
> **Euroman said:**
> Actually I would like to measure the energy consumption that way, I have such a meter. Too bad the wall socket is very inconveniently located (under the desk and in the corner).

use an extension cord?

---

### Post by Bucky Ball on 2013-11-04
> **mastablasta said:**
> use an extension cord?

+1. My thoughts exactly ... ;)

---

### Post by tgalati4 on 2013-11-04
I was able to get Ubuntu 9.10 to get close to Windows XP several years ago on an IBM Thinkpad T43p by doing the following:

1.  Recompile the kernel to allow undervolting.
2.  Set a conservative undervolt profile at all CPU step speeds (around -20% of stock voltage).
3.  Set dynamic clocks in xorg.conf to allow the ATI GPU to throttle depending on load.
4.  Use *thinkfan* to control fan speeds and allow fans to go to 0, but also go higher when needed.  This results in slightly higher CPU/GPU temps (they share the heatsink) under normal use, but quieter operation.
5.  Shutdown unused services.

I went from 22 watts to around 17 watts and battery life went from 2.5 hours to 3 hours.  In Windows battery life was a solid 3 to 3.5 hours.  So even with all of that work, I could only just meet but not exceed Windows battery life/power management.  So there must be other factors like motherboard chipset power management, disk drive idle power, and perhaps wireless power savings.  

You would need a special equipment to isolate and measure the power consumption of all of the subsystems.

The bottom line, you will seem some improvement, but it takes a lot of work.  If you really need more battery life, buy a bigger battery (like a 9-cell) or a battery that fits into another bay.

---

### Post by richardsdma on 2013-11-04
@tgalati4
very impresive man, that is what i call a real nice job. on my machine, also with an old ati x1270, the only thing i did was to decrease the frequency of video precessor from 400 to 140 mhz using a script named powerplayswitcher, that means "low" profile. using "dynamic" profile makes the screen to flicker.

---

### Post by tgalati4 on 2013-11-04
Each machine will behave differently.  At -30% undervolting I was getting lockups, so there is only so low you can go before stability is compromised.  I never noticed any flickering with the FireGL ATI card, but the temperature dropped 3 to 5C so that is a visible energy savings.  I think the clock would switch from 400 MHz to 200 MHz.  I didn't try lower, but with other utilities, you could go lower, but again at the risk of locking up the GPU--which requires a hard shutdown to recover.

My conclusion from all of this is that there are power savings to be had from all subsystems.  The proprietary Windows drivers provided by the manufacturer (IBM in this case) appear to be tweaked to give the best power performance from all of the subsystems.  Intel's speedstep and powertop gives a decent optimization of processes that wake the CPU, but there are a lot of subsystems that use power.  Cycling the RAM clock, controlling I/O port power, North and Southbridge optimization, etc are probably needed to get to Window's power management.

I have yet to see anyone find a magic switch in Linux to improve power, so it must be difficult to achieve.

I don't know enough about how the Window's kernel operates, but I think the true multi-user, multi-tasking design of linux uses more power at idle.  There is no way around those differences.

---

### Post by richardsdma on 2013-11-04
to be honest, these are the real issues that need to be adressed, but instead, a lot of manpower is wasted away into new forks, desktop environments, etc. 
i read a lot of complains about the battery life in ubuntu versus windows, especially nowadays when you have a lot of machine with hybrid GPU, it is a real mess.

---

### Post by mdrag13 on 2013-11-04
> **richardsdma said:**
> **to be honest, these are the real issues that need to be adressed, but instead, a lot of manpower is wasted away into new forks, desktop environments, etc. **
i read a lot of complains about the battery life in ubuntu versus windows, especially nowadays when you have a lot of machine with hybrid GPU, it is a real mess.

+1

---

### Post by tgalati4 on 2013-11-04
Apple Macbook Airs can get 10-11 hours of battery life.  Install Windows on those machines and you are looking at 6-7 hours.  I'm not sure what Ubuntu gets on that hardware, but it shows that tight integration of hardware and software is needed to get battery life.  And that tight integration takes a lot of time and money and results in proprietary hardware and software.

---

### Post by Erik1984 on 2013-11-05
> **richardsdma said:**
> to be honest, these are the real issues that need to be adressed, but instead, a lot of manpower is wasted away into new forks, desktop environments, etc. 
i read a lot of complains about the battery life in ubuntu versus windows, especially nowadays when you have a lot of machine with hybrid GPU, it is a real mess.

There is not much that Ubuntu can do. It's mainly a hardware vendor/manufacturer related to the kernel  thing. Only thing desktop environments can do is to try to reduce CPU  usage. Compared to any linux desktop distro Microsoft, Apple and Google have insane budgets to tackle power issues for their hardware/software combinations.

---

### Post by mastablasta on 2013-11-05
yup this is mainly problem with hardware anufacturers. they do not open the code and they have one or two people working on these drivers (e.g. hybrid GPU) so sometimes they win other times they fail. mostly they fail. anyway people (manpower) really can't work on this unless they get certain specs from manufacturers which they do not want to give. 

but sometimes they do help. e.g. AMD helped quite a bit with latest opensource drivers in kernel. i don't think they helped enough to make them on par with proprietary though... i guess they do not really see any benefit in that.

i think with power consumption it seems like it is mainly GPU issue. as Linux is used on massive supercomputers. and there power drinage would/could really show. then again it could be they use modified kernel.

---

### Post by Erik1984 on 2013-11-05
Okay, I did the test but results are not reliable as I can't measure the most important stat with this meter: average power consumption. It only stores highest and lowest values.

Test: 10 minutes of normal daily desktop usage for me: browsing + listening music in the background.
System: Deskop Ivy Bridge i5 with intel hd2500 graphics and wireless internet via USB dongle.

**Windows 8** + Firefox + Foobar2000

High: 57.0 W
Low: 38.4 W
_Estimated_ modal consumption: 38 W - 40 W

**Kubuntu 13.10 (kernel 3.11.0-12)** + Firefox + Amarok

High: 51.5 W
Low: 38.2 W
_Estimated_ modal consumption: 38 W - 40 W (maybe with more peaks now and then compared to Windows)

For both systems the meter seems to alternate between values in the 38 to 40 Watt interval most of the time. With spikes when doing something CPU intensive. So overall Windows and Linux seem to have a very comparable power usage for my average tasks.

---

### Post by richardsdma on 2013-11-05
@euroman
a lot of thanx for your feedback.
so, you are a kind of "lucky luciano" because it seems to have a very compatible hardware. overall, it seems that a full-intel configuration is much more suitable for linux than the otheres. that is quite sad for me because i am an amd fanboy....but i think that i will change the team....will see!

---

### Post by mastablasta on 2013-11-06
intel opensources most of their GPU drivers. while AMD keeps them locked. so if you have AMD GPU and proprietary drivers the consumpiton should be ok. also if oyu have older AMD card. as for CPU i think intel has better power consumption overall. but i am not sure by how much and if you gain anything with that. i mean the price of AMD is a lot lower lower.

---

### Post by Bucky Ball on 2013-11-06
The second link in my signature is old but the ethos is relevant. Search for energy efficient parts in the first place (and build a desktop). If you're using anything but an 80+ efficient PSU (85+, even better) in a desktop you're wasting money (and generic silver box PSUs are *_dangerous_* and generally <70% efficient heat boxes). 

Intel (and I think AMD) have energy-efficient processor models. Western Digital have their Green Power hard drives (and there are others). Take some time and compare the standby and on power consumption of monitors and other components. Heck, it ain't rocket science. Just takes some time. And look for RoHS (which was rare five years ago even, but is now on just about all hardware).

In my opinion, if you're running a desktop, you should have built the most energy efficient box you could before you even install an operating system. If you are going for a laptop, power consumption specs, like standby and on, are right there on their website in the tech specs. Too easy.

So yea, blah blah about the software, but if you have a 700Watt PSU and all you use your computer for is to check your emails and surf the net, you've got it wrong, and who cares about checking with a meter or any other way. Get the hardware right first, and most importantly, get the wattage of the 80+ PSU right ...

Calculator here:

[http://psucalc.tk/](http://psucalc.tk/)

The best, as it is based on their extremely efficient PSUs, is the Antec one, but their site is being worked on. Plenty here, though:

[https://duckduckgo.com/?q=psu+calculator](https://duckduckgo.com/?q=psu+calculator)

---

