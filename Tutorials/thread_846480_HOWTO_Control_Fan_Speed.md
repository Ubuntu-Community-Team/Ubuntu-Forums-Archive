---
title: "HOWTO Control Fan Speed"
date: 2008-07-01
forum: Tutorials
---

### Post by zgornel on 2008-07-01
This is how fan speeds should be managed using powersaved . I do not guarantee that it will work on any system, use it at your own risk. Some steps also might be superfluous.
More documetation (read it to be familiar with what will happen) before proceeding can be found here: [http://powersave.sourceforge.net/powersave/Thermal.html](http://powersave.sourceforge.net/powersave/Thermal.html) 
I will also show the readings on my system (HP 6820s, Core2 Duo T7250, 4GB Ram, ATI X1350, Kubuntu 8.04) in order to get a better idea of what you should see.
1. First of all, some check are necessary:
```
cat /proc/acpi/thermal_zone/*/trip_points

``` 
The result is some blah blah about trip points, temperatures etc. You should see something here, I still do not know if it is absolutely necessary for something to appear in order for thermal throttling to be supported on the system. My output:
```
critical (S5):           256 C
active[0]:               80 C: devices=C36B
active[1]:               72 C: devices=C36C
active[2]:               62 C: devices=C36D
active[3]:               45 C: devices=C36E
active[4]:               30 C: devices=C36F
critical (S5):           108 C
passive:                 105 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1
critical (S5):           110 C
active[0]:               105 C: devices=C372
active[1]:               70 C: devices=C370
active[2]:               60 C: devices=C371
critical (S5):           108 C
passive:                 60 C: tc1=1 tc2=2 tsp=300 devices=CPU0 CPU1
critical (S5):           110 C

```
In order to continue, you have to install **powersaved**:
```
sudo apt-get install powersaved
``` 
This might lead to the removal of **apmd** and **powernowd**, not to worry ;). Check that powersaved is in the autostart process list and **reboot**. 
2. The next step is to see which thermal device is actually active (in my case only one, the processor). To do this, do a:
```
sudo powersave -T
```
My output:
```
Thermal Device no. 0:
Temperature: 53
Critical: 108
Passive: 105
**Thermal Device no. 1:**
Temperature: 57
**State: ACTIVE**
Critical: 256
Active 0: 80
Active 1: 72
Active 2: 62
Active 3: 45
Active 4: 30
Thermal Device no. 2:
Temperature: 50
Critical: 110
Thermal Device no. 3:
Temperature: 33
Critical: 108
Passive: 60
Thermal Device no. 4:
Temperature: 50
Critical: 110
Active 0: 105
Active 1: 70
Active 2: 60

```
So, in my case **Thermal Device 1** is active. I did a double check with:
```
cat /proc/acpi/thermal_zone/TZ1/trip_points

```
Result:
```

critical (S5):           108 C
passive:                 105 C: tc1=1 tc2=2 tsp=300 devices=**CPU0 CPU1**

```
3. The final step is editing the config file with the desired trip points
```
sudo kate /etc/powersave/thermal
```
There are several modifications that have to be done:
```

#Enable thermal management
ENABLE_THERMAL_MANAGEMENT="yes"
#Use fan to cool the device
COOLING_POLICY="active"

#Temperature Trip Points
THERMAL_CRITICAL_**X**="95"
THERMAL_HOT_**X**="90"
THERMAL_PASSIVE_**X**="40"
THERMAL_ACTIVE_**X**_0="50"
THERMAL_ACTIVE_**X**_1="62"

```
The **X** stands for the ACTIVE thermal device, in my case X is **1** so a line would look like ```
THERMAL_PASSIVE_1="40"
```. The numbers are the temperatures. Basically, it means that starting from 40C the fans will start to spin, increasing speed when each trip point is reached. 
I still do not know how how reliable the reported trip points (fan speeds) are. What I did was to take the results from the thermal device **0**: 
```
cat /proc/acpi/thermal_zone/TZ0/trip_points

```
which are:
```

critical (S5):           256 C
active[0]:               80 C: devices=C36B
active[1]:               72 C: devices=C36C
active[2]:               62 C: devices=C36D
active[3]:               45 C: devices=C36E
active[4]:               30 C: devices=C36F

```
and made the assumption that the active device  has also 5 trip points (TZ0 is the thermal zone for Core0 and TZ1 is the thermal zone for Core1). What is confusing is that powersave -T reports Thermal Device 1 with the powr trip points of thermal zone 0, I suppose the system is not yet fully supported. Everyone is free to decide how many trip points to choose.
4. Last but not least, reboot.
You can test if it is working by monitoring temperatures while running glxgears or something like that.
Hope this helps.

