---
title: "2 Months of Ubuntu - the trails of noob setup"
date: 2006-08-26
forum: Testimonials &amp; Experiences
---

### Post by moeFinley on 2006-08-26
Ubuntu is great, easy initial setup and beyond that all you need do is refer to these wonderful forums!  Thanks to anyone who has reply to a post in the last 2 months.

However of course it's not been easy getting Ubuntu to do everything my Windows machine did and so I'm writing this to highlight some of the problems, share my solutions and maybe, if the right person(s) are listening, help improve Ubuntu.

These are the main things that were so simple on Windows, but I had a nightmare with in Linux:
Use dual monitor
Watch movies (DVD, XVid) through my TV and sound system
Watch, record, pause TV (DVB-T)

My Windows machine wasn't just media PC it also did all the standard stuff office, internet and email.  But that hardly needs to be mentioned here as Ubuntu does it so well straight out the box.


**Use dual monitor**

Should be easy right?  Go to display settings and enable the second monitor that has already been detected?

No you have to edit config files!  I wouldn't be surprised if there is a nice third party GUI that makes this easier that I have yet to stubble apon.  But this isn't the point, dual monitor setups are not unusual.  Ubuntu should make it easier to enable and then switch between display setups.


**Watch movies through my TV**

The TV out suffered with the same problems as above but further hindered by the fact I'd get no signal from any of the following:

Built in graphics on my Shuttle FN41 MB (GeForce 4)
Elsa Gladiac GeForce 2
WinFast GeForce2MX DH Pro

These all would all correctly output to VGA.  The TV Out would also be detected (looking at nvidia-settings a great GUI I only recently found).  But there was no signal going to the TV.

I bought a second hand GeForce 6600 LE from eBay, plugged it in with the same settings and it's working perfectly.  Switch back to the others and it's still the same.  I have idea why?

Lastly, I know this is probably NVidia's problem not Ubuntu, but why are goldmines like nvidia-settings hidden away.  All it takes is an icon and somebody's curiosity?


**Watch movies through my and sound system**

Sound in Linux seems to suffer from too many drivers and controls trying to accommodate to much hardware.  Similar to the graphics, I couldn't get the integrated sound card on my Shuttle motherboard to output through the optical.  Even more bizarre,  I could through the terminal typing aplay -Dplug:iec958 "test.wav" and in MPlayer if I checked the AC3 Passthough, but nowhere else.

Looking through the forums it seems sound configuration is complex and a common problem?

I'm now using a Sound Blaster Extigy which works perfecly.  I guess thats a good rule for Linux, the best hardware is common hardware.


**Watch, record, pause TV (DVB-T)**

I've only just started with this, but again it's more messing around in the terminal with strange commands trying to figure out what's going on.  I have a Nebula TV card which there seems to be mixed feelings about how easy they are to setup.

This kind of optimises all of my struggles to get something running in Ubuntu.  Plug it in, boot up Ubuntu, nothing.  

Has it install correctly?  Nothing has come up, no tray icon like Windows?  How do you find out, go to the terminal and type some weird command.

This is great if you know what your doing but if your a noob!!!


**Summary**

I guess then although Ubuntu/Linux has accommodated the noob when running applications in day to day use.  But when it come to setup and installations it's still very much readme files and terminal commands.

I'm not an average user.  I've been using computers since I was 11 and work as a Multimedia Producer (my first IBM PC only ran DOS and had no hard drive).  Don't get me wrong, I can understand how using the terminal and config files is simple and effective.  But during my two months there have been times even I have thought this isn't worth it (mainly during the recent X server probs!).  I think most ordinary users with £80 in their pocket would have switched to avoid the hassles I've highlighted here and wouldn't have even struggled passed the first hurdle.

Having said all this I am now converted.  I have no intention of switching back to Windows.  Viva la Open Source! :D

---

