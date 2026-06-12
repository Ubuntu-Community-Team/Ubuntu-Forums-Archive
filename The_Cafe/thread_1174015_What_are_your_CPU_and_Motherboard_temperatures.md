---
title: "What are your CPU and Motherboard temperatures?"
date: 2009-05-30
forum: The Cafe
---

### Post by Gucko on 2009-05-30
[CENTER][COLOR=Red]What are your CPU and Motherboard temperatures?[/COLOR]

[LEFT]I have an Intel Core 2 Duo 2.4GHz processor and its temperature is 45 C.
My MOBO is ASUS P5P SE and its temperature is also between 40-50C!

I feel that I have a problem or something. What about yours? 
[/LEFT]
[/CENTER]

---

### Post by Icehuck on 2009-05-30
> **Gucko said:**
> [CENTER][COLOR=Red]What are your CPU and Motherboard temperatures?[/COLOR]

[LEFT]I have an Intel Core 2 Duo 2.4GHz processor and its temperature is 45 C.
My MOBO is ASUS P5P SE and its temperature is also between 40-50C!

I feel that I have a problem or something. What about yours? 
[/LEFT]
[/CENTER]

Off the top of my head I believe that 45C is ok for the processor. Is that at idle or at full load? I have an old P4 that idles at about 37C and at load gets up to about 60C. It's motherboard doesn't have a sensor for heat so I have no idea what it's at.

---

### Post by Paqman on 2009-05-30
For a laptop that temp is absolutely fine. For a desktop it's a little high, but nothing to worry about.

---

### Post by m_duck on 2009-05-30
I *think* coretemp seems to overread temps for me. In Windows my e6600 usually idles at 29-30C whereas in Linux it tends to be closer to 40C. Not sure what the actual idle temp is more recently though as its constantly [folding]("http://folding.stanford.edu/") and so sits at 50-55C (throttled to 1600MHz otherwise it's hitting 70C!).

On the other hand I have a knackered celeron laptop at home which idles somewhere from high 60's to low 70's.

EDIT: I also have a big ol' Zalman copper heatsink and fan on it.

---

### Post by Paqman on 2009-05-30
> **m_duck said:**
> I *think* coretemp seems to overread temps for me. In Windows my e6600 usually idles at 29-30C whereas in Linux it tends to be closer to 40C.

I'd be inclined to trust the Linux one more. Windows is pretty flaky with temp readings.

---

### Post by m_duck on 2009-05-30
> **Paqman said:**
> I'd be inclined to trust the Linux one more. Windows is pretty flaky with temp readings.
Ok, cheers thats good to know.

---

### Post by Tipped OuT on 2009-05-30
My laptop sits on an ice box (a small metal box full of ice) and with a laptop cooler, with full ventilation, for when I'm gaming on it, so my CPU doesn't over heat. But when I'm just browsing the web, I'm sure my CPU gets cold... very cold hehe.

Why so much cooling? Well when your CPU over heats, it starts slow down so it doesn't fry. Which means low FPS for me and I can't have that. The cooler the better is what i always say.

---

### Post by surfed on 2009-05-30
Intel Quad Q9550 Core 30C idle 40-45C load (not overclocked otherwise add 5 - 10 C)
System 33-39C
Asus Nvidia 9600GT Fanless GPU 40 idle 70 - 75 load
Hard Drives 31 - 36C
All this in a Antec P182 case.

---

### Post by Gucko on 2009-05-30
I got my temperatures from BIOS.

When I spend so long time (like 10 hours) on my computer (browsing, gaming, programming) and I restart my compute then I go to BIOS, I find my CPU temp is between 45-53C or something like that.

Even when I turn my computer on for the first time and go to BIOS, I find the temp between 40-50C

Is that normal? I worried cuz a computer shop told me that the normal temp should be between 10-25C

---

### Post by surfed on 2009-05-30
> I worried cuz a computer shop told me that the normal temp should be between 10-25C

Logic: how can your CPU be 10C ? Are you sitting in a Fridge? CPU will always be above ambient unless you bathe your MB in liquid nitrogen.

---

### Post by Paqman on 2009-05-30
> **Gucko said:**
> I worried cuz a computer shop told me that the normal temp should be between 10-25C

I would suggest that whoever told you that was talking out of his buttocks. Anything from 35C up about 50C is groovy. Depends on the type of machine, the chip, the cooling setup and the latitude you live at!

---

### Post by Gucko on 2009-05-30
I don't have anything fancy. Just the cooling fan & the heatsink that came with the CPU.

So that guy is completely an idiot! Actually I was really surprised when he told me that, that was a shock for me. Before having the new CPU (I had P4 3GHz with temp over 70C) that guy told me that the new Intel CPUs temperature are between 10-25C using the normal heatsink and fan that come with the CPU, so I kinda believed him cuz I thought that Intel made a new invention or something to beat AMD ;)