**UPDATE**: Changed thermal variables to correct ones

---

### Post by ahmedh on 2008-07-12
Nice tutorial, this is exactly what I was looking for. However, this is my output of sudo powersave -T after a reboot: 

```
Device no. 0:
Temperature: 46
Critical: 100
Passive: 96
Thermal Device no. 1:
Temperature: 51
Critical: 127

```

It says neither of my thermal devices are active, so I don't know what to do about editing etc/powersave. Also, the outputs of ```
cat /proc/acpi/thermal_zone/TZ1/trip_points

``` and ```
cat /proc/acpi/thermal_zone/TZ0/trip_points
``` are that the respective files/directories could not be found.

I am slightly worried, because some googling showed that the operating range for my processor (Intel T8300, 2.4ghz Core 2 Duo) is between 45 to 95F, and running just Firefox I'm getting temps of between 110-120F.

I would greatly appreciate any help!

---

### Post by zgornel on 2008-07-12
What version of Ubuntu are you running ? The thing is the T8300 might just be a bit too new to work with powersave (actually the acpi version of the system). Before Hardy I had problems in 7.10 (the fans would stop but would not start). There is another ugly way of cooling your machine, by enabling the fans (still, if they are supported) manually. By the way, 120F is not at all much for a Core2 at that frequency. 120F would mean more or less 50C and that is also what I'm having on a T7250 at 2GHz (normal load).

---

### Post by ahmedh on 2008-07-12
It's 8.04, the most recent release. 

Oh okay, that's good. My fan does turn on, but it seems to always be on. I installed acpitool to monitor the fan speed, and it ranges from about 2400-2800 RPM. I haven't performed any heavy-load operations yet, so at idle with the temp that high I got a bit worried, that the fan should be spinning faster (it also doesn't help that it's nearly silent--that's why installed acpitool, to make sure that it was actually on!). So do you think I should just let it be and not worry about it?

---

### Post by zgornel on 2008-07-13
At those temperatures, there absolutely no problems. Critical values for Core2 CPUs are over 80C (at about 90C-100C the CPU shuts down). If you want to see if you have support for multiple fan speeds in ACPI try
```
ls /proc/acpi/fan
``` If more hex code like directories are present, means that each one is associated to a fan (actually not a physical fan but a fan speed) and I can help you from there. If nothing is listed, you have to rely on BIOS to regulate the fan speed.

---

### Post by ahmedh on 2008-07-13
Okay, thank you!

---

### Post by schuerstedt on 2008-07-20
Hi,


thx for your posts as I am looking forward to keep my 6820s once I manage to stop the fan from running all the time...

I did all the above steps. 

But powersave -T still shows the same entries at the beginning. powersaved is running (at least when I am starting it, it says it is already running) and the fan is running at level two even when my temp just shows 57 (and will not slow down when temp goes down - I assume it will just go down when it is below 45). 

I have exactly the same 6820s as you (2 GHz with 4Gig).

Any help appreciated. 

Marcus

---

### Post by zgornel on 2008-07-20
> **schuerstedt said:**
> Hi,


thx for your posts as I am looking forward to keep my 6820s once I manage to stop the fan from running all the time...

I did all the above steps. 

But powersave -T still shows the same entries at the beginning. powersaved is running (at least when I am starting it, it says it is already running) and the fan is running at level two even when my temp just shows 57 (and will not slow down when temp goes down - I assume it will just go down when it is below 45). 

I have exactly the same 6820s as you (2 GHz with 4Gig).

Any help appreciated. 

Marcus

Yes, the fan will go down only when the temperature will go under 45C. From my experience it is not recommended to shud down the fan completely. If you make it start at , let's say 70C, the cpu will get hot eventually and the fans will start anyway very quickly. A decent solution is to simply 'kill' the fan: stop one speed of the fan so that the fan will change speed only at the next trip point. When the temperature goes down and the fan stops (from high speed), the killed trip point is reactivated. At least that's what I observed. What I did was to create a script that (in my case) stops the third fan (third speed) which starts at 62C and starts the first one. If the cpu gets hot, The next fan starts at 72 so I'm safe anyway. I attached the script (added a .txt extension), just put it in /usr/local/bin . It 's a faster and guaranteed to work solution ( I think this model of HP is not quite supported by powersave, I even tried the last git version ... :/ )

---

### Post by aptperson on 2008-10-17
Hi,

I have tried to follow your instructions. The problem I am having is that I can't get powersave on the autostart list. I have tried to edit my /etc/rc.local file inserting powersave & but to no avail. Any Ideas?

Thanks.

---

### Post by elyobelyob on 2009-01-08
> **zgornel said:**
> What version of Ubuntu are you running ? The thing is the T8300 might just be a bit too new to work with powersave (actually the acpi version of the system). Before Hardy I had problems in 7.10 (the fans would stop but would not start). There is another ugly way of cooling your machine, by enabling the fans (still, if they are supported) manually. By the way, 120F is not at all much for a Core2 at that frequency. 120F would mean more or less 50C and that is also what I'm having on a T7250 at 2GHz (normal load).

Hi,

I've got a similar question to the above ... 

Thermal Device no. 0:
Temperature: 29
Critical: 100
Passive: 90
Active 0: 85


Processors  	2
Model 	Intel(R) Pentium(R) 4 CPU 2.80GHz @  35°C
CPU Speed 	2.81 GHz

Kernel Version  	2.6.24-22-server (SMP)
Distro Name 	 Ubuntu 8.04.1

It's an old Shuttle computer and I'd really like the fans off whenever possible and appreciate any pointers

Thanks

edit : 

Further info :

root@ubuntu:~# cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           100 C
passive:                 90 C: tc1=4 tc2=3 tsp=60 devices=CPU0
active[0]:               85 C: devices= FAN

root@ubuntu:~# ls /proc/acpi/fan
FAN

---

### Post by elyobelyob on 2009-01-08
Further info ... 

root@ubuntu:~# cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           100 C
passive:                 90 C: tc1=4 tc2=3 tsp=60 devices=CPU0
active[0]:               85 C: devices= FAN

root@ubuntu:~# ls /proc/acpi/fan
FAN

---

### Post by elyobelyob on 2009-01-08
> **elyobelyob said:**
> Hi,

I've got a similar question to the above ... 

Thermal Device no. 0:
Temperature: 29
Critical: 100
Passive: 90
Active 0: 85


Processors  	2
Model 	Intel(R) Pentium(R) 4 CPU 2.80GHz @  35°C
CPU Speed 	2.81 GHz

Kernel Version  	2.6.24-22-server (SMP)
Distro Name 	 Ubuntu 8.04.1

It's an old Shuttle computer and I'd really like the fans off whenever possible and appreciate any pointers

Thanks

Further info :

root@ubuntu:~# cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           100 C
passive:                 90 C: tc1=4 tc2=3 tsp=60 devices=CPU0
active[0]:               85 C: devices= FAN

root@ubuntu:~# ls /proc/acpi/fan
FAN

---

### Post by abdusamed on 2009-10-13
in my xubuntu 9.04 on p4 256ram [random intel video card i think]

```
cat /proc/acpi/thermal_zone/*/trip_points
``` doesn't work! plzz help

---

### Post by wally83 on 2009-10-13
> **abdusamed said:**
> in my xubuntu 9.04 on p4 256ram [random intel video card i think]

```
cat /proc/acpi/thermal_zone/*/trip_points
``` doesn't work! plzz help

* refers to some directory with variying name, so for me it's:

```
cat /proc/acpi/thermal_zone/TZ00/trip_points
```

Just run this first:

```
ls /proc/acpi/thermal_zone/
```

... to see thermal zones you have available. Then do:

```
cat /proc/acpi/thermal_zone/<thermal zone you just found>/trip_points
```

***

I'm going to make my Acer TravelMate 8371 less noisy when on AC power

---

### Post by wally83 on 2009-10-13
Didn't went that well with Acer 8371 TravelMate.

No fans available?
```

