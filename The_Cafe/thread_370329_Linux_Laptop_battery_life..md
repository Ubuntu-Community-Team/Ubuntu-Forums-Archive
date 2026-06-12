---
title: "Linux Laptop battery life."
date: 2007-02-25
forum: The Cafe
---

### Post by muguwmp67 on 2007-02-25
I haven't done any benchmarking, but it seems to me that installing linux on my 2 older laptops has improved their battery life.  I get about 3-4 hours on a charge now, whereas in windows these barely lasted 2.

Am I just imagining things?  Does this have something to do with swap files and hard drive usage?  What are your experiences?

---

### Post by Skia_42 on 2007-02-25
I get around an hour more of battery life in Ubuntu then Windows Xp.

---

### Post by The Noble on 2007-02-25
Its sketchy at best. Some people have better life, while some have worse. My battery should last over and hour, but it barely stretches 15 minutes.

---

### Post by TheWizzard on 2007-02-25
i'm dual booting on my laptop. ubuntu has muck longer battery life compared to w2k.

---

### Post by prizrak on 2007-02-25
It depends on hardware in my experience laptops with Intel graphics and chips last longer on Ubuntu then on Windows. The benchmarking I have done on my tablet with a GeForce gives me 10 minutes more in Windows than in Ubuntu. That was with Beryl on though not sure if it would be different without Beryl. 

The biggest reason for Ubuntu battery life is it's dynamic CPU usage. While on Windows you normally get to choose a speed level of the CPU and it will stick to it no matter what, on Ubuntu the CPU will run at the lowest possible speed and will step up as needed. On my system for instance unless there is something going on the CPU will run at 50% of the speed it's capable of and will go in increments all the way to a 100%. 

Video cards make a difference because the nVidia driver for Windows includes a GPU throttling feature for battery operation, it does not have it on Ubuntu so your battery life is worse. 

There are a few other factors, some ACPI implementations require special proprietary drivers so Ubuntu/Linux won't get as much use out of it as Windows will.

---

### Post by Onyros on 2007-02-25
I get worse battery life in Ubuntu, in general, especially due to my laptop's graphics card (ATi X700), even though I always throttle the GPU manually, when on battery power, with the command

```
aticonfig --set-powerstate= (1 for low voltage + lowest speed, 2 for low voltage + higher speed, 3 for default)
```

People with ATi graphics cards (and fglrx) can check their GPU's powerstates with

```
aticonfig --list-powerstates
```

On my Thinkpad T23 I got 2h30 with Ubuntu, whereas I had max 1h50, 2h with XP, so it depends on the hardware, basically :)

---

### Post by Mateo on 2007-02-25
battery technology sucks.

Why is it that things that used to be a problem in technology are no longer a very big deal (like hard drive storage capacities) but battery life is still always a problem on every device.

---

### Post by prizrak on 2007-02-25
> **Mateo said:**
> battery technology sucks.

Why is it that things that used to be a problem in technology are no longer a very big deal (like hard drive storage capacities) but battery life is still always a problem on every device.

Because things have different capacity for improvement. Li-Ion batteries are very new and not well developed yet. There are many new experimental things going on with them. Battery life-to-weight/size ratio has improved immensely. 3 hours is normal for just about any modern laptop where is about 5 years ago 2-2.5 hours was the average and getting more required bigger batteries. There are some developments as far as battery life span that I have read about. Like current batteries will last for about a year or so they had some that would charge in minutes and be able to handle 3 times to charge/recharge cycles. There are also some very creative ways of decreasing power consumption. 

Things are improving, some faster than others some slower but don't be too upset it's going on. Li-Ion batteries are among the most complex components of any modern electronics so it's tough and expensive to make new technology widespread.

---

### Post by Mateo on 2007-02-25
So... battery life has improved by 1/2-1 hour in 5 years?  By contrast, how much has processor speed improved by?  How much has hard drive capacity improved by?  I think 5 years ago my hard drive was maybe 16gb, now it's 250gb and that's a 2 year old computer!  My next will be 400-500gb for sure.

It always feels like technology is slowed by battery capacity.  I'm sick of having to worry about battery life all the time.

---

### Post by Anthem on 2007-02-25
My battery life is MUCH worse in Ubuntu than in Windows.  I have no idea why.

I'll glad to accept advice, but it's a mystery to me.

---

### Post by reacocard on 2007-02-25
Mine's about the same regardless of OS: 7 hours. :p

---

### Post by sparX CG on 2007-02-25
2 hours in Ubuntu, 3 in Windows.  Don't know why.

---

### Post by honns on 2007-03-08
My t23 lasts for 4.5 hours at the end of a charge, which drops to 3.5 quickly.  This is way better than the 2ish hours I got with windows 2000.  I noticed something, my battery (which is only a year old) is at a 51% capacity.  I'd like to refrain from buying a new one, so does anyone know of a way to increase the capacity?

---

### Post by om3ganet on 2007-03-09
My laptop (an [HP zv5213AP]("https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionZV5213AP")) used to be very, VERY bad for battery life in Ubuntu 6.06 (15 minutes maybe?), but for some reason now that I have 6.10 installed, it can last up to two hours (when idling), but it still wont work on suspend :(

The laptop doesn't have any power scaling abilities, although now with 6.10, the fan isn't on continuously, that's a major improvement.

---

### Post by reacocard on 2007-03-11
> **om3ganet said:**
> My laptop (an [HP zv5213AP]("https://wiki.ubuntu.com/LaptopTestingTeam/HPPavilionZV5213AP")) used to be very, VERY bad for battery life in Ubuntu 6.06 (15 minutes maybe?), but for some reason now that I have 6.10 installed, it can last up to two hours (when idling), but it still wont work on suspend :(

The laptop doesn't have any power scaling abilities, although now with 6.10, the fan isn't on continuously, that's a major improvement.

idk about suspend, but you may be able to get hibernation working with suspend2: [http://ubuntuforums.org/showthread.php?t=284994](http://ubuntuforums.org/showthread.php?t=284994)
I have an HP dv4000, suspend has never worked well for me either, but suspend2 works beautifully.

---

### Post by hannaman on 2007-03-14
I am getting a strange problem on my laptop.
When I try to start my laptop on battery it tells me that my battery is at about 98% full and will shutdown in 2 minutes.  It then shuts down.  I get more than 2 1/2 hours from the battery when I just unplug the AC adapter with the laptop booted up.  Does anyone have any ideas?

Thanks

---

### Post by ShadowVlican on 2007-03-14
i get worse battery life in ubuntu than winxp tablet edition

my guess is because i can't (or don't know how) manage the speed settings in ubuntu where as in winxp toshiba has a speed management program that sets CPU speed, fan cooling, hard drive shutdown, etc.....

---

### Post by reacocard on 2007-03-14
> **ShadowVlican said:**
> i get worse battery life in ubuntu than winxp tablet edition

my guess is because i can't (or don't know how) manage the speed settings in ubuntu where as in winxp toshiba has a speed management program that sets CPU speed, fan cooling, hard drive shutdown, etc.....

There are ways, assuming your hardware is supported. cpufreq-set, lm-sensors/fancontrol, laptop-mode, etc. It's just a matter of digging deep enough.

---

