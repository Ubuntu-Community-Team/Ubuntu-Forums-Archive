---
title: "[HowTo] Undervolting the AMD Turion X2 (and some others)"
date: 2010-03-19
forum: Tutorials
---

### Post by nema.arpit on 2010-03-19
As most are aware,AMD's processors tend to overheat ... a lot.Worried due to the heat, I searched for some solutions.Undervolting is one of the easier ones,but finding a suitable tool to do the job on the k8 line is difficult.Through my searches I came across TurionPowerControl.
**quoting** Ares Drake from  				**HowTo: Undervolt your notebook CPU for longer  battery life**
<quote>**From [wikipedia:]("http://en.wikipedia.org/wiki/Undervolting")** Undervolting is the practice of reducing the supply voltage of a computer's CPU. There are many reasons to perform this sort of modification, but a common one is to reduce power consumption and thus heat generation in laptop computers. Lower heat generation provided by undervolting and underclocking is also helpful in making computers quieter.
Performance will not suffer as the energy you will save was just wasted (as heat) before.

**Safety:**
Undervolting notebook processors is not uncommon. My older notebook (Toshiba S1) even came with a Windows utility that did automatic undervolting preinstalled. So the "undervolted" processor is nothing dangerous.
</quote>

Still **I take no responsibilities for any damage you may cause to your system**.Do this at your own discretion.

Here are the steps I followed: 
**1)**Download the TurionPowerControl rar from [http://amdath800.dyndns.org/amd/tpc-0.12.rar](http://amdath800.dyndns.org/amd/tpc-0.12.rar)
**2)**Extract the rar.**Read the _readme._**_**txt**_.Fire up a terminal ,navigate to the **linux src** sub-directory and enter ```
 c++ TurionPowerControl.cpp Processor.cpp cpuPrimitives.cpp -o TurionPowerControl 
```.This will create a binary file by the name of TurionPowerControl in that folder.Copy this file over to /bin (requires root access).
**3)**Now the program is in place.To execute it,you need to first load the modules **cpuid **and  **msr.**
```

sudo modprobe msr
sudo modprobe cpuid

```
Thats it. To run it simply execute ```
sudo TurionPowerControl -{*}
```
Replace the {*} with suitable commands,listed in the readme.

I have a Turion X2 2.1 ghz processor,and this works for me.At least from what TPC tells.Do tell if you know of a more official/ better way to verify the processor voltages.

**Tip:** I would suggest creating a shell script with the repetitive commands needed to set the correct voltages to all the states, and executing it with sudo ( this has to be done at every startup.)
Or even better,make this script execution automatic.I don't know how to automatically execute a script as superuser at startup, please do tell if you know.

---

### Post by ChaosHead on 2010-03-20
Hi again.
It looks like it doesn't work on processor MV-40 (aka Amd  Athlon Neo).
```

Turion Power States Optimization and Control - by blackshard - v0.12
cpuid:pread: Invalid argument
Cpuid_Fn8000_0008 Instruction failed
Error: unable to get processor specifications
```
To bad. Do you think that there may be a special file/package for this cpu?

---

### Post by nema.arpit on 2010-03-20
Sorry to hear that.Unfortunately I have no idea about any package for your cpu.I found the tpc reference here [http://forum.notebookreview.com/showthread.php?t=373878](http://forum.notebookreview.com/showthread.php?t=373878). Maybe they might have some ideas.

This thread might also be of some help (it uses a different program to undervolt - the linux_phc) [http://www.linux-phc.org/forum/viewtopic.php?f=8&t=113](http://www.linux-phc.org/forum/viewtopic.php?f=8&t=113)

---

### Post by ChaosHead on 2010-03-20
Thanks for your help and time. I'll maybe write some guide when I get it to work :P.

---

### Post by 2hot6ft2 on 2010-03-20
Interesting, and a nice how to. I have the AMD Turion X2 and while I may consider doing this at some point it wont be right now. My CPU's run at about 38C so I'm not concerned about the heat right now. But I may want to cut down on the battery drain one day soon.

Now if you find a way to monitor the fan speed using the GNOME Sensors Applet I would be interested in doing that.

Nice write up and thanks for sharing the info with us. I'll certainly be saving the info and the package for a later date.
:popcorn:

---

### Post by mothersh1p on 2010-04-18
> **ChaosHead said:**
> Hi again.
It looks like it doesn't work on processor MV-40 (aka Amd  Athlon Neo).
```

Turion Power States Optimization and Control - by blackshard - v0.12
cpuid:pread: Invalid argument
Cpuid_Fn8000_0008 Instruction failed
Error: unable to get processor specifications
```
To bad. Do you think that there may be a special file/package for this cpu?

I have had the same problem! My error was: 

```

Turion Power States Optimization and Control - by blackshard - v0.12
cpuid:pread: Invalid argument
Cpuid_Fn8000_0008 Instruction failed
Error: unable to get processor specifications
```

tpc-0.12 is written for 64-bit boxes. Just add option -D_FILE_OFFSET_BITS=64 to the cflags.


```

c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp >Processor.cpp config.cpp -o TurionPowerControl

```

---

### Post by skythus on 2010-05-07
I also have an HP DV2 with AMD Athlon Neo processor, however when I try and create the binary I get the following error:

skythus@skythus-laptop:~/Downloads/tpc/linux src$ c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp >Processor.cpp config.cpp -o TurionPowerControl
c++: config.cpp: No such file or directory
TurionPowerControl.cpp: In function ‘void processorStatus(Processor*)’:
TurionPowerControl.cpp:222: warning: NULL used in arithmetic

Any thoughts?

---

### Post by mothersh1p on 2010-05-11
Hi skythus,

this must be a typo! The "greater than" sign isn't that meaningful in this context! My apologize!

[PHP]
c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp Processor.cpp config.cpp -o TurionPowerControl
[/PHP]

Here is my config:

TurionPowerControl -pallc 0 37 0 14
TurionPowerControl -pallc 1 54 1 16
TurionPowerControl -pallc 2 61 2 19
TurionPowerControl -nbvid 54
TurionPowerControl -rampuptime 3
TurionPowerControl -rampdowntime 3
TurionPowerControl -pallc 6 41 1 20
TurionPowerControl -pallc 7 41 1 20
TurionPowerControl -altvidslamtime 5

And here is what it looks like (I have a ZM-82):

Turion Power States Optimization and Control - by blackshard - v0.21
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0x520	
Detected Physical Cores: 2
Processor has 3 Power Planes (not accurate)
Detected processor: Turion Ultra ZM processor
Processor has 2 cores
Processor has 8 p-states

Power States table:
core 0 pstate 0 - En:1 VID:37 FID:14 DID:0 Freq:2200 VCore: 1.0875
core 0 pstate 1 - En:1 VID:54 FID:16 DID:1 Freq:1200 VCore: 0.8750
core 0 pstate 2 - En:1 VID:61 FID:19 DID:2 Freq:675 VCore: 0.7875
core 0 pstate 3 - En:0 VID:48 FID:14 DID:1 Freq:1100 VCore: 0.9500
core 0 pstate 4 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 0 pstate 5 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 0 pstate 6 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
core 0 pstate 7 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
core 1 pstate 0 - En:1 VID:37 FID:14 DID:0 Freq:2200 VCore: 1.0875
core 1 pstate 1 - En:1 VID:54 FID:16 DID:1 Freq:1200 VCore: 0.8750
core 1 pstate 2 - En:1 VID:61 FID:19 DID:2 Freq:675 VCore: 0.7875
core 1 pstate 3 - En:0 VID:48 FID:14 DID:1 Freq:1100 VCore: 0.9500
core 1 pstate 4 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 1 pstate 5 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 1 pstate 6 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
core 1 pstate 7 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
Processor Maximum PState: 2
Processor Startup PState: 3

Minimum allowed VID: 64 (0.750v) - Maximum allowed VID 28 (1.200v)
Processor AltVID: 64 (0.750v)
Processor Northbridge VID: 54 (0.875v)

SMAF7 is disabled; processor is using LMM Configuration
	Registers for Power Management
DID to apply when in C1E state: 0

Voltage Regulator Slamming time register: 5
Voltage Regulator AltVID Slamming time register: 5
Voltage Regulator Step Up Ramp Time: 3
Voltage Regulator Step Down Ramp Time: 3

Best regards!

---

### Post by skythus on 2010-05-11
I'm still getting errors, which I think has to do with the fact that I need to install Linux PHC to be able to gain access to undervolting. I will read up on patching the kernel (possibly Zen) and going from there. Thanks for the info Mothersh1p!

---

### Post by mothersh1p on 2010-05-11
You are welcome! In fact you have only to enable the model-specific-register support in the kernel ([http://cateee.net/lkddb/web-lkddb/X86_MSR.html](http://cateee.net/lkddb/web-lkddb/X86_MSR.html)). Linux-PHC is not helpful here and AFAIK has some bugs.

FYI: When compiling I'm getting a warning, but it doesn't control the binary.

> 
TurionPowerControl.cpp: In function &#8216;void processorStatus(Processor*)&#8217;:
TurionPowerControl.cpp:227: warning: NULL used in arithmetic


---

### Post by exjinn on 2010-06-04
I copied your config and made it an executable scipt, I'm curious if what I've done is helping I get the following when running the script.


```

root@v3lm4:/home/exmage/Downloads# ./turionuv 
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Done!

```

Is this doing anything or am I crazy? :P

---

### Post by mothersh1p on 2010-06-04
Maybe you are lucky!? It shouldn't work, because you have a 2.0 Ghz CPU. But it looks alright from what you have posted. Could you try TurionPowerControl -l and post the result here and attach yor script here, too!?

---

### Post by exjinn on 2010-06-04
Lol I'm so confused! What's strange is when I run the script now it fails.

TurionPowerControl -l & infobash output
```

root@v3lm4:/home/exmage# TurionPowerControl -l
Turion Power States Optimization and Control - by blackshard - v0.12
cpuid:open: No such file or directory
Cpuid_Fn0 Instruction failed
Error: unable to get processor specifications
root@v3lm4:/home/exmage# infobash -v3
Host/Kernel/OS  "v3lm4" running Linux 2.6.34-0.slh.7-sidux-amd64 x86_64 [ sidux 2010-01 - &#910;&#960;&#957;&#959;&#962; Preview 1 - xfce-lite - (201005262039) ]
CPU Info        (1) AMD Turion X2 Dual-Core Mobile RM-72 512 KB cache flags( sse3 ht nx lm svm ) clocked at [ 525.000 MHz ]
                (2) AMD Turion X2 Dual-Core Mobile RM-72 512 KB cache flags( sse3 ht nx lm svm ) clocked at [ 1050.000 MHz ]
Videocard       ATI Mobility Radeon HD 3650  X.Org 1.7.7  [ 1366x768@60.0hz ]
Network cards   ATHER USB2.0 WLAN
Processes 132 | Uptime 4:44 | Memory 410.1/3963.8MB | HDD ST9320320AS Size 320GB (51%used) | Client Shell | Infobash v3.31

```

Script: turionuv
```

root@v3lm4:/home/exmage/Downloads# cat turionuv 
TurionPowerControl -pallc 0 37 0 14
TurionPowerControl -pallc 1 54 1 16
TurionPowerControl -pallc 2 61 2 19
TurionPowerControl -nbvid 54
TurionPowerControl -rampuptime 3
TurionPowerControl -rampdowntime 3
TurionPowerControl -pallc 6 41 1 20
TurionPowerControl -pallc 7 41 1 20
TurionPowerControl -altvidslamtime 5

```

---

### Post by mothersh1p on 2010-06-04
Hi exjinn,

you lost me there. Could you try find /dev/cpu/ and post the result? Probably you are looking for CONFIG_X86_MSR and CONFIG_X86_CPUID in your config-file? BTW. my kernel compile time is:

Kernel: arch/x86/boot/bzImage is ready  (#37)
  Building modules, stage 2.
  MODPOST 93 modules

real	1m31.982s
user	0m47.717s
sys	0m11.462s

---

### Post by exjinn on 2010-06-05
I forgot to modprobe msr and moprobe cpuid. That's why things didn't work the second time around. It seems to be working now.

I've added both of those commands to the script and it seems to fine.

And here is the output of TurionPowerControl -l


```
root@v3lm4:/home/exmage# TurionPowerControl -l
Turion Power States Optimization and Control - by blackshard - v0.12
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0xc80	
Detected Physical Cores: 2
Processor has 3 Power Planes
Detected processor: Turion Ultra RM processor
Processor has 2 cores
Processor has 8 p-states
core 0 pstate 0 - En:1 VID:37 FID:14 DID:0 Freq:2200 VCore: 1.0875
core 0 pstate 1 - En:1 VID:54 FID:16 DID:1 Freq:1200 VCore: 0.8750
core 0 pstate 2 - En:1 VID:61 FID:19 DID:2 Freq:675 VCore: 0.7875
core 0 pstate 3 - En:0 VID:48 FID:13 DID:1 Freq:1050 VCore: 0.9500
core 0 pstate 4 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 0 pstate 5 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 0 pstate 6 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
core 0 pstate 7 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
core 1 pstate 0 - En:1 VID:37 FID:14 DID:0 Freq:2200 VCore: 1.0875
core 1 pstate 1 - En:1 VID:54 FID:16 DID:1 Freq:1200 VCore: 0.8750
core 1 pstate 2 - En:1 VID:61 FID:19 DID:2 Freq:675 VCore: 0.7875
core 1 pstate 3 - En:0 VID:48 FID:13 DID:1 Freq:1050 VCore: 0.9500
core 1 pstate 4 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 1 pstate 5 - En:0 VID:0 FID:0 DID:0 Freq:800 VCore: 1.5500
core 1 pstate 6 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
core 1 pstate 7 - En:0 VID:41 FID:20 DID:1 Freq:1400 VCore: 1.0375
Processor Maximum PState: 2
Processor Startup PState: 3

Minimum allowed VID: 64 (0.750v) - Maximum allowed VID 28 (1.200v)
Processor AltVID: 64 (0.750v)
Processor Northbridge VID: 54 (0.875v)

SMAF7 is disabled; processor is using LMM Configuration Registers for Power Management
DID to apply when in C1E state: 0

Voltage Regulator Slamming time register: 5
Voltage Regulator AltVID Slamming time register: 5
Voltage Regulator Step Up Ramp Time: 3
Voltage Regulator Step Down Ramp Time: 3
Done!
```

---

### Post by mothersh1p on 2010-06-05
No problem! But I still doesn't understand your question:

> AMD Turion X2 Dual-Core Mobile RM-72 

It shouldn't worked!

---

### Post by exjinn on 2010-06-05
I was just wondering if I was setting it up correctly that was question. :)

I don't know why it worked when it shouldn't have, does it look like it is working to you?

---

### Post by mothersh1p on 2010-06-05
Yes, but what is strange is that Linux doesn't support Hyper-Threading. According to cat /proc/cpuinfo ht is supported (ht-flag) but it shows only 2 cpus when I want to see 2 physical and 2 logical cpus. You may also look if you didn't overclocked your pc by chance. AFAIK the RM-72 is only specified to 2100 Mhz. You can check this with TurionPowerControl -CM.

---

### Post by exjinn on 2010-06-05
That is odd as the TurionPowerControl seems to think my processor is the Turion Ultra, which runs at 2.2ghz. However cpufreq-info says its running at 2.10Ghz.

I have not overclocked my processor.

```
root@v3lm4:/home/exmage# cpufreq-info 
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 1000 ns.
  hardware limits: 525 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.05 GHz, 525 MHz
  available cpufreq governors: performance, powersave, ondemand, conservative, userspace
  current policy: frequency should be within 525 MHz and 2.10 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 525 MHz (asserted by call to hardware).
  cpufreq stats: 2.10 GHz:2.20%, 1.05 GHz:9.57%, 525 MHz:88.23%  (1326)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 1000 ns.
  hardware limits: 525 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 1.05 GHz, 525 MHz
  available cpufreq governors: performance, powersave, ondemand, conservative, userspace
  current policy: frequency should be within 525 MHz and 2.10 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 525 MHz (asserted by call to hardware).
  cpufreq stats: 2.10 GHz:1.76%, 1.05 GHz:8.50%, 525 MHz:89.73%  (1100)
```

---

### Post by blackshard on 2010-06-18
Hi guys, I'm the author of TurionPowerControl. I saw in my web server log this discussion on ubuntu forums and so I got here to give you support if you wish.

Feel free to ask any questions about the program and its usage.

):P

ps: I forgot to say that you can read the latest news and download the latest versione here: [http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html](http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html)

---

### Post by exjinn on 2010-06-19
> **blackshard said:**
> Hi guys, I'm the author of TurionPowerControl. I saw in my web server log this discussion on ubuntu forums and so I got here to give you support if you wish.

Feel free to ask any questions about the program and its usage.

):P

ps: I forgot to say that you can read the latest news and download the latest versione here: [http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html](http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html)


Hi blackshard thanks for your work. 

If you look above the only issue I'm having is I'm not sure if it's actually doing what it's supposed to do. 

I have a AMD Turion X2 Dual-Core Mobile RM-72 however the turion script says: Detected processor: Turion Ultra RM processor. Is this a mistake or something I setup improperly?

---

### Post by mothersh1p on 2010-06-20
> **exjinn said:**
> Hi blackshard thanks for your work. 

If you look above the only issue I'm having is I'm not sure if it's actually doing what it's supposed to do. 

I have a AMD Turion X2 Dual-Core Mobile RM-72 however the turion script says: Detected processor: Turion Ultra RM processor. Is this a mistake or something I setup improperly?

It's a bug. The setup is correct. You could try TurionPowerControl -CM.

---

### Post by blackshard on 2010-06-20
> **exjinn said:**
> Hi blackshard thanks for your work. 

If you look above the only issue I'm having is I'm not sure if it's actually doing what it's supposed to do. 

I have a AMD Turion X2 Dual-Core Mobile RM-72 however the turion script says: Detected processor: Turion Ultra RM processor. Is this a mistake or something I setup improperly?

Well, Turion Ultra RM processor is probably a minor bug. Try latest version (0.21) and check if it has been corrected.

However it won't affect the performance of the software, it will work fine anyway.

Most important is the fact you see some kind of overclocking with the turionuv script you ran.

It is a script made for a 2.2 ghz processor. It will set your processor to 2.2 ghz, but actually it won't go over 2.1 ghz because its FID multiplier is locked and can't go over 13 (instead in the script you see that FID of pstate0 is set to 13). All the programs of this world will tell you that your processor is working at 2.2 ghz, but if you do a simple benchmark, you will see that it has the same performances of 2.1 ghz. Also don't believe at all the cpufreq-* stats, they are not updated since the cpu scaler daemon starts, despite the fact cpufreq-info says that it is obtaining information with a hardware call.

Also notice that you can put all the switches on a single command line instead of calling the program many times. Also newer versions can have an external configuration file to recall settings.

---

### Post by mothersh1p on 2010-06-20
> **blackshard said:**
> Well, Turion Ultra RM processor is probably a minor bug. Try latest version (0.21) and check if it has been corrected.


Hi blackshard,

thank you for your help! Although I think that your program is only made for 64 bit, I have found this switch to compile it for 32 bit:

```

c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp >Processor.cpp config.cpp -o TurionPowerControl

```

Maybe it is useful to add it to your Makefile? (IF-THEN) Could it be that the turionuv-script doesn't work properly for 32 bit?

Although, in the sample output (using your program) from exjinn, I cannot see that pstate 0 has a FID of 13 after he ran turionuv. Could you clarify this?

---

### Post by blackshard on 2010-06-20
> **mothersh1p said:**
> Hi blackshard,

thank you for your help! Although I have found that your program is only made for 64 bit, I have found this switch to compile it for 32 bit:

```

c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp **>**Processor.cpp config.cpp -o TurionPowerControl

```Maybe it is useful to add it to your Makefile? (IF-THEN) Could it be that the turionuv-script doesn't work properly for 32 bit?

Although, in the sample output (using your program) from exjinn, I cannot see that pstate 0 has a FID of 13 after he or she ran turionuv. Could you clarify this?

Hello mothersh1p, thank you for your notice about compiling on 32 bit platforms. Actually, as far as I remember, I once tried to compile it on a 32 bit fedora box with success. I'll try as soon as possible your solution (isn't there a ">" in the wrong place?) and will report it in the readme file. 

exjinn said he has a processor running at 2.1 Ghz, it means that its maximum FID is 13 (just check the little formula in the readme file to calculate frequency with DID and FID given values).
All family 11h processors (Athlon QL, Turion RM/ZM processors) cap the overflowing values to the hardwired maximum value. In case of exjinn, the maximum FID value is 13, so you can set FID=14, 15 or even 20, the processor will accept the value but then it will internally cap that value to 13.

---

### Post by mothersh1p on 2010-06-20
> **blackshard said:**
> Hello mothersh1p, thank you for your notice about compiling on 32 bit platforms. Actually, as far as I remember, I once tried to compile it on a 32 bit fedora box with success. I'll try as soon as possible your solution (isn't there a ">" in the wrong place?) and will report it in the readme file. 


