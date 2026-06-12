---
title: "Tascam US122 under Hardy - No Initialization"
date: 2008-04-22
forum: Ubuntu Studio
---

### Post by drewdlephone on 2008-04-22
Hey all. I know there are many how-tos on this subject, and I have gone over all of them, and am at a halt here. The two pieces of software required to make the Tascam work, the ALSA firmware and the usx2yloader, are both updated to the newest versions (1.0.15 & 0.1b, respectively), and yet I can't get an initialization to go through. When I type:

```
usx2yloader
```

I get this output:

```
usx2yloader: no usx2y compatible cards found
```

I'm also having an issue with bus support. I know my motherboard is working fine from a USB standpoint, as I've tested with other devices and had success. But every time I try the initialization command, the bus number on the card changes. So whereas I was at /002/002 when I first tried it, I was at 002/003 afterwards. Here's the output from both the audio card query and lsusb.

```
drew@GiR:~$ lsusb
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 1604:8007 Tascam US-122 Audio/Midi Interface
Bus 001 Device 001: ID 0000:0000
```

```
drew@GiR:~$ cat /proc/asound/cards
0 [IXP ]: ATIIXP - ATI IXP
ATI IXP rev 2 with ALC658D at 0xfe02a000, irq 22
1 [USX2Y ]: USB US-X2Y - TASCAM US-X2Y
TASCAM US-X2Y (1604:8007 if 0 at 001/006)

```

I had this working under Gutsy no problem; I followed the Community Documentation on getting it working, both times with success. So I'm at a bit of a loss here. Especially considering the system sees it under CAT as a USX2Y card, but the initializer says I don't have a compatible card. Anyone have any experience with this?

*Please note, this is a repost of a thread I created two hours before the board went down for maintenance and my question ended up archived. :) Any help is appreciated, as I still don't have it working.*

---

### Post by energymomentum on 2008-04-28
Hi, the error message you are getting is probably due to the change in the default firmware location usx2yloader assumes. I used to have the same error before I found the workaround, which is explained in [ this thread of mine]("http://ubuntuforums.org/showthread.php?t=734730").

The incremental change of the bus number is the normal behavior and nothing to worry about. The udev rule in [this thread for Feisty ]("http://ubuntuforums.org/showthread.php?t=431066") is still good for Hardy.

---

### Post by fxw1121 on 2008-04-29
The incremental change of the bus number is the normal behavior and nothing to worry about. The udev rule in this thread for Feisty is still good for Hardy.

---

### Post by altropianeta on 2008-04-29
...but I've discovered that I can't send private messages to anybody, here, because I'm a new user of these forums. So...

SFN shoud be the creator of the official wiki of Tascam US-122 soundcard under ubuntu. Please read the private message I was tryin' to send him. Here we go:

-------------------------------------------------------------------

Hi! Sorry for my English, I'm Italian. Please have a look at here: [https://help.ubuntu.com/community/TASCAM_US-122](https://help.ubuntu.com/community/TASCAM_US-122)

Are you the creator of this tutorial, right? Could you please update it? I think that under ubuntu 8.04 something has changed and the soundcard does not work with old tutorials... Neither with this one:

[http://alsa.opensrc.org/index.php/Tascam_US-122](http://alsa.opensrc.org/index.php/Tascam_US-122)

I'm not an expert, and I think that a new tutorial should be useful for a lot of people like me. Actually I've found a couple of threads about this matter... But something was wrong with me. Can you help me, please? Now the green light of my Tascam us-122 is on and if I open an mp3 file it does work, but I get no sound if I watch a Youtube video (I use Firefox)... And even when I log in the system I get no sound (you know, when you have to type your user name and your password, you should ear a beat of a tribal drum and whatever).

Thank you in advance.

Regards, 
Filippo

----------------------------------------------------------------------

If anybody of you has a suggestion for me I will be very happy... And let's hope that mr. SFN should read this post! 

;)

---

### Post by SFN on 2008-05-09
Hi. Just found this.

Although I am the creator of the original HOWTO, I don't use the US-122 anymore. Having said that, I would imagine that if anything changed it would only be the particular files to download. 

Beyond that, I can't really provide much assistance anymore.

---