When he told me that, I asked myself a question: If I buy the new Intel CPU and buy a decent Asus cooler, what on earth the temperature will be? Maybe under 0..LOOL!

He did that just to let me buy the new CPU.....but actually Intel Core 2 Duo is wonderful.

---

### Post by hatten on 2009-05-30
Can i in someway see the temperature that bios reports inside linux?

---

### Post by Redache on 2009-05-30
This is something fairly subjective.

If you live somewhere warm then your CPU will run hotter by default. Normally you should expect around 30-40c idle on a Core 2 Duo and up to around 70c max under load. AMD's are a bit more flaky when it comes to temps but I wouldn't worry if it's under 70-75c as that would be the Thermal Cutoff point(When the CPU starts to throttle speed before eventually turning off due to over heating). 

Saying that a GPU can run surprisingly warm these days.I wouldn't be panicking if I saw 80-90c under load from these. Unless there's actually a problem, i.e. your Computer Slows down or it turns itself off I wouldn't worry too much about temperature. If you want to improve things then just buy some extra case fans to push more air through.

RealTemp is a good program for checking Temps as you can do a Sensor Test and Bench the temperature over a period of time.

---

### Post by Gucko on 2009-05-30
I didn't find RealTemp in the repos

---

### Post by lovinglinux on 2009-05-30
> **Icehuck said:**
> Off the top of my head I believe that 45C is ok for the processor. Is that at idle or at full load? I have an old P4 that idles at about 37C and at load gets up to about 60C. It's motherboard doesn't have a sensor for heat so I have no idea what it's at.

Same processor, same temps.

---

### Post by Warpnow on 2009-05-30
e6750, stock cooler, stock paste, idles at 30c.

---

### Post by Paqman on 2009-05-31
> **hatten said:**
> Can i in someway see the temperature that bios reports inside linux?

Install sensors-applet then run:
```

sudo sensors-detect

```

It'll give you a nice little temp monitoring applet that you can add to a panel.

---

### Post by Vostrocity on 2009-05-31
It's a cool day today so I'm running at a good 100F (38C) but on really warm days I've gotten to over 200F (93C). I don't know, it sounds a bit unrealistic. My laptop's pretty good about not overheating, never happened to me in the two years I've had it.

---

### Post by CP1256 on 2009-05-31
My desktop has a Pentium 4 and is running at 38C, but when I open the case it drops to about 30/32C. 

My server which has an Athlon XP 2000+ is running at about 50C.

The amount of heat depends on the stress of the processor and on how well your heatsink performs.

---

### Post by Lajik on 2009-05-31
i'm running at 48.5C.  When I leave my laptop on for long periods of time or i'm doing heavy processing my cooling = a big *** fan pointed at my laptop :)

---

### Post by Rackstar on 2009-05-31
Dual core: 66° and 64° 
GPU: 60°

Hmm, I think I might have a problem here. It's an Acer Aspire. Maybe there is too much dust in my laptop. Can a laptop be cleaned easely?

---

### Post by omar8 on 2009-05-31
Desktop:
CPU - AMD Phenom X3 - 22°C idle - 50°C load
Motherboard - ASUS m2n68 - 30°C idle - 40°C load
Graphics card - ATI HD4850 - 35°C idle - 50°C load
Powersupply - Corsair 450W HS - 25°C idle - 50°C load

Cooling:
Scythe Mini Ninja for CPU
Sapphire Vapor-X cooling for GPU
2 120mm case fans "pushing" air
1 80mm case fan pulling air

PSU temp is measured using temperature sensors at the exhaust fan.

Mine isn't really supposed to be cool, it is more of a silent computer, all fans are undervolted to about 7V and the CPU fan is controlled to only speed up once the CPU reaches about 40°C.
On Windows the GPU is underclocked and fanspeed reduced to 20%.

Laptop:
Well, lets just say the plastic is discolouring and is easily moulded. :)

