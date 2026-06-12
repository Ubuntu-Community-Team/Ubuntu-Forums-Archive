---
title: "Power Management for baremetal"
date: 2014-09-24
forum: Ubuntu, Linux and OS Chat
---

### Post by Jarrod_Class on 2014-09-24
Hello all! I have an issue that I just cannot find a work around to. I have tried all options to disabling power management. So I can get it to work perfectly when the laptop is plugged in on boot. it will stay off when unplugged and plugged back in power management stays off. But when the laptop is not plugged in on boot the power management is set to on. But as soon as you plug it in with a charger it works perfectly from there on out. when unplugged after that is stays off. The script we are running that works the best is the short sweet simple #!/bin/sh sudo iwconfig wlan0 power off     I have tried all other ideas (creating the wireless directory using chmod) also the rc.local option and lead back to this one working the best with only the one minor issue. My question here is what could I do to modify this command to just disable pm when unplugged on boot. Any help would be greatly appreciated thanks again!

Jarrod

---

### Post by tgalati4 on 2014-09-24
Open a terminal and post:

```
ps aux | grep power
```

A laptop with a battery would need some sort of power management, otherwise you would not get proper charging or CPU scheduling.

In a separate terminal, use this tool for monitoring:

```
upower --monitor-detail
```

What is the Use Case that you are trying to address?

---

### Post by Jarrod_Class on 2014-09-24
Internet is throttled on the laptop when unplugged It fixed a lot of our issues here at school. We  do a 1 to 1 program and all the students are having this issue when there laptops are not plugged in. when pm is off it works great.
the only issue is if they boot up the laptop it turns pm on until they plug in then the script takes over.... it weird honestly.... everything else works fine. Im not sure what you mean by use case?

---

### Post by tgalati4 on 2014-09-24
Describe the problem that you are having.  That is the Use Case.  Power management for a wifi card is different than power management for the system.  Yes, if your laptop is unplugged, chances are that the wifi card inside will go to sleep--or a lower power state--and that can interfere with wifi access and throughput.  

Check the BIOS on the computer for power settings for the wifi card and turn them off.

What linux module are you using for your wireless?  For me, I am using a "b43" module.

To check for power management switches:

```
modinfo b43
```

Your module will be different.

To see what modules are loaded:

```
lsmod
```

To narrow it down to 802.11 devices (wireless)

```
lsmod | grep 802
```

---

### Post by Jarrod_Class on 2014-09-25
This is a wifi card power management issue
I checked BIOS and there is only power management for cpu stuff


when I do a
code
> lsmod | grep 802
I get
> 
vmmon                           80278    0
mac80211                      623607   1  iwldvm
cfg80211                        499466  3  iwldvm,mac80211,iwlwifi
squashfs                         48026    2 


Thanks again for your help

---

### Post by Jarrod_Class on 2014-09-25
So for BIOS Power Options I have
Intel SpeedStep Technology  -  Enabled
CPU Power Management - Enabled  
Power On with AC Attach - Disabled
Intel Rapid Start Technology - Enabled
          Entry after   -   3 hours

---

