---
title: "Laptop Battery life"
date: 2009-08-14
forum: The Cafe
---

### Post by Sashin on 2009-08-14
Has anyone noticed that Ubuntu's battery life is nothing compared to Vista's. I've bought a laptop, called the Acer timeline which advertises more than 8 hours of battery life, but all I can get is 3 and a half.

All of the articles I've read about extending battery life involve sacrificing something important such as usb automount, cd rom polling or enabling usb auto suspend. Does anyone know of a better way to significantly increase battery life as powertop only gives me one thing and less watts is confusing.

---

### Post by winjeel on 2009-08-14
I don't think it's that simple. If you use peripherals like a mouse, an external hard drive, wifi, and such, and also if you work continuously, and considering the monitor takes a lot of juice, then 3.5 hours sounds good to me. The other question is, how do they measure "8 hours". To me that sounds totally amazing, and unbelievable. I guess, if you turned on a computer with a brand new 6 cell battery, and left it running with the screen turned off, then it will maintain power for 8 hours, I'm sure. Oh, and one more thing matters, assuming it's not too cold, too.

---

### Post by Sashin on 2009-08-14
It was over four hours before I got wireless internet. And I use a mouse. But I'm not sure how to get it any higher.

According to reviews, claim of 8 hours is no exaggeration, I'm just hoping I can get it to at least 5+ under ubuntu but don't know how.

---

### Post by Sashin on 2009-08-14
The default battery thing says 3 hours 50 minutes, powertop gives me five hours and the gnome panel applet gives me 5 hours 3 minutes which is more accurate?

---

### Post by winjeel on 2009-08-14
My feeling is, a computer with Vista, that's been used for about one year, loaded with a lot of programs that are doing nothing, but are running anyway (eg: PhotoShop Elements, iTunes, Apple Sync, Veoh, AVG, etc) , then even with a new battery, you're not going to get the manufacturer's claim of running time. My Windows XP is extraordinarily slow now (despite defrag'ing), and the cooling fan runs overtime, whilst Ubuntu on mine runs quickly, and the fan doesn't seem to need to run constantly (I hope that isn't an indication of a problem).

Companies tend to exaggerate. Go now, and double check the connection speed of the internet you're paying for now, then check what [your real connection speed is here]("http://www.speedtest.net/"). And then repeat that test in quiet and busy periods for a few days. I bet you'll never achieve what your provider claims.

---

### Post by ddrichardson on 2009-08-14
Is frequency scaling enabled?

---

### Post by DeadSuperHero on 2009-08-14
Try installing the package "cpufrequtils", I found it definitely extended my battery life by an hour.

---

### Post by twright on 2009-08-14
Well if you want the longest possible battery life then it is well worth sacrificing stuff like automount, CD autopolling and brightness. You could also try running less whilst on battery. You could also try setting the CPU scaling to powersave whilst on battery.

There are however no miracle solutions otherwise they would have been done by default - Ubuntu's power efficiency is getting better each version and there are some useful features coming up in Karmic which should improve things.

edit: I can usual get 4-5 hours on my eeepc which also promised about 8 hours; I have never ran Windows on it so I do not know how they compare but it is usually long enough for me.

---

### Post by Sashin on 2009-08-14
I get about the claims, of "just under a meg a second". With internet, but most reviews say something like "for once acer isn't exaggerating" etc.

I've probably enabled CPU scaling, I applied some of the things from Lesswatts using a thread on the dell MPS. But it doesn't seem to have made a difference.

I think the estimate could be wrong. I read somewhere that I have to let my battery fully discharge and charge before it reads properly. The battery applet and powertop give different numbers. About 5 hours when idle but only 3 hours when running a few apps. I don't know which one of them or if any of them is accurate.

---

### Post by twright on 2009-08-14
> **Sashin said:**
> I get about the claims, of "just under a meg a second". With internet, but most reviews say something like "for once acer isn't exaggerating" etc.

I've probably enabled CPU scaling, I applied some of the things from Lesswatts using a thread on the dell MPS. But it doesn't seem to have made a difference.

I think the estimate could be wrong. I read somewhere that I have to let my battery fully discharge and charge before it reads properly. The battery applet and powertop give different numbers. About 5 hours when idle but only 3 hours when running a few apps. I don't know which one of them or if any of them is accurate.
How many watts does Powertop say your computer is using? (usually I would expect it to be the most accurate but both are based on estimation). Mine hovers at around 11-12 when on battery.

---

### Post by Sashin on 2009-08-14
nothing its 10, a few programs and full brightness its 13.