Hi Blackshard,

my apologize, the "greater"-sign is a typo. Just erase the ">" typo to make the cflag working. Would you mind to tell me > in my web server log this discussion on ubuntu forums
how can this be possible? Do you have an own website-crawler? Do you work for Google? Or do you plan to use such technology?

---

### Post by blackshard on 2010-06-20
> **mothersh1p said:**
> Hi Blackshard,

my apologize, the "greater"-sign is a typo. Just erase the ">" typo to make the cflag working. Would you mind to tell me 
how can this be possible? Do you have an own website-crawler? Do you work for Google? Or do you plan to use such technology?

Ehehe, nothing so exotic :)

I just told apache on my personal webserver to enable referrer logging ;)

---

### Post by mothersh1p on 2010-06-20
> **blackshard said:**
> 
I just told apache on my personal webserver to enable referrer logging ;)

My apologize for my english. I'm a bit paranoid about new technology.

Here are the bits again in case you need it:

> 
c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp Processor.cpp config.cpp -o TurionPowerControl


Why didn't you use a Makefile? I guess it isn't possible to guess 32 bit boxes? I should try this oneliner, every time I boot into Linux I get this big output! XXX

---

### Post by blackshard on 2010-06-20
Mmmh, I just tried to compile on a 32 bit box running Ubuntu 10.04 LTS  and compilation went good just using the compile.sh script included with the  package. 

I'd like to understand what is the problem related to 32bit cpuid instruction to let the program compile and run well even without the compilation flag.
I prefer not to give a makefile just because it is a bunch of .cpp files and a trivial shell script is just enough to compile the program.

---

### Post by mothersh1p on 2010-06-20
> **blackshard said:**
> 
I'd like to understand what is the problem related to 32bit cpuid instruction to let the program compile and run well even without the compilation flag.
I prefer not to give a makefile just because it is a bunch of .cpp files and a trivial shell script is just enough to compile the program.

Maybe you want me to make your Makefile?

---

### Post by blackshard on 2010-06-20
Oh well, I would be glad to include your makefile in my project ;)

Thanks!

---

### Post by mothersh1p on 2010-06-20
> **blackshard said:**
> Oh well, I would be glad to include your makefile in my project ;)

Thanks!

I can fork your thing! Is it a GPL-Licence?

---

### Post by exjinn on 2010-06-20
> **blackshard said:**
> Well, Turion Ultra RM processor is probably a minor bug. Try latest version (0.21) and check if it has been corrected.

However it won't affect the performance of the software, it will work fine anyway.

Most important is the fact you see some kind of overclocking with the turionuv script you ran.

It is a script made for a 2.2 ghz processor. It will set your processor to 2.2 ghz, but actually it won't go over 2.1 ghz because its FID multiplier is locked and can't go over 13 (instead in the script you see that FID of pstate0 is set to 13). All the programs of this world will tell you that your processor is working at 2.2 ghz, but if you do a simple benchmark, you will see that it has the same performances of 2.1 ghz. Also don't believe at all the cpufreq-* stats, they are not updated since the cpu scaler daemon starts, despite the fact cpufreq-info says that it is obtaining information with a hardware call.

Also notice that you can put all the switches on a single command line instead of calling the program many times. Also newer versions can have an external configuration file to recall settings.

