---
title: "Small bugs"
date: 2013-04-22
forum: Ubuntu Development Version
---

### Post by Dark_Horizon on 2013-04-22
Right at this time when I use the software updater, I get the message unable to contact server with a try again option when I click ok the updates if any then appear. I'm not getting any error reports. when I load some pages in firefox the whole computer freezes for a second or two then jumps the page forward.
Even on induced crash reboot I don't get any error reports which leads me to believe the error report system is broken, is there any way of sorting that out?? Essentially this is the biggest problem since I can't publish any fault information for anyone to look at here, in order to get any help. I've looked through the sys logs but there does not appear to be anything I can otherwise publish that would be helpfull. Anyone got any ideas, I can publish the sys log if you think it will help.

---

### Post by dino99 on 2013-04-22
the workaround is to use the well ironed apt-get and/or synaptic
the other tools are still buggy and give erratic warnings/errors (probably due to index and/or events syncing)

---

### Post by Dark_Horizon on 2013-04-23
Thanks, I tried that and it worked on my PC and laptop both of which were getting the same error.  
 

 However, today&#8217;s glitch list grows ever larger Still, getting freezes on the desktop graphics. I can't get left click or any click menu's at times on both; a log out and in solves it temporary. There are clearly some big graphics issues , still no error reports for the graphics. Though my Laptop did say that aisolitair had crashed and would I like to relaunch. I get hangs and full graphics corruption on some of the interfaces which requires a reboot, for something about to be released on an unsuspecting public it has more bugs than MI5 I would hope that they put the release date back this is clearly in no state to be released beyond Beta in two days time. I've used Beta's before but nothing that comes close to this for Bugs. They Expect 14.04 t be the big convergence, some hope more like converging on a black hole if this is anything to go by.

  	 	 	 	   
Sorry for going on but it's frustrating not knowing what's going on, there are simply hundreds of these entries in the syslog

 

 &#8220; kernel: [ 3053.315341] nouveau E[   PFIFO][0000:02:00.0] CACHE_ERROR - Ch 2/0 Mthd 0x0000 Data 0x6b000000&#8221;

---

### Post by dino99 on 2013-04-23
which is your graphic card/chipset ?
are you using some ppa(s) ?

purge then reinstall xserver-xorg-video-nouveau

---

### Post by Dark_Horizon on 2013-04-24
Nvidia C77 Geforce 8100 /nforce 720a and am currently not using any proprietary drivers  X.Org X server Nouveau display driver.

Last time I used one of the proprietary drivers I could only get 1280x1024 rez which was useless since I have a 22 inch 16:9 1920 x1080 screen and it resulted in a full reinstall.

   **Today's glitch****es****!** My laptop Compaq Presario with 1.3 ghz processor and 1 gig of ram using 13.04, when I copy and paste more than a couple of files or documents the mouse pointer goes inactive one can move it around but that&#8217;s all, one can't click on links or shortcuts or menu's. one has to log out and back in to get it to work again? no error report. 

On the PC I get scroll hangs with the screen while scrolling documents or web pages its just momentary but annoying.

---

### Post by Dark_Horizon on 2013-04-24
Jeebuzz I should rename this bleeding big bugs
 

 I just thought I would try one of the proprietary drivers a tested and trusted Nvidia C77 Geforce 8100 /nforce 720a.
 

 Squeak squeak went the terrified mouse as it watched its unity and compiz fall off the abyss, after the initial panic I thought restart Unity and compiz a few flashy screens later and things were worse so I reverted my driver to the X.org one rebooted things went ok but no compiz no unity try the restart again Hmmm things are not looking good I thought at this point. Now I had the sense to have previously installed Cairo Dock so I had access to all my applications, after a whole 10 min searching I realised all this restart thing is not working compiz may be broken.... so I did this to remove compiz
 [TABLE]
[TR]
[TD]sudo apt-get remove compizconfig-settings-manager 
sudo apt-get remove compiz-fusion-plugins-extra
 sudo apt-get remove compiz-plugins-extra 
sudo apt-get purge compiz*         [/TD]
[TD="width: 1"]            [/TD]
[/TR]
[TR]
[TD="width: 484"]then
 sudo apt-get install ubuntu-desktop 
sudo apt-get install compizconfig-settings-manager 
sudo apt-get install compiz-plugins-extra 
sudo apt-get install unity         [/TD]
[TD="width: 1"]            [/TD]
[/TR]
[TR]
[TD="width: 484"]unity-reset             
            [/TD]
[TD="width: 1"]            [/TD]
[/TR]
[/TABLE]
 Then by magic up came a rather shaky unity desktop the dash didn't seem to clever so I guessed it had not restarted everything, so I went to my ever handy Cairo dock scrolled through till I found compiz settings manager and looked down the list until I found Unity.

It was at this point I discovered that unity plug-in was disabled so I re-enabled and applied and there it was several warning boxes later Unity and working. this is not something I would like to repeat, There is one thing I found out, that Cairo dock is a must install for all, it saved a lot of time and remembering keyboard short-cuts. now I'm off to reboot to see if this is just misplaced confidence. No its not misplaced confidence its all up and working and actually better, well the dash is, still get the occassional hang on web pages and a horizontal shadow from desktop applications but its working.

---

### Post by Dark_Horizon on 2013-04-25
**Today's glitches! **I thought I would try similar to the above on the Compaq Presario 300 laptop however, in additional drivers there are none??? no proprietary drivers, no default why is that??
 does it not come up to minimum spec for 13.04 or are there just no drivers for it. It previously had 11.04 on it and it worked well.

