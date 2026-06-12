---
title: "One quick question - Please HELP! DESPERATE!"
date: 2008-02-28
forum: Windows
---

### Post by videocardsmakememad on 2008-02-28
Where do I find the "SmartGart" section or the AGP-speed or AGP-write section on my video card: ATI Radeon HD 2600XT PCIe?! Please help me! :confused:

---

### Post by igknighted on 2008-02-28
> **videocardsmakememad said:**
> Where do I find the "SmartGart" section or the AGP-speed or AGP-write section on my video card: ATI Radeon HD 2600XT PCIe?! Please help me! :confused:

Why do you need these?  Explain your situation a little more, like what you are trying to do (play a game, use compiz, get the drivers to work at all, etc.), and we can advise better.

---

### Post by Fred_E _krugar on 2008-02-28
First off it is PCIe  there is no agp stuff involved

---

### Post by videocardsmakememad on 2008-02-28
I need this because it will most likely fix my problem with the game "World of Warcraft" occuring with a freeze then a blackscreen. I found another topic in another forum saying the solution is to turn my AGP-Speed from 8x to 4x and my AGP-Write off under the SmartGart which is in the Graphic's Settings tree. But when I went to my ATI Catalyst Control Center for my ATI Radeon HD 2600XT PCIe, there was no "SmartGart" section. I just need to find that and turn my AGP-speed down to 4x and my AGP-Write off and my problems are fixed! Plx help. :(

---

### Post by Fred_E _krugar on 2008-02-28
Ok PCIe...............dont use AGP(accelerated graphics port)memory write speeds and the such.

I am sorry this is just the facts.

---

### Post by videocardsmakememad on 2008-02-28
Is there any way that I can disable PCIe Write or lower the speed of my PCIe-speed from 8x to 4x?

---

### Post by igknighted on 2008-02-28
> **videocardsmakememad said:**
> I need this because it will most likely fix my problem with the game "World of Warcraft" occuring with a freeze then a blackscreen. I found another topic in another forum saying the solution is to turn my AGP-Speed from 8x to 4x and my AGP-Write off under the SmartGart which is in the Graphic's Settings tree. But when I went to my ATI Catalyst Control Center for my ATI Radeon HD 2600XT PCIe, there was no "SmartGart" section. I just need to find that and turn my AGP-speed down to 4x and my AGP-Write off and my problems are fixed! Plx help. :(

These are settings in xorg.conf, and (I thought) more relevant to the radeon/ati drivers than fglrx.

Fire up your favorite editor (gedit/nano/vim/etc.) with sudo privileges (sudo nano /etc/X11/xorg.conf, for example).  Now scroll down to the Device section.  Add these two lines:
```
Option "AGPFastWrite" "0"
Option "AGPMode" "4"
```
then save/exit and log out/in

EDIT: backup your xorg.conf first, as you may break xorg by doing this

---

### Post by videocardsmakememad on 2008-02-28
Wait, igknighted I didn't get that, where do I need to go on Windows XP 5.1? O_O

---

### Post by igknighted on 2008-02-28
> **videocardsmakememad said:**
> Wait, igknighted I didn't get that, where do I need to go on Windows XP 5.1? O_O

?? Do you mean you want to fix your linux drivers from windows, or you are trying to fix a windows install?

If it's the first, you need a special driver to see linux partitions from windows.  If it's the later, you are in the wrong forums.

---

### Post by JoshuaRL on 2008-02-28
> **videocardsmakememad said:**
> Wait, igknighted I didn't get that, where do I need to go on Windows XP 5.1? O_O

That was the fix for Ubuntu, as you are on a Ubuntu Forum.  :p

There may or may not be anyone here who can help you with fixing XP.

---

### Post by uberlube on 2008-02-28
:lolflag:

---

### Post by igknighted on 2008-02-28
You can turn down the bus speed for AGP in your bios, I would guess you could do it with PCIE too...

---

### Post by videocardsmakememad on 2008-02-28
Ouch... No fix for this on a Windows XP? T_T Or I'm just incredibly stupid and not able to comprehend what you guys are saying... Hehe... /cry

---

### Post by igknighted on 2008-02-28
> **videocardsmakememad said:**
> Ouch... No fix for this on a Windows XP? T_T Or I'm just incredibly stupid and not able to comprehend what you guys are saying... Hehe... /cry

well... this is a linux forum, many of us do not use windows (xp or otherwise) at all.  You could ask a moderator to move this to the windows discussion section, you might find someone there.

---