I have not tried the new version as I'm just happy to know it's working as I needed, again thank you. I did however condense the command to one line as you suggested, much neater. 

Unfortunately my understanding of the undervolting process is more limited than yours or mothersh1p's but I'm trying to learn. ):P

---

### Post by blackshard on 2010-06-20
> **mothersh1p said:**
> I can fork your thing! Is it a GPL-Licence?

Well, there's actually a fork, trying to implement a GUI:

[https://launchpad.net/tpc](https://launchpad.net/tpc)

but I don't know if the author is updating it or not.
I'm uploading any newer command line version on notebookreview forum, but the author seems to have lost interest in the project and he's not continuing to update the GUI project.

At the moment there's no real licence.

---

### Post by blackshard on 2010-06-20
> **exjinn said:**
> I have not tried the new version as I'm just happy to know it's working as I needed, again thank you. I did however condense the command to one line as you suggested, much neater. 

Unfortunately my understanding of the undervolting process is more limited than yours or mothersh1p's but I'm trying to learn. ):P

You can always ask here if you have problems or just for knowledge ;)
Also undervolting is a safe trick, you can't break anything, maybe you can just hang your computer. Just reboot and voilà... :)

---

### Post by Viberer on 2010-07-07
Hello!

I have ZM-82 processor and ubuntu 10.4. I receive this message from

TurionPowerControl -l


Turion Power States Optimization and Control - by blackshard - v0.12
cpuid:pread: Invalid argument
Cpuid_Fn8000_0008 Instruction failed
Error: unable to get processor specifications

I have been wondering what should i do with the KConfig file.

Im quite new to Ubuntu and thats why I would like to have exact instructions what to do. I'm familiar with undervolting and I have done it with XP and Vista before.

About the link posted before to the KConfig files: File for arch/x86_64/Kconfig doesnt exist so will it work with X86 file since I have a 64 bit processor?

---

### Post by blackshard on 2010-07-07
Try to load cpuid and msr modules before:

sudo modprobe cpuid
sudo modprobe msr

Then launch the program as sudo:

sudo TurionPowerControl -l

---

### Post by Viberer on 2010-07-07
Hi! I got the exact same message again...

---

### Post by blackshard on 2010-07-07
Oops, i forgot to say that if you're compiling on a 32bit platform you need to add -D_FILE_OFFSET_BITS=64 flag.
Try to compile this way:

c++ -D_FILE_OFFSET_BITS=64 TurionPowerControl.cpp cpuPrimitives.cpp Processor.cpp config.cpp -o TurionPowerControl

BTW, you can find latest version (0.21 at the moment) here:

[http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html](http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html)

---

### Post by Viberer on 2010-07-07
Yes, I use 32bit Ubuntu. When I use the command in /linux src/src i get this:

TurionPowerControl.cpp: In function &#8216;void processorStatus(Processor*)&#8217;:
TurionPowerControl.cpp:227: warning: NULL used in arithmetic
Processor.cpp: In member function &#8216;virtual void Griffin::perfMonitorCPUUsage()&#8217;:
Processor.cpp:1019: warning: spurious trailing &#8216;%&#8217; in format
/tmp/cc856DdK.o: In function `main':
TurionPowerControl.cpp:(.text+0x125c): undefined reference to `Scaler::Scaler(Processor*)'
TurionPowerControl.cpp:(.text+0x24a7): undefined reference to `Scaler::beginScaling()'
/tmp/ccEfDLdE.o: In function `CfgManager::consumeScalerSection()':
config.cpp:(.text+0xb63): undefined reference to `Scaler::setSamplingFrequency(int)'
config.cpp:(.text+0xbdb): undefined reference to `Scaler::setUpPolicy(int)'
..

I tried with to compile with other computer too and it didn't work, but I somehow managed to get it working by editing compile.sh... atleast it seems like working! Thank you very much for your time!

---

### Post by blackshard on 2010-07-07
No problem ;)

Anyway, have you tried to compile version 0.21 (latest) or version 0.12?

I'm glad you finally compiled the program, I'll put all the fixes when i will release next version.
Post here for any question regarding the program or processor undervolting, we will be glad to reply you!

---

### Post by Viberer on 2010-07-11
Sorry for it took long to reply!

First I was trying 0.12, before I asked help and now 0.21. Great software!

---

### Post by blackshard on 2010-07-20
hello guys, I just want to let you know that TurionPowerControl 0.22 is available.

As usual, this page is for general referement:

[http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html](http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html)

And the software is available directly from here:

[http://amdath800.dyndns.org/amd/tpc-0.22.tar.gz](http://amdath800.dyndns.org/amd/tpc-0.22.tar.gz)

Changelog:

- Fixed Dual Plane/Triple plane operational mode reporting
- Added some more interesting bit reporting (PSI_L enable/threshold,
clock ramp hysteresis)
- Added capability to control PSI_L bit enable/disable and threshold
- Added C1E state reporting
- Added C1E bit set enable/disable

---

### Post by exjinn on 2010-07-20
> **blackshard said:**
> hello guys, I just want to let you know that TurionPowerControl 0.22 is available.

As usual, this page is for general referement:

[http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html](http://forum.notebookreview.com/hp-compaq-voodoo-pc/373878-all-newer-amd-turion-owners-strange-power-handling-hp-dv5.html)

And the software is available directly from here:

[http://amdath800.dyndns.org/amd/tpc-0.22.tar.gz](http://amdath800.dyndns.org/amd/tpc-0.22.tar.gz)

Changelog:

- Fixed Dual Plane/Triple plane operational mode reporting
- Added some more interesting bit reporting (PSI_L enable/threshold,
clock ramp hysteresis)
- Added capability to control PSI_L bit enable/disable and threshold
- Added C1E state reporting
- Added C1E bit set enable/disable

Many thanks as usual seems to work just fine here. :p

---

### Post by mothersh1p on 2010-07-22
I've written an ultra-fast Hilbert and Moore-Curve implementation in
PHP. It uses a non-recursive and table-based approach. It is the first
in the internet avaible with sourcecode and OpenSource-Licence (Copy-
left, Royality-Free etc. pp). If you are in Hilbert-Curve, PHP and
such, grab it, it's hot! I'm planning to add a 3D-Hilbert-Curve, too.
You can find it all here:

> hilbert-curve.sourceforge.net

---

### Post by thegnu on 2010-08-21
> **nema.arpit said:**
> 
**Tip:** I would suggest creating a shell script with the repetitive commands needed to set the correct voltages to all the states, and executing it with sudo ( this has to be done at every startup.)
Or even better,make this script execution automatic.I don't know how to automatically execute a script as superuser at startup, please do tell if you know.

you would put it in /etc/rc.local, most likely.  i'm not at an ubuntu machine, but that's a standard linux custom startup script.  any commands will be executed with root permissions.

if you have to make the command wait to execute so that modules load, you would prepend a sleep command:

```
#wait 5 seconds, then execute command
sleep 5;command
```

if for whatever reason other processes wait until rc.local finishes, you could create another file, such as /usr/local/bin/mystartup and call it in rc.local:

mystartup:

```
#!/bin/bash
sleep5
command
othercommand
sleep 2
yetanothercommand

```

make it executable:

```
sudo chmod a+x /usr/local/bin/mystartup
```

and then put the following in rc.local:

```
/usr/local/bin/mystartup &
```

the '&' calls backgrounds the process and allows the script to continue without waiting for it to complete.

hope this helps.

---

### Post by blackshard on 2010-09-17
Hello guys, new tpc version!

This is the changelog:

- Added preliminary support for **Family 10h** processor, like **Phenom, **
**Phenom II**, **Athlon II** and **Turion II** processors. Only base functions are 
currently supported and has not been really tested enough. Please report
any problem to my email, so I can fix bugs. Scaler is totally untested on
Family 10h processors, so use it at your own risk!

- Added some simple usage examples to the readme file

So if you got a desktop processor, or a newer Turion II mobile processor, you can also try tpc!

It is available here:

[TurionPowerControl v0.29pre-alpha]("http://amdath800.dyndns.org/amd/tpc-0.29pa.tar.gz")

---

### Post by Roby86 on 2010-09-24
Hi, first of all thx for the app. I've been looking for some replacement for RMClock which I'm using in Windows 7 for a long time, and it's doing the job very well.

But in Ubuntu, temperatures are just too high to work for some reasonable time on it. They're like 70 - 75 C on max.performance, and like 60 C on power saver mode. In windows in 100 % workload, temps are 60-62, on usual work on 55 C.

These are the results of undervolting in Win :

**Max. Performance : 1800 MHz**

Original : 9.0x - 1.075 V 
Temp :70 - 75 C
Undervolt : 9.0x - 0.875 V
Temp : 55-60 C

**Max. Battery : 800 MHz**

Original : 4.0x - 0.800 V - 57 - 60
Undervolt : 4.0x - 0.6875 V - 47-52


I have Turion 64 X2 TL-56 1.8 Ghz processor, and I didn't realize is it Turion II processor which you mentioned that is supported?

I've compiled your app, but after I started it with -l parameter it says : Unsupported processor. :(

Please help. Thx!

---

### Post by blackshard on 2010-09-24
Sry but no support for K8 processors. I have none and I cannot implement such a support.

---

### Post by Roby86 on 2010-09-24
Ok, thx anyway. Cheers!

---

### Post by mothersh1p on 2010-10-01
Exiciting news:

> [http://winqual.microsoft.com/help/default.htm#obtaining_a_verisign_class_3_digital_id.htm](http://winqual.microsoft.com/help/default.htm#obtaining_a_verisign_class_3_digital_id.htm)

---

### Post by blackshard on 2010-10-01
Sorry but the link doesn't work to me.

---

### Post by mothersh1p on 2010-10-01
> **blackshard said:**
> Sorry but the link doesn't work to me.

It*s just about a windows driver licence. The driver you work with is not more supported.
> [https://securitycenter.verisign.com/celp/enroll/retail;jsessionid=MlHJUyp3FiEkdIfcyQr3OGIIAd2f2xQQ32z7NtgtuPpno2pgTAnj!-1742402472](https://securitycenter.verisign.com/celp/enroll/retail;jsessionid=MlHJUyp3FiEkdIfcyQr3OGIIAd2f2xQQ32z7NtgtuPpno2pgTAnj!-1742402472)

---

### Post by vozmem on 2010-10-16
[SIZE="3"][COLOR="Green"]My laptop has a Turion TL-58. Does TurionPowerControl support Turion TL-58? Actually I tried TurionPowerControl 0.12, 0.22, 0.29.1a but when I type 'TurionControlPower' then I just only got the error message: "TurionPowerControl: command not found".[/COLOR][/SIZE]

---

### Post by blackshard on 2010-10-16
No, it doesn't support tl-58.

---

### Post by mothersh1p on 2010-11-17
I'm using this TPC-Config with TPC-0.30 with 64-Bit-Windows:

TurionPowerControl -pallc 0 39 0 14
TurionPowerControl -pallc 1 50 1 20
TurionPowerControl -pallc 2 50 1 20

TurionPowerControl -pallc 6 39 0 14
TurionPowerControl -pallc 7 39 0 14
TurionPowerControl -nbvid 57

TurionPowerControl -rampuptime 3
TurionPowerControl -rampdowntime 3

Although I have less or lesser framedrops with the lowest Powerstate 2 and the cpu heat doesn't getting remarkable lower and the cpu is switching back and forward to Powerstate 2 it's working great.

---

### Post by shane2peru on 2011-07-22
Ok, I stumbled upon this thread after a few years of overheating problems with my AMD Turion x2 64bit computer.  I have only ever run about 2 distros that don't overheat my computer, only to have them break after a while, and I return to Ubuntu with my overheating problems.  At any rate, can someone post good reading material on undervolting?  I think this is what I'm going to do.  Is the first post in this thread still the way to activate this stuff?  Thanks for any feedback.  I know NOTHING about over/under clocking computers.  So this is new for me.  I'm pretty tech minded, and enjoy working in the terminal, so that shouldn't be a problem.  I'm perhaps a little hardware ignorant.

Shane

---

### Post by mothersh1p on 2011-07-23
> **shane2peru said:**
> Ok, I stumbled upon this thread after a few years of overheating problems with my AMD Turion x2 64bit computer.  I have only ever run about 2 distros that don't overheat my computer, only to have them break after a while, and I return to Ubuntu with my overheating problems.  At any rate, can someone post good reading material on undervolting?  I think this is what I'm going to do.  Is the first post in this thread still the way to activate this stuff?  Thanks for any feedback.  I know NOTHING about over/under clocking computers.  So this is new for me.  I'm pretty tech minded, and enjoy working in the terminal, so that shouldn't be a problem.  I'm perhaps a little hardware ignorant.

Shane

I use this app for gaming on windows. It helps a bit but the main problem is my hardware. I'm also using this app with Linux maybe it's usefull but I got other problems with my fan turning always on. Anyway it works and it's easy to install and there seems to be not much alternative. K10 isn't working for me i.e. there isn't any update anymore and the built-in Linux driver seems to suffer from the same problem but that could be because I didn't update my computer for a long time or something else. My conclusion: very good app - very nice support.

---

### Post by mothersh1p on 2011-08-31
I want to disable the powernow-k8 module and all frequency scaling modules from Linux and control it completely with this great tool, because, my Laptop get's massive overheating problem (and I want to keep my Laptop for some more time). So I read the manual, and I tried this:

tpc -scaler samplingrate 75 uppolicy rocket downpolicy rocket

When I watch the frequency with tpc -CM and put some stress on the cpu I didn't get any frequency scaling at all. I tried to compile v0.22 and v0.30 with -m32 and -D_FILE_OFFSET_BITS=64 but I failed, the shell gives me this error:

> 
sh compile_i386.sh 
In file included from TurionPowerControl.cpp:19:0:
Processor.h: In member function &#8216;virtual PState Processor::getMaximumPState()&#8217;:
Processor.h:139:10: warning: passing NULL to non-pointer argument 1 of &#8216;PState::PState(uint32_t)&#8217;
TurionPowerControl.cpp: In function &#8216;void processorStatus(Processor*)&#8217;:
TurionPowerControl.cpp:224:43: warning: NULL used in arithmetic
In file included from Processor.cpp:15:0:
Processor.h: In member function &#8216;virtual PState Processor::getMaximumPState()&#8217;:
Processor.h:139:10: warning: passing NULL to non-pointer argument 1 of &#8216;PState::PState(uint32_t)&#8217;
Processor.cpp: In member function &#8216;virtual PState Griffin::getMaximumPState()&#8217;:
Processor.cpp:426:10: warning: passing NULL to non-pointer argument 1 of &#8216;PState::PState(uint32_t)&#8217;
In file included from config.h:3:0,
                 from config.cpp:3:
Processor.h: In member function &#8216;virtual PState Processor::getMaximumPState()&#8217;:
Processor.h:139:10: warning: passing NULL to non-pointer argument 1 of &#8216;PState::PState(uint32_t)&#8217;
In file included from scaler.h:3:0,
                 from scaler.cpp:1:
Processor.h: In member function &#8216;virtual PState Processor::getMaximumPState()&#8217;:
Processor.h:139:10: warning: passing NULL to non-pointer argument 1 of &#8216;PState::PState(uint32_t)&#8217;


My question is how do I use v0.21 scaler the option? Why is the scaler option in v0.40a disabled? Is v0.21 good enough for my needs? I want to disable the powernow-k8 module and all frequency scaling modules from Linux and control it completely with this great tool. Any idea?

Update: I tried the -cfg option but it gives me this error and the tool sits there and does nothing. I put some load to the cpu and watch with option -CM but the frequency is always the same.

> TurionPowerControl -cfg example.cfg -scaler
Turion Power States Optimization and Control - by blackshard - v0.30
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0x520	
Detected Physical Cores: 2
Core 0 is using already set Performace Counter 0
Core 1 is using already set Performace Counter 0


My Scaler option:

> 
samplingrate 50
uppolicy rocket
downpolicy rocket


BTW: cflag -m32 doesn't work for me. I deleted it.

---

### Post by blackshard on 2011-08-31
> **mothersh1p said:**
> I want to disable the powernow-k8 module and all frequency scaling modules from Linux and control it completely with this great tool, because, my Laptop get's massive overheating problem (and I want to keep my Laptop for some more time). So I read the manual, and I tried this:

tpc -scaler samplingrate 75 uppolicy rocket downpolicy rocket

When I watch the frequency with tpc -CM and put some stress on the cpu I didn't get any frequency scaling at all. I tried to compile v0.22 and v0.30 with -m32 and -D_FILE_OFFSET_BITS=64 but I failed, the shell gives me this error:

...cut...



Hello. Those aren't errors, but just warnings. probably on ubuntu the gcc compiler has a different warning level than other distributions I compiled on.
Anyway, those warnings won't affect the behaviour of the program. The program will compile fine anyway.

> **mothersh1p said:**
> 
My question is how do I use v0.21 scaler the option? Why is the scaler option in v0.40a disabled? Is v0.21 good enough for my needs? I want to disable the powernow-k8 module and all frequency scaling modules from Linux and control it completely with this great tool. Any idea?


I see you have a Family 11h processor, so any version will work fine, except for latest 0.40a version which has the scaler disabled. The scaler has been disabled because version 0.40 saw a major code revamping to support multiprocessor machines. I rewrote a scaler implementation in latest developer code available on the google code project page: [http://code.google.com/p/turionpowercontrol/](http://code.google.com/p/turionpowercontrol/)

But you need to download the delevoper code via SVN and it is totally experimental.

For your purpose, I suggest to use version 0.30.

> **mothersh1p said:**
> 
Update: I tried the -cfg option but it gives me this error and the tool sits there and does nothing. I put some load to the cpu and watch with option -CM but the frequency is always the same.


That's the right way to use the scaler: specify a configuration file with **-cfgfile** switch (and not **-cfg** like you wrote above) and then specify the -scaler switch to put the tool in scaler mode.

With a command like this you can specify a configuration file and put the program in scaler mode:

> TurionPowerControl -cfgfile example.cfg -scaler

But to test the scaler mode with its default values you can simply write:

> TurionPowerControl -scaler

Also if you want to interrupt the program, you can press CTRL-C.

If you wish to run the scaler mode at boot and let it run in background, you can put this line in /etc/rc.local file:

TurionPowerControl -cfgfile example.cfg -scaler &


A good way to test if the scaler is working correclty is, as you said, to launch another instance of TurionPowerControl with -CM. Then you should apply a load to your machine to see if the scaler is effectively changing the pstate.

---

### Post by mothersh1p on 2011-09-01
> **blackshard said:**
> Hello. Those aren't errors, but just warnings. probably on ubuntu the gcc compiler has a different warning level than other distributions I compiled on.
Anyway, those warnings won't affect the behaviour of the program. The program will compile fine anyway.


I saw that after I posted to this message board. I saw that you split src and bin for distribution or compiling reasons. What is -m32 good for? It didn't worked for me, I have a 64-bit cpu and a 32-bit os? Thanks for the help, I didn't know it was -cfgfile option. After a bit of evaluation I stick to the Linux module because it seems to work better. The -scaler option makes my cpu sit on ps7 and ps2 a long time no matter which attribute (rocket or dynamic, or threshold). I can attach my cfgfile and -CM output if you want?

---

### Post by blackshard on 2011-09-01
> **mothersh1p said:**
> I saw that after I posted to this message board. I saw that you split src and bin for distribution or compiling reasons. What is -m32 good for? It didn't worked for me, I have a 64-bit cpu and a 32-bit os? Thanks for the help, I didn't know it was -cfgfile option. After a bit of evaluation I stick to the Linux module because it seems to work better. The -scaler option makes my cpu sit on ps7 and ps2 a long time no matter which attribute (rocket or dynamic, or threshold). I can attach my cfgfile and -CM output if you want?

-m32 compiler switch just tell the compiler to produce a 32 bit binary for a 32 bit operating system.

Attach your configuration file and the output of -CM, it could be interesting to see.

---

### Post by mothersh1p on 2011-09-01
> **mothersh1p said:**
> I saw that after I posted to this message board. I saw that you split src and bin for distribution or compiling reasons. What is -m32 good for? It didn't worked for me, I have a 64-bit cpu and a 32-bit os? Thanks for the help, I didn't know it was -cfgfile option. After a bit of evaluation I stick to the Linux module because it seems to work better. The -scaler option makes my cpu sit on ps7 and ps2 a long time no matter which attribute (rocket or dynamic, or threshold). I can attach my cfgfile and -CM output if you want?

I use only 70,59% of my cpu maxspeed to reduce my overheating problems. I bought a notebook cooler, I updated to the latest OS, and I use this option to start my Linux-Kernel:

> rw root=/dev/sdb2 rw resume=/dev/sdb1 showopts quiet fastboot raid=noautodetect radeon.modeset=1 radeon.lowpoweosr=1 radeon.dynpm=1 video=1440x900 acpi_osi="Linux" pcie_aspm=force
.

Overall my system is a bit better, but it's still very unstable. Maybe it helps to update to 64-bit? Especially when watching Flash-Videos it can compromise the system.

Here is my .cfgfile:

> # TurionPowerControl configuration file
#
# This file is composed of comments, statements and items
# As you can see, a comment has a # as the very first symbol of each
# line, followed by a space and then the comment itself
#
# A statement starts with semicolon (:) symbol, followed by an
# uppercase literal.
# For example, a statement is like this:
#
# : GENERAL
#
# Each statement defines a section:
#
# ----- PSTATESET statement
#
# PSTATESET statement is used to define a section for pstate configuration
# information. It must be followed by pstate word and an integer representing
# the pstate you want to configure. For example:
#
# : PSTATESET pstate 2
#
# allows you to configure pstate 2 for all cores.
# You can also use the word core to define a specific core in such way:
#
# : PSTATESET pstate 2 core 1
#
# Inside a PSTATESET section you can define these items:
#
# vid <integer>
# fid <integer>
# did <integer>
# enable
# disable
#
# Clearly vid, fid and did must be followed by an integer representing
# the value you want to set for that item.
# enable and disable set the enabled bit of the specific pstate.
#
#
# ----- GENERAL statement
#
# GENERAL statement allows you to configure general aspects of the
# processor. Accepted items are:
#
# psmax <integer>		- sets maximum pstate
#
# nbvid <integer>		- sets northbridge (memory controller)
#				voltage
# altvid <integer>		- sets alternate VID (range from 28 to
#				128, as processor VIDs)
# slamtime <integer>		- sets voltage regulator module slamming
#				time. Value here is a register
#
# altvidslamtime <integer>	- sets voltage regulator module for
#				slamming voltage when entering AltVID
#				state. Value is a register here too.
#
# psienable			- enables PSI bit
#
# psidisable			- disables PSI bit
#
# psithreshold <integer>	- Sets PSI threshold to defined VID value
#				valid values range from 28 to 128, as
#				processor VIDs)
#
# C1Eenable <integer>		- Enables C1E state on specified core
#
# C1Edisable <integer>		- Disables C1E state on specified core
#
#
# ----- SCALER statement
#
# SCALER statement allows to control the integrated CPU scaler inside
# TurionPowerControl. Also SCALER can be controlled only using this
# configuration file.
# Items for SCALER are:
#
# samplingrate <integer>		- This item sets the sampling
#					frequency for the scaler in
#					milliseconds. Faster sampling
#					frequencies denote a more 
#					reactive system, but may consume
#					more CPU power. Good values
#					are around 50-75ms
#
# uppolicy <step/rocket/dynamic>	- This item sets the policy
#					for pstate upgrade when 
#					more power is required.
#					-> step policy allows to upgrade
#					one pstate each time; Acts like
#					conservative policy in Linux
#					Scaler.
#
#					-> rocket policy upgrades directly
#					to fastest pstate when required.
#					Acts like on demand policy in Linux
#					Scaler and like Windows Vista/7 default
#					scaler.
#
#					-> dynamic policy upgrades to
#					faster pstates dynamically depending
#					on the cpu load.
#					Default policy is step.
#
# downpolicy <step/rocket/dynamic>	- This sets the policy for pstate
#					downgrade when less power is required
#
#					Check uppolicy item for details.
#
#					Default policy is step.
#
# upperthreshold <integer>		- Sets the cpu usage threshold to bring
#					the processor to an higher pstate
#					Default threshold is 80%
#
# lowerthreshold <integer>		- Sets the cpu usage threshold to bring
#					the processor to a lower pstate
#					Default threshold is 20%


# These pstates are default Pstates coming from my Turion ZM 80 processor.
# Feel free to modify them depending on your processor and your tastes.

: PSTATESET pstate 0

vid 40
fid 9
did 0
enable

: PSTATESET pstate 1

vid 40
fid 8
did 0
enable

: PSTATESET pstate 2

vid 62
fid 14
did 2
enable

# Uncomment the following PSTATESET to rid of pstate 6 anomalous transitions.
# This needs no modification, it will work on any model with these values.

# : PSTATESET pstate 6
# vid 48
# fid 13
# did 1
# disable

# Modify according to your pstate 0 the following PSTATESET and uncomment it
# to take rid of pstate 7 anomalous transition. Note that touching pstate 7
# on some systems may cause an immediate crash.

# : PSTATESET pstate 7
# vid 36
# fid 13
# did 0
# disable

: GENERAL

# psmax is set by default to 2 with Turion ZM/RM and to 1 with Athlon QL
# processors. You can set this value to 3 or more (if it works for you)
# to gain more pstates. Remember that you MUST configure them before
# you are going to use more pstates

psmax 2
psienable
nbvid 54
altvidslamtime 3
psithreshold 48
 
: SCALER

# Following scaler options are used by TurionPowerControl only if you set the
# -scaler command line switch.

samplingrate 60
uppolicy dynamic
downpolicy dynamic


---

### Post by mothersh1p on 2011-09-03
For Gaming on Windows 64-Bit I use this .cfgfile:

> 
TurionPowerControl -pallc 0 39 0 14
TurionPowerControl -pallc 1 56 1 24
TurionPowerControl -pallc 2 56 1 24

TurionPowerControl -pallc 6 39 0 14
TurionPowerControl -pallc 7 39 0 14
TurionPowerControl -nbvid 54

TurionPowerControl -rampuptime 4
TurionPowerControl -rampdowntime 4

TurionPowerControl -psienable


TurionPowerControl -altvidslamtime 4
TurionPowerControl -psithreshold 48

TurionPowerControl -c1enable 0
TurionPowerControl -c1enable 1

---

### Post by blackshard on 2011-09-03
> **mothersh1p said:**
> I use only 70,59% of my cpu maxspeed to reduce my overheating problems. I bought a notebook cooler, I updated to the latest OS, and I use this option to start my Linux-Kernel:

.

Overall my system is a bit better, but it's still very unstable. Maybe it helps to update to 64-bit? Especially when watching Flash-Videos it can compromise the system.



If you have overheating problems, you have to check

- Dust inside the exhaust vents. This is terrible, dust will not let air flow outside

- Change thermal paste between the cpu and the heatspreader. When the thermal paste becomes old, dirt and solid, it loses the heat transmission capacity.

A 64 bit environment won't help at all, you must clean your system before all.

> **mothersh1p said:**
> For Gaming on Windows 64-Bit I use this .cfgfile:

I saw you configuration file and it won't work good. As stated in the documentation, FID values above the maximum FID will be capped by the processor itself.

For example, my ZM-80 maximum FID is 13, if I set any pstate with FID above 13, the processor will just cap the value to the maximum. This is true even if DID is different than 0.
Note that maximum frequency equivalent for FID 13 is 2100 Mhz, for FID 14 is 2200 Mhz, and so on...

Instead I see you use FID values like 24 for pstate 1 and pstate 2: this is just wrong.
That's another reason why I suggest to use **frequency** and **vcore** configuration options.
Also I suggest in the documentation not to change frequencies of pstates in family 11h processors because it is often source of instability.

I assume that your processor is running at 2200 Mhz (FID=14), so I suggest you a configuration like this:

```


TurionPowerControl -set core all pstate 0 vcore 1.050 pstate 1 vcore 0.800 pstate 2 vcore 0.775 pstate 6 frequency 2200 vcore 1.050 pstate 7 frequency 2200 vcore 1.050 -nbvid 54 -slamtime 4

TurionPowerControl -psienable

TurionPowerControl -altvidslamtime 4
TurionPowerControl -psithreshold 48

TurionPowerControl -c1enable 0
TurionPowerControl -c1enable 1

```

But of course you must keep clean notebook internal if you have overheating problems.

---

### Post by mothersh1p on 2011-09-03
> **blackshard said:**
> If you have overheating problems, you have to check

- Dust inside the exhaust vents. This is terrible, dust will not let air flow outside

- Change thermal paste between the cpu and the heatspreader. When the thermal paste becomes old, dirt and solid, it loses the heat transmission capacity.

A 64 bit environment won't help at all, you must clean your system before all.



I saw you configuration file and it won't work good. As stated in the documentation, FID values above the maximum FID will be capped by the processor itself.

For example, my ZM-80 maximum FID is 13, if I set any pstate with FID above 13, the processor will just cap the value to the maximum. This is true even if DID is different than 0.
Note that maximum frequency equivalent for FID 13 is 2100 Mhz, for FID 14 is 2200 Mhz, and so on...

Instead I see you use FID values like 24 for pstate 1 and pstate 2: this is just wrong.
That's another reason why I suggest to use **frequency** and **vcore** configuration options.
Also I suggest in the documentation not to change frequencies of pstates in family 11h processors because it is often source of instability.

I assume that your processor is running at 2200 Mhz (FID=14), so I suggest you a configuration like this:

```


TurionPowerControl -set core all pstate 0 vcore 1.050 pstate 1 vcore 0.800 pstate 2 vcore 0.775 pstate 6 frequency 2200 vcore 1.050 pstate 7 frequency 2200 vcore 1.050 -nbvid 54 -slamtime 4

TurionPowerControl -psienable

TurionPowerControl -altvidslamtime 4
TurionPowerControl -psithreshold 48

TurionPowerControl -c1enable 0
TurionPowerControl -c1enable 1

```


But of course you must keep clean notebook internal if you have overheating problems.

Thsnks for the reply and for the great tool. First off I've cleansed from dust and applied new thermal paste, it's more stable now. I think it is really good now, but I wanted to say I'm a bit frustrated about the thermal design and the lack of support from the notebook vendor. I guess really good notebooks are rare, and it depends heavily on the use case. I don't move around a lot with my notebook.

Second, the idea of my gaming cfgfile is that I want only 2 Pstate 2200 Mhz and 1700 Mhz. I didn't know that FID is capped to max. Maybe I should read the manual again. Thanks for hint. 

 Cam I write like this?

> TurionPowerControl -set core all pstate 0 frequency 2200 vcore 1.050 pstate 1 frequency 1700 vcore 0.800 pstate 2 frequency 1700 vcore 0.775 pstate 6 frequency 2200 vcore 1.050 pstate 7 frequency 2200 vcore 1.050 -nbvid 54 -slamtime 4


I'm missing the support for the Athlon 64 X2. When can we expect it?

---

### Post by blackshard on 2011-09-03
> **mothersh1p said:**
> Thsnks for the reply and for the great tool. First off I've cleansed from dust and applied new thermal paste, it's more stable now. I think it is really good now, but I wanted to say I'm a bit frustrated about the thermal design and the lack of support from the notebook vendor. I guess really good notebooks are rare, and it depends heavily on the use case. I don't move around a lot with my notebook.



don't tell me that to me. I own a pavilion dv5 and it's internals are one of the worst designed ever.

Everything reaches high temperatures after half an hour or so.

> **mothersh1p said:**
> 
Second, the idea of my gaming cfgfile is that I want only 2 Pstate 2200 Mhz and 1700 Mhz. I didn't know that FID is capped to max. Maybe I should read the manual again. Thanks for hint. 

 Cam I write like this?


IMHO such command will freeze your machine almost immediately. You can't expect stability with only 0.800v and frequency like 1700 Mhz. You have to fetch *at least* 1.000v at such frequency, maybe more.
But anyway I don't see the point of doing this, normally the linux cpu scaler handles high loads by itself, doing that you will just reduce the cooling capacity of the processor.


> **mothersh1p said:**
> 
I'm missing the support for the Athlon 64 X2. When can we expect it?

Sorry, but those processors won't be supported. I did extensive research upon Athlon 64 processors. First of all I found that they are completely different than recent AMD processors. Then they have no pstates table to manipulate, and all pstate transitions are done in software. For this reason, there's the need for a kernel module to do that, and at the moment there's a "fork" of powernow-k8 kernel module that is called linux-phc, but it is not as easy as tpc.

---

### Post by mothersh1p on 2011-09-03
> **blackshard said:**
> 
IMHO such command will freeze your machine almost immediately. You can't expect stability with only 0.800v and frequency like 1700 Mhz. You have to fetch *at least* 1.000v at such frequency, maybe more.


Thanks for the fast reply, but this doesn't work either: frequency 2200 vcore 1.050v. At 2200 Mhz it must be at least 1.0625v in my laptop. With 1.050v I'm getting spurious blue screens during a game. I'm using this .cfgfile now:

> 
TurionPowerControl -set core all pstate 0 frequency 2200 vcore 1.0625 pstate 1 frequency 1800 vcore 1.050 pstate 2 frequency 1800 vcore 1.050 pstate 3 frequency 1800 vcore 1.050 pstate 6 frequency 2200 vcore 1.0625 pstate 7 frequency 2200 vcore 1.0625 -nbvid 54 -slamtime 4
TurionPowerControl -rampuptime 4
TurionPowerControl -rampdowntime 4
TurionPowerControl -psienable
TurionPowerControl -altvidslamtime 4
TurionPowerControl -psithreshold 48
TurionPowerControl -c1enable 0
TurionPowerControl -c1enable 1

> But anyway I don't see the point of doing this, normally the linux cpu scaler handles high loads by itself, doing that you will just reduce the cooling capacity of the processor.

First, I don't use Linux to play. Not for now. Second, my idea is to disable the scaler for gaming. In fact I wanted to try the -psmax switch from this tool. But then I think to myself I can try 2 transitions to give the cpu some time to recover, because of the heat problem. Another problem is when the cpu overheats the BIOS or something else is limiting the transitions. I didn't experience it latetly but when it happens I don't want my cpu is sitting at pstate 2 or 550 Mhz during a game session for the rest of the time. I have read about BIOS and NVRAM max. temperature settings in the Internet and I was more then happy to raise this barrier. But the tool didn't worked and the vendor (of my laptop) didn't understand me. Then I have experiemented with a custom DSDT, but I wasn't lucky, too. Can you explain how I can use the -psmax switch, please?

---

### Post by blackshard on 2011-09-04
> **mothersh1p said:**
> First off, I don't use Linux to play. Not for now. My idea is to disable the scaler for gaming. In fact I wanted to try the -psmax switch from this tool. But then I think to myself I can try 2 transitions to give the cpu some time to recover, because of the heat problem. Another problem is when the cpu overheats the BIOS or something else is limiting the transitions. I didn't experience it latetly but when it happens I don't want my cpu is sitting at pstate 2 or 550 Mhz during a game session for the rest of the time. I have read about BIOS and NVRAM max. temperature settings in the Internet and I was more then happy to raise this barrier. But the tool didn't worked and the vendor (of my laptop) didn't understand me. Then I have experiemented with a custom DSDT, but I wasn't lucky, too. Can you explain how I can use the -psmax switch?


The processor has built-in overheating prevention, it can be configured using -htc, -htcenable, -htcdisable, -htctemplimit, etc... switches. See paragraph 2.4 of the documentation. Maybe this is the limiting factor is your system.

Try TurionPowerControl -htc to see how thermals are configured for your processor, but I suggest not to disable hardware thermal control. Instead you can reduce your processor frequency (and voltage) at fastest pstate: that surely will reduce the amount of heat produced.
Anyway, that overheating problem can't be caused by the processor itself, I'm sure there's something wrong with the heat dissipation system or the motherboard.

---

### Post by mothersh1p on 2011-09-04
> **blackshard said:**
> The processor has built-in overheating prevention, it can be configured using -htc, -htcenable, -htcdisable, -htctemplimit, etc... switches. See paragraph 2.4 of the documentation. Maybe this is the limiting factor is your system.

Try TurionPowerControl -htc to see how thermals are configured for your processor, but I suggest not to disable hardware thermal control. Instead you can reduce your processor frequency (and voltage) at fastest pstate: that surely will reduce the amount of heat produced.
Anyway, that overheating problem can't be caused by the processor itself, I'm sure there's something wrong with the heat dissipation system or the motherboard.

On my laptop the -htc switch gives me this:
> HTC features enabled flag: false. Hardware Thermal Control is disabled.
HTC features currently active (means overheating): false
HTC features has been active (means overheated in past): false
HTC parameters are locked: false
HTC Slew control: by Tctl without Slew register
HTC Limit temperature (equal or above means overheating): 100
HTC Hysteresis temperature (equal or below means no more overheating) : 95
HTC PState Limit: 1
Processor AltVID: 64 (0.750v)

But I know for sure that my laptop shutdowns at 105 degree celsius. I think I can explain it that in Linux something isn't right because the fan is always turning at a higher level and I'm reaching 105 degree celsius very easy when I put a bit load on the cpu. That's why I limit it to 71% of the max cpu speed in Linux. The -htc switch is the same in Linux. In Windows the fan is turning much slower at the same load, and I barely touch the max 105 degree celsius limit. That's why I thought it's a BIOS or NVRAM setting. I'm not sure what to do next, but it seems that Linux is not supported by this laptop. It's totally missing the (ACPI)-fan control and its gets hot with a great magnitude or capped/limit my transitions to soon. I would be happy if I can modify the DSDT or control the fan in Linux. But I guess I have to wait.

I'm using max performance energy profile in Windows and the output of the -CM switch is like this:

```
Timestamp: 4611857 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 89
 Detected pstate 7 on core 1
Timestamp: 4611904 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4612107 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4612263 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4612309 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4612419 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4612965 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613027 - c0:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 0
Timestamp: 4613183 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 89
 Detected pstate 7 on core 1
Timestamp: 4613277 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613339 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4613635 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613838 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613901 - c0:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 0
Timestamp: 4613947 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4614244 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 89
 Detected pstate 7 on core 1
Timestamp: 4614805 - c0:ps0 vc1.063 fr2200 - c1:ps0 vc1.063 fr2200 - Tctl: 91
```

You can see pstate 7 very often, I think it's the same with your -scaler switch but I didn't test it with the energy profile off? I saw the -CM sometimes giving the right pstate 2 for a some time but mostly it alternates between pstate 7 and pstate 0.

---

### Post by blackshard on 2011-09-04
> **mothersh1p said:**
> On my laptop the -htc switch gives me this:


But I know for sure that my laptop shutdowns at 105 degree celsius. I think I can explain it that in Linux something isn't right because the fan is always turning at a higher level and I'm reaching 105 degree celsius very easy when I put a bit load on the cpu. That's why I limit it to 71% of the max cpu speed in Linux. The -htc switch is the same in Linux. In Windows the fan is turning much slower at the same load, and I barely touch the max 105 degree celsius limit. That's why I thought it's a BIOS or NVRAM setting. I'm not sure what to do next, but it seems that Linux is not supported by this laptop. It's totally missing the (ACPI)-fan control and its gets hot with a great magnitude or capped/limit my transitions to soon. I would be happy if I can modify the DSDT or control the fan in Linux. But I guess I have to wait.

The 105°C temp limit is set in bios and cannot be changed or disabled. This is clearly a measure to not destroy your processor and motherboard.
Obviously your system should never reach such limit, in any case.
The fact the system shuts down is normal, but the fact the system is reaching such temperature is not normal and there's clearly a hardware problem that you can't fix with software.

> **mothersh1p said:**
> 
I'm using max performance energy profile in Windows and the output of the -CM switch is like this:

```
Timestamp: 4611857 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 89
 Detected pstate 7 on core 1
Timestamp: 4611904 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4612107 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4612263 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4612309 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4612419 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4612965 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613027 - c0:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 0
Timestamp: 4613183 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 89
 Detected pstate 7 on core 1
Timestamp: 4613277 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613339 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4613635 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613838 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 90
 Detected pstate 7 on core 1
Timestamp: 4613901 - c0:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 0
Timestamp: 4613947 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 -
 Detected pstate 7 on core 1
Timestamp: 4614244 - c0:ps0 vc1.063 fr2200 - c1:ps7 vc1.063 fr2200 - Tctl: 89
 Detected pstate 7 on core 1
Timestamp: 4614805 - c0:ps0 vc1.063 fr2200 - c1:ps0 vc1.063 fr2200 - Tctl: 91
```You can see pstate 7 very often, I think it's the same with your -scaler switch but I didn't test it with the energy profile off? I saw the -CM sometimes giving the right pstate 2 for a some time but mostly it alternates between pstate 7 and pstate 0.

Yes, pstate 6 and 7 are anomalies I can't yet explain happening only in Family 11h processors.
BTW, are those 90°C reached during high cpu load or just during idling? Because that temperature is absolutely normal during a stress test but it is not if the system is doing nothing.

---

### Post by mothersh1p on 2011-09-04
> **blackshard said:**
> The 105°C temp limit is set in bios and cannot be changed or disabled. This is clearly a measure to not destroy your processor and motherboard.
Obviously your system should never reach such limit, in any case.
The fact the system shuts down is normal, but the fact the system is reaching such temperature is not normal and there's clearly a hardware problem that you can't fix with software.



Yes, pstate 6 and 7 are anomalies I can't yet explain happening only in Family 11h processors.
BTW, are those 90°C reached during high cpu load or just during idling? Because that temperature is absolutely normal during a stress test but it is not if the system is doing nothing.

I know of a guy changing the bios max temperature in the NVRAM to something like 115°C. I think this will work with this thermal design, or at least it would be worth a try but unfortunately his tool doesn't support my laptop. The same is for the fan control. There is a tool that control the fan without the bios but my laptop isn't supported. I did the -CM switch when I did some huffman decoding on my laptop. This can explain the high load and high temperature.

---

### Post by mothersh1p on 2011-09-05
```
TurionPowerControl -set core all pstate 0 frequency 2200 vcore 1.0625 pstate 1 frequency 1800 vcore 1.050 pstate 2 frequency 1800 vcore 1.050 pstate 3 frequency 1800 vcore 1.050 pstate 6 frequency 2200 vcore 1.0625 pstate 7 frequency 2200 vcore 1.0625 -nbvid 54 -slamtime 4
TurionPowerControl -rampuptime 4
TurionPowerControl -rampdowntime 4
TurionPowerControl -psienable
TurionPowerControl -altvidslamtime 4
TurionPowerControl -psithreshold 48
TurionPowerControl -c1enable 0
TurionPowerControl -c1enable 1 
```

It seems to me that undervolting is generally a bad idea in Windows and when Gaming. I had to use the default 1.100v for 2200 Mhz and also I need to limit the max cpu speed to 1900 Mhz to avoid overheat to 105°C. I got several emergency shutdown because of overheat, I believe it's the BIOS.

I'm using something like this now:

```
TurionPowerControl -set core all pstate 0 frequency 1900 vcore 1.100 pstate 1 frequency 1900 vcore 1.100 pstate 2 frequency 1900 vcore 1.100 pstate 3 frequency 1800 vcore 1.100 pstate 6 frequency 1900 vcore 1.100 pstate 7 frequency 1900 vcore 1.100 -nbvid 54 -slamtime 4
TurionPowerControl -rampuptime 4
TurionPowerControl -rampdowntime 4
TurionPowerControl -psienable
TurionPowerControl -altvidslamtime 4
TurionPowerControl -psithreshold 48
TurionPowerControl -c1enable 0
TurionPowerControl -c1enable 1 
```

I need some better cooling.

---

### Post by blackshard on 2011-09-05
> **mothersh1p said:**
> It seems to me that undervolting is generally a bad idea in Windows and when Gaming. I had to use the default 1.100v for 2200 Mhz and also I need to limit the max cpu speed to 1900 Mhz to avoid overheat to 105°C. I got several emergency shutdown because of overheat, I believe it's the BIOS.


Usually it's not a bad idea if you want to reduce temperatures without losing performance. 
But you'll surely lose something in stability.


> **mothersh1p said:**
> 
I'm using something like this now:
I need some better cooling.

Indeed. Reducing frequency reduces in a proportional manner power consumption.

---

### Post by mothersh1p on 2011-09-08
I have installed linux-phc module but it doesn't work either. I can insert it (Linux Kernel 3.0.3) but the phc_controls virtual device is not present. What is strange to me is that linux-phc or powernow-k8 module can control the fan. With a module loaded the system has 2 fan states. I'm able to read the temperature and to write to empty RAM of the embedded control by hand (IO ports 0x66 and 0x62). I can dump all the register of the ec and I can see the difference of the two fan states by looking at the dump but I can only write to the register 0x92 (TTID) and to empty registers. When I unload the modules and let tpc scales its working better, because there is a bug(?) in the linux-phc and powernow_k8 module that makes my computer very quickly disable the transitions and stays at the lowest pstate like forever when the cpu is under load. With those modules unloaded and set -htctemplimit to 110 and force -fo with tpc I can stress the cpu much longer (like unlimited). This is a bit strange because in Windows I had to limit max cpu. I should try again with the same setting.

EDIT: I didn't know there is something like CPU throtteling in the thermal module. So I've disabled the thermal module with the boot switch thermal.act=90 thermal.nocrt and disabled it in the kernel config. Hopefully it stops throtteling my cpu when its getting a bit hot. But when I want to fork the tpc process in to the background with "&" switch the program just disappear. This is my code:

> TPC -cfgfile scaler.cfg

Output of TPC:

> Turion Power States Optimization and Control - by blackshard - v0.30
Detected CPU:
Family: 0xf		Model: 0x3		Stepping: 0x1
Extended Family: 0x11	Extended Model: 0x3
Package Type: 0x2	BrandId: 0x520	
Detected Physical Cores: 2
Configuration file: scaler.cfg
Parsing configuration...
Configuration file has been parsed!

Here is my -cfgfile:

> 
: SCALER

samplingrate 60
uppolicy dynamic
downpolicy dynamic


But the program is not in the background (bg) and not in the process list (ps). Can you help, please?

---

### Post by rountrey on 2011-09-10
This is the first I had ever heard about this program. It sounds great but I found something called Granola ([www.grano.la](www.grano.la)) and it works really well for keeping the temp down, and helps in battery life too.

---

### Post by blackshard on 2011-09-11
> **rountrey said:**
> This is the first I had ever heard about this program. It sounds great but I found something called Granola ([www.grano.la]("http://www.grano.la")) and it works really well for keeping the temp down, and helps in battery life too.

I've always been very skeptical about that product. It talks about miracles but doesn't tell anyone what does it really do.

---

### Post by mothersh1p on 2011-09-11
> **blackshard said:**
> I've always been very skeptical about that product. It talks about miracles but doesn't tell anyone what does it really do.

It's needs cpufreq in Linux. Maybe it's just a clever replacement for a cpu-governor?

---

### Post by blackshard on 2011-09-11
> **mothersh1p said:**
> It's needs cpufreq in Linux. Maybe it's just a clever replacement for a cpu-governor?

Probably it is just a replacemente. If it is clever I don't know. Actually I don't think kernel developers are dummy people

---

### Post by mothersh1p on 2011-09-11
> **blackshard said:**
> Probably it is just a replacemente. If it is clever I don't know. Actually I don't think kernel developers are dummy people

It's good to have a choice? It's something clever and it's closed source? I think of using a quadtree or a space-filling-curve for a governor.

EDIT: I installed it but it gives me this: 
> 
sudo /usr/sbin/granola -D
/usr/sbin/granola: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by /usr/sbin/granola)


---

### Post by mothersh1p on 2011-09-13
> **mothersh1p said:**
> 
EDIT: I didn't know there is something like CPU throtteling in the thermal module. So I've disabled the thermal module with the boot switch thermal.act=90 thermal.nocrt and disabled it in the kernel config. Hopefully it stops throtteling my cpu when its getting a bit hot. But when I want to fork the tpc process in to the background with "&" switch the program just disappear. This is my code:

I've found out the problem, I forgot the -scaler switch:

```
tpc -cfgfile example.cfg -scaler &
```

Now it works in the background, too. But I have noticed a big improvement in speed with TPC over powernow_k8. My systems feels faster. Loading time of Firefox for example. Maybe it's better code? BTW. I managed to switch my fan on/off with some embedded register. But I couldn't find how to control the speed. Switching off thermal module with thermal.nocrt and thermal.act=90 seems to help a lot (to reduce throtteling and noise). I think I will test TPC scaler for a while. Seems to be a good option :).

---

### Post by mothersh1p on 2011-09-17
When I run switch -scaler and "&" I get this:

```
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0

```

My TPC version is 0.30. Any Idea?

---

### Post by blackshard on 2011-09-18
> **mothersh1p said:**
> When I run switch -scaler and "&" I get this:

```
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0
PState.cpp: Wrong pstate 8, assuming default PState 0

```My TPC version is 0.30. Any Idea?

yes, it's normal on your processor due to the fact that it autonomously go in pstate 6 and 7. You may try latest v0.41 version which has a completely different scaler implementation.

---

### Post by mothersh1p on 2011-09-18
> **blackshard said:**
> yes, it's normal on your processor due to the fact that it autonomously go in pstate 6 and 7. You may try latest v0.41 version which has a completely different scaler implementation.

Where can I get this? It would be nice if you can post a link?

---

### Post by blackshard on 2011-09-18
> **mothersh1p said:**
> Where can I get this? It would be nice if you can post a link?

You can find it on [http://amdath800.dyndns.org/amd](http://amdath800.dyndns.org/amd) or [http://code.google.com/p/turionpowercontrol](http://code.google.com/p/turionpowercontrol)

---

### Post by mothersh1p on 2011-09-18
> **blackshard said:**
> You can find it on [http://amdath800.dyndns.org/amd](http://amdath800.dyndns.org/amd) or [http://code.google.com/p/turionpowercontrol](http://code.google.com/p/turionpowercontrol)

I'm new to Linux programming, but I just wrote a kernel module to control my fan speed. I enjoy a silent laptop now. It shouldn't be too complicated to make a kernel module from your scaler or tpc. Did you think of it? The scaler seems to work good. I will try 0.41 and report it later. So far tpc 0.30 seems to work well. What is your changes to the scaler?

---

### Post by mothersh1p on 2011-09-18
> **blackshard said:**
> You can find it on [http://amdath800.dyndns.org/amd](http://amdath800.dyndns.org/amd) or [http://code.google.com/p/turionpowercontrol](http://code.google.com/p/turionpowercontrol)

I get this error:
```

Unknown identifier: uppolicy
Error: invalid configuration identifier at row 4800

```

my cfg file:
```

: SCALER

# Following scaler options are used by TurionPowerControl only if you set the
# -scaler command line switch.

samplingrate 75
uppolicy dynamic
downpolicy dynamic
upperthreshold 30
lowerthreshold 10


```

---

### Post by blackshard on 2011-09-19
> **mothersh1p said:**
> I get this error:
```

Unknown identifier: uppolicy
Error: invalid configuration identifier at row 4800

```my cfg file:
```

: SCALER

# Following scaler options are used by TurionPowerControl only if you set the
# -scaler command line switch.

samplingrate 75
uppolicy dynamic
downpolicy dynamic
upperthreshold 30
lowerthreshold 10


```

Yeah I changed some policy names but I forgot to update the configuration file with the proper names, now there are no more uppolicy and downpolicy, but just policy that controls both upward and downward transistions. Also dynamic policy has been removed, now there are just rocket and step.

---

### Post by mothersh1p on 2011-09-19
> **blackshard said:**
> Yeah I changed some policy names but I forgot to update the configuration file with the proper names, now there are no more uppolicy and downpolicy, but just policy that controls both upward and downward transistions. Also dynamic policy has been removed, now there are just rocket and step.

Why is dynamic and uppolicy removed? I think it's very useful, at least uppolicy, because I just wrote the same for my cpu fan?

---

### Post by blackshard on 2011-09-21
> **mothersh1p said:**
> Why is dynamic and uppolicy removed? I think it's very useful, at least uppolicy, because I just wrote the same for my cpu fan?

They were removed for simplicity. They may return, but can't promise anything.

---

### Post by mothersh1p on 2011-09-25
> **blackshard said:**
> They were removed for simplicity. They may return, but can't promise anything.

When I try me new fan control kernel module without running TPC with my settings the fan control measure wrong temperature and writing to ec doesn't seems to do anything? I think TPC change some bios variable in my laptop?

---

### Post by blackshard on 2011-09-25
> **mothersh1p said:**
> When I try me new fan control kernel module without running TPC with my settings the fan control measure wrong temperature and writing to ec doesn't seems to do anything? I think TPC change some bios variable in my laptop?

Absolutely doesn't interact with bios settings.

---

### Post by mothersh1p on 2011-09-25
> **blackshard said:**
> Absolutely doesn't interact with bios settings.

I get config error at boot time, too. But the cfgfile I use after startup is the same and it works when I manually load it with TPC 0.30. My kernel module works. Maybe my laptop is broken? I use it a lot.

---

### Post by mothersh1p on 2011-10-03
> **mothersh1p said:**
> I get config error at boot time, too. But the cfgfile I use after startup is the same and it works when I manually load it with TPC 0.30. My kernel module works. Maybe my laptop is broken? I use it a lot.

I've found the reason for the config error the program didn't found the file (incorrect path).

Do your program and the cpu-scaler works on Windows?

---

### Post by blackshard on 2011-10-03
> **mothersh1p said:**
> I've found the reason for the config error the program didn't found the file (incorrect path).

Do your program and the cpu-scaler works on Windows?

Of course

---

### Post by mothersh1p on 2011-10-25
> **blackshard said:**
> Of course

Thank you for your fast reply. I want to learn from your code and make a fan control for my laptop but I found it hard to find a working example for winring0. So I decided to check your project but I got this problem when I load tpc 0.30 into VS 2008 and try to compile it:

```
>Compiling...
1>Compiling manifest to resources...
1>Microsoft (R) Windows (R) Resource Compiler Version 6.0.5724.0
1>Copyright (C) Microsoft Corporation.  All rights reserved.
1>Linking...
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "unsigned long __stdcall GetDriverVersion(unsigned char *,unsigned char *,unsigned char *,unsigned char *)" (?GetDriverVersion@@YGKPAE000@Z) referenced in function "int __cdecl initWinRing0(void)" (?initWinRing0@@YAHXZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "unsigned long __stdcall GetDllStatus(void)" (?GetDllStatus@@YGKXZ) referenced in function "int __cdecl initWinRing0(void)" (?initWinRing0@@YAHXZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "int __stdcall InitializeOls(void)" (?InitializeOls@@YGHXZ) referenced in function "int __cdecl initWinRing0(void)" (?initWinRing0@@YAHXZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "void __stdcall DeinitializeOls(void)" (?DeinitializeOls@@YGXXZ) referenced in function "int __cdecl closeWinRing0(void)" (?closeWinRing0@@YAHXZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "int __stdcall Cpuid(unsigned long,unsigned long *,unsigned long *,unsigned long *,unsigned long *)" (?Cpuid@@YGHKPAK000@Z) referenced in function "int __cdecl processorSupport(void)" (?processorSupport@@YAHXZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "int __stdcall ReadPciConfigDwordEx(unsigned long,unsigned long,unsigned long *)" (?ReadPciConfigDwordEx@@YGHKKPAK@Z) referenced in function "void __cdecl processorStatus(class Processor *)" (?processorStatus@@YAXPAVProcessor@@@Z)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: unsigned long __thiscall PState::getPState(void)" (?getPState@PState@@QAEKXZ) referenced in function "void __cdecl processorStatus(class Processor *)" (?processorStatus@@YAXPAVProcessor@@@Z)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: void __thiscall PState::setPState(unsigned long)" (?setPState@PState@@QAEXK@Z) referenced in function "void __cdecl processorStatus(class Processor *)" (?processorStatus@@YAXPAVProcessor@@@Z)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: __thiscall PState::PState(unsigned long)" (??0PState@@QAE@K@Z) referenced in function "void __cdecl processorStatus(class Processor *)" (?processorStatus@@YAXPAVProcessor@@@Z)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: unsigned long __thiscall Processor::HTLinkToFreq(unsigned long)" (?HTLinkToFreq@Processor@@QAEKK@Z) referenced in function "void __cdecl processorHTLinkStatus(class Processor *)" (?processorHTLinkStatus@@YAXPAVProcessor@@@Z)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: void __thiscall Scaler::beginScaling(void)" (?beginScaling@Scaler@@QAEXXZ) referenced in function _main
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: int __thiscall CfgManager::parseCfgFile(void)" (?parseCfgFile@CfgManager@@QAEHXZ) referenced in function _main
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: bool __thiscall CfgManager::openCfgFile(char *)" (?openCfgFile@CfgManager@@QAE_NPAD@Z) referenced in function _main
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: __thiscall CfgManager::CfgManager(class Processor *,class Scaler *)" (??0CfgManager@@QAE@PAVProcessor@@PAVScaler@@@Z) referenced in function _main
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "public: __thiscall Scaler::Scaler(class Processor *)" (??0Scaler@@QAE@PAVProcessor@@@Z) referenced in function _main
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "protected: void __thiscall Processor::setProcessorIdentifier(unsigned long)" (?setProcessorIdentifier@Processor@@IAEXK@Z) referenced in function "public: __thiscall TurionZM::TurionZM(void)" (??0TurionZM@@QAE@XZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "protected: void __thiscall Processor::setProcessorStrId(char const *)" (?setProcessorStrId@Processor@@IAEXPBD@Z) referenced in function "public: __thiscall TurionZM::TurionZM(void)" (??0TurionZM@@QAE@XZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "protected: virtual void __thiscall Griffin::setPCtoIdleCounter(int,int)" (?setPCtoIdleCounter@Griffin@@MAEXHH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall Griffin::convertVIDtoVcore(unsigned long)" (?convertVIDtoVcore@Griffin@@UAEMK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::convertVcoretoVID(float)" (?convertVcoretoVID@Griffin@@UAEKM@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::convertFDtoFreq(unsigned long,unsigned long)" (?convertFDtoFreq@Griffin@@UAEKKK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setVID(class PState,unsigned long,unsigned long)" (?setVID@Griffin@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setVID(class PState,unsigned long)" (?setVID@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setFID(class PState,unsigned long,unsigned long)" (?setFID@Griffin@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setFID(class PState,unsigned long)" (?setFID@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setDID(class PState,unsigned long,unsigned long)" (?setDID@Griffin@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setDID(class PState,unsigned long)" (?setDID@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getVID(class PState,unsigned long)" (?getVID@Griffin@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getVID(class PState)" (?getVID@Griffin@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getFID(class PState,unsigned long)" (?getFID@Griffin@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getFID(class PState)" (?getFID@Griffin@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getDID(class PState,unsigned long)" (?getDID@Griffin@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getDID(class PState)" (?getDID@Griffin@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setFrequency(class PState,unsigned long,unsigned long)" (?setFrequency@Griffin@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setFrequency(class PState,unsigned long)" (?setFrequency@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setVCore(class PState,float,unsigned long)" (?setVCore@Griffin@@UAEXVPState@@MK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setVCore(class PState,float)" (?setVCore@Griffin@@UAEXVPState@@M@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getFrequency(class PState,unsigned long)" (?getFrequency@Griffin@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getFrequency(class PState)" (?getFrequency@Griffin@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall Griffin::getVCore(class PState,unsigned long)" (?getVCore@Griffin@@UAEMVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall Griffin::getVCore(class PState)" (?getVCore@Griffin@@UAEMVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::pStateEnable(class PState,unsigned long)" (?pStateEnable@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::pStateEnable(class PState)" (?pStateEnable@Griffin@@UAEXVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::pStateDisable(class PState,unsigned long)" (?pStateDisable@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::pStateDisable(class PState)" (?pStateDisable@Griffin@@UAEXVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::pStateEnabled(class PState,unsigned long)" (?pStateEnabled@Griffin@@UAE_NVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::pStateEnabled(class PState)" (?pStateEnabled@Griffin@@UAE_NVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setMaximumPState(class PState)" (?setMaximumPState@Griffin@@UAEXVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual class PState __thiscall Griffin::getMaximumPState(void)" (?getMaximumPState@Griffin@@UAE?AVPState@@XZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setNBVid(unsigned long)" (?setNBVid@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getNBVid(void)" (?getNBVid@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::forcePState(class PState,unsigned long)" (?forcePState@Griffin@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::getSMAF7Enabled(void)" (?getSMAF7Enabled@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::c1eDID(void)" (?c1eDID@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::minVID(void)" (?minVID@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::maxVID(void)" (?maxVID@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::startupPState(void)" (?startupPState@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::maxCPUFrequency(void)" (?maxCPUFrequency@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getTctlRegister(void)" (?getTctlRegister@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getTctlMaxDiff(void)" (?getTctlMaxDiff@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getSlamTime(void)" (?getSlamTime@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setSlamTime(unsigned long)" (?setSlamTime@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getAltVidSlamTime(void)" (?getAltVidSlamTime@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setAltVidSlamTime(unsigned long)" (?setAltVidSlamTime@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::HTCisCapable(void)" (?HTCisCapable@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::HTCisEnabled(void)" (?HTCisEnabled@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::HTCisActive(void)" (?HTCisActive@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::HTChasBeenActive(void)" (?HTChasBeenActive@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::HTCTempLimit(void)" (?HTCTempLimit@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::HTCSlewControl(void)" (?HTCSlewControl@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::HTCHystTemp(void)" (?HTCHystTemp@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::HTCPStateLimit(void)" (?HTCPStateLimit@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::HTCLocked(void)" (?HTCLocked@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getAltVID(void)" (?getAltVID@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::HTCEnable(void)" (?HTCEnable@Griffin@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::HTCDisable(void)" (?HTCDisable@Griffin@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::HTCsetTempLimit(unsigned long)" (?HTCsetTempLimit@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::HTCsetHystLimit(unsigned long)" (?HTCsetHystLimit@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setAltVid(unsigned long)" (?setAltVid@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::getPsiEnabled(void)" (?getPsiEnabled@Griffin@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getPsiThreshold(void)" (?getPsiThreshold@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setPsiEnabled(bool)" (?setPsiEnabled@Griffin@@UAEX_N@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setPsiThreshold(unsigned long)" (?setPsiThreshold@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getHTLinkSpeed(void)" (?getHTLinkSpeed@Griffin@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setHTLinkSpeed(unsigned long)" (?setHTLinkSpeed@Griffin@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::checkMode(void)" (?checkMode@Griffin@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::getC1EStatus(unsigned long)" (?getC1EStatus@Griffin@@UAE_NK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::setC1EStatus(unsigned long,bool)" (?setC1EStatus@Griffin@@UAEXK_N@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::perfCounterGetInfo(void)" (?perfCounterGetInfo@Griffin@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::perfCounterGetValue(int,int)" (?perfCounterGetValue@Griffin@@UAEXHH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::perfCounterMonitor(int,int)" (?perfCounterMonitor@Griffin@@UAEXHH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::perfMonitorCPUUsage(void)" (?perfMonitorCPUUsage@Griffin@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall Griffin::initUsageCounter(unsigned long *)" (?initUsageCounter@Griffin@@UAE_NPAK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getUsageCounter(unsigned long *,unsigned long,int)" (?getUsageCounter@Griffin@@UAEKPAKKH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Griffin::getUsageCounter(unsigned long *,unsigned long)" (?getUsageCounter@Griffin@@UAEKPAKK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall Griffin::getCurrentStatus(struct procStatus *,unsigned long)" (?getCurrentStatus@Griffin@@UAEXPAUprocStatus@@K@Z)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "protected: void __thiscall Processor::setPowerStates(unsigned long)" (?setPowerStates@Processor@@IAEXK@Z) referenced in function "public: __thiscall Griffin::Griffin(void)" (??0Griffin@@QAE@XZ)
1>TurionPowerControl.obj : error LNK2019: unresolved external symbol "protected: void __thiscall Processor::setProcessorCores(unsigned long)" (?setProcessorCores@Processor@@IAEXK@Z) referenced in function "public: __thiscall Griffin::Griffin(void)" (??0Griffin@@QAE@XZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall Processor::convertVIDtoVcore(unsigned long)" (?convertVIDtoVcore@Processor@@UAEMK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Processor::convertVcoretoVID(float)" (?convertVcoretoVID@Processor@@UAEKM@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall Processor::convertFDtoFreq(unsigned long,unsigned long)" (?convertFDtoFreq@Processor@@UAEKKK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "protected: virtual void __thiscall K10Processor::setPCtoIdleCounter(int,int)" (?setPCtoIdleCounter@K10Processor@@MAEXHH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall K10Processor::convertVIDtoVcore(unsigned long)" (?convertVIDtoVcore@K10Processor@@UAEMK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::convertVcoretoVID(float)" (?convertVcoretoVID@K10Processor@@UAEKM@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::convertFDtoFreq(unsigned long,unsigned long)" (?convertFDtoFreq@K10Processor@@UAEKKK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setVID(class PState,unsigned long,unsigned long)" (?setVID@K10Processor@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setVID(class PState,unsigned long)" (?setVID@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setFID(class PState,unsigned long,unsigned long)" (?setFID@K10Processor@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setFID(class PState,unsigned long)" (?setFID@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setDID(class PState,unsigned long,unsigned long)" (?setDID@K10Processor@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setDID(class PState,unsigned long)" (?setDID@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getVID(class PState,unsigned long)" (?getVID@K10Processor@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getVID(class PState)" (?getVID@K10Processor@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getFID(class PState,unsigned long)" (?getFID@K10Processor@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getFID(class PState)" (?getFID@K10Processor@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getDID(class PState,unsigned long)" (?getDID@K10Processor@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getDID(class PState)" (?getDID@K10Processor@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setFrequency(class PState,unsigned long,unsigned long)" (?setFrequency@K10Processor@@UAEXVPState@@KK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setFrequency(class PState,unsigned long)" (?setFrequency@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setVCore(class PState,float,unsigned long)" (?setVCore@K10Processor@@UAEXVPState@@MK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setVCore(class PState,float)" (?setVCore@K10Processor@@UAEXVPState@@M@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getFrequency(class PState,unsigned long)" (?getFrequency@K10Processor@@UAEKVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getFrequency(class PState)" (?getFrequency@K10Processor@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall K10Processor::getVCore(class PState,unsigned long)" (?getVCore@K10Processor@@UAEMVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual float __thiscall K10Processor::getVCore(class PState)" (?getVCore@K10Processor@@UAEMVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::pStateEnable(class PState,unsigned long)" (?pStateEnable@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::pStateEnable(class PState)" (?pStateEnable@K10Processor@@UAEXVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::pStateDisable(class PState,unsigned long)" (?pStateDisable@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::pStateDisable(class PState)" (?pStateDisable@K10Processor@@UAEXVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::pStateEnabled(class PState,unsigned long)" (?pStateEnabled@K10Processor@@UAE_NVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::pStateEnabled(class PState)" (?pStateEnabled@K10Processor@@UAE_NVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setMaximumPState(class PState)" (?setMaximumPState@K10Processor@@UAEXVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual class PState __thiscall K10Processor::getMaximumPState(void)" (?getMaximumPState@K10Processor@@UAE?AVPState@@XZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setNBVid(class PState,unsigned long)" (?setNBVid@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setNBDid(class PState,unsigned long)" (?setNBDid@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getNBVid(class PState)" (?getNBVid@K10Processor@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getNBDid(class PState)" (?getNBDid@K10Processor@@UAEKVPState@@@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getNBFid(void)" (?getNBFid@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getMaxNBFrequency(void)" (?getMaxNBFrequency@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::getPVIMode(void)" (?getPVIMode@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::forcePState(class PState,unsigned long)" (?forcePState@K10Processor@@UAEXVPState@@K@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::minVID(void)" (?minVID@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::maxVID(void)" (?maxVID@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::startupPState(void)" (?startupPState@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::maxCPUFrequency(void)" (?maxCPUFrequency@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getTctlRegister(void)" (?getTctlRegister@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getTctlMaxDiff(void)" (?getTctlMaxDiff@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getSlamTime(void)" (?getSlamTime@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setSlamTime(unsigned long)" (?setSlamTime@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getStepUpRampTime(void)" (?getStepUpRampTime@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getStepDownRampTime(void)" (?getStepDownRampTime@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setStepUpRampTime(unsigned long)" (?setStepUpRampTime@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setStepDownRampTime(unsigned long)" (?setStepDownRampTime@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::HTCisCapable(void)" (?HTCisCapable@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::HTCisEnabled(void)" (?HTCisEnabled@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::HTCisActive(void)" (?HTCisActive@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::HTChasBeenActive(void)" (?HTChasBeenActive@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::HTCTempLimit(void)" (?HTCTempLimit@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::HTCSlewControl(void)" (?HTCSlewControl@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::HTCHystTemp(void)" (?HTCHystTemp@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::HTCPStateLimit(void)" (?HTCPStateLimit@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::HTCLocked(void)" (?HTCLocked@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getAltVID(void)" (?getAltVID@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::HTCEnable(void)" (?HTCEnable@K10Processor@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::HTCDisable(void)" (?HTCDisable@K10Processor@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::HTCsetTempLimit(unsigned long)" (?HTCsetTempLimit@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::HTCsetHystLimit(unsigned long)" (?HTCsetHystLimit@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setAltVid(unsigned long)" (?setAltVid@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::getPsiEnabled(void)" (?getPsiEnabled@K10Processor@@UAE_NXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getPsiThreshold(void)" (?getPsiThreshold@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setPsiEnabled(bool)" (?setPsiEnabled@K10Processor@@UAEX_N@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setPsiThreshold(unsigned long)" (?setPsiThreshold@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getHTLinkSpeed(void)" (?getHTLinkSpeed@K10Processor@@UAEKXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setHTLinkSpeed(unsigned long)" (?setHTLinkSpeed@K10Processor@@UAEXK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::checkMode(void)" (?checkMode@K10Processor@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::getC1EStatus(unsigned long)" (?getC1EStatus@K10Processor@@UAE_NK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::setC1EStatus(unsigned long,bool)" (?setC1EStatus@K10Processor@@UAEXK_N@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::perfCounterGetInfo(void)" (?perfCounterGetInfo@K10Processor@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::perfCounterGetValue(int,int)" (?perfCounterGetValue@K10Processor@@UAEXHH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::perfCounterMonitor(int,int)" (?perfCounterMonitor@K10Processor@@UAEXHH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::perfMonitorCPUUsage(void)" (?perfMonitorCPUUsage@K10Processor@@UAEXXZ)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual bool __thiscall K10Processor::initUsageCounter(unsigned long *)" (?initUsageCounter@K10Processor@@UAE_NPAK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getUsageCounter(unsigned long *,unsigned long,int)" (?getUsageCounter@K10Processor@@UAEKPAKKH@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual unsigned long __thiscall K10Processor::getUsageCounter(unsigned long *,unsigned long)" (?getUsageCounter@K10Processor@@UAEKPAKK@Z)
1>TurionPowerControl.obj : error LNK2001: unresolved external symbol "public: virtual void __thiscall K10Processor::getCurrentStatus(struct procStatus *,unsigned long)" (?getCurrentStatus@K10Processor@@UAEXPAUprocStatus@@K@Z)
1>C:\Users\Chi\Documents\Visual Studio 2008\Projects\TurionPowerControl\Debug\TurionPowerControl.exe : fatal error LNK1120: 185 unresolved externals
1>Build log was saved at "file://c:\Users\Chi\Documents\Visual Studio 2008\Projects\TurionPowerControl\TurionPowerControl\Debug\BuildLog.htm"
1>TurionPowerControl - 186 error(s), 2 warning(s)
========== Build: 0 succeeded, 1 failed, 0 up-to-date, 0 skipped ==========

```

I'm new to VC 2008 and C/C++. I just loaded the main file TurionPowerControl.cpp and hit build. Did I forget to load the project file? Do I have to use the windows console? You have written that this project is for VS 2005/2008. Or do you have a sample how to use winring0?

---