---

### Post by MechaMechanism on 2009-05-31
3 hard drives.
/dev/sda=314 K
/dev/sdb=310 K
/dev/sdc=311 K

Nvidia 8800 GT=348 K

Motherboard=Not Supported :(

---

### Post by PurposeOfReason on 2009-05-31
Idle temps are worthless most of the time, it is load that you need to worry about. I have a core i7 920 sitting at 3.2Ghz. Idle, the cores sit at ~42C but load never hits more than ~73C. My mainboard temps are a bit high though, ~53C, because the asus p6t6 SB runs hot from what I gather. You also have to factor in the ambient temp. My dorm is 26C. At home in the basement, it is 21C which makes everything much nicer.

The main point is, if it's working, you're fine.

---

### Post by iTrickU on 2009-05-31
CPU: 51°C
PWM: 54°C
Graphics Card: 65°C

My room is small enough for my computer to heat it during winter, but in summer there is direct sunlight comming into the room for most of the evening and its like a sauna in here :(

---

### Post by Skripka on 2009-05-31
> **PurposeOfReason said:**
> Idle temps are worthless most of the time, it is load that you need to worry about. I have a core i7 920 sitting at 3.2Ghz. Idle, the cores sit at ~42C but load never hits more than ~73C. My mainboard temps are a bit high though, ~53C, because the asus p6t6 SB runs hot from what I gather. You also have to factor in the ambient temp. My dorm is 26C. At home in the basement, it is 21C which makes everything much nicer.

The main point is, if it's working, you're fine.

I'd **_*strongly*_** disagree. a 130W CPU running in the 70+ on load ranges is something I would genuinely worry about.

My (current) 95W Phenom II has a critical temp of ~70C.  My prior Athlonx2 125W, had a critical temp of 64C.  With a Zalman cooler I never go north of ~45C on load, even in my 23-25C apartment.

---

### Post by Dark Aspect on 2009-05-31
Stock ~ 2.0 Ghz

Idle:
[IMG]http://img268.imageshack.us/img268/8193/stockmin.png[/IMG]
100% load:
[IMG]http://img503.imageshack.us/img503/6597/stockmax.png[/IMG]

@1.376v

Overclocked ~ 2.5 Ghz

Idle:
[IMG]http://img10.imageshack.us/img10/1421/tempejn.png[/IMG]
100% load:
[IMG]http://img521.imageshack.us/img521/4151/ocmax.png[/IMG]

@1.440v

I considered playing Nexuiz on the highest setting as being on a load, but I usually don't see these kind of temps unless I am running mprime.My CPU was above 50c but I added two fans to the front and the back of my case. I have also made a case mod on the top of my computer, that to my great surprise, actually cools very well. Possible because air rises, I can't really explain it any other way since a 120mm fan on the back og my case doesn't cool as well for some reason. My Ram is also overclocked so it could be that the fan is directly over the ram chips, keeping that heat from spreading to other hardware components.

[IMG]http://ubuntuforums.org/picture.php?albumid=904&pictureid=4082[/IMG]

How can I check hard drive temps? I have a 120mm fan directly in front of both my drives but I was curious.

---

### Post by PurposeOfReason on 2009-05-31
> **Skripka said:**
> I'd **_*strongly*_** disagree. a 130W CPU running in the 70+ on load ranges is something I would genuinely worry about.

My (current) 95W Phenom II has a critical temp of ~70C.  My prior Athlonx2 125W, had a critical temp of 64C.  With a Zalman cooler I never go north of ~45C on load, even in my 23-25C apartment.
What do you define as load then? To me, it means small packages through prime95. That is one of the few ways to reach a true 100% all cores load. Something you will never hit in real world applications (besides folding) so if you're hitting 70s in that, you're fine. I've built and OCd many computers, air and liquid cooled, the 70s are fine for a p95 load.

---

### Post by surfed on 2009-05-31
> **PurposeOfReason said:**
> What do you define as load then? To me, it means small packages through prime95. That is one of the few ways to reach a true 100% all cores load. Something you will never hit in real world applications (besides folding) so if you're hitting 70s in that, you're fine. I've built and OCd many computers, air and liquid cooled, the 70s are fine for a p95 load.

I guess this depends on ones own comfort levels. I would try to improve my temps if they ever get above 60 for the cpu.

---

### Post by Dark Aspect on 2009-05-31
> **surfed said:**
> I guess this depends on ones own comfort levels. I would try to improve my temps if they ever get above 60 for the cpu.

+1

I try to keep mine below 50c really because ambient temperatures can play a large role.

---

### Post by surfed on 2009-05-31
> **Dark Aspect said:**
> +1

I try to keep mine below 50c really because ambient temperatures can play a large roll.

Yeah, its a challenge sometimes as I am into silent (quiet) computing. All my Fans are 120mm and only one runs at 1000rpm (CPU cooler) the other 4 (two exhaust, two intake) at 550 ~ 700 rpm. My 9600GT is fanless and my CPU a 9550 Quad.

---

### Post by samjh on 2009-05-31
These temperatures obviously depend on ambient air temperature and available ventilation around the computer.
CPU (Intel Core 2 Duo E8500) right now: 47C at near-idle load.  This is autumn weather with ambient air temperature of around 25C and good ventilation.

Motherboard is usually around 50C to 55C.  This temperatures doesn't change much, even between seasons.

My NVidia card (GeForce 9800GT with cooling fan) usually rates around 45C when idling, and 65C in summer with heavy processing load.

---

### Post by t0p on 2009-05-31
```
t0p@machine:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +55.0°C  (crit = +90.0°C)                  

eeepc-virtual-0
Adapter: Virtual device
fan1:        920 RPM

```

---

### Post by Greenwidth on 2009-06-01
This should keep things a bit cooler:
[http://www.youtube.com/watch?v=PtufuXLvOok&eurl=http%3A%2F%2Fwww.pugetsystems.com%2Fsubmerged.php&feature=player_embedded](http://www.youtube.com/watch?v=PtufuXLvOok&eurl=http%3A%2F%2Fwww.pugetsystems.com%2Fsubmerged.php&feature=player_embedded)

---

### Post by Dark Aspect on 2009-06-01
> **Greenwidth said:**
> This should keep things a bit cooler:
[http://www.youtube.com/watch?v=PtufuXLvOok&eurl=http%3A%2F%2Fwww.pugetsystems.com%2Fsubmerged.php&feature=player_embedded](http://www.youtube.com/watch?v=PtufuXLvOok&eurl=http%3A%2F%2Fwww.pugetsystems.com%2Fsubmerged.php&feature=player_embedded)

I want one...

I would think that would destroy the fans and the hard drive though, I suppose the computer is booting from a flash drive.

---

### Post by ohbuntu on 2009-06-01
Desktop PC:
Core i7 920 @ 3.8Ghz being cooled by a Noctua UH12P HSF: 43C at near idle. Mobo is a couple of degrees lower than that.
Backup PC:
Athlon XP 2400+ @ 2.2Ghz with a CoolerMaster HSF: 44C at idle. Mobo is at 40-41C.

The Athlon is over 2 generations old, yet runs a degree hotter at idle.

---

### Post by PmDematagoda on 2009-06-01
Intel Core T2050 at about 55C idle, when a kernel is being compiled using both processors at the maximum, the temperature is at about 82C(If I remember properly). I also have an Intel P4 Prescott at 3.2 Ghz, it runs idle at about 60C and when under heavy load goes to around 80C, it's a great singer with 2 fans on the chassis and one processor fan, and is a great big gas guzzler too. ;)

---

### Post by VyacheslavS on 2009-12-23
> **Gucko said:**
> [CENTER][COLOR=Red]What are your CPU and Motherboard temperatures?[/COLOR]
[LEFT]I have an Intel Core 2 Duo 2.4GHz processor and its temperature is 45 C.
My MOBO is ASUS P5P SE and its temperature is also between 40-50C!
I feel that I have a problem or something. What about yours? 
[/LEFT]
[/CENTER]

I did so:
download and install the new libs from Debian
[http://packages.debian.org/sid/lm-sensors](http://packages.debian.org/sid/lm-sensors) (lm-sensors 1:3.1.1-4)
[http://packages.debian.org/sid/libsensors4](http://packages.debian.org/sid/libsensors4) (libsensors4 1:3.1.1-4)

Now everything is OK!
All temperature and voltage, I see. Speed of the fans also displayed.

---

### Post by Exodist on 2009-12-23
AMD64 x2 (6000+), 125w version, Dual core 3Ghz
CPU is idle at 25Celcius. 

ATI RadeonHD 4850, PCI-16x
Video is at 46Celcius.

---

### Post by tad1073 on 2009-12-24
```
thomas@thomthom:~/Desktop$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +20.0°C  (crit = +60.0°C)                  

thomas@thomthom:~/Desktop$ cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | uniq
Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz

```

---

### Post by PurposeOfReason on 2009-12-24
> **tad1073 said:**
> ```
thomas@thomthom:~/Desktop$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +20.0°C  (crit = +60.0°C)                  

thomas@thomthom:~/Desktop$ cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | uniq
Intel(R) Core(TM)2 Quad CPU    Q6700  @ 2.66GHz

```
May I ask what cooling that has?

EDIT - If it's the one in your sig, your temps are way off. No way that is sitting at 20C unless you're living in a sub zero place.

---

### Post by slumbergod on 2009-12-24
Since upgrading to Karmic, my laptop fan is a mess. I use an Acer laptop with a dual core intel chip and it is never less than 65 degrees. In fact, watching certain HD mkv files or encoding to ogg is enough to overheat the system and cause it to shutdown.

This is the wonderful world of Karmic.

---

### Post by fatcrab on 2009-12-24
P4 3.2HT--41C to 59C
7300gt--48C to 60C

E8400--40C to 51C
9800gt--51C to 70C

---

### Post by cariboo on 2009-12-24
AMD Athlon(tm) II X2 240 Processor
MSI K9N6PGM2-V motherboard

Currently sitting at 34°C for cpu and 29°C for motherboard. This is using the OEM cooler that hasn't been cleaned for a couple of weeks.

---

### Post by tad1073 on 2009-12-24
> **PurposeOfReason said:**
> May I ask what cooling that has?

EDIT - If it's the one in your sig, your temps are way off. No way that is sitting at 20C unless you're living in a sub zero place.

I have the side panel off and the just the cpu fan that came with it.

---

### Post by PurposeOfReason on 2009-12-24
> **tad1073 said:**
> I have the side panel off and the just the cpu fan that came with it.
Yeah, no way it's at 20C then. Might want to look into calibrating your sensors.

---

### Post by Exodist on 2009-12-24
> **PurposeOfReason said:**
> May I ask what cooling that has?

EDIT - If it's the one in your sig, your temps are way off. No way that is sitting at 20C unless you're living in a sub zero place.
Mine is sitting at 25C with air cooling. :confused:

---

### Post by PurposeOfReason on 2009-12-24
> **Exodist said:**
> Mine is sitting at 25C with air cooling. :confused:
You do realize that 20C is 68F and that would mean his room would have to be less than that? At least lower than ~58F which I highly doubt for that processor. I know less about yours, but 25C still seems off though much more plausible. Even more, he is using the intel stock HS which is pure crud.

---

### Post by djurny on 2009-12-24
gigabyte ga-e7aum-ds2h
Intel(R) Core(TM)2 Quad CPU Q8200 @ 2.33GHz stepping 07

temp1:       +29.0°C # cpu casing/system
temp2:       +27.0°C # cpu casing/system
Core 0:      +58.0°C
Core 1:      +51.0°C
Core 2:      +54.0°C
Core 3:      +47.0°C
display '0' at '40' degrees
display '1' at '39' degrees
sda: 24 C

--

intel atom 330

Chipset Temp: +28.0°C
System Temp:  +34.0°C
CPU Temp:     +49.0°C
sda: sleeping/standby
sdb: sleeping/standby
sdc: 23 C
sdd: 18 C
sde: unknown
sdf: 22 C
sdg: sleeping/standby

hope that helps :)

---

### Post by Exodist on 2009-12-24
> **PurposeOfReason said:**
> You do realize that 20C is 68F and that would mean his room would have to be less than that? At least lower than ~58F which I highly doubt for that processor. I know less about yours, but 25C still seems off though much more plausible. Even more, he is using the intel stock HS which is pure crud.
Room temp would really help pay a big role player, but if that pic of his PC is the one that has the snorkle to get outside case air, then idle its possible. Mind you it wouldnt be in my house. I would freeze. My uncle keeps his house like 52F during the summer, a nuclear reactor wouldnt over heat in his house. I prefer to stay outside. :-)

Room temp at my house it set to 68F. With the case and cooling fans I have. 25C idle is normal. But can go higher to like 35C under load (hour of world of warcraft).

PC Pics = [http://picasaweb.google.com/exodist2009/MyPCNov2009#](http://picasaweb.google.com/exodist2009/MyPCNov2009#)

Centurion5 ATX mid tower case.

---

### Post by Dropbear on 2009-12-24
My processor temp is usually around 45C at idle. The onboard nvidia graphics chip has been up to 112C while gaming.

---

### Post by MooPi on 2009-12-24
CPU=42, System=27  I've got my processor oc'd slightly from 2.7 GHz to 3.0 GHz or otherwise system would run cooler.

---

### Post by tom66 on 2009-12-24
Core 2 Duo Mobile 2.0GHz: 37/38 C idle on each core. Can hit 71 on a single core when I run an intensive program, but that is rare. GPU always runs hot, about 56 C.

---

### Post by The Real Dave on 2009-12-24
I've worked hard to get a cool system, it used be filled with dust, and the CPU would sit at 50C idle, and rocket to 66C the moment you put load on it. 

A good cleaning, and an additional 120mm fan pushing air down on top of it brought down the heat immensely. I changed some PWM configs to make the CPU fan run faster too.

Its a 2993Mhz P IV 
Idle - ~25C @ 2000Rpm
Load - ~35C (never above 37C) @ ~3000Rpm

Its constantly underload with Folding@Home :)

Motherboard is at 30C under load, can't remember what it is without load :)

I've a 1Ghz Pentium III that will sit happily maxed out at 100C with no cooling :) It doesn't bother it :)

---

### Post by Psumi on 2009-12-24
```
it8718-isa-0290
Adapter: ISA adapter
in0:         +1.06 V  (min =  +0.00 V, max =  +4.08 V)   
in1:         +1.92 V  (min =  +0.00 V, max =  +4.08 V)   
in2:         +3.36 V  (min =  +0.00 V, max =  +4.08 V)   
in3:         +3.01 V  (min =  +0.00 V, max =  +4.08 V)   
in4:         +0.18 V  (min =  +0.00 V, max =  +4.08 V)   
in5:         +0.03 V  (min =  +0.00 V, max =  +4.08 V)   
in6:         +0.10 V  (min =  +0.00 V, max =  +4.08 V)   
in7:         +3.04 V  (min =  +0.00 V, max =  +4.08 V)   
in8:         +3.22 V
fan1:        842 RPM  (min =    0 RPM)
fan2:        741 RPM  (min =    0 RPM)
fan3:          0 RPM  (min =    0 RPM)
fan4:       1184 RPM  (min =    0 RPM)
temp1:       +36.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
temp2:       +28.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        -2.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
cpu0_vid:   +2.050 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +40.0°C  (high = +78.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +33.0°C  (high = +78.0°C, crit = +100.0°C)
```

---

### Post by markp1989 on 2009-12-24
My e8400 @ 4ghz idles at 25C and load is 45-50C water cooled (for noise  reasons)


@ The Real Dave : 35C under load seems low for a P4 them things were known or running toasty, you must have good air flow, and a low house temp  :)

---

### Post by The Real Dave on 2009-12-24
> **markp1989 said:**
> My e8400 @ 4ghz idles at 25C and load is 45-50C water cooled (for noise  reasons)


@ The Real Dave : 35C under load seems low for a P4 them things were known or running toasty, you must have good air flow, and a low house temp  :)

I've worked hard to keep it cold, P IVs are damn hot chips :) I've got quite good airflow, its a very small case, but with 3 80mm and 1 120mm fan shifting alot of air :) Cable management helps too :) That and the huge stock cooler this came with, an 80mm fan with about a million fins :) Ill put up some pics later

