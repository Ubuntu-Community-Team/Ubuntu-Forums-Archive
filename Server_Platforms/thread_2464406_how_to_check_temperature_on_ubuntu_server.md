---
title: "how to check temperature on ubuntu server"
date: 2021-07-01
forum: Server Platforms
---

### Post by s-grind on 2021-07-01
Hi,

I want to check my system temperature on my ubuntu server.
If I google, I read a lot about installing lm-sensors and things like that. 
To be honest; I do not want to install anything at this moment; whenever I log in with SSH to my server, it gives me the temperature already.
So my main question is: where is this information comming from and how do I obtain that information without installing anything else?

See screenshot.
[ATTACH=CONFIG]288756[/ATTACH]

Thanks for the help!

---

### Post by Doug S on 2021-07-01
For the restrictions of not wanting to install anything else, then:

Step 1: Determine what devices there are:
```
doug@s19:~$ grep . /sys/devices/virtual/thermal/thermal_zone*/type
/sys/devices/virtual/thermal/thermal_zone0/type:acpitz
/sys/devices/virtual/thermal/thermal_zone1/type:x86_pkg_temp
```

Step 2: List the temperatures of those devices:
```
doug@s19:~$ grep . /sys/devices/virtual/thermal/thermal_zone*/temp
/sys/devices/virtual/thermal/thermal_zone0/temp:27800
/sys/devices/virtual/thermal/thermal_zone1/temp:36000
```
Noting that the values are in units of millidegrees C. So my processor package temperature is currently 36 degrees C and my acpitz-acpi-0, ACPI interface, is 27.8 degrees.

