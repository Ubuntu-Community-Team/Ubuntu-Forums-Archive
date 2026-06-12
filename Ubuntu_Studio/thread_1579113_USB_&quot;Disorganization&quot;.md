---
title: "USB &quot;Disorganization?&quot;"
date: 2010-09-21
forum: Ubuntu Studio
---

### Post by DragonFlyEye on 2010-09-21
I'm not sure what else to call this thread, since I'm not at all sure what's going on or how to find out.

This is a box recently converted from Windows to Ubuntu Studio. In Windows, I had no problems with USB devices, so I'm assuming there must be something to configure in Ubuntu that will get me past the problem.

The issue is that I have several USB devices plugged into the system and they occasionally get "lost," either when I start using or when I plug in a new device. For example, I attempted to plug in a USB headset and found that my mouse stopped working once, my keyboard stopped working another time and my USB HDD was unmounted the next time. It's seeming to alternate randomly.

The most recent was when I attempted to use JAMin with Ardour and again lost control of the mouse. I have a USB MIDI keyboard which I assume is triggering the same behavior as other USB devices. The interesting thing here is: 
[LIST=1]
[*]The mouse worked fine until I logged into my account
[*]The mouse works fine in another account
[/LIST]
In this case, unplugging the connection to my USB MIDI keyboard solved the problem. But that's not exactly a solution. Does anyone know what is happening here and how to fix it?

I greatly appreciate your help!

---

### Post by AutoStatic on 2010-09-22
Hello DragonFlyEye, could you post the outcome of the terminal command **lsusb** with the devices attached?

Best,

Jeremy

---

### Post by mango42 on 2010-09-22
Could it be a power issue? That is, too many current demands on one USB buss?

I have a similar problem getting a Samsung USB HDD recognised. No problem if I reboot, though I don't think this is how USB was intended to work.

Perhaps 'plug'n'pray' is a universal phenomenon, not just a windoze issue? ;-)

---

### Post by DragonFlyEye on 2010-09-22
Thanks to both of you for your replies! Here is the output of lsusb (a utility I didn't find out about till after I posted): 

tbelknap@purpleroses:~$ lsusb
Bus 004 Device 004: ID 0582:009d Roland Corp. EDIROL UM-1
Bus 004 Device 003: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 004 Device 002: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:0a0c Logitech, Inc. 
Bus 003 Device 002: ID 045e:0730 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 4971:ce17 SimpleTech 
Bus 001 Device 004: ID 152e:2507 LG (HLDS) 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tbelknap@purpleroses:~$ 

At the moment, all these things plugged in together seems to be working fine. But that's now. If I have another issue, I'll have to try to do the lsusb thing again. Probably won't have control of the mouse, however, so I'll have to remember to open a shell before I start plugging things in!

As for power, that's a good thought, but I haven't experienced this problem in Windows. It's entirely possible that the change in OS and the degredation of the power situation are coincidental, though. Having played with hardware a lot, though, my gut's telling me this is a Linux issue.

---