---

### Post by cariboo on 2009-12-24
Ambient temperatures have a lot to do with cpu/motherboard temps. This is in my shop, The heat was turned off all night, and the temp reached -22°C currently it is -14° outside and +12°C inside. See the screenshot.

CPU is an AMD X@ 3400+ with stock cooler, and no sides on the case.

---

### Post by LowSky on 2009-12-24
Im at or bit under 30°C at idle
I get up around 45°C at full load

3 140mm case fans, 1 120 rear case fan, and stock cooler.
Its super quiet, except for one of the 140mm fans that I think has a bad bearing. $15 should replace it just fine

---

### Post by SuperSonic4 on 2009-12-24
```
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +78.0°C, crit = +100.0°C)
Core 1:      +31.0°C  (high = +78.0°C, crit = +100.0°C)

/dev/sda: SAMSUNG HD501LJ: 32°C
/dev/sdb: SAMSUNG HD502IJ: 27°C
/dev/sdc: SAMSUNG HD154UI: 26°C

```

sdb is my OS drive, sda my media drive

This is on minimal load and the CPU scaled down to 1.9GHz (via cpufrequtils)

---

### Post by Zoot7 on 2009-12-24
As I type right now all 4 cores of my CPU are at 35C, and my northbridge is at 45C.
That's with a Phenom II X4 955 and a 790FX chipset.