---

### Post by Sashin on 2009-08-15
at normal brightness. 11.8 watts 5.7 hours.

---

### Post by Sashin on 2009-08-15
What is cpufrequtils?

---

### Post by Warpnow on 2009-08-15
Do a command line install of ubuntu and apt-get a less resource hungry DE, in my experience there's a 25-50% difference in battery life without all the unnecessary processes running.

But in the end Linux loses to Windows in battery life every time, sorry to say.

---

### Post by Warpnow on 2009-08-15
> **winjeel said:**
> 


Companies tend to exaggerate. Go now, and double check the connection speed of the internet you're paying for now, then check what [your real connection speed is here]("http://www.speedtest.net/"). And then repeat that test in quiet and busy periods for a few days. I bet you'll never achieve what your provider claims.

Actually I get more. My last provider was almost double the advertised speed.

---

### Post by ddrichardson on 2009-08-16
The quoted life will not have been with both cores working 100%, my guess is that the scaling governer is set to performance rather than on demand.

Type:```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

If it says the file's not there then you need to load a module, otherwise let us know what it says.

---

### Post by ddrichardson on 2009-08-16
> **Warpnow said:**
> Actually I get more. My last provider was almost double the advertised speed.
If he's referring to the UK it's normally half:

[http://www.theregister.co.uk/2009/07/28/ofcom_speeds/](http://www.theregister.co.uk/2009/07/28/ofcom_speeds/)
[http://news.bbc.co.uk/1/hi/technology/8171074.stm](http://news.bbc.co.uk/1/hi/technology/8171074.stm)
[http://www.out-law.com/page-9698](http://www.out-law.com/page-9698)

---

### Post by raminaghrobis on 2009-09-04
> Do a command line install of ubuntu and apt-get a less resource hungry DE, in my experience there's a 25-50% difference in battery life without all the unnecessary processes running.

What are these unecessary processes Warpnow?

Also, I ran powertop and it suggested: "Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
This wakes the disk up less frequently for background VM activity"

What's that supposed to mean and how do I do it? (I tried sudoing echo 1500 > /proc/sys/vm/dirty_writeback_centisecs in a terminal and it said permission denied...)

---

### Post by hanzomon4 on 2009-09-04
Mine is on demand but battery life is still like an hour and 30 mins tops. In OS X it's 4

---

### Post by hessiess on 2009-09-04
Tern the screen brightness down as low as possible, this saves a lot of power.
Disable *EVERYTHING* you are not using, shut off compiz if you haven't already.
You could also try underclocking the CPU, modern CPU's are WAY more powerful than needed and just run idle 99% of the time,

---

### Post by Sashin on 2009-09-04
But compiz is cool.

---

### Post by hessiess on 2009-09-04
> **Sashin said:**
> But compiz is cool.

And it is also uses a lot of resources unesoseraly, which is not something you want tf you are trying to make your battery last longer.

---

### Post by hugmenot on 2009-09-04
A lot of misleading info in this thread. Stop recommending fiddling with the governor, people!

This is the way to optimize battery life:

using powertop
- Make sure CPU is in the lowest C-state for as much time as possible. A modern CPU when idle is in deep sleep and draw next to no power.
- Make sure you follow the recommendations of Powertop. USB power saving does not affect functionality, for example.
- Look at how many wakeups are generated in Powertop. Some apps are offenders, some are not. For example compiz on my system is not a power draw at all. It wakes up less than once per second. The longer your CPU sleeps, the better. I get upwards of 100ms idle time. When I disable stuff that is not strictly necessary, like Gnome Do and wireless, wakeups go down to below 10 per second (6.5W). When wireless is on and gimmicks are running I get 60-80 wakeups and 11W.

I also have a script to maximize power saving (btw, you cannot "sudo echo" into proc files owned by root because the redirection by > is run as your unpriviledged user):
```
#!/bin/sh
echo disabled > /proc/acpi/ibm/bluetooth
echo 5 > /sys/class/net/wlan0/device/power_level
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
for foo in /sys/class/scsi_host/host*/link_power_management_policy
  do echo min_power > $foo
