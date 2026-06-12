---
title: "measuring operating CPU frequency like CPUz"
date: 2013-05-06
forum: Ubuntu, Linux and OS Chat
---

### Post by raxman on 2013-05-06
On Windows there is a program called CPUz which reports the operating frequency.  On Linux I have only found one program which does this: powertop.  All the other programs I have tried (top, /proc/cpuinfo) report the base frequency before turbo-boost. 

Do you have any other suggestions.  One with a GUI like CPUz would be nice.  Powertop is not so convenient.

---

### Post by Malsasa on 2013-05-07
Maybe GUI apps like: 

[http://sourceforge.net/projects/gsysinfo/](http://sourceforge.net/projects/gsysinfo/)
[http://www.horejsek.com/text/my-work](http://www.horejsek.com/text/my-work) (infopanel)
[http://hardinfo.berlios.de/Screenshots](http://hardinfo.berlios.de/Screenshots)
[http://openhardwaremonitor.org/screenshots/](http://openhardwaremonitor.org/screenshots/)
[http://cuda-z.sourceforge.net/#block-linux](http://cuda-z.sourceforge.net/#block-linux)

meet you criterias. And I am glad to know there are many GUI tools like this for Linux.

---

### Post by monkeybrain2012 on 2013-05-07
Cpu frequency scaling indicator?

[http://handytutorial.com/cpu-frequency-scaling-indicator-on-ubuntu-12-04-12-10/](http://handytutorial.com/cpu-frequency-scaling-indicator-on-ubuntu-12-04-12-10/)

---

### Post by raxman on 2013-05-07
I tried  gsysinfo.  It does not show the operating frequency, only the base frequency
cuda-z is for the GPU
openhardwaremonitor requires mono, i doubt it shows the operating frequency
I have not got the other options working.
frequency scaling indicator does not show the operating frequency either.

For example, my CPU is a i5-3317U @1.7 GHZ.  However, the 1.7 GHz revers to the non turbo-boosted freqeucny.  When I run my CPU under load on only one core turbo boost clocks up to 2.6 GHz.  On both cores they both go to 2.4GHz.  The only application on Linux that I have found that shows this correctly is powertop.

---

### Post by mips on 2013-05-07
If you run conky and have the parameter showing cpu frequency you will see it change under load.

---

### Post by raxman on 2013-05-08
[FONT=arial]I can show the frequency changing under load simply
[/FONT]
[FONT=arial]watch grep \"cpu MHz\" /proc/cpuinfo
  
The problem is that most programs don't show the real frequency under load.  It's not so easy.  For one the program needs 
root access since it has to use model specific registers to get there operating frequency.  That's one reason powertop requires root access.
[/FONT]

---

### Post by slickymaster on 2013-05-08
> **raxman said:**
> On Windows there is a program called CPUz which reports the operating frequency.  On Linux I have only found one program which does this: powertop.  All the other programs I have tried (top, /proc/cpuinfo) report the base frequency before turbo-boost. 

Do you have any other suggestions.  One with a GUI like CPUz would be nice.  Powertop is not so convenient.

I think what you're looking for is [CPU-G]("https://launchpad.net/~cpug-devs/+archive/ppa") (it's in the repositories) . It's a GUI application that displays useful information about your hardware and can collect information about your computer's CPU, RAM, Motherboard, and other general information about your system kernel, architecture, Linux distribution and more.

---

### Post by raxman on 2013-05-09
I already tried CPU-G.  When I my CPU under load it shows 1.7 GHz not 2.4 GHz.  It does not show the operating frequency.  Not only that but it does not show the frequency changing.  It appears to read the frequency only on startup.

What are all the overclockers using on Linux?  Windows?

---

### Post by boog321 on 2013-05-09
> **raxman said:**
> I already tried CPU-G.  When I my CPU under load it shows 1.7 GHz not 2.4 GHz.  It does not show the operating frequency.  Not only that but it does not show the frequency changing.  It appears to read the frequency only on startup.

What are all the overclockers using on Linux?  Windows?

With new systems, I just haven't felt the need to overclock.

But, as raxman said, using "watch grep \"cpu MHz\" /proc/cpuinfo" is an easy way to watch the cpu.

I have felt more inclined to use gkrellm to monitor tempretures and fans.

---

### Post by raxman on 2013-05-09
Whether you overclock manual or not does not change the fact that a modern Intel CPU uses turbo-boost which is a type of dynamic overclocking.  The operating CPU frequency of a modern Intel CPU is reported wrong by every application I have used except powertop.

---

### Post by boog321 on 2013-05-09
Got confused as to who was posting what on my last reply.


I understand your frustration, but I think most of the tools are reporting their current speed instead of their max. I have been there. One of my first scaleable cpu's gave me that fustration, I never knew if it was hitting the max, and everything I checked made it look like it was only running at it's lowest. Since then I have found that it does indeed scale, and as you have found, there are ways to watch it, just no fancy all in one like cpuz

---