---

### Post by Skripka on 2009-12-24
> **Zoot7 said:**
> As I type right now all 4 cores of my CPU are at 35C, and my northbridge is at 45C.
That's with a Phenom II X4 955 and a 790FX chipset.

Are you posting these temps from Windows?  The Sensors kernel module doesn't have drivers yet to read AMD K10 series CPU/chipset temp data yet. :confused:

---

### Post by Zoot7 on 2009-12-24
> **Skripka said:**
> Are you posting these temps from Windows?  The Sensors kernel module doesn't have drivers yet to read AMD K10 series CPU/chipset temp data yet. :confused:
Yeah from Windows 7 using the AMD Overdrive utilty. I've never got the temperature sensors to work in either Ubuntu, Fedora or openSUSE. There is a driver in the wild someplace that does work apparently, but I've yet to try it.

---

### Post by Skripka on 2009-12-24
> **Zoot7 said:**
> Yeah from Windows 7 using the AMD Overdrive utilty. I've never got the temperature sensors to work in either Ubuntu, Fedora or openSUSE. There is a driver in the wild someplace that does work apparently, but I've yet to try it.

Yea, I've compiled it and have loaded it...it isn't in a state yet where it is worth the trouble.  It only returns 2 temp values, and no fan speeds, and no voltages.

