---
title: "Game with low requirements running slow under wine"
date: 2009-08-10
forum: Wine
---

### Post by calsaverini on 2009-08-10
Hi, 
I tried to install the game Freelancer under wine. The installation was smooth but the game run VERY slow.

I suppose it shouldn't be so slow cause the specs for the game are well under my machine's capabilities even though I don't have a cutting edge hardware.

The specs recommended by M$ Games for this game are:

[LIST]
[*] 1 Gigahertz (GHz) or faster processor.
[*]256 MB of RAM.
[*]An 8x or faster CD or DVD drive.
[*]A 32 MB video adapter with a DirectX 9 compatible 				driver.
[/LIST]

I have a Turion TL-50 x2 1.6 GHz, 3Gb of RAM and a ATI Radeon X1200 (which is not great, but have way more than 32Mb of video memory).

I tried to install Cedega and it didn't recognized my video card in the diagnostics menu. 

I'm using Ubuntu Jaunty x86_64 with the default radeon driver (tried to install radeonhd with apt-get with no success - the system starts in the low graphics configuration because of some error).

---

### Post by spoons on 2009-08-11
It will be probably a combination of your slow graphics chip and the open source drivers lacking in completeness.

---

### Post by Nezin on 2010-03-17
This is a little late, but you need some windows files to make Freelancer run.  Here is a link to a forum on setting up Freelancer in wine.
[http://freelancercommunity.net/viewtopic.php?p=2466#2466](http://freelancercommunity.net/viewtopic.php?p=2466#2466)

Freelancer now runs fine for me after following the instructions.

---

### Post by asdfoo on 2010-03-17
It sounds like the original posters problem was that he had the wrong video driver installed.

---

