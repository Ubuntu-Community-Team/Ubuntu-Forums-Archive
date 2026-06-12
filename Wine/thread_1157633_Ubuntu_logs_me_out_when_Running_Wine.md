---
title: "Ubuntu logs me out when Running Wine"
date: 2009-05-12
forum: Wine
---

### Post by Ravernomina on 2009-05-12
When i try to run Age of mythology in ubuntu it will fully load and ill here a little bit of the sound from the game. Then my screen will turn black and im back to the ubuntu log-in page THIS HAPPENS EVERY TIME, IM REALLY UPSET RIGHT OVER THIS!!! could some 1 please give me a solution to this cuz im totally confused and enraged right now

---

### Post by Ravernomina on 2009-05-12
Bump!

---

### Post by Ravernomina on 2009-05-12
Bump

---

### Post by TransitMan on 2009-05-12
You might want to look at your hardware for possible problems, like the memory or video card failing.

Further, is this the only time that Ubuntu does this, or are there other programs that this happens on?

---

### Post by Ravernomina on 2009-05-12
1 i got this game to run on windows along time ago before DirectX 9 and 2 it has low hardware requirements and ubuntu only does this on this app.

---

### Post by TransitMan on 2009-05-13
Take a look at this site - [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1979](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1979)
According to it, you should have no problems running your game in WINE.

Which version of WINE are you using to play this game?

---

### Post by Ravernomina on 2009-05-13
the recommended verson

---

### Post by TransitMan on 2009-05-13
You might want to head over to the WINE forums - [http://forum.winehq.org/viewforum.php?f=2](http://forum.winehq.org/viewforum.php?f=2) and search and/or pose your questions there, as someone there may be able to help you with a better direction to look in.

---

### Post by hikaricore on 2009-05-13
This is video related.

What hardware/driver do you have?

---

### Post by Altay_H on 2009-05-14
I don't think this issue is hardware-related. I have both Jaunty Jackalope and Intrepid Ibex, both running WINE v1.1.21. Intrepid Ibex can run Age of Mythology, but it freezes after playing about 5 minutes. I can switch to a virtual terminal, but I usually just run "sudo reboot" from there. Intrepid Ibex logs out as soon as the video sequence ends after launching the game. This issue is Jaunty-specific.

---

### Post by Ravernomina on 2009-05-15
well i got it to work. I left 64 bit and pathced some DLLs.

---

### Post by Altay_H on 2009-05-15
> **Ravernomina said:**
> well i got it to work. I left 64 bit and pathced some DLLs.
Could you please be more specific? I'm running 32 bit. Which DLLs did you patch? What did you patch them with? Thanks for your help.


EDIT:
By the way, when Ubuntu logs me out I first see a console screen which says something along the lines of
```
/dev/sda:
Setting Advanced Power Management level to 0x80
```
Does this happen to you too, or are you immediately logged out?



EDIT:
A system update (including an update of wine) solved my problem. I'm still interested in which DLLs you patched though. Also, have you figured out how to get Age of Mythology to sit above the GNOME toolbars? The intro cinematics display perfectly and are above the toolbars, but once the game begins the toolbars are on top.



EDIT:
Well, I thought the system update fixed the problem, but I guess Age of Mythology just coincidentally worked twice in a row after the update, because the problem is back. I've found a temporary fix though. If you press Ctrl+Alt+[right] to switch screens partway through the first intro cinematic you won't be logged out. It's a strange solution, but it works consistently for me.

---

### Post by psihokiller4 on 2010-10-17
simular problem here how did you solved? I don't get it
witch dll s did you pached and how

I can run game cultures but I can't play when I click to play button it logs me off

---

### Post by Altay_H on 2010-10-17
[quote=Altay Hunter]
[quote=Jim Hill]
[quote=Altay Hunter]
[quote=Jim Hill]
[quote=Altay Hunter]
[quote=Jim Hill]
[quote=Altay Hunter]
I'm surprised this still has yet to be mentioned here, but Age of Mythology Gold on Jaunty Jackalope has a strange issue. The video sequence works, but as soon as it ends the user is logged out and ends up at the login screen. Skipping the video sequence (either by modifying the launcher to skip the video or by pressing Esc during the video) causes the user to be immediately logged out. The only times I've gotten past the video sequence are when I pressed Ctrl+Alt+Right to switch workspaces during the video sequence. This does not always work, but without doing it Age of Mythology never works. Once I've gotten past the video sequence the game runs without issues. 

This sounds like a problem that's user-specific, but I've had this problem on multiple computers running Ubuntu 9.04. Has anyone gotten Age of Mythology to work in Jaunty Jackalope, or at least encountered the same problem I have? Does anyone have any suggestions? I'm currently just hoping that a newer version of Wine or Ubuntu will eventually solve the problem.
[/quote]
Here's my ~/bin/aomx, which fixes the logout issue and the failure to switch to fullscreen under compiz for me on karmic + wine from git: 

#!/bin/sh 
cd "$HOME/.wine/drive_c/Program Files/Microsoft Games/Age of Mythology" 
metacity --replace & 
sleep 1 
wine aomx.exe +noIntroCinematics ${1+"$@"} 
wait $! 
sleep 1 
compiz --replace & 
xrandr -s 1280x1024 

aom is the same with the obvious edit. I still need the no-cd crack to get aomx to run, but both games run beautifully, the only winetricks you need are mfc42 and msxml4: 

$ mv .wine .wine-preserve 
$ winecfg # to set up sound 
$ winetricks msxml4 mfc42 
$ # install the game 
$ # install the nocd for aomx 
$ # install the above scripts 
$ aomx 

Hope that works for you on jaunty+1.1.32. 

the games do crash on exit but with no apparent ill effects.
[/quote]
I tried the script that you gave (without the winetricks) and it solved the logout issue. About the winetricks, do I need to uninstall the game, set the winetricks, reinstall the game, and re-apply the nocd patch in order to get it to work? That's a decent amount of work, so I can't try it out immediately, but if it works for me I'll be eternally grateful to you. Thanks so much!
[/quote]
How close to my setup you have to get I don't know, I did the wipe to be sure I wasn't posting instructions that depended on cruft. 

If the game runs at all I think that means you've already got mfc42 and msxml4 installed so the winetricks part is done. 

Since this solved the logout and fullscreen issues, what's left that doesn't work?
[/quote]
It starts up with an error box telling me that the sound won't work. Then it loads the main menu, but it renders very slowly and the water doesn't render correctly. I didn't try clicking any options other than Exit because of how slowly it was running. To sum up: 
1) Sound doesn't work 
2) Water doesn't work 
3) Runs slowly (probably due to sound/water problem) 