[http://aur.archlinux.org/packages.php?ID=28734](http://aur.archlinux.org/packages.php?ID=28734)

With my Zalman cooler under Win7 and my 720 turned into a quadcore,  my box idles at ~30C with northbridge around 31C (in a 22C room).

---

### Post by Zoot7 on 2009-12-24
> **Skripka said:**
> Yea, I've compiled it and have loaded it...it isn't in a state yet where it is worth the trouble.  It only returns 2 temp values, and no fan speeds, and no voltages.

[http://aur.archlinux.org/packages.php?ID=28734](http://aur.archlinux.org/packages.php?ID=28734)

With my Zalman cooler under Win7 and my 720 turned into a quadcore,  my box idles at ~30C with northbridge around 31C (in a 22C room).
That's the one yeah.

I get about 30-35C idle and roughly 50-55C under load after a few hours of Prime95. That is with the voltage dropped back to 1.22V, stock speed (I got sick of overclocking a long time ago), and with Cool N' Quiet enabled. The default 1.35V of the black edition Phenoms is *waaay *too high, I was getting roughly 60-65C with Prime95, and AMD themselves quote the max safe temperature for 24/7 usage at 62C.

---

### Post by PurposeOfReason on 2009-12-24
Here are idle, gpu load, cpu load in that order. Ambient of 22C, fans on low speed.

---

### Post by cariboo on 2009-12-24
Apparently the the K10 sensors module in the .33 kernel release.

---

### Post by markp1989 on 2009-12-24
from my server / htpc when playing a video. 
```
mark@torrentslave:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +39.0°C  (high = +76.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (high = +76.0°C, crit = +100.0°C)  

mark@torrentslave:~$ sudo hddtemp /dev/sd[a-b]
[sudo] password for mark: 
/dev/sda: SAMSUNG HD154UI: 26°C
/dev/sdb: SAMSUNG HD154UI: 25°C
mark@torrentslave:~$ 

```

---

### Post by sandyd on 2009-12-24
CPU: 57 (idle)(x2)(x2 dual cores)
GPU: 61
Motherboard: 63
seems like theirs something wrong with one of the fanson my comp.
its not spinning up even as the temperatures are reaching 60.
now debating to myself wether to take off one of the dual cores.....

---

### Post by imjafo on 2009-12-24
After 72 hours uptime: 
CPU: core 0 31C  Core 1 31C
(Intel E6300 O.C. to 3.0GHZ)
GPU: 43C   Mobo: 22C  HDD: 26C
CPU fan @ 2812 rpm  Sys rear fan @ 2250 rpm
Ambient room temp: 21C

---

