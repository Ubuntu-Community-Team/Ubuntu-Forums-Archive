---
title: "What is your idle CPU temperature?"
date: 2013-04-13
forum: Ubuntu, Linux and OS Chat
---

### Post by dalpi on 2013-04-13
My idle cpu temp is 45 C.

Specs: Xubuntu 12.10 64-bit, Sony Vaio laptop, quadcore i7, amd catalyst graphics card driver

I started this thread because I want to know what is the "normal" cpu temp on Ubuntu. I know on Windows 7, the idle cpu temp is much lower than 45 C. Through [power saving tweaks]("https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks") and the [kernel power regression fix]("http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html") and the [Jupiter applet]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html"), I have lowered the idle cpu temp from 55 C to 45 C, but I want to get it as low as possible.

---

### Post by JayKay3OOO on 2013-04-13
Depend on ambient temp and their own spec.

Zalman cooler on an AMD 965BE, CPU Fan tuned to silent, 6 web tabs open and no case exhaust fan I've got 33 degrees C. CPU 'danger level' as stated by AMD is 60 + so I guess 33, 34 is normal and I'd not expect to see 40 even transcoding video or converting files. (I ran a youtube video and it dropped to 32).

---

### Post by mreq on 2013-04-13
40-50° on a sony vaio VPCZ2; also a quadcore i7

no special tweaks, just using lightweight XFCE as I found out I don't need anything of Unity/Gnome

---

### Post by breezypt on 2013-04-13
I'm in Ubuntu 12.10 and have an intel Core2Quad Q8400 my temps at idle are 53 C. My max temp for this cpu is 70 C, sorry for the edit, and my GPU is a NVidia GTX 650 running at 33C at idle

---

### Post by andrew.46 on 2013-04-13
How are you all estimating the temp?

---

### Post by kevdog on 2013-04-13
I've got a crappy core 2 duo on a laptop -- and looking at the system monitor applet -- its part of cairo dock -- it says
Core 1 64 degrees, max 105
Core 2 63 degrees, max 105

I have no idea if these monitoring apps are even calibrated -- just saying

---

### Post by dandroid13 on 2013-04-13
> **andrew.46 said:**
> How are you all estimating the temp?

You can install Jupiter from webupd8 ppa.

---

### Post by dalpi on 2013-04-14
> **andrew.46 said:**
> How are you all estimating the temp?

Just install lm-sensors and run sensors in the terminal. More info here: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by sammiev on 2013-04-14
I really like GKrellM system monitor. Included a screen shot.

---

### Post by kevdog on 2013-04-14
> **dalpi said:**
> Just install lm-sensors and run sensors in the terminal. More info here: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

Yep amazingly that works too!!!
$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +30.0°C  (crit = +115.0°C)
temp2:        +70.0°C  (crit = +105.0°C)
temp3:        +28.4°C  (crit = +112.0°C)
temp4:        +72.0°C  (crit = +112.0°C)
temp5:        +54.0°C  (crit = +90.0°C)
temp6:        +16.0°C  (crit = +112.0°C)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +77.0°C  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +68.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +67.0°C  (high = +105.0°C, crit = +105.0°C)

---

### Post by Cheesemill on 2013-04-14
i3-530 overclocked to 3.7GHz...
```
rob@raring:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +28.0°C  (high = +89.0°C, crit = +105.0°C)
Core 2:       +21.0°C  (high = +89.0°C, crit = +105.0°C)

```
It runs about 10°C - 20°C hotter most of the time as I'm usually folding at 100%.

---

### Post by BrokenKingpin on 2013-04-14
i3 in a Laptop

Core 0: 57C
Core 1: 46C

Seems a bit hight, bit it is a pretty small laptop and was just watching some videos.

---

### Post by VinDSL on 2013-04-14
> **andrew.46 said:**
> How are you all estimating the temp?
PSensor...

[INDENT][ATTACH=CONFIG]241357[/ATTACH][/INDENT]

* Rig specs are in my sig

---