also why is there no big announcement by Ubuntu as to the imminent release of the new 13.04 less than 24 hours. I am completely underwhelmed by Ubuntu at this time. when 12.04 came around they made a big song and dance about it, 13.04 they may be keeping things under wraps but honestly how under cover does it have to be? so far that no one gets to know about it, its almost like the release they didn't want to release. I find it hard to believe that this is out in final in less than 24 hours. do we have to reload the new final is there things in it we have not seen yet in the beta?  like Scopes? or is this all we can expect an OS that works when it feels like it, I'll be honest I'm about reinstalled out Ubuntu may have been shooting its self in the foot lately but there's no reason to move from foot to head. If this gets out in its current form there may not be a big enough user base by 14.04 the big convergence to make it matter. unlucky 13 it would appear to be.

---

### Post by dino99 on 2013-04-25
the rolling game is on the way :P

---

### Post by Dark_Horizon on 2013-04-25
This is terrible answering my own problem with the solution, The Compaq presario 300 Laptop has an intel graphics chip-set so I did a bit of searching and found this  [https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)  I downloaded the graphical interface for 12.04 which was the latest available and discovered I had come to the right place after installing and running the .deb file even though Ubuntu software centre was against it, but I discovered one thing the operating system isn't supported I'd have to go back to 12.04 or wait for the release of 13.04 drivers.  
 

 It could be months before they release a set of drivers for 13.04.

---

### Post by roly33 on 2013-04-25
The Intel drivers built into 13.04 are pretty good so you shouldn't need the drivers from 01.org.

 Toshiba Notebook has got an Intel graphics chipset and it runs good with the drivers built into Ubuntu.

Roland

---

### Post by rrich1974 on 2013-04-25
look what i have got...other than that, is is fine! 
this is on my laptop...
on other machime, it looks fine
so, it is in liveUSB...

---

### Post by Dark_Horizon on 2013-04-25
I'm reverting the laptop to 12.04.2, the inbuilt drivers for 13.04 were just too twitchy, having your mouse going inoperative every few clicks or copies,  having to re login every time isn't working so I'll attempt to see what happens to it in 12.04.2 if not I can always reload 13.04. Until there are a set of drivers for the C300 updated it makes using the laptop impossible it may look good but it has to work for its keep. I see they've just released 13.04 but whither I need drivers from 01.org is academic 13.04 with its own drivers just didn't work and in the end that’s all that matters, does it work or not, if not try something else.
here's my desktop 13.04

---

### Post by Dark_Horizon on 2013-04-26
The Presario C300 is working well with the 12.04 no need for additional drivers, the inbuilt ones are working fine. The Pc with 13.04 still with the graphics glitch horizontal shadow coming off of anything open on the desktop. The C300 with 12.04 32 bit is actually booting faster than the Pc, bear in mind the laptop is older with an intel 1.3ghz celeron with 1 gig of ram and 250 graphics ram, the Pc is a AMD Athlon(tm) II X2 245 Processor × 2 with 2gig of ram and 700mb graphics ram with 13.04 32bit  both booting with the same desktop applications Cairo dock and screenlets as you can see in the screennshot above. the laptop is a good 15 -20 seconds faster from boot to login.

I thought we were supposed to get better performance out of 13.04, on the whole at this time I would say no. Still can't believe this has shipped. It still has all the glitches and twitches of a Beta 1.
 I was surprised at the time when I went to 12.10 on the pc just how many crash reports and general glitches came up, that’s why I was moving to 13.04 I thought a .04 version bound to be better more stable LTS. Its actually worse in some respects with any number of rumoured and promised new gadgets that have not materialised or “didn't make it” the youtube videos and promises have come to this Ubuntu vista. I'm quite disappointed, but I'll stay with it for now and reload over the weekend see if it helps a clean install.

---

### Post by Dark_Horizon on 2013-04-26
Can't believe this presario c300 laptop with a celeron and 12.04 is beating my main PC to the punch, I just timed it and I'm still getting graphics crashes on my PC with 13.04 on it fully updated.

 Is there anyone getting graphics problems and crashes similar to this? Is there any diagnostic software you can suggest available that will help me with this problem?

you can see the ghosting on this desktop or I hope you can. the ambient interface crashes too and i get flickering graphics it affects open gl as well

---

### Post by Dark_Horizon on 2013-04-28
proprietary drivers now in use and so far nothing has crashed went whoops or mashed my graphics even after reboot fingers crossed; still have the horizontal shadow but I now suspect that may be somethhing to do with the chipset and compability issues rather than a full blown fault or bug but I could be wrong. It is annoying and I don't get it on the live disk which is odd the shadow only affects the active parts of windows, or applications not the ambient theme its self; beats me if its a bug its a strange one. I just have to run the drivers under various loads to see if things stay ok otherwise it will be a reinstall and if its still an issue going back to 12.04.

One thing I did at one point try Xdiagnose but it didn't work and I read about a lot of other people with the same; rather pointless bit of software apparently.

---

### Post by Dark_Horizon on 2013-04-29
The ghosting problems have now gone things are all working but Banshee occasionally just stops and closes but that&#8217;s a small problem, so far today no ghosting no graphics crashes and even the software updater worked...Result!
 This rolling development has its drawbacks though; less than a week ago I thought it would be insane to put out 13.04 in the state it was in, so what happens now we just continually update till 14.04? uninterrupted distribution update? This one has been problematic to say the least. If we are entering a phase of rolling development are we also going to find ourselves in the act of rolling development, that could be a problem for a lot of us. Without a clear division between test and  development releases. Rolling development of this sort only makes sense after a beta 2 has been issued.
 

 Anyway its all up and working so I think this thread can be marked as solved for now!

---

