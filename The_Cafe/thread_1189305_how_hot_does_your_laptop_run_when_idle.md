---
title: "how hot does your laptop run when idle?"
date: 2009-06-16
forum: The Cafe
---

### Post by earthpigg on 2009-06-16
im curious where my laptop sits on this scale.

when your computer is idle (turned on, but not really doing anything), how warm does it run?

if you don't have it already, lm-sensors is the package in the repos that can tell you:

```
sensors-detect
```

to configure

```
sensors
```

to detect


if you have multiple OSs on your laptop, please share that too.

feel free to include how old your laptop is, how often you open it up and clean its innards, etc.

mine:
```

acpitz-virtual-0
Adapter: Virtual device
temp1:      +144.0°C  (crit = +100.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +100.0°C, crit = +100.0°C)  

```

---

### Post by aysiu on 2009-06-16
It feels *really* hot to me, but when I checked, it's only 51°C ```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +51.0°C  (crit = +93.0°C) 
```

---

### Post by HappinessNow on 2009-06-16
my laptop never gets hot, but I did have the fan replaced under warranty recently.

Sometimes, as in my case the laptop heat is caused by a fan not working to it's full ability, it just gets gunked up and it happens.

---

### Post by Onyros on 2009-06-16
@ aysiu: That's showing the CPU's temperature, normally the HDD is the hottest component of a laptop other than a dedicated graphics chip.

An easier way to get a temperature reading is to good 'ol cat it:

e.g., cat /proc/acpi/thermal_zone/THRM/temperature

(Some laptops may have different thermal zones assigned for monitoring, other than the CPU)

Mine hovers around 50º C, too.

---

### Post by aysiu on 2009-06-16
> **Onyros said:**
> 
An easier way to get a temperature reading is to good 'ol cat it:

e.g., cat /proc/acpi/thermal_zone/THRM/temperature This is the output I get from that (although my Mini has been sleeping for a while, so it's had some time to cool down): ```
cat /proc/acpi/thermal_zone/THRM/temperature
temperature:             39 C
``````
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +42.0°C  (crit = +93.0°C)  
```

---

### Post by alket on 2009-06-16
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +99.0°C)                  
temp2:       +59.0°C  (crit = +110.0°C)    
```

So, which is the way to prevent heating ?

---

### Post by earthpigg on 2009-06-16
> **babaroga said:**
> 
So, which is the way to prevent heating ?

1 - take the laptop apart and spray it with an air duster thingie to remove dust that slows the fan down and holds heat in.
2 - keep it on a solid flat surface to ensure the fans on the bottom can circulate air. blankets = fail. i have also found that putting beer bottle caps (or something similar) under all 4 corners lets it breathe a bit better and cool down.

---

### Post by HappinessNow on 2009-06-17
> **earthpigg said:**
> 1 - take the laptop apart and spray it with an air duster thingie to remove dust that slows the fan down and holds heat in.
2 - keep it on a solid flat surface to ensure the fans on the bottom can circulate air. blankets = fail. i have also found that putting beer bottle caps (or something similar) under all 4 corners lets it breathe a bit better and cool down.

+1 x 2

One of these are helpful also:

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=117927&d=1245215720[/IMG]
[/CENTER]

---