Now, apply some CPU load and read again:
```
doug@s19:~$ grep . /sys/devices/virtual/thermal/thermal_zone*/temp
/sys/devices/virtual/thermal/thermal_zone0/temp:27800
/sys/devices/virtual/thermal/thermal_zone1/temp:68000
```And observe the processor has gone up to 68 degrees (it is water cooled, it'll take awhile to go higher. The power has gone from 1.4 to 130 watts and will throttle to 125 watts shortly.)

EDIT: Supporting data, using turbostat (an installed utility via linux-tools-common (I think)):
```
doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt GFXWatt RAMWatt
0.01    2438    262     39      1.39    0.00    0.89
0.01    1301    114     39      1.38    0.00    0.89
0.01    908     117     39      1.37    0.00    0.89
5.38    4478    1243    66      8.16    0.00    0.89
98.67   4530    18091   69      129.24  0.00    0.89  <<< 1st level power throttle
98.67   4527    18085   70      129.05  0.00    0.89
98.68   4527    18075   72      129.02  0.00    0.89
98.68   4523    18075   72      128.84  0.00    0.89
99.01   4496    18092   72      127.09  0.00    0.89
99.68   4490    18078   72      124.93  0.00    0.89 <<< 2nd level power throttle
```Note temperatures are higher, because this was done later, and the coolant was already warmer to start with.

---

### Post by TheFu on 2021-07-01
Put a thermometer inside the case?

Sensors are drivers specific to the different chips.  If they were automatically installed, great. Now you just need a program to display those - which you'll likely need to install.
Some chips don't have drivers that work with the included sensors, so those drivers are necessary.  For example AMD Ryzen CPUs and the north bridge often don't provide data without extra modules loaded.

As for how any information is displayed at login, you can trace back through the different login files until you locate which value is actually being displayed.

For example, AMD CPUs provide 1 temperature, but Intel CPUs provide a different temperature per core.
There are temperature sensors in different chips on the motherboard, inside the GPU, and near fans.  Most HDDs and SSDs also have temperatures. Accessing this information requires different drivers to make the information available, then a program or 2 or 5 to display the data.

Why are you afraid to install a program that displays data?  That's all a computer really does, right?

---

### Post by slickymaster on 2021-07-01
*Thread moved to **Server Platforms**.*

---

### Post by MAFoElffen on 2021-07-01
> **Doug S said:**
> For the restrictions of not wanting to install anything else, then:

Step 1: Determine what devices there are:
...
This where mine fails... It has no extra's installed (although I have in the past for other boxes for Conky to use):
```
mafoelffen@Opti-Ubuntu-Main:~/Scripts$ ls /sys/devices/virtual/thermal/
cooling_device0   cooling_device12  cooling_device2  cooling_device6
cooling_device1   cooling_device13  cooling_device3  cooling_device7
cooling_device10  cooling_device14  cooling_device4  cooling_device8
cooling_device11  cooling_device15  cooling_device5  cooling_device9
```
Which is one per CPU core, but type on them shows Processor, and it's ahs no temp values to it shown there...

But my "mtod" banner on the host does not show the temp... Maybe because either it's not had additional installed, a different processor and/or server board(?)

EDIT : Yes. The CPU model changes that. "Doug S' is using Intel CPU... For the AMD, there is no "Temp" found anywhere recursively below /sys/devices/virtual/thermal/...

---

### Post by TheFu on 2021-07-01
Some observations:
[LIST]
[*]Intel is better supported than AMD. 
[*]Some AMD support of newer chipsets/MBs has been "coming" for 2 yrs. It hasn't arrived for many.  Slight differences in the MB names drastically changes sensors support.
[*]Higher end CPUs and MBs get better support.
[*]Some chipsets don't ever get supported.  It takes someone with C programming skills to have "an itch" to scratch to get anything working. Getting that stuff included in the kernel is much harder and some people just don't want to spend the effort.
[/LIST]

The OP will need to do a little research for the exact CPU and exact MB to determine what is easy and what is hard to get working.

I think
```
$ inxi -CM
```
provides the needed hardware information in a compact way, at least for the CPU, motherboard, BIOS version and date.
From that, searching for _sensor support linux_ for the exact motherboard might find instructions.  Maybe "it just works", if lucky.

I haven't been lucky with MBs.

But with HDDs, 
```
$ sudo /usr/sbin/hddtemp /dev/sd[a-z]
/dev/sda: WD easystore 25FB: S.M.A.R.T. not available
/dev/sdb: WD easystore 25FB: S.M.A.R.T. not available
/dev/sdc: HGST HMS5C4040ALE640: 37°C
/dev/sdd: ST3320620AS: 42°C
/dev/sde: HGST HUS726T4TALA6L4: 40°C
/dev/sdf: WDC WD40EFRX-68WT0N0: 39°C
/dev/sdg: HGST HMS5C4040ALE640: 42°C
```

And for a different system, the WD-Black 1TB runs hot:
```
$ sudo /usr/sbin/hddtemp /dev/sd[a-z]
/dev/sda: PluagablUSB3-SATA-U3:  drive supported, but it doesn't have a temperature sensor.
/dev/sdb: WD My Book 1140: S.M.A.R.T. not available
/dev/sdc: WDC WD1001FALS-00J7B0: 46°C
/dev/sdd: TOSHIBA DT01ACA200: 34°C
/dev/sde: Hitachi HUA723020ALA641: 37°C
/dev/sdf: WDC WD20EFRX-68AX9N0: 34°C
/dev/sdg: WDC WD20EFRX-68AX9N0: 32°C
```

SSDs run a little hotter:
```
$ sudo /usr/sbin/hddtemp /dev/sd[a-z]
/dev/sda: Hitachi HDP725050GLA360: 44°C
/dev/sdb: Micron_1100_MTFDDAV512TB N              &#65533;@: [COLOR="#FF0000"]51°C[/COLOR]
```

I find this a little concerning:
```
/dev/sda: Samsung SSD 860 EVO 500G B              &#65533;@:  [COLOR="#FF0000"]no sensor[/COLOR]
```

I feel pretty lucky to get that drive temperature data so easily.

---

### Post by MAFoElffen on 2021-07-01
LOL. Same for mine:
```
mafoelffen@Opti-Ubuntu-Main:~$ sudo /usr/sbin/hddtemp /dev/sd[a-z]
/dev/sda: WDC WD40EZAZ-00SF3B0: 34°C
WARNING: Drive /dev/sdb doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/[COLOR=#ff0000]dev/sdb: Samsung SSD 870 EVO 500G B              &#65533;@:  no sensor[/COLOR]
/dev/sdc: ST5000DM000-1FK178: 36°C
/dev/sdd: WDC WD40EZRZ-22GXCB0: 35°C
/dev/sde: WDC WD40EZAZ-00SF3B0: 34°C
```

---

### Post by Doug S on 2021-07-02
> **MAFoElffen said:**
> This where mine fails... It has no extra's installed (although I have in the past for other boxes for Conky to use):
```
mafoelffen@Opti-Ubuntu-Main:~/Scripts$ ls /sys/devices/virtual/thermal/
cooling_device0   cooling_device12  cooling_device2  cooling_device6
cooling_device1   cooling_device13  cooling_device3  cooling_device7
cooling_device10  cooling_device14  cooling_device4  cooling_device8
cooling_device11  cooling_device15  cooling_device5  cooling_device9
```
Which is one per CPU core, but type on them shows Processor, and it's ahs no temp values to it shown there...

But my "mtod" banner on the host does not show the temp... Maybe because either it's not had additional installed, a different processor and/or server board(?)

EDIT : Yes. The CPU model changes that. "Doug S' is using Intel CPU... For the AMD, there is no "Temp" found anywhere recursively below /sys/devices/virtual/thermal/...

Interesting, no default thermal zones at all, and only processor cooling types. Here's mine:

```
doug@s19:~/idle/teo/pipe-test/powersave$ grep . /sys/devices/virtual/thermal/*/type
/sys/devices/virtual/thermal/cooling_device0/type:Fan
/sys/devices/virtual/thermal/cooling_device10/type:Processor
/sys/devices/virtual/thermal/cooling_device11/type:Processor
/sys/devices/virtual/thermal/cooling_device12/type:Processor
/sys/devices/virtual/thermal/cooling_device13/type:Processor
/sys/devices/virtual/thermal/cooling_device14/type:Processor
/sys/devices/virtual/thermal/cooling_device15/type:Processor
/sys/devices/virtual/thermal/cooling_device16/type:Processor
/sys/devices/virtual/thermal/cooling_device17/type:intel_powerclamp
/sys/devices/virtual/thermal/cooling_device18/type:TCC Offset
/sys/devices/virtual/thermal/cooling_device1/type:Fan
/sys/devices/virtual/thermal/cooling_device2/type:Fan
/sys/devices/virtual/thermal/cooling_device3/type:Fan
/sys/devices/virtual/thermal/cooling_device4/type:Fan
/sys/devices/virtual/thermal/cooling_device5/type:Processor
/sys/devices/virtual/thermal/cooling_device6/type:Processor
/sys/devices/virtual/thermal/cooling_device7/type:Processor
/sys/devices/virtual/thermal/cooling_device8/type:Processor
/sys/devices/virtual/thermal/cooling_device9/type:Processor
/sys/devices/virtual/thermal/thermal_zone0/type:acpitz
/sys/devices/virtual/thermal/thermal_zone1/type:x86_pkg_temp
```As a side note, I find the cooling/thermal file structure in linux extremely confusing and difficult to follow.

And yes, my processor is: Intel(R) Core(TM) i5-10600K CPU @ 4.10GHz

I don't seem to have the hddtemp command installed (server):

```
$ sudo /usr/sbin/hddtemp /dev/sd[a-z]
sudo: /usr/sbin/hddtemp: command not found
```

---

### Post by s-grind on 2021-07-02
Hi all,

Thank you so much for the information, I will try some of the suggestions!

To be clear: of course I can install additional drivers and/or applications. But I was wondering why the temperature states in my screen when I connect by SSH, so my thoughs were that I should be able to obtain that information, without installing software...
But with the suggested answers, I will set this threat as solved; If those options do not work for me, I will install some software, or maybe I will skip the check on temperature; I was just curious, no really need for knowing (or monitoring) the temperature. ;-)

