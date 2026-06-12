---
title: "what drivers do I need to install for Windows? (MB)"
date: 2007-04-01
forum: The Cafe
---

### Post by billdotson on 2007-04-01
I am going to re-install Windows and I have an Asus P5B Deluxe/Wi-fi AP motherboard.  I have donwloaded the Marvell Yukon Gigabit Ethernet Driver and the JMicron JMB36X RAID Controller Driver so far.  I do not use the onboard wi-fi or the onboard sound so I don't need those drivers.  There is a driver on the disc called Intel Chipset Inf Update program.  I am also downloading the Asus PCProbe II and the Asus Ai Suite utilities.  If I am not mistaken the Ai suite is to allow you to easily overclock from the Windows environment.  I don't overclock any of my stuff because that can ruin warranties and I really am not that knowledgeable about overclocking.

There is also a driver called USB2.0 on the install disc but I cannot find a USB driver on Asus site.  I assume I need to install some chipset drivers but I do not know what those are.  
BTW, when someone says they are upgrading their chipset they are getting the latest chipset drivers correct?  I have also heard people saying they are upgrading their northbridge or southbridge.. you can't physically upgrade your northbridge on the MB can you?

---

### Post by siya_kh1983 on 2007-04-01
It's simple.
First answer to me that you wanna install a windows without formatting or you wanna format the windows drive and then install the windows again.
second: with ver of windows you wanna install?

3:do you use any linux os on your computer

4:nothbridge and south.. can't physically upgrade , the update of these chip is on the your mother board site... but I rec that don't do it. becuase it's not a good job ;)

---

### Post by azkehmm on 2007-04-01
And people say installing linux is difficult...](*,)

---

### Post by siya_kh1983 on 2007-04-01
you wanna motherBoard driver, soundCard,Monitor(rec),connections(ex:modem,networkCard,WirelessCard). 

this is a usual driver that must have...
ok?

---

### Post by siya_kh1983 on 2007-04-01
plus graphic Card driver (this is more importent)

but maybe the windows can recognize your driver and have them and install them

---

### Post by prizrak on 2007-04-01
I happen to have a system with such a board :) The most important thing that you will need is to create a driver floppy disk with the SATA driver. NIC is going to need a driver and so is the sound. My advice is get the network working right first then you can pull down w/e is necessary. Chances are the video won't be recognized properly either
XP won't need a USB 2.0 driver, Vista shouldn't either.

---

### Post by billdotson on 2007-04-01
I am talking about drivers I need for my motherboard stuff.  I know that I need my videocard driver and my soundcard driver but I was asking about drivers for my motherboard.  I am installing Windows XP SP2.  I have never installed Windows myself as the local university has a blanket license for Windows so I can get it for free and they will install it for free.  So they have always been installing Windows for me and I have never actually done it myself.

I am going to reformat the entire HDD and reinstall Windows.  I want to make 2 partitions, a 160-175GB partition for my Windows install and programs and the second partition will have the remaining HDD space for files and such.  I have Ubuntu on my external HDD and am using it right now.  I have put the JMicron driver, the Asus Ai Suite utility, the Asus PCProbe II utility and the Marvell Yukon Gigabit Ethernet driver on my external HDD.  I also have my videocard and sound card drivers on the external as well.  There is something called Intel Chipset Inf Update utility on the install CD and I was wondering what that is for.

What do you mean by having a floppy with the SATA driver on a floppy? Does the motherboard not support SATA w/o a driver?  Do I really need a driver for the onboard ethernet?  I do not use a network card as I just connect to the router via ethernet cable, plugged into the onboard ethernet.

---

### Post by macogw on 2007-04-02
> **prizrak said:**
> I happen to have a system with such a board :) The most important thing that you will need is to create a driver floppy disk with the SATA driver. NIC is going to need a driver and so is the sound. My advice is get the network working right first then you can pull down w/e is necessary. Chances are the video won't be recognized properly either
XP won't need a USB 2.0 driver, Vista shouldn't either.

SP2 fixed the SATA thing. You only need a floppy with SATA drivers if you install SP1.

---

### Post by prizrak on 2007-04-02
> **macogw said:**
> SP2 fixed the SATA thing. You only need a floppy with SATA drivers if you install SP1.

I so wish it did. Was installing SP2 very recently (like this past weekend) on the same board. Well almost the same board mine didn't have the Wi-Fi built in. To use SATA as AHCI or RAID it will need a driver if you put your SATA into IDE mode then it gets recognized but what is the point of SATA then?

> There is something called Intel Chipset Inf Update utility on the install CD and I was wondering what that is for.
Basically an updated driver (or updater program) for the chipset. You can install it or not install it doesn't seem to make any difference. In theory it should make it work better/faster in reality I never noticed any difference. 

> What do you mean by having a floppy with the SATA driver on a floppy? Does the motherboard not support SATA w/o a driver? 
The SATA II controller on the board can work in 1 of 3 ways. You can set it as IDE, as AHCI (native SATA basically), or RAID. If you choose to set it into IDE (will be slower) then you will be able to just install XP and not worry about it. If you choose to go with AHCI (you should IMO) then during the XP setup you will have a chance to install a 3rd party driver (it will ask you to hit F6 in the beginning if you are planning on installing the driver, you will have a chance to do so later, if not it will plain fail). As XP installer was designed by complete morons it will only accept a driver on a floppy disk and nothing else. Your board documentation should tell you how to create the driver disk, basically you just boot into the driver CD that came with the board and it will allow you to create the disk from there. 

> Do I really need a driver for the onboard ethernet? I do not use a network card as I just connect to the router via ethernet cable, plugged into the onboard ethernet.
Yes, Windows XP SP2 Pro does not recognize the on-board ethernet adapter. You will need to install the driver that came with your board. I'm talking wired ethernet not wireless (just wanted to make it clear).

---

