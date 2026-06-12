---
title: "Audacity records no sound"
date: 2008-10-02
forum: Ubuntu Studio
---

### Post by ssdt on 2008-10-02
When I record using Audacity, there is no sound coming out of the line-in. I am recording from the internet but there is nothing after I have recorder. There is no sound but the frames show a line in the screen but it is plain and straight. Can anyone please help me with the problem of Audacity?

Thanks

---

### Post by Bungo Pony on 2008-10-02
> I am recording from the internet but there is nothing after I have recorder.

With the inclusion of Pulse Audio in Hardy, that feature seems to be gone (it existed in Gutsy). The best suggestion I can give you is to loop the audio, unless someone knows a better way.

You might be able to restore that functionality by getting rid of Pulse Audio and going back to strictly ALSA.

---

### Post by Crafty Kisses on 2008-10-03
What are the results of this command?
```
lspci
```

---

### Post by venik212 on 2008-10-07
I have exactly the same problem.  I THINK Audacity worked fine in previous Kubuntu versions.
lspci produces:
di@udi-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 04)
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.3 FireWire (IEEE 1394): Silicon Integrated Systems [SiS] FireWire Controller
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:08.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:0e.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: ATI Technologies Inc RV516 [Radeon X1300 Pro] (Secondary)
udi@udi-desktop:~$
udi@udi-desktop:~$

---

### Post by ssdt on 2009-08-20
It seems as if no one know how to fix this but please help because i need to know this as soon as possible.

---

### Post by ssdt on 2009-08-20
Bump again. Please, my friends whom I had gotten Ubuntu are now getting away from it just because of what I can't answer about Audacity. Please help me with this issue.

---

### Post by sgx on 2009-08-22
> **ssdt said:**
> Bump again. Please, my friends whom I had gotten Ubuntu are now getting away from it just because of what I can't answer about Audacity. Please help me with this issue.

If you have qjackctl  and audacity running, press the record button in audacity, and see if audacity now appears in qjackctl. It does for me. Then hit the pause button in audacity, start an audio program to record from, and connect it to audacity in qjackctl, and hit the pause button again, to resume recording. If you can hear internet audio, streaming podcasts, etc with your browser, you should be able to connect alsa system sound to audacity in qjackctl. Connections are made by selecting an item in both the input and output panels, and then clicking the 'connect' button. Again, audacity will not appear as a connection until you press its record button.
Don't give up!

---