### Post by Wra!th on 2009-06-17
Like this for the first 1-2 hours, then it ups to atleast 65 for the day. Laptop is kind of old though...some replacing of stuff may be in order (not doing that since I'll get a new one soon).
```

&#9484;&#9472;[ wraith ][ ~ ]
&#9492;&#9472;&#9596; cat /proc/acpi/thermal_zone/THRM/temperature 
temperature:             59 C
&#9484;&#9472;[ wraith ][ ~ ]
&#9492;&#9472;&#9596;
```

---

### Post by jelle_ on 2009-06-17
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +41.0°C  (crit = +105.0°C)                  
temp2:       +41.0°C  (crit = +105.0°C)  


my screen gets hot when using maximum brightness, but remains cool whit lower brightness.

---

### Post by jespdj on 2009-06-17
How hot? What measurement do you want to look at: CPU, GPU, harddisk, something else?

I have temperature sensor icons added to my GNOME bar at the top of my desktop. Right now the temperatures are:

GPU: 58 C - CPU: 43 C - Harddisk: 41 C

How hot is normal, and what is too hot, highly depends on your hardware. Some CPUs and GPUs get hotter than others, and some can tolerate higher temperatures than others.

For my specs, see my signature. (I'm talking about my XPS M1530).

---

### Post by csmith6594 on 2010-05-30
I get the following:
acpitz-virtual-0
Adapter: Virtual device
temp1:    +46.0C     (crit = +110.0 C)
MY laptop is as basic as can be, but this bastard runs hot.

---

### Post by bunburya on 2010-05-30
Mine slowly heats from 40C to 49C, at which point the fan kicks in and cools it back down to 40. It's a Lenovo N500. I used to have an Advent 9112 which AFAIK uses Toshiba parts (?), it used to heat up to the high 50s, low 60s with the fan running near constantly, and if the fan was off for more than a few minutes it would often shut down due to overheating. Then the fan went and you got temperatures in the high 70s after a few minutes of use, obviously had to get rid of it then.

---

### Post by YuiDaoren on 2010-05-30
> **HappinessNow said:**
> +1 x 2

One of these are helpful also:

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=117927&d=1245215720[/IMG]
[/CENTER]

Kinky. What is it?

---

### Post by Random_Dude on 2010-05-30
52 C

It's usually at this temperature. Is it too high?

Cheers :cool:

---

### Post by Rodney9 on 2010-05-30
Toshiba Satellite L500 -
$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +34.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +36.0°C  (high = +105.0°C, crit = +105.0°C)

---

### Post by The Real Dave on 2010-05-30
My sister's laptop (Toshiba A200) used run in the 70's until I opened it and cleaned it. The dust that came out was incredible. 

There was an almost solid chunk of dust (50x10mm) in the heatsink, which the blower was attempting to force air through. In fairness to it, it never thermally shut down, though it did blue screen a couple times when it got seriously hot. 

There's a reason why I clean all my computers once a month (my main desktop twice, it shifts a lot of air :P)

---

### Post by undecim on 2010-05-30
Hot enough for the BIOS to power the computer off...

Unfortunately, I can't get a temperature reading no matter what I do, and I cant find that threshold value in the manual or the BIOS.

---

### Post by MadCookie on 2010-05-30
My fan goes crazy and generates a lot of heat: 80-89 C, when idle after a while.

---

### Post by ve4cib on 2010-05-30
My CPU is typically around the 45-55 mark (I voted for 50-59, but sometimes its lower).  It used to be cooler; I think I need to open it up and clean out the fan.

My GPU is another matter.  I'm using a relatively old Nvidia driver (180.44) under 9.04, with Compiz enabled.  The GPU is typically somewhere around the 70C mark, which seems rather hot to me.  But dirty fans + old (possibly buggy) driver + older distro generally means not so good performance.  I'm planning on reformatting and installing 10.04 sometime in June, so we'll see if that will improve the Nvidia temperature at all.

---

### Post by Wee_Guy on 2010-05-30
Laptops with CPUs in the 40s?!?!?!?!?!

My desktop runs at around 50 something degrees, currently its at 57°. (my fault though, I set the fan to the lowest speed to make it quietish)

This isn't a laptop CPU though, and according to AMD it will break if it gets over 70° (but they lie! I got it to 74° once and there wasn't even smoke!) so to prevent the CPU from exploding, the minuscule fan will nearly explode whenever I let things get toasty.
This minuscule and very very noisy fan will be replaced as soon as I can get a massive fan mounted on the heatsink, unless I give in and take a hammer to it first.

---

### Post by sgosnell on 2010-05-30
Toshiba Satellite

Adapter: Virtual device
temp1:        +0.0°C  (crit = +106.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +40.0°C  (high = +100.0°C, crit = +100.0°C)

That's not really idle.  I've been transferring >2.5GB of files, and surfing, for a good while.

---

### Post by NightwishFan on 2010-05-30
Model: ASUS K50ij Laptop
OS: Debian Testing (Gnome)
CPU: Intel T4400 @ 2.20ghz
RAM: 310/2988

Tasks Running: I am browsing the web, and installing some packages, currently on battery.

Temp: 41 C

---

### Post by Vostrocity on 2010-05-30
In the winter my laptop usually idles at 120F, which is about 50C. In the summer, and with a Flash applet open which maxes one of my cores, it easily goes over 200F or 90C. It was a bit scary at first, but it goes over 200F almost everyday (for a couple minutes at a time) thanks to YouTube so I'm used to it. My laptop's metal, you can't even touch it or it would burn you. But surprisingly no component has ever failed and the laptop has never overheated. It's a Dell, I love Dells. :P

I have this awesome temperature applet right next to my system info and it's interesting to see the temperature rise as soon as the CPU spikes up.
[IMG]http://imgur.com/cWHLn.png[/IMG]

Edit: I suppose one of the reasons my laptop gets so hot is because it has a dedicated graphics card (see sig).

---

### Post by stmiller on 2010-05-30
Asus 1000H netbook Atom 1.6Ghz / SSD hard drive

Fanless. :)
 
```
stmiller@mahler:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +48.0°C  (crit = +85.0°C)  
```

---

### Post by ceelo on 2010-05-30
Usually settles somewhere in the mid 50s to low 60s.

---

### Post by libssd on 2010-05-30
> **babaroga said:**
> ```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +60.0°C  (crit = +99.0°C)                  
temp2:       +59.0°C  (crit = +110.0°C)    
```

So, which is the way to prevent heating ?

If I'm going to be running my netbook for a long time, I use a little folding double fan cooling support. The Gnome sensors applet is currently showing 27 degrees, but the bottom of the case feels warmer than that. The biggest improvement I have seen in operating temperature was after a switch from HDD to SSD.

---