$ ls /proc/acpi/fan/
$ 

```

I have just one thermal zone:
```

$ cat /proc/acpi/thermal_zone/TZ00/trip_points 
critical (S5):           127 C

```

Temperature is always exactly 27 C. It could be hdd temperature, otherwise it doesn't make any sense. 
```

$ cat /proc/acpi/thermal_zone/TZ00/temperature 
temperature:             27 C

```

At least something I managed to set in /etc/powersave/thermal:
```

cat /proc/acpi/thermal_zone/TZ00/polling_frequency 
polling frequency:       5 seconds

```
```
THERMAL_POLLING_FREQUENCY="5"

```

And finally:
```

$ sudo powersave -T
Thermal Device no. 0:
Temperature: 27
Critical: 127

```

Maybe I have something missing somewhere. I tried to set settings like this:
```

#Temperature Trip Points
THERMAL_CRITICAL_0="95"
THERMAL_HOT_0="90"
THERMAL_PASSIVE_0="40"
THERMAL_ACTIVE_0_0="50"
THERMAL_ACTIVE_0_1="62"

```

---

### Post by abdusamed on 2009-10-13
i don;t know my directory! sorry... WHY is everything soo hard to run on ubuntu... or do something?? the only reason why i want to set my fan to the slowest speed but runnin is so that i an run it all night ... downloading stuff... i want it only to DOWNLOAD ... nothing else... but sometimes the fan becomes a hovercraft! plz 

i btw did install powersaved.. but i have NO clue what to do... any help willl be greatly appreciated,,thanks in advance ..rememeber..runnin xubuntu [pretty much the same as ubuntu]

---

### Post by TheKorn2 on 2009-11-03
> **abdusamed said:**
> i don;t know my directory! sorry...

So GO LOOK:

```

