---
title: "Help me make the greener choice"
date: 2008-03-05
forum: Server Platforms
---

### Post by DevilWithin on 2008-03-05
Hi guys,
I want to put up a home server that will handle tasks easily yet is low in power consumption.  The expected number of users will most probably be under 3 at any one time.  I have basically two systems at my disposal.

System1:
P3-933
1G Ram

System2:
P4-1.6
768M Ram

I want to set up a server that mainly does the following:
- Samba
- Torrent
- amule
- VPN (possibly Hamachi to allow friendly connections)
- ftp
I may try to set up the following secondary functions in the future:
- Apache
- PHP
- MySql

I hear that P3 consumes much less power.  But does the power saving justify the sacrifice in CPU performance? And to be honest to myself, I guess I am fine as long as the server performs those task smoothly.

---

### Post by sancho panza on 2008-03-05
I'd suggest you move this thread to another category since its not a general, ubuntu desktop related question. Also, you might get a better response to ur query if you move it to another category.

---

### Post by DevilWithin on 2008-03-05
Sure, but which board should I move this to?  Not sure what category this question would fall under.

---

### Post by sancho panza on 2008-03-05
Maybe u could try the server section, hardware section or even the installation section.

---

### Post by Sef on 2008-03-05
Moved to Server Platforms.

---

### Post by dasunst3r on 2008-03-05
Just so you know, I am currently running a server with HTTP, SSH, MySQL, PHP, and FTP, and it is only using up 128 MB of RAM.  I think the P3 will serve you well.

---

### Post by Whiffle on 2008-03-05
P3 w/o a doubt.  My p4 is an energy hog...which is why it spends most of the time off.

---

### Post by MJN on 2008-03-06
I'd second (or should that be third?!) the P3 choice - I've got a similar machine running all that you've put, and more besides (mail server, centralised backup server, ZoneMinder CCTV system ...) without any problems.
 
The other bonus is that by virtue of it consuming less power it also creates less heat hence can be run near-silent with some attention to fans etc.
 
Mathew

---

### Post by FakeOutdoorsman on 2008-03-06
Try something like a Kill-a-Watt on a few of your friends computers and measure watts while the computer is off, idle, and doing something CPU intensive.  You can also measure killawatt hours and multiply it by your power rate to see how much it would cost you.  Here are some unscientific examples from my office (in watts, off/idle/CPU):

PII  400 MHz dev box: ?/35/46
P4 3 GHz: ?/96/156 (mine)
P4 3+ GHz: 9/138/216
AMD (don't have specs with me now): 5/140/200

And a monitor for no real reason:
Dell 20" 2005FPW: 1/41 white background/37 black background
The later model 2007WPF? uses about the same.

Look at the difference between the P4s.  Mostly due to number of hard drives.  The AMD also has a glutton of hard drives, about four or five I think, so these numbers aren't that helpful.

---

### Post by netlogic on 2008-03-07
If you want to go green, AVOID P4 at ALL COST!
P4 uses twice the power of Sempron and 46% more than most Core2DUO!  P4 is almost power hungry as the server processor line platforms. The lowest watt processors that can be used for home servers are Celeron 215 and 220. I believe they idle at 5w and max at 25w. 215 is only 32bit at 1.33ghz and 220 is 64bit at 1.2ghz. P4 sucks up enough power even at idle.

---

### Post by Whiffle on 2008-03-07
Yeah my p4 sucks about 96 watts at idle, 120 at full load (1.6Ghz).  yeaaah....

---

### Post by netlogic on 2008-03-07
Yea, P4 is pure evil, but I do love Core2DUO. Twice the power at half of the energy cost. Intel has also gone very green by bringing back Celeron and making more efficient. I ordered a Celeron 220 board in order to replace the existing home server. It will pay for itself within 2yrs with the energy saving. It feels good to save the planet and save some pocket money.

---