[edit]
The suggestions of Doug S worked quite well! Thanks!!

---

### Post by TheFu on 2021-07-02
```
man update-motd 
```
explains how the messages are updated to be shown at login.  Those can be disabled.  The systemctl term is "mask".  Look in /etc/update-motd.d/ for the scripts.
I just ```
chmod -x /etc/update-motd.d/*
``` to get silence.

If you want to be reminded to reboot or that fsck will to be run at the next reboot, don't chmod those scripts.

---

### Post by MAFoElffen on 2021-07-02
@"Doug S" Yes. The cooling_devices" down the line down the tree, seem to have power and state. And in the state files just contain a ) or 1, so leading me to think that they are just a boolean implying if it indicates that cooling is needed (turn fans off or run them higher(?) My box has 14 fans.

@et_all - Sensors does work great on my system. Low overhead. (About 0.13% CPU) You do have to configure it, where it goes through a script to ID what chips are on the system and it's buses itself, and what to include in it's own config file. Once it is configured, I can call it from CLI or from Conky to display what I want to see, where. The overhead is only present when it makes a call to it, a short query, then exit's with results.

---

### Post by Bashing-om on 2021-07-02
et all;

My old AMD system:
```

cat /sys/class/thermal/thermal_zone0/temp

```
yields:
> 
26500

where it too is milli-degrees in centigrade.

:D

---

### Post by MAFoElffen on 2021-07-04
> **Bashing-om said:**
> et all;

My old AMD system:
```

cat /sys/class/thermal/thermal_zone0/temp

```
yields:

where it too is milli-degrees in centigrade.

:D

Thanks Bashing-om, except...Mine does have that. LOL
```
mafoelffen@Opti-Ubuntu-Main:~$ cat /sys/class/thermal/thermal_zone0/temp
cat: /sys/class/thermal/thermal_zone0/temp: [COLOR=#ff0000]No such file or directory[/COLOR]

root@Opti-Ubuntu-Main:/sys/class/thermal/cooling_device0# ls
cur_state  device  max_state  power  stats  subsystem  type  uevent

```

---

### Post by sudodus on 2021-07-04
For the sake of completeness, I can add a command to see the temperature in nvme drives:

```

sudo apt install nvme-cli            # if not already installed

**sudo nvme smart-log /dev/nvme0n1**     # you can identify a single drive with lsblk

# or generally (to find available nvme drives automatically and focus on temperature)

**for i in /dev/nvme?;do echo -n "$i: ";sudo nvme smart-log "$i" | sudo grep -i '^temperatur' ;done**

# or if it would add details

for i in /dev/nvme???;do echo -n "$i: ";sudo nvme smart-log "$i" | sudo grep -i '^temperatur' ;done

# or

for i in /dev/nvme*;do echo -n "$i: ";sudo nvme smart-log "$i" | sudo grep -i '^temperatur' ;done

```

If you know a more convenient way to get the temperature of an nvme drive (corresponding to hddtemp), please tell us :-P

---

