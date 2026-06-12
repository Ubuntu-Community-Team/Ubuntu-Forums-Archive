---
title: "No network configuration tool in Ubuntu 10.04"
date: 2010-06-13
forum: Ubuntu Studio
---

### Post by carusoswi on 2010-06-13
I used NDISWrapper to load the driver for my Belkin N1 wireless adapter.  However, no wireless icon appears when I boot up (no wired network icon shows up, either), and, if I try to configure the adapter from the 'windows wireless drivers' dialog box, I receive a message that no configuration tool is available.  Hardware present = 'yes'

Help appreciated.

Thanks.

Caruso

---

### Post by trulan on 2010-06-14
That is left out of Ubuntu Studio intentionally.  So if you want to use wireless, you probably want to install a network manager manually.  Either Gnome Network Manager or WICD will do the job nicely.  Install one of those, either through Synaptic Package Manager or via command line if you prefer.

---

### Post by mango42 on 2010-06-14
As I'm labelled as a complainer just now (but sure, I roast my own beans anyway) I'd like to ask anyone 'in the know' how to use UbuntuStudio (9.10 or 10.04) without any net connection? Personally, I'd love to, (as this also appears to be the devs intention) - so is there any other (user-friendly?) way to obtain updates? 

F'rinstance, I'm running Karmic vanilla to access the net on a 32bit system but I'd like to able to update a 64bit UbuntuStudio machine that doesn't have a net connection.

---

### Post by cchhrriiss121212 on 2010-06-14
I don't think the people packaging studio want people to use it without internet connections mango, it is just that network manager causes conflicts so it is left out of the build. If you install studio with a wired connection then you will be able to update and use the internet perfectly.
You can install network manager to your studio machine from the studio image, which has it in various deb packages.

If you are using studio without a net connection then you shouldn't need any security updates, and you could install programs from .deb packages.

---

### Post by fmxshark on 2010-06-14
so to make sure that i got this right, a brand new ubuntu-studio cannot connect to the internet wireless'ly until you install gnome network manager via synaptics or cmd line, and can you do this without having internet. Also, since im extremely lazy and new to linux, can anyone tell me what it is you need to type into the cmd line to get said program.

---

### Post by Dangerouge on 2010-06-15
[http://ubuntuforums.org/showthread.php?t=1479788](http://ubuntuforums.org/showthread.php?t=1479788)

This thread has a solution to your problem, I believe. I have the same problem, but I haven't yet tested that it works, but I'm quite sure. However, you probably also have to install the packages in network-manager, not just the network-manager-applet, because of the dependencies.

---

### Post by mango42 on 2010-06-15
> **Dangerouge said:**
> [http://ubuntuforums.org/showthread.php?t=1479788](http://ubuntuforums.org/showthread.php?t=1479788)

This thread has a solution to your problem, I believe. I have the same problem, but I haven't yet tested that it works, but I'm quite sure. However, you probably also have to install the packages in network-manager, not just the network-manager-applet, because of the dependencies.

++1

Basically, I found that navigating to /media/cdrom0/pool/main/n/ on the UbuntuStudio DVD and installing everything 'net' with a .deb ending (the order of installation is important but useful error messages will set you right) did work, thanks once again to **cchhrriiss121212**. However, that then leads to other problems that **trulan** solved by reminding me to look at ```
cat /proc/interrupts
``` to see if there was an IRQ conflict (so, so 1980's :) ) with audio - there was - hence my desire to follow the devs and keep Studio off the net altogether.

----------

Synaptic is brilliant and I'm wondering whether there isn't a way to use it with 'locally introduced' updates but so far I don't know enough about it. Alternatively, is there an online resource whereby we could pick up 'bundled' updates for each Ubuntu version, stick them on a USB stick and point Synaptic to them? I suspect I'm way behind the curve on this one... ! {;-)

---

### Post by carusoswi on 2010-06-15
So, could I install a network manager when I want to work with a wireless connection, then, uninstall it when I want to make certain that my machine has no conflicts during audio work, is that correct?
Caruso

---

### Post by carusoswi on 2010-06-15
> **trulan said:**
> That is left out of Ubuntu Studio intentionally.  So if you want to use wireless, you probably want to install a network manager manually.  Either Gnome Network Manager or WICD will do the job nicely.  Install one of those, either through Synaptic Package Manager or via command line if you prefer.

Your suggestion was, of course, exactly correct.  I'm just wonderin'.  How'd you know I was using Studio?  I checked my post, and I neglected to add that detail.

At any rate, thanks for the tip.  I'm up and running again - need my wireless connection at times.

Next question - when I'm only using the machine for audio, must I uninstall that network manager?  Does uninstalling it eliminate conflicts?  Just curious.

Thanks.

Caruso

---

### Post by trulan on 2010-06-15
I'd just let Network Manager installed.  It has never caused a problem for me, though I do have to turn off my wireless card to use firewire due to an irq conflict.  I don't uninstall network manager, I just turn off the wireless card before bootup, and everything is fine.

How'd I know you were using Studio? You wouldn't have this problem on regular Ubuntu.

---

### Post by cchhrriiss121212 on 2010-06-16
There's no need to install and uninstall when you need net access. You can just remove network manager from autostarting and run nm-applet from a terminal whenever you need it, hasn't caused me any issues so far.

---

### Post by Darktrax on 2010-07-14
For me - its a long-winded hassle to put away Ubuntu Studio, find a PC that CAN get on the internet, play Google until I find various procedures, and then get back to tackle the Ubuntu Studio 10.04 that has a network setup tool with the "connections" tab missing.

Very likely one of the recipes might work - if one can get up to a good one without mangling the system with the first attempts.

Yes - I can do it by using a series of ***ifconfig*** commands to stop all, then force a static address in the range my ASDL router DHCP allows, and forcing the DNS addresses, and forcing the gateway to 192.168.0.1, and restart ...... but..

A clean re-install comes with a nicely working network! The trouble is - it will not stay that way. Boot up next day, and the internet connection has evaporated!!

Please folks, in the absence of a fix for bug 57067, apparently also known as bug 570828, are there any clear, authoritative, instructions for getting past this problem in a way that will stick?

EDIT: Er.. duh. It is not consistent! 3 re-boots without network, then suddenly, its back! ??  The network configure tool remains unusable. In my ignorance, I just feel confused. This may end up as one of those things where I have to play elsewhere (PureDyne, 64Studio ?? ) until one day it gets mysteriously fixed.

---

### Post by sgx on 2010-07-15
I have pclinuxos installed on usbsticks, and usb hardisks, there are
versions for gnome, xfce, lxde, openbox, enightenment, as well as the
still rolling KDE4 trainwreck. Even an older working RT audio version with a nice kde3.5.7 

Their focus as a linux, is stability for users, rather than the bleeding edge. ;)

[http://www.mellosonic.com/rocxshop.htm](http://www.mellosonic.com/rocxshop.htm)

---