done
echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
# hal-disable-polling --device /dev/cdrom  (I disabled my CD-Rom in the BIOS because I never use it)
#echo powersave > /sys/module/pcie_aspm/parameters/policy
echo 5 > /sys/module/snd_hda_intel/parameters/power_save
echo Y > /sys/module/snd_hda_intel/parameters/power_save_controller
# ethtool -s eth0 wol d   (I blacklisted my eth0 module, because I never use it)
```

Watch this talk by Matthew Garrett for introduction:
[http://www.geeksoc.org/gcds/Matthew%20Garrett,%20Power%20management.ogv](http://www.geeksoc.org/gcds/Matthew%20Garrett,%20Power%20management.ogv)

---

### Post by hugmenot on 2009-09-04
Here&#8217;s two screenshots. One with the wireless disabled by hardware kill-switch and lowered brightness and one just after boot on battery with max brightness. The difference is 3 hours vs. 6 hours.

The third image explains why Power Manager gives you a differing time remaining estimate. It profiles your battery discharge rate to be more precise. Some batteries discharge faster or slower depending on the charge level. The profiling corrects the time remaining by this non-linear discharge behaviour.

---

### Post by ddrichardson on 2009-09-04
> **hugmenot said:**
> A lot of misleading info in this thread. Stop recommending fiddling with the governor, people!

I didn't recommend "fiddling with the governer".

The file I asked him to check not being there is evidence that the required modules are not being loaded.

The rest of what you say is sound advice but it might be better if you didn't make statements such as this - regardless of whether you feel you are right. [http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct) - respectful to others.

---

### Post by hanzomon4 on 2009-09-04
*shakes head*

Anyway how do I get powertop settings to stick?

---

### Post by RabbitWho on 2009-09-04
Someone probably said this allready, but you mentioned your laptop is new, don't forget you have to leave it waste out and then fully charge it a few times before it reaches maximum capacity. 

That goes for L-ion s anyway. Different types of batteries need to be treated differently anyway.

---

### Post by raminaghrobis on 2009-09-05
Good question hanzomon4.

---

### Post by Sashin on 2009-09-05
same way you get lesswatts to stick.

---

### Post by AlexanderDGreat on 2009-09-05
I'm using cpuscaling because before in Vista, I have Balanced, Powersave, and High Performance, isn't it intuitive that I should also have this in Ubuntu?

I also found this website to power optimize your linux box:

[http://lesswatts.org/](http://lesswatts.org/)

---

### Post by raminaghrobis on 2009-09-05
Excuse my lack of expertise,but how do you get less watts to stick?

---

### Post by hugmenot on 2009-09-05
> **ddrichardson said:**
> I didn't recommend "fiddling with the governer".
Was I quoting you? Why do you jump in on this?
> **twright said:**
> You could also try setting the CPU scaling to powersave whilst on battery.
I guess I was quoting him. And there was decidedly too much talk about scaling settings in this thread as a whole. It seemed like this thread was giving misleading or diversionary advise. Watch the video.

> **ddrichardson said:**
> The rest of what you say is sound advice but it might be better if you didn't make statements such as this - regardless of whether you feel you are right. [http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct) - respectful to others.
Come on now. Surely you must be joking.

---

### Post by jrusso2 on 2009-09-05
I have a Macbook pro with OS X, Vista and Linux on it.  By far Linux has the worst battery life even with PowerTop.

Not sure why but it does.

---

### Post by ddrichardson on 2009-09-05
> **hugmenot said:**
> Come on now. Surely you must be joking.
No and you've done it again telling me to watch a video - how can you know I haven't?

---

### Post by hanzomon4 on 2009-09-05
> **hugmenot said:**
> Was I quoting you? Why do you jump in on this?

I guess I was quoting him. And there was decidedly too much talk about scaling settings in this thread as a whole. It seemed like this thread was giving misleading or diversionary advise. Watch the video.


Come on now. Surely you must be joking.

Trust me.... he isn't

---

### Post by hanzomon4 on 2009-09-05
> **Sashin said:**
> same way you get lesswatts to stick.

Which is...

> **AlexanderDGreat said:**
> I'm using cpuscaling because before in Vista, I have Balanced, Powersave, and High Performance, isn't it intuitive that I should also have this in Ubuntu?

I also found this website to power optimize your linux box:

[http://lesswatts.org/](http://lesswatts.org/)

I'm not jumping through all those hoops especially If I have to lose functionality.. NO WAY!

---

### Post by twright on 2009-09-06
> **hugmenot said:**
> 
I guess I was quoting him. And there was decidedly too much talk about scaling settings in this thread as a whole. It seemed like this thread was giving misleading or diversionary advise. Watch the video.

Switching to powersave mode can save power - I know there are better ways but it can help. You should also see a moderate boost when karmic is released. Another way to cut off another 10% is using the lpia kernel.

---

### Post by msrinath80 on 2010-08-24
To hugmenot: Dude, what font is that on those screenshots. Awesome!! Do tell us...

---

