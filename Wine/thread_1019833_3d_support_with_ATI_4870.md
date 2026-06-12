---
title: "3d support with ATI 4870"
date: 2008-12-23
forum: Wine
---

### Post by ender1598 on 2008-12-23
I just put together a new system...  Intel i7 quad core processor and the Asus P6T Deluxe motherboard and the Asus 4870 ATI video card.  I'm running 64 bit Ubuntu 8.10.  Everything seems to be running fine except for the 3D aspect.  

I initially installed the drivers through EnvyNG and this allowed me to have my desktop cube and eye candy on the desktop with no problem.  But then I tried to run World of Warcraft and nothing would happen.  I uninstalled the EnvyNG drivers and tried the official drivers from ATI and those seemed to install fine.  I could run WoW but the login screen was very garbled.  I could see the places to enter the login/password and could read the notice on the left but the 3D was completely unrecognizable.  I then went to the desktop and tried to enable the highest level of visual affects under appearance.  This prompted me for a password to enable some drivers and I proceeded with this.  Now I've got these new drivers enabled and can have visual effects but WoW will once again not run.  

I guess my main question is if anyone else out there is running 64 bit Ubuntu 8.10 and an ATI 4870 has gotten World of Warcraft to run?  If so I'd love to know the details of exactly what drivers you used and what settings you had to play around with.

---

### Post by ender1598 on 2008-12-23
Okay I got some help from onetinsoldier in the ubuntu chatroom and he walked me through compiling the latest kernal properly and removing the other drivers.  Now WoW works almost perfectly...  just some small kinks to work out but it seems to okay in general.

---

### Post by earthforce_1 on 2009-01-02
So what was your secret advice?  I am building an ubuntu i7/940 system with a sapphire 4870x2 card, it would probably save me a lot of pain.

---

### Post by ap90033 on 2009-04-30
> **earthforce_1 said:**
> So what was your secret advice?  I am building an ubuntu i7/940 system with a sapphire 4870x2 card, it would probably save me a lot of pain.

Here is the secret: Post your question Jan 2nd (which you did), check back on APRIL 30th (today), now bring up a terminal and type /I am an ID10T for expecting an answer to this question.  :lolflag: 
Just kidding. I am like you in the same boat. Sounds like we have very similiar hardware and FYI, dont install ATI Drivers unless you like Ubuntu Garbled Edtion... LOL 

I wish I could help you and I both, I would.. I have spent Weeks trying to get this working....

---

### Post by ap90033 on 2009-04-30
Holy crap 4 months and no solution lol

---

### Post by asdfoo on 2009-05-01
seriously people, you are wasting your money buying ati cards and expecting them to perform as well as on windows.

if you want things to work with Wine then buy nvidia.

---

### Post by Dimarchi on 2009-05-01
Running 64-bit Ubuntu here (was 8.10, now 9.04), *with* Ati 4870 card. Here's how I managed to get the whole show working at least a little bit...

Hardware: Intel Quad 9650 3.00ghz, Asus Rampage Extreme, 4gb OCZ 1333mhz memory, Gigabyte 4870 1gb, two Samsung 640gb hard drives, Benq 24 inch LCD monitor (1920x1200 resolution).
Software: Vista 64-bit on one hard drive, Ubuntu on the other. WoW copied from Vista install, Config.wtf in WTF folder trashed (it will be recreated by WoW) or using the downloadable version (prepare for a very long session...did this for Vista since the original install discs were broken), Ubuntu version of Wine installed. Whenever I need to update Addons in the Interface folder I replace the whole folder...from whichever install I updated it first.

In Configure Wine, Graphics tab: Shader disabled (ticked off). No other modifications.

OpenGL is not used at any point: not in Config.wtf nor in the shortcut (wine path/to/wow.exe).

WoW settings: default, windowed 1680x1050 (plus some options off that I can't remember just at the moment).

Ati drivers from AMD's site, not the repository ones (drivers for 4870 did not exist in the before 9.04, and 9.04 repo version didn't work for me). Drivers updated as new ones became available...tested and if they didn't work, back to the ones that did work (9.2 for 8.10 in my case).

3.1 version of WoW brought its own complications, just as 9.04. Basically UI icons became garbled. SET UIFaster "2" in Config.wtf solved that for me.

Works for the most part, frame rate: single digit and up, mostly very low. Dalaran equals crash.

---

