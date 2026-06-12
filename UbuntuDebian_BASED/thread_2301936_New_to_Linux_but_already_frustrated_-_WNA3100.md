---
title: "New to Linux but already frustrated - WNA3100"
date: 2015-11-06
forum: Ubuntu/Debian BASED
---

### Post by johann6 on 2015-11-06
Hi all,

First i'm new to Linux (OS: Elementary OS) but not an unskilled user. 
Two full days long I 've tried to get my netgear wlan adapter working.

I downloaded a few driver but non of them worked for me... 
If i install this [ONE]("http://ubuntuforums.org/showthread.php?t=2249030&highlight=Invalid+Driver+Netgear+WNA3100") i can see my network but there always a Authentication required by Wi-fi network popup...

I installed the netgear suit with wine and installed these drivers with the ndis gui.

Now it looks like this:
[[IMG]http://www2.pic-upload.de/img/28781407/Screenshotfrom2015-11-06160716.png[/IMG]]("http://www.pic-upload.de/view-28781407/Screenshotfrom2015-11-06160716.png.html")

But under Network connections there are no wireless networks...

Pls help me

---

### Post by howefield on 2015-11-06
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by duncedrive on 2015-11-08
I'd like to get help on this similarly. I purchased the Netgear N600 USB adapter as well, and have been struggling. I'm pretty well tempted to take this back to Wal-mart, but if it's at all possible, I'd like to make this work.

Model is identified as a WNDA3100_v3_. From my end, those drivers won't work because it's for 3100_v2_, which is manufactured by a different company.

On the lsusb, it's identified as _0846:9014_. The driver that Netgear offers, the latest of which is 1.0.0.10 on their site, is marked as **netr28ux**.

WNDA3100v3 appears to be manufactured by MediaTek, which was apparently Ralink, who had some good support on Linux. I'm dubious of it despite this. The problem I'm having is working with this software through SteamOS, which, while Debian-based, lacks a lot of necessary applications (like the much-needed NDISwrapper that I would've needed to make this stick work).

However, after all that, I'm sitting on ndisgtk, waiting to figure out the answer. As I sit here, I do consider that mention of XP drivers. It's a stretch, but possibly, Netgear dumps a specific variant of the drivers from their install utility depending on the OS? I zipped and shuttled the drivers from a Windows 7 machine.

I'll work on a Windows XP installation and find out real quick.

---

### Post by jeremy31 on 2015-11-10
Check [http://ubuntuforums.org/showthread.php?t=1695036&p=11838453#post11838453](http://ubuntuforums.org/showthread.php?t=1695036&p=11838453#post11838453) for the windows driver in the attachment.  Then you can use the Windows driver tool to use them
It is what I used to get my WNA3100 going but it still didn't work great so I mailed it to Chili555 and this was what he found [http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100](http://ubuntuforums.org/showthread.php?t=2264020&highlight=WNA3100)

---

### Post by duncedrive on 2015-11-11
My personal struggles were in vain. Netgear is a sin on the Linux industry. It doesn't even have value to my brother, who has a keyboard that can be equipped with wi-fi if it's a WNA1100. This dongle's going back to Wal-mart in the next 10 days, and after that, [I'm just gonna score one of these Wireless N adapters.]("https://www.thinkpenguin.com/catalog/wireless-networking-gnulinux") It's sad that we have to rely on an external company for a functional and reliable product like this. Only Atheros and sometimes Realtek NICs seem to have real support around here, and it has to be reverse-engineered before being thrown onto the builds.

[SIZE=4]In short, drop the WNDA3100 and buy a straight Linux-compatible adapter.
[/SIZE][SIZE=2]ThinkPenguin, and Panda Wireless seem to be optimal Linux wireless devices.[/SIZE]

---

