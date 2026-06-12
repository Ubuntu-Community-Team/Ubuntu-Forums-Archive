---
title: "Has the 9.10 Koala eaten your intel graphics resolution?"
date: 2009-12-16
forum: The Cafe
---

### Post by SonicSteve on 2009-12-16
Yes as the title says,

I've now tested Koala on 6-10 different systems. Some being quite old P3 systems and some very new Intel based G41 based motherboards. From Intel, ATI, Nvidia, to SIS based systems. 

The systems that have an Intel graphics chip onboard have been very hit and miss. 
845 OK
865 OK
900 series bad
G3100 OK
x4500 bad.

Interestingly though the 3D capacity of the Intel chip is functional but the resolution is stuck at 800x600 with no easy fix found yet. 

SO... has the Koala eaten your Intel graphics also? What has been your experience? If you have Intel graphics I would love to know what chipset you have and if your resolution is broken.

---

### Post by Psumi on 2009-12-16
Intel 945 GM (Gateway MX Series)

Good experience to be honest, everything but blur was good in compositing, and, I could set the resolution higher than 800x600 out of the box with Ubuntu 8.xx. I don't have the laptop anymore, so I cannot test it with 9.10.

---

### Post by SonicSteve on 2009-12-16
> **Psumi said:**
> Intel 945 GM (Gateway MX Series)

Good experience to be honest, everything but blur was good in compositing, and, I could set the resolution higher than 800x600 out of the box with Ubuntu 8.xx. I don't have the laptop anymore, so I cannot test it with 9.10.

That's good to hear, Though I'm a bit surprised. 

One of the chipsets more specifically I've noticed is the 915. It's on an Intel Asus p5gv-mx board. It worked under previous versions quite well. Now with Karmic it's unusable until I can find a fix. Same for the x4500 on p5g41-m boards.

---

### Post by cariboo on 2009-12-16
I've got an atom powered motherboard with a 945 graphics chipset. I've connected it to three different monitors, 17" crt, 19" crt and 32" HD LCD, and it automagically set the correct resolution for each one. I've got full effects enabled.

Running Karmic upgraded from Jaunty.

---

### Post by hobo14 on 2009-12-17
945, 9.10 didn't automatically offer the resolution I wanted (1440 x 900), had to search for a fix.

---

### Post by treesurf on 2009-12-17
Karmic was a big step up from Jaunty for my Intel 4500MHD.

---

### Post by Grenage on 2009-12-17
A lot of Intel GFX users are having a problem with getting the correct res in 9.10.  Modelines in xorg.conf sort most of them out.

---

### Post by SonicSteve on 2009-12-17
I really hope this is mostly resolved for 10.04, Intel graphics have suffered alot recently. Not by any stretch are they the best but they are very prevalent in laptops and onboard desktops. 

I'll try the modelines and see if this makes the difference. I tried creating a xorg.conf file so at least that is done.

I added a poll, you can choose multiple options in case you have had varying experiences.

EDIT
I just installed Karmic 9.10 on the Asus p5g41-m (Intel x4500) machine again, during the Live session before installing I noticed that the resolution was working. I have a new theory on this. The only difference between this install and the last time was that previously I had the computer connected with a Dlink KVM (Keyboard, Video, Mouse) switch. Perhaps certain Intel chips don't detect Monitors well through a KVM. To test this I started the Asus P5GV-mx system (intel 915 chip) without using the KVM, this didn't yield any better results. 
I will soon test that system with a different monitor to see if Karmic simply doesn't like the monitor for some reason. Perhaps is plug and play communication is strange.

EDIT AGAIN, NEW INFO

It seems that some monitors are not detecting well. I have 2 monitors on my workbench.
1. through KVM a Gateway EV700
2. A dell m782p 

Karmic seems to not like the Gateway monitor. Both of my installations have detected the Dell pefectly.

This is the first time I've seen Ubuntu have trouble with my Gateway monitor.

---

### Post by SonicSteve on 2009-12-17
> **cariboo907 said:**
> I've got an atom powered motherboard with a 945 graphics chipset. I've connected it to three different monitors, 17" crt, 19" crt and 32" HD LCD, and it automagically set the correct resolution for each one. I've got full effects enabled.

Running Karmic upgraded from Jaunty.

I've been curious how about how well Ubuntu installs on these kinds of systems and what kind of performance you get. The horse power at first glance seems comparable to a 4-5 year old laptop. I have an old Compaq 1.5ghz centrino laptop. I have to turn Compiz off in order for it to not lag. I can't offhand remember the chipset it uses other than an older Intel.

---

### Post by SunnyRabbiera on 2009-12-17
My intel 915 GM card works better with karmic then it did in jaunty.

---