### Post by dalpi on 2013-04-16
> **Cheesemill said:**
> i3-530 overclocked to 3.7GHz...
```
rob@raring:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +28.0°C  (high = +89.0°C, crit = +105.0°C)
Core 2:       +21.0°C  (high = +89.0°C, crit = +105.0°C)

```
It runs about 10°C - 20°C hotter most of the time as I'm usually folding at 100%.

Whoa, how did you get your temperatures so cool? laptop or desktop?

---

### Post by pqwoerituytrueiwoq on 2013-04-16
40-45C on my laptop; 40 C is the fan off temp and 45C is the turn back on temp
my desktop idles at 27-34 C depending on the ambient temp, it has a CM hyper 212 evo with 2 fans on it keeping it cool

---

### Post by t430 on 2013-04-17
Hi,

On my Thinkpad T430 (i5 Third Gen) - idle temp is 40-42C. Hope its not too high.

---

### Post by paulisdead on 2013-04-18
i7 2600k, Asus P8P67 Deluxe custom job here
```
Physical id 0:  +32.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +31.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +32.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +30.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +29.0°C  (high = +80.0°C, crit = +98.0°C)
```

I'll hit 60C at full load when it turbos up all four cores to 4.4GHz, though.

---

### Post by Pako Pako on 2013-09-04
How do you guys get such low temps on such new machines?
Even my old core duo 1GHz idles at 54°C

---

### Post by mseney on 2013-09-07
AMD Athlon(tm) 64 X2 Dual Core Processor 6400+ (3.2Ghz)
Core0 Temp:   +34.0°C  
Core1 Temp:   +35.0°C

---

### Post by monkeybrain20122 on 2013-09-07
Before or after cleaning the fan? :)

---

### Post by codingman on 2013-09-08
@Cheesemill

How do you overclock in Linux? BIOS? I used to love OCing back when I was using Windows... Oced an Athlon 64 FX-55 to 3.2Ghz.

---

### Post by CharlesA on 2013-09-08
> **codingman said:**
> @Cheesemill

How do you overclock in Linux? BIOS? I used to love OCing back when I was using Windows... Oced an Athlon 64 FX-55 to 3.2Ghz.

BIOS.

My Server reads 44C for the CPU, but 34C for the hard drives. It's not fully idle, though (VMs are running).

Oh, the CPU is a i7 2600K @ 3.4Ghz (Sandy Bridge).

---

### Post by santosh83 on 2013-09-08
For me it is 42&#8451; after 14 hours of uptime. The temperature just after a cold boot is normally around 35&#8451;. It's a Pentium Dual Core E2140 1.6 GHz on a run-of-the-mill MSI mainboard.

---

### Post by buzzingrobot on 2013-09-08
Thinkpad W530; I7-3630; two 500-gig drives; using onboard Intel:  40-45C, with occasional higher and lower outliers. Fans perk up at 44/45.  

Always on AC at "max performance". No throttling or battery coddling.

---

### Post by codingman on 2013-09-08
Thanks CharlesA, will be doing that tonight, I'm buying a new fan tonight, so I'll wait till then to post my CPU temp. :D

---

### Post by QIII on 2013-09-08
A raw CPU temp may or may not have much meaning (beyond whether or not it is in the safe operating temperature zone) due to the configuration of the system.

For instance, it might sound impressive for me to tell you that my CPU idles at around 30°.  But it's not by magic.

At 20 - 22° C ambient, my AMD Phenom II x6 1100T idles at 19 - 21° per AMD's goofy temperature output as interpreted by sensors.  I add 10° via a script to feed to my conky for a corrected reading of 29 - 31°.

It's air cooled by a Noctua NH-D14, voltage regulated fan speed (because Noctua's fans that came with it when I bought it are not PWM), with the fans running ~ 500 - 525 rpm (max is 1200).  The machine is in a Cooler Master HAF X case with 4 200mm fans.

Running pi on all six cores for 30 minutes gives me a stable temperature of 50°C +/-1° at 100% core load.  I've never seen the CPU cooling fans kick up above 1000 rpm (83% of 1200 rpm).

The reason the CPU runs as cool as it does is that I'm blowing massive amounts of cool air over it.

Right now, with several things running, sensors is giving me this on the CPU:

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +22.2°C  

```

My conky shows this:

[ATTACH=CONFIG]246117[/ATTACH]

---

