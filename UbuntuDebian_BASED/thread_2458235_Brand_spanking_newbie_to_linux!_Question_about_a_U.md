---
title: "Brand spanking newbie to linux! Question about a USB network adapter."
date: 2021-02-19
forum: Ubuntu/Debian BASED
---

### Post by jmgmr2 on 2021-02-19
[COLOR=#1F1F1F][FONT=&quot]I installed the newest Pop OS(and Ubuntu 20.04) on a Ryzen 3700x/32GB/Gigabyte DS3H. No wireless card. I inserted a USB TP-Link AC1200 V2 wireless adapter. (It would work on Ubuntu 20.04 after a lot of work via github). The adapter did not autodetect when I started the Pop OS up. It *did* however detect that it needed the correct rtl8812au driver and installed it when I manually clicked install.[/FONT][/COLOR]

[COLOR=#1F1F1F][FONT=&quot]Great! I thought. That would be the most polished linux install ever in the history of time. Except, well, except the wireless adapter doesn't start up and doesn't work. So I entered the usual suspects:[/FONT][/COLOR]

[COLOR=#1F1F1F][FONT=&quot]dmesg -w (no errors)[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]lsusb (The wireless adapter is clearly listed as the Realtek rtl8812au T4U.[/FONT][/COLOR]
[COLOR=#1F1F1F][FONT=&quot]dkms status (lists the module installed for the rtl8812au T4U).[/FONT][/COLOR]

[COLOR=#1F1F1F][FONT=&quot]But the adapter won't start. It just sits there. I tried on both the motherboard ports and the case USB ports. Both USB 2 and 3. Nothing. A smaller, slower, simpler TP-Link USB adapter works flawlessly out of the box but at 10 MBps, it's just too slow to do anything.[/FONT][/COLOR]

[COLOR=#1F1F1F][FONT=&quot]I've tried for weeks to get the driver to work on Ubuntu, then Pop OS.  All I want is to get a supported USB wireless adapter to work but when it does work, it works for a few hours and then drops connection mysteriously.  Else it just never works at all.  Can someone please give me a hint as to what to do?  Help appreciated.[/FONT][/COLOR]

---

### Post by schragge on 2021-02-19
The best place to start your search is probably [https://linux-hardware.org](https://linux-hardware.org). Examine [the probes]("https://linux-hardware.org/?id=usb:0bda-8812") where this piece of hardware worked, and see what drivers were used in them.

---

### Post by jmgmr2 on 2021-02-19
I know which drivers were used.  The only driver was the [http://github.com/aircrack-ng/](http://github.com/aircrack-ng/) rtl8812au driver.  But it would just go dead for no reason.  I checked cron...but nothing was there (new install!).  I would check the modules via dkms status...and it was installed.  I tried every USB port.  But nothing.  And then, I'd use Timeshift and the machine would have wifi again...and then lose it a scant hour later.  I've already trolled through dozens of threads online and reinstalled from Ubuntu 20, to Ubuntu 16, to Mint, to Debian,  to Fedora, to Ubuntu, to Pop OS.  It works great on Mac and Windows 10 but once I plug it into Linux...nothing.  I didn't just come here at the first sign of trouble.  Promise.  I really am stumped. :)

---

### Post by jmgmr2 on 2021-02-19
Like I don't get how Pop OS can detect the USB wireless adapter...ask me if I want to install it.  It installs the correct rtl8812 driver.  I do an lsusb...it recognizes the device.  A quick dkms status shows that the module is properly installed...but the wireless adapter shows *no* activity.  How can the OS both detect the required driver, install it correctly and then...produce no result?  I legit don't know where to go from here and, to be honest, the idea of spending another 20+ hours (how many I've already spent on this one problem), just to make a plug in wireless adapter work...is really putting me off the idea of Linux in general.  I'm about half a step away from just reaching for HyperV as my virt platform instead of kvm (which works great so far).

---

### Post by ActionParsnip on 2021-02-19
Considering how cheap USB wifi is, I'd just find one that works out of the box with no muss or fuss

---

### Post by jmgmr2 on 2021-02-19
I already thought of that.  I bought a new TP-Link AND a Panda wireless that my professor recommended.  Neither worked for any period of time. Returned.

I used a mm to check my PSU for power issues.  None.  Then put it on a UPS just for good measure.  I'm 99% sure it's not the adapter or the hardware.  It's a software issue with my mobo.  I'm not buying a new mobo and since the adapter works for short bursts quite nicely (300-450 mbps), I was wondering if anyone had any ideas.

As an aside, I have another TPLink that does work out of the box, but it's an n adapter that only nets me a max of 25 mbps.  I've tried a total of five wifi usb adapters and only one has worked out of the box.

---

### Post by howefield on 2021-02-19
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by jmgmr2 on 2021-02-19
Pop OS installed the driver module for rtl8812.  Should I uninstall it?  Should I try to install the aircrack-ng git driver?  That puts me back to playing the same games I was experiencing with Ubuntu 20.04. :(

I don't want the modules to conflict, so maybe I need to rip it out?

---

### Post by schragge on 2021-02-19
> **jmgmr2 said:**
> I know which drivers were used.  The only driver was the [http://github.com/aircrack-ng/](http://github.com/aircrack-ng/) rtl8812au driver
I wouldn't be so sure. [This probe]("https://linux-hardware.org/?probe=3ed3643d8b") shows me **rtl8821au** which is probably [https://github.com/ulli-kroll/rtl8821au](https://github.com/ulli-kroll/rtl8821au). And [this probe]("https://linux-hardware.org/?probe=c74de8e6b2") shows me **rtl88XXau** which is probably [https://github.com/n0ss/realtek-rtl88xxau-dkms](https://github.com/n0ss/realtek-rtl88xxau-dkms).

There are some others as well. Like [https://github.com/gordboy/rtl8812au-5.9.3.2](https://github.com/gordboy/rtl8812au-5.9.3.2).

---

### Post by jmgmr2 on 2021-02-19
No. I mean when I had Ubuntu installed the only driver I used was the aircrack-ng.  On prior Ubuntu installs I used gnab and others.  But aircrack was the only truly successful one.

---

### Post by schragge on 2021-02-19
Look, I see there three Pop!_OS probes with the working adapter: [Pop!_OS 20.04]("https://linux-hardware.org/?probe=cd3018f0d7"), [Pop!_OS 20.10]("https://linux-hardware.org/?probe=ba1c44690a"), and again [Pop!_OS 20.04]("https://linux-hardware.org/?probe=c1576f7b77"). Cannot be sure about the first two, but the last one definitely uses [https://github.com/n0ss/realtek-rtl88xxau-dkms](https://github.com/n0ss/realtek-rtl88xxau-dkms).

---

### Post by jmgmr2 on 2021-02-19
Whelp, same problem with Pop as Ubuntu 20.04 LTS.  I install the wireless adapter from n0ss' github.  Works great.  Then I leave the server to log off...ping it every 30 min or so... Still up. Great!

2 hours later.  Ping fails.  Server internet is down.  What gives? :(

---

### Post by TheFu on 2021-02-20
Check the power settings for the adapter. Could be that the wifi assumes a laptop on battery and disables extra power use devices.

---

### Post by jmgmr2 on 2021-02-20
I set the wifi power settings to 2 (from 3).  It was connecting/running.  I stepped away for 2 hours.  Network connection down.  So stumped. :(

---