vince@Toshtop:~$ cd /proc/acpi/thermal_zone
vince@Toshtop:/proc/acpi/thermal_zone$ ls
THRM

```

So, my directory is THRM (in caps).

---

### Post by me13221 on 2009-11-04
Thanks for this post-- it looks to be just what I'm looking for-- but I tried the steps you suggested and it did not work.

I have a brand new system, running ubuntu 9.10: AMD Athlon dual core 5050e, I don't know how to tell what kind of motherboard it is but it definitely has ACPI support.

I installed powersaved (along with all the acoutrements), rebooted, edited the config files and restarted powersaved, but the fan continues to run at blazing top speed.  The CPU temperature is 40C.  The trip points I set in /etc/powersaved/thermal are:

THERMAL_HOT_0="65"
THERMAL_CRITICAL_0="70"
THERMAL_PASSIVE_0="35"
THERMAL_ACTIVE_0_0="45"
THERMAL_ACTIVE_0_1="55"

but when I cat /proc/acpi/thermal_zone/THRM/trip_points I get:

critical (S5):       60 C
active[0]:           50 C: devices= FAN

so they're not showing up at all.  And, as I mentioned, the fan is still full blast.

help?

thanks in advance

---

### Post by abdusamed on 2009-11-04
i give up.. ubuntu is just soo hard to use..they should've made it more easier to use..like simply double on a apps and run it. It does all the magic and volia..control fan speed with a slide from a bar.


very hard :(. I give up

---

### Post by jackdale on 2010-01-30
Have a look at [this]("http://linux.softpedia.com/get/System/System-Administration/QtFan-31543.shtml")

It does not seem as functional as the mac [SMC Fan Control]("http://mac.softpedia.com/get/System-Utilities/smcFanControl.shtml"), but I have not tried it yet.

I'll reply if it happens to be fantastic ;)

---

### Post by dawin45 on 2011-07-19
sorry for refreshing the topic
but I installed a new Ubuntu 11.04 Natty Narwhal and wondered what is the code for this release in order to program the fan speed,tried various code in the beginning but failed to find the files...
thank you for your understanding...

---

### Post by geazzy on 2011-07-21
great job :)

---

### Post by tumutanzi on 2011-07-22
Sounds interesting.

---

### Post by pconwell on 2011-08-31
> **dawin45 said:**
> sorry for refreshing the topic
but I installed a new Ubuntu 11.04 Natty Narwhal and wondered what is the code for this release in order to program the fan speed,tried various code in the beginning but failed to find the files...
thank you for your understanding...

Same questions (I think). I don't have a /proc/acpi/thermal_zone or /proc/acpi/fan...

ubuntu 11.04 server edition.

---

### Post by Gotlieb on 2011-09-02
Thanks.. worked like a charm

---

