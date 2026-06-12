---
title: "No Internet wired connection after install"
date: 2012-03-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Hazzabin on 2012-03-18
Installed Precise 12.04 into my 'testing computer' as per the normal it gets the packages etc etc via internet, once completed and re-boot, it's telling me I have no 'wired connection', strange cos its just got everything.
I've tried to reset the etho settings but nothing seems to work, any ideas please......I do have other OS's on same machine in their own partitions they work ok.:confused:

Hazz

---

### Post by ratcheer on 2012-03-18
If your ethernet card is pci, run "sudo lspci -n". This will tell you both whether the card is detected and, if it is, what if any driver is loaded for it.

Tim

---

### Post by VinDSL on 2012-03-18
I never could get network-manager to work with the Linux 3.2 / Linux 3.3 kernels, on this machine's onboard LAN.  Works fine on =< Linux 3.1

The problem is, this mobo has an onboard LAN device that runs off of the southbridge, e.g. it's a pseudo LAN device.

The intermediate fix was to remove network-manager and install Wicd.  It worked fine with the onboard LAN.

Finally, after a few weeks, I tried a real nic and network-manager started working again.

That said, last week, network-manager quit working at boot, but worked on the desktop.  The most recent network-manager upgrade took care of this situation.  Now, I get a network connection at boot, and on the desktop.

My suggestion is to switch to Wicd, and/or try a real nic, if you're running a bridge-driven pseudo LAN device.

---

### Post by Hazzabin on 2012-03-18
ratcheer sorry mate having trouble getting the terminal image into here (which I've not done b4)
anyway the info from 'lspci -n' is exactly the same as I get with ubuntu 11.10, same machine diff partition

[http://dl.dropbox.com/u/67399412/Screenshot%20at%202012-03-19%2009%3A58%3A37.png](http://dl.dropbox.com/u/67399412/Screenshot%20at%202012-03-19%2009%3A58%3A37.png)

---

### Post by cariboo on 2012-03-18
lspci -n really doesn't give you the results we are looking for. It would be better to use :

```
lspci
```

without any options. You can just highlight the output in a terminal, then use the centre mouse button to paste what you highlighted in a post. No need for a screen shot.

---

### Post by ratcheer on 2012-03-18
And I apologize, I meant -v, not -n.

Tim

---

### Post by VinDSL on 2012-03-18
> **cariboo907 said:**
> lspci -n really doesn't give you the results we are looking for. It would be better to use :

```
lspci
```
Here's a cute combo...  ;)

```
vindsl@Zuul:~$ **[COLOR="DarkRed"]lspci[/COLOR]**
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation G73 [GeForce 7600 GT] (rev a2)
**[COLOR="Blue"]02:0c.0[/COLOR]** Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)

vindsl@Zuul:~$  **[COLOR="DarkRed"]lspci [/COLOR][COLOR="Blue"]-vvv -s 02:0c.0[/COLOR]**
02:0c.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 20)
	Subsystem: Netgear FA310TX
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at a400 [size=256]
	Region 1: Memory at fc000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 40000000 [disabled] [size=256K]
	Kernel driver in use: tulip
	Kernel modules: tulip

vindsl@Zuul:~$ 

```

---

### Post by Hazzabin on 2012-03-18
ok guys this is what I get

[http://dl.dropbox.com/u/67399412/Screenshot%20at%202012-03-19%2012%3A51%3A43.png](http://dl.dropbox.com/u/67399412/Screenshot%20at%202012-03-19%2012%3A51%3A43.png)

PS I'm going to be away for a while 2 hours at most

---

### Post by Hazzabin on 2012-03-19
hey guys still haven't been able to solve this issue

---

### Post by ratcheer on 2012-03-19
Well, your "lspci -v" output shows that the ethernet device is connected and the r8169 driver is loaded and in use. You could try installing the r8168 driver, which I have had to do for a long time. However, the r8169 seems to work with the latest kernels (3.1 and 3.2).

See if you can find and download r8168 version 8.028. I can help you install it. If you can't find it, I could even email it to you.

Tim

---

### Post by Hazzabin on 2012-03-19
ok mate and thanks again for info, I think I found it and it's a .tar.bz2 file

A step by step instructions for this old man be appreciated

---

### Post by ratcheer on 2012-03-20
We seem to be on different schedules.

There is an easy way and a hard way. Let's try the easy way first and, if it doesn't work, we'll have to try the hard way.

First, make sure your system has packages build-essential and the linux-headers package for your kernel, e.g., linux-headers-3.0.0-16 installed (if you are running kernel 3.0.0-16).

Then, edit file /etc/modprobe.d/blacklist.conf and add a new line: "blacklist r8169" (without the quotation marks).

Next, expand the file you downloaded into a directory by itself. cd to that directory. Make sure the autorun.sh file is executable (755 permissions). Then, run "sudo ./autorun.sh". If this works the way it did on my system, it should modprobe the new module and your connection should come up within 30 seconds or so.

To verify, run "sudo lspci -v" again. It should now show, "Kernel module in use: r8168". If not, reboot and see if it picks it up. If all of this doesn't work, we will have to try the hard way.

Tim

---

### Post by Hazzabin on 2012-03-20
Ratcheer, mate many thanks for that.....and yes we sure are on different time frames, downside too I got a heavy work load for the next couple of days.....so just don't know quite when I'll get to that computer yet.

Hazz

---

### Post by neu5eeCh on 2012-03-20
This may or may not be similar to a bug I experienced in 11.10 (installing Edubuntu).

1.) When I first put in the LiveCD, I opted to go to the DE (rather than straight to the install). Once I had an Internet connection, I clicked on install. 

2.) During install, I was asked whether I wanted to use (install) the current wireless connection (a checkbox) as part of the installation. I checked that option.

3.) Once installed, I rebooted and was **not**, was **never** able to get wireless working. It insisted that there were no wireless networks and when I clicked on my wireless network (which it nevertheless showed!), it disabled the "Enable Wireless" option and I could **not** re-enable it. I filed a bug about this but got no satisfaction.

Ultimately, I had to reinstall and this time I unchecked the "install current wireless network" option (this was a while ago). It worked beautifully.

If this sounds like what you did, then my advice is to re-install.

---

### Post by varunendra on 2012-03-21
See if this post can help: [http://ubuntuforums.org/showthread.php?p=11733546](http://ubuntuforums.org/showthread.php?p=11733546)

---

### Post by VinDSL on 2012-03-21
Here's a funny one for you... :D

I bought a Netgear PS110 Print Server, the other day -- and decided to set it up this morning.

I didn't want to mess around with my production machine, changing IPs and the subnet mask, blah, blah, blah, so I got my Eee PC out of the closet and used it as the guinea pig.

Dude, I tried to get the onboard LAN (wired connection) working for 2-3 hours.  I couldn't even get it to light up my LAN switch. Wifi worked fine.

Eventually, I happened to check BIOS, and the !#@& onboard LAN port was disabled.

Bwahahahahaha!  I'll swear, I didn't turn it off, now or ever.

Um... you checked your BIOS settings, yes?!?!?  ;)

---

### Post by cryptotheslow on 2012-03-21
There's several suggested workarounds in the comments to this bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393)

The bug was filed against Oneiric, so not sure if it is entirely relevant.

---

### Post by Hazzabin on 2012-03-21
Thanks guys for all suggestions, I decided to switch hard-drives for now back to the one that connected, I know there was a problem within the packages on that day as the install process was happening.
Only because the previous day it installed fine on the above drive, and all other OS's work perfectly.

So for now I'll mark this as solved

---

