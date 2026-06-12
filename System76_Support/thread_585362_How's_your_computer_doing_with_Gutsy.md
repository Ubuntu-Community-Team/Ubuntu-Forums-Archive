---
title: "How's your computer doing with Gutsy?"
date: 2007-10-21
forum: System76 Support
---

### Post by greg_g on 2007-10-21
Hello all of you System76 owners!

I have been watching the posts by people upgrading their computers to gutsy, sometimes flawlessly, sometimes with a couple issues.

I thought it would be nice for those customers who haven't already upgraded to get an idea of what to expect.  What I propose is for everyone who has upgraded their System76 computer to Gutsy to post some information about it.  

**This thread isn't for support, so just list the problem.  For support issues it is best to either open a new thread or email Tom (support-at-system76-dot-com).**

If there is a bug report already associated with an issue, please post it.

This isn't a thread just for problems either, the most important posts will come from those who's upgrade worked well.
[B]
Please work with this format[/B]
System Model: (eg: daru2) (System->Administration-Systme76 Driver-> "System Model")
Upgrade method: (Upgrade-Manager or clean install)
Graphics work? (Yes/No, if No, what doesn't work)
Wireless work? (Yes/No, if No, what doesn't work)
Sound work? (Yes/No, if No, what doesn't work)
Suspend? (Yes/No, if No, what doesn't work)
Hibernate? (Yes/No, if No, what doesn't work)
Something else?

**Also, if something changes, please edit your post instead of adding another, just so things don't get confusing.**

Thanks everyone!

---

### Post by palintheus on 2007-10-21
System Model : daru2
Upgrade Method : Update Manager (internet)
Graphics : Yes
Wireless : Yes, still will not recognize ethernet cable unless booted with it plugged in
Sound : Only on 2.6.20* kernel
Suspend : Yes
Hibernate : not tested

Power management is still buggy. I seem to have ridded myself of the blanking, I have changed the power management to nothing where ever it said blank screen. I have a message pop-up when I log in about my X settings being different than my GNOME settings in regards to my keyboard, haven't looked into it though. I cannot configure my touchpad, when I select it in System > Preferences it says "GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

I think thats it so far.....will update as it changes

====EDIT====

System Model : daru2
Upgrade Method : Clean Install (Alternate CD)
Graphics : Yes
Wireless : Yes, now recognizes when ethernet cable is plugged in, does not need to be plugged in on boot
Sound : Worked after install reboot, installed and ran Sys76 Drvier and now sound will not work
Suspend : Yes
Hibernate : Yes

Still have the pop-up about the keyboard settings, and still cannot configure my touchpad. Will check screen blanking, and power management

====EDIT====

Edited my xorg.conf changed the keyboard from *105 to *104. This stopped the pop-up about the differences in the X and GNOME settings.

====EDIT====

I reinstalled again (almost feels like Windows) because sound is very important to me. Now suspend and hibernate will not work, these are minor, but I would like them to work (in some way). I have not ran my System76 driver, nor have I installed it. It broke my sound and for the daru2 sound works natively under Gutsy.

---

### Post by GregCwx1 on 2007-10-21
Per Greg_g's request to follow the format of his original post, here's the deal...

System Model: daru2

Upgrade method: Upgrade-Manager via the net

Graphics work? Not like they used to. It seems I'm stuck with 1280x800 screen rez. I used to be able to go to a higher virtual vertical resolution (1280x1000?) but the system doesn't seem to know about my screen or video h/w now. 

Wireless work? Haven't tried yet. will update later. Wired does work.

Sound work? Yes

Suspend? Got the lid-close/open to work again after reading this thread: [http://ubuntuforums.org/showthread.php?t=582294](http://ubuntuforums.org/showthread.php?t=582294) However, after coming out of lid close the system kept dimming the screen and
going back into lock-out! Not good. Power management seems as shaky as ever!

Hibernate? Haven't tried yet. It worked great before the "upgrade". I'll let you know.

Something else? It seems that booting into Ubuntu 7.10, kernel 2.6.20-16-generic instead of the default Ubuntu 7.10, kernel 2.6.22-14-generic keeps the entire system a bit more stable. However, I'm tempted to go back to Feisty if I can't change resolution and get around the video issues with compviz.

Here's my original post. Sorry for not following the posted guidelines!

Just upgraded to Gusty with a few errors but overall system appears
stable. I reinstalled the the system 76 driver ver. 2.2.1 on my darter ultra.
However, Gnome destop-effects now fails to work. The error I'm getting is

No nvidia hardware available
Checking for Xgl: not present.
Blacklisted PCIID '8086:2a02' found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

This used to work in ubuntu 7.04 on this laptop. Any help would be appreciated. Thanks!

---

### Post by palintheus on 2007-10-21
.

---

### Post by Zxaos on 2007-10-21
Model: PanV3 - complete new install (not upgrade)

Problems:
Sound doesn't work, even after running sys76 driver
WOW Audio and WOW Video hotkeys do not work
Deskop Effects don't work unless you override blacklisting (and then you have to change how gstreamer renders video to make it work)
Laptop-Lid closing doesn't lock the screen without some editing of gconf

Improvements:
Banding issue is gone (true 24-bit colour now, no dithering)

---

### Post by osx424242 on 2007-10-21
System Model: panv3 (Pangolin Value)
Upgrade method: Upgrade-Manager (took several hours but worked without a hitch)
Graphics work? The banding problem is fixed in Gutsy. Visual Effects don't work but I don't care so I haven't investigated. I can change resolution without the X Server crashing, but I fixed that in Feisty a week before the Gutsy upgrade, so I don't know if it works only because of the hint I used, or if the Gutsy upgrade would also have fixed it.
Wireless work? Yes.
Sound work? Yes.
Suspend? Haven't tried / don't care.
Hibernate? Haven't tried / don't care.
Something else?
CD-ROM works after some work, see [http://ubuntuforums.org/showthread.php?t=584100](http://ubuntuforums.org/showthread.php?t=584100)
SD card reader works (didn't in Feisty), hooray!
Printer (Canon Pixma iP3000) worked as soon as I plugged it in (I never tried with Feisty).

---

### Post by happyisland on 2007-10-21
I use a Sable at work for email and web and the upgrade went flawlessly. I've NEVER had an OS upgrade be so easy.

---

### Post by cwej on 2007-10-21
System Model: PANv3
Upgrade method: First Upgrade-Manager, then clean install, then retrograde restore to 7.04, then Upgrade-Manager again)
Graphics work? (Yes)
Wireless work? (Yes)
Sound work? (Yes) -- no at first, then got to work after installing Driver v2.1.1 
Suspend? (Yes)
Hibernate? (Yes)
Something else? -- Will not mount CD/DVD Drive when inserting CD (hear it spin, can select by f12 for booting, but will not mount when inserting CD in drive-- still working forums, hoping for new driver to fix -- next step will be to ask for direct support via email...

---

### Post by steveneddy on 2007-10-22
System Model: Serval Performance Type 1 - Core 2 Duo, 2Gig RAM
Upgrade method: Upgrade-Manager (upgrade-manager -d)
Graphics work? Yes (nVidia)
Wireless work? Yes - Intel
Sound work? Yes
Suspend? Yes
Hibernate? Not yet - having problems

:popcorn:

---

### Post by jerry47 on 2007-10-22
System Model: Serval Performance Type 2 - Core 2 Duo, 1Gig RAM
Upgrade method: Upgrade-Manager 
Graphics work? Yes (nVidia)
Wireless work? Yes - Intel
Sound work? Yes
Suspend? Yes
Hibernate? Yes

---

### Post by jhofmann on 2007-10-22
System Model: PANv1 System76 Driver v2.1.1
Upgrade method: Upgrade-Manager 
Graphics work? Yes
Wireless work? Yes
Sound work? Yes
Suspend? Yes
Hibernate? No
    Or maybe I just don't know how to work it.  I get the login box
    again, and the machine doesn't stop.
Something else?
    No console screens (Ctrl-Alt-F1-F6) This is a serious setback for
    me.

    Card reader still doesn't work.  Never has.

I don't think the blank consoles is a System76 issue, but the hibernate and card reader issues definitely are.

---

### Post by mstager on 2007-10-22
System Model: gazv1

Upgrade method: Upgrade-Manager

Graphics work? Yes but getting second/external monitor to work takes some playing around with and primary and secondary monitor alway seem to get the same resolution setting.

Wireless work? Yes

Sound work? Yes

Suspend? No, goes into suspend fine. Coming out there is some disk activity but is stops fairly quickly. nothing on screen, keyboard/mouse not functiona, wireless appears to stay powered off (from looking at led on case)l. must do hard reboot

Hibernate? Yes

CPU Frequency Scaling? No, message saying not supported but worked in Feisty

---

