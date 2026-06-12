---
title: "(YACR2S) Yet Another Compelling Reason To Switch"
date: 2007-04-09
forum: The Cafe
---

### Post by elephant007 on 2007-04-09
I am a technician for a place that has over 5,000 computers.  Today I was dispatched to a lab that had 8 computers that had the same problems (all running Windows XP) an error windows popped up with "svchost.exe -- application error the instruction at 0x745f2780 reference memory at 0x00000000. the memory could not be read"

  Several of my fellow technicians insisted that it was a physical memory error and that I should change out the memory module, reluctantly I did and the error still occurred.  After further investigation I discovered that this error was a sign of a corrupted WGA Tool.  Now as most of us know WGA or Windows Genuine Authentication tool is Microsoft's way to verify that the operating system is a legit copy.  
  Long story short, I had to re-register 7 DLL's, stopped the Windows Automatic Update, rename the default 'softwaredistribution' directory, restart Windows Automatic Update, reboot the computer and then run the Windows Update manually.  What a PITA!!!!  Anyone else ran into this problem?

  This is yet one more reason to switch to Ubuntu.  
How many people have ever had problems with Update Manager corrupting their Ubuntu OS?  I know that Microsoft Updates jacks up their operating systems often... whether it be hardware or software, some updates jack up their own operating system... Thanks for allowing me to vent!

---

### Post by WiseElben on 2007-04-09
There have been several (or maybe just one, I don't remember) Ubuntu updates that destroyed system, but they were always quickly taken care of. What I hate the most about the Windows Updates is that it asked me to reboot every 5 minutes and I have to press "Remind me later" every time. Come on, I need to finish downloading my Ubuntu ISO first!

---

### Post by BarfBag on 2007-04-09
There have been several incidents with updates breaking Xorg.  However, I'm pretty sure these breaks were exclusive to users of the proprietary graphics drivers.  They aren't included out of the box, so cut 'em some slack.

At least with Ubuntu, you can drop into a virtual terminal and fix the problem from there.  With Windows, you have to find a way to graphically do it.  Indeed - a total PITA.

---

### Post by Sunnz on 2007-04-10
So the problem was with WGA, which if you like, is more or less an 'artificial' error... Xorg is needed for a desktop but WGA is pretty much junk that serves no technical purpose at all.

I guess that's what I like about Linux, code are written for technical purpose, not wasting CPU cycles for junk processes.

---

### Post by Polygon on 2007-04-10
only real thing was xorg dropping users of the nvidia closed source drivers to a terminal cause xorg failed to start... did not crash the system

and also some problem about the kernel not being packaged properly so it wouldent download... didnt cause any problems cause you couldent download it lol

but other then that in the year plus ive used ubuntu those are the only problems

---

### Post by LookTJ on 2007-04-10
I have gotten the exact same error popping up on startup.. that was months ago with a different pc...before our comp repair guy traded us one of his pc...he inserted our RAM from the our pc...so far to this present time...have no problems.

---

### Post by LookTJ on 2007-04-10
Forgot to say I think that was causing the blue screen of death.

---

### Post by beefcurry on 2007-04-10
Kernal Upgrades and X server updates have always broken my system, but thats just me using nVidia drivers. But that is still far less inoying then Windows Errors :P

---

### Post by samjh on 2007-04-10
> **elephant007 said:**
> How many people have ever had problems with Update Manager corrupting their Ubuntu OS?  I know that Microsoft Updates jacks up their operating systems often... whether it be hardware or software, some updates jack up their own operating system... Thanks for allowing me to vent!

The Ubuntu update manager has never *directly* crapped out my computer.  But there was a X and kernel update which broke my Ubuntu installation, and my computer was down for around a day.

On the other side of the coin, I've never had a problem with Microsoft/Windows Update either, in .... 5 years of usage.

---

### Post by Gargamella on 2007-04-10
> **WiseElben said:**
> There have been several (or maybe just one, I don't remember) Ubuntu updates that destroyed system, but they were always quickly taken care of. What I hate the most about the Windows Updates is that it asked me to reboot every 5 minutes and I have to press "Remind me later" every time. Come on, I need to finish downloading my Ubuntu ISO first!

Oh my god, it is frustrating if you are working or playing

---

### Post by jiminycricket on 2007-04-10
Did vesa still work for the proprietary Nvidia driver users?

---

### Post by Tuna-Fish on 2007-04-10
> **jiminycricket said:**
> Did vesa still work for the proprietary Nvidia driver users?

X wouldn't voluntarily switch to it, you had to make it do it.

---

### Post by elephant007 on 2007-04-10
Great responses.  As mentioned before, if Ubuntu craps out and you can at least get into a terminal session, more and likely you'll be able to repair the problem.  With Microsoft Windows, if you can't get into a GUI you're basically SOL.  Even with Ubuntu, couldn't you use the Live CD to fix problems?  Anyhow,  the Chief Technology Officer is toying with switching to some sort of flavor of Linux to run on our some 5,000 computers at least the Lab computers, not so much office computers.

---