### Post by videocardsmakememad on 2008-02-28
Wait, wheres my BIOS? I'm going nuts... Hahahaha... Been trying to fix this for over 2 weeks now.

Reinstalled WoW
Reformated
Updated all drivers and chipsets

No clue where BIOS is and how to access the AGP-speed and AGP-write from there and on... Hehe... Short explanation please? T_T

---

### Post by igknighted on 2008-02-28
> **videocardsmakememad said:**
> Wait, wheres my BIOS? I'm going nuts... Hahahaha... Been trying to fix this for over 2 weeks now.

Reinstalled WoW
Reformated
Updated all drivers and chipsets

No clue where BIOS is and how to access the AGP-speed and AGP-write from there and on... Hehe... Short explanation please? T_T

BIOS = Basic Input Output System... it's what is running when you first turn on your computer.  Hit either f2 or del (it should tell you a button to hit to enter setup).  But if you don't know what you are doing, you can damage things.  Ask a friend to help you out or take your computer to a PC shop.

[http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)

---

### Post by JoshuaRL on 2008-02-28
Okay, when the computer first boots up and it says for a few seconds the name of the computer/motherboard manufaturer, that is BIOS.  It means Basic Input Output System.  BIOS.  You can get into the BIOS settings by hitting one of the F-keys usually.  It'll say something like "Press F2 to go into Settings".

---

### Post by videocardsmakememad on 2008-02-28
Alright thanks, but where do I access the AGP-speed and AGP-write from there on? :) I'm finally going somewhere. Haha.

---

### Post by igknighted on 2008-02-28
> **videocardsmakememad said:**
> Alright thanks, but where do I access the AGP-speed and AGP-write from there on? :) I'm finally going somewhere. Haha.

Every BIOS is different, you would have to look around.

---

### Post by aysiu on 2008-02-28
> **igknighted said:**
> well... this is a linux forum, many of us do not use windows (xp or otherwise) at all.  You could ask a moderator to move this to the windows discussion section, you might find someone there.
I've moved the thread from Absolute Beginner to Windows Discussions. You're right, though--we can try to be helpful, but this is a Linux forum, not a Windows one.

---

### Post by Dr.Gringo on 2008-02-28
I hope u get somewhere with that since u seem to be in the wrong forums... maybe u would like to explain ur situation a little more explicitly.

---

### Post by videocardsmakememad on 2008-02-28
Ok, no problem, I'll continue this over there. :)

---

### Post by videocardsmakememad on 2008-02-28
No! Did igknighted and JoshuaRL leave?! They were my saviours! :(

---

### Post by JoshuaRL on 2008-02-28
I think we're still here, but I don't have the knowledge you seek.  If it was me, I'd go into BIOS and just look (**DON'T CHANGE ANYTHING**) for the AGP options you seek.  If you find something promisng, post back here.  We can* try*.

---

### Post by videocardsmakememad on 2008-02-28
Ok, going to BIOS now. Only looking for things related to AGP-speed or AGP-write or PCIe-speed or PCIe-write.

---

### Post by videocardsmakememad on 2008-02-28
Alright, I didn't find anything related to AGP / PCIe / PCI - write or AGP / PCIe / PCI - speed, the only thing I saw was Plug and Play O/S under PCIePnP or something that was relevant.

---

### Post by JoshuaRL on 2008-02-28
Well, doesn't sound like your BIOS supports messing with that.  Could you either take it to a shop or contact your manufacturer?  Or maybe Microsoft?  I'm seriously all out of ideas.

---

### Post by anewguy on 2008-02-28
First of all, as was mentioned several posts back, you have an PCIe card, so don't look for AGP anything - it won't do you any good.  I would suspect the "tip" you found was for a very specific problem and ONLY with AGP.

You would be far better served to find a Wow forum on the net and ask for help there.  Specifically, do a Yahoo! or Google search on your version of Windows, world of warcraft and forum, sort of like the following:

Windows XP world of warcraft forum

you will get MANY returns, and you stand a far better chance getting a reply there.

Also, there is a Ubuntu forum for just games and leisure - you may check there if you want:

[http://ubuntuforums.org/forumdisplay.php?f=93]("http://ubuntuforums.org/forumdisplay.php?f=93")


The main thing to keep in mind here and on the other Ubuntu forums is that Ubuntu is not Windows and they don't work the same.  Ubuntu is based on Linux, which is based in an operating system called Unix.  Please don't expect the people here to be able to answer many Windows questions - we are more interested in Ubuntu and providing grass-roots level support for it.

Good Luck! :)

---