There were a whole bunch of errors displaying in the terminal when I ran the script. I think the first ones were ALSA related. I can post the errors if they'd be helpful.
[/quote]
This is getting beyond my competence with wine, but yeah, I'd say do the clean install to be sure you're not getting interference from cruft. I know I had to install a lot of winetricks and keep ubuntu's 1.1.20 to get Rise of Nations working completely, and that setup produces horrendous results with aom. So I have multiple wineprefixes and my ron script includes PATH=~/debs/wine_1.1.20/usr/bin:$PATH and WINEPREFIX=~/.ron. ron works great with compiz btw. 

If it's worth putting any time into getting this working I'd say getting all karmic would be good too. Nothing dramatic, it just ... feels better. 

I've got a cheapie nvidia 9500 and onboard ATI audio, wine's set up for alsa with 44100/16/full hardware accel, I know the wine guys don't like pulse and I used to need to do things like padsp audacity, but I don't have to do that anymore. I told nvidia to sync to vblank. That's about all I know that might be relevant here.
[/quote]
I reinstalled on one of my computers with Jaunty Jackalope and it's working perfectly. Thank you very much. 

On my other computer I have Karmic Koala and I'm running into an issue that's preventing Age of Mythology from launching. The following error prints out in the terminal from which I try to run the aomx script: 

X Error of failed request: BadRequest (invalid request code or no such operation) 
Major opcode of failed request: 135 (GLX) 
Minor opcode of failed request: 19 (X_GLXQueryServerString) 
Serial number of failed request: 545 
Current serial number in output stream: 545
[/quote]
This is directly from [WineHQ](http://appdb.winehq.org/objectManager.php?sClass=version&iId=5323). It only worked for one of my computers.

The logout issue is caused by X crashing. It's a graphics card issue. Turning off Compiz may fix it.

---

### Post by YokoZar on 2010-10-17
Please avoid forum necromancy (bumping long-dead threads), you most likely have a new issue.

Regardless, crashing X (causing logouts, complete freezes, or reboots) is not something Wine or any user application should be able to do.  It's not a bug in Wine -- Wine is exposing some deeper problem in the system.  This means video drivers, or occasionally a kernel or X bug.


So, what video card do you have?

---

### Post by psihokiller4 on 2010-10-23
```
military@dusanlaptop:~$ sudo lspci
[sudo] password for military: 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
```


and ubuntu 9.10 LTS(Long Term Support)as I tried newer ones and I always had problems

or maybie I need to change kernel witch I've never tried

---

### Post by Rytron on 2011-07-17
I play 'Volvo The Game' in WINE and notice that sometimes when I exit the game, it logs me out of GNOME. The game runs perfectly otherwise.

---

### Post by Altay_H on 2011-07-17
> **Rytron said:**
> I play 'Volvo The Game' in WINE and notice that sometimes when I exit the game, it logs me out of GNOME.
This probably means that X is crashing. It's likely a problem with the graphics card driver.

---

### Post by Rytron on 2011-07-17
> **Altay_H said:**
> This probably means that X is crashing. It's likely a problem with the graphics card driver.

Is there a solution?

---

### Post by Altay_H on 2011-07-18
> **Rytron said:**
> Is there a solution?
Try running metacity instead of compiz (under Appearance choose None). That's the only solution that has worked for me. You could also try using a different graphics card driver, if there is one available.

---

### Post by Rytron on 2011-07-18
> **Altay_H said:**
> Try running metacity instead of compiz (under Appearance choose None). That's the only solution that has worked for me. You could also try using a different graphics card driver, if there is one available.

Cheers Altay_H. I will try that. BTW this is [image attached] the driver that I use as it was marked recommended. Which of the other 2 would be better?

---

### Post by Altay_H on 2011-07-18
> **Rytron said:**
> Which of the other 2 would be better?
Try them both and see if either of them prevents the crash from occurring. It's likely that it will occur on all three versions, but it's worth giving each a try anyway.

---

### Post by Rytron on 2011-07-18
> **Altay_H said:**
> Try them both and see if either of them prevents the crash from occurring. It's likely that it will occur on all three versions, but it's worth giving each a try anyway.

Thank you Altay_H. I will first try metacity and then perhaps the 2 other video drivers.

---

### Post by Rytron on 2011-07-21
> **Altay_H said:**
> Try them both and see if either of them prevents the crash from occurring. It's likely that it will occur on all three versions, but it's worth giving each a try anyway.

I tried metacity and I was logged out on my 3rd game. If I run the game in a window either via Wine config or via 'Volvo The Game' Config.exe I get no auto log outs. Would hz or vsync have anything to do with this? I am reluctant to change my video driver as I know of no other problem with any game and changing the video driver may bring new problems.

---