### Post by SonicSteve on 2009-12-17
It seems that the monitor you use has a great deal to do with detecting resolution, I never thought that a monitor could have incompatibilities but it seems true. The poll seems to indicate this as well as my own testing. When I started out this never entered my consciousness.

---

### Post by Grenage on 2009-12-17
It's down to whether the proper protocols are able to work, and the monitor cable itself has a lot to do with it.

---

### Post by blackened on 2009-12-17
> **SonicSteve said:**
> It seems that the monitor you use has a great deal to do with detecting resolution, I never thought that a monitor could have incompatibilities but it seems true. The poll seems to indicate this as well as my own testing. When I started out this never entered my consciousness.

My first question was going to be whether or not you were testing these rigs on the same peripheral hardware, but you seem to have figured that part out now. Ubuntu can only offer appropriate resolutions if your monitor correctly reports its EDID to the system.

I have a 22" KDS that has never been recognized correctly, however my old 17" KDS was picked up every time. Even using the same cable.

---

### Post by SonicSteve on 2009-12-18
Ok so a little more,

In my upgrading of machines I put my old 9.04 Hdd into a 915 chipset box. Attached the Gateway monitor and yessiree! It detected the old Gateway perfectly.

9.10 has indeed introduced some incompatibility into monitor detection. It doesn't seem to be very prevalent but it does seem to be happening.

---

### Post by cariboo on 2009-12-18
> **SonicSteve said:**
> I've been curious how about how well Ubuntu installs on these kinds of systems and what kind of performance you get. The horse power at first glance seems comparable to a 4-5 year old laptop. I have an old Compaq 1.5ghz centrino laptop. I have to turn Compiz off in order for it to not lag. I can't offhand remember the chipset it uses other than an older Intel.

The system has never had Windows installed on it, so I can't say how the performance is there, It has had Intrepid, Jaunty and is currently running Karmic. 

For what the system was designed for, it works perfectly. I use it for watching ripped DVD's, and tv shows recorded on my dvr, plus playing music from my collection.

This past weekend I was showing some family members some youtube vides in HQ at full screen, and I was really happy with the performance.

As far as monitor detection goes, I also use a D-Link KVM in my shop with a KDS VS-190 19" crt. I've found that monitor detection seems to be pretty hit and miss on occasion, depending on which version of Windows, or which distibution I'm running, as well as what hardware is being used.

---

### Post by SonicSteve on 2009-12-18
> **cariboo907 said:**
> The system has never had Windows installed on it, so I can't say how the performance is there, It has had Intrepid, Jaunty and is currently running Karmic. 

For what the system was designed for, it works perfectly. I use it for watching ripped DVD's, and tv shows recorded on my dvr, plus playing music from my collection.

This past weekend I was showing some family members some youtube vides in HQ at full screen, and I was really happy with the performance.

As far as monitor detection goes, I also use a D-Link KVM in my shop with a KDS VS-190 19" crt. I've found that monitor detection seems to be pretty hit and miss on occasion, depending on which version of Windows, or which distibution I'm running, as well as what hardware is being used.

That's quite interesting, to this point I have only encountered once where Windows was unable to set the resolution I wanted. It was a cheesy SIS graphic chip and it's bios was simply unable to do widescreen. I guess it was old enough that 4x3 was the only thing conceived of. 

With my latest experiment with Ubuntu though a system running 9.04 was able to detect the Gateway correctly, but that same system running 9.10 couldn't. I made sure the KVM was out of the mix.

---

### Post by DougieFresh4U on 2009-12-18
I got out my old  desktop that hasn't been used for over a year. Has the 865 chipset and when I installed (dual boot) Karmic and Lucid the other day (also the .33 kernel) I was shocked at how well it responded to the install. It gave me 1280x1024 res and compiz is working well.  I didn't have to 'tweak' any thing.  Working great here.

---

### Post by cariboo on 2009-12-19
> **Grenage said:**
> It's down to whether the proper protocols are able to work, and the monitor cable itself has a lot to do with it.

+1, I have a couple of generic monitor cables connecting my media center pc to my HD LCD Tv, with only one cable it isn't detected  properly, when daisy chaining the two cables the monitor is detected and the resolution is set properly.

---

### Post by kerry_s on 2009-12-19
mine would freeze as soon as it got to the desktop, turning effects off is the fix, but you can't fix it when it's frozen, catch 22.  :lolflag:

i just wish it was the old way where you turned on effects if you wanted it, not by default. :(

---

### Post by Psumi on 2009-12-19
> **kerry_s said:**
> mine would freeze as soon as it got to the desktop, turning effects off is the fix, but you can't fix it when it's frozen, catch 22.  :lolflag:

i just wish it was the old way where you turned on effects if you wanted it, not by default. :(

+1, my IBM computer is too slow to use compiz graphics, so it should be disabled by default. At least I can fix it though. :|

---

