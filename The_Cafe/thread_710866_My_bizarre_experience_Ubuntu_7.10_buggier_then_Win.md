---
title: "My bizarre experience: Ubuntu 7.10 buggier then Windows XP?"
date: 2008-02-28
forum: The Cafe
---

### Post by JaggedOne on 2008-02-28
I have been using Ubuntu for bout half a year now. I switched over from Windows XP because I wanted more control over my PC and I wanted a more stable and secure environment. I also loved the idea of open source and was not to fond of Microsoft.

So far my experience has been very positive. Even with the bugs I am about to mention I love Linux and Ubuntu and have no interest in switching back to windows.

However it has been far from perfect. Here is a list of the major bugs I have encountered since my switch:

* Suspend/Hibernate is a huge show stopper for me since I am on a laptop. I know you are all aware of it. It is still an important bug I did not have to deal with in Windows.

* Ubuntu does not always boot up right. Sometimes I get no gnome-panel. I have to reboot to fix that. Sometimes My mouse is unresponsive and I have to press ctrl-alt-backspace a bunch of times to re-login. Occasionally I boot up with no background wallpaper for no reason.  There are several other more rare smaller things that happen on boot from time to time that forces me to re-log in or reboot.

* occasionally Ubuntu does not shut down properly for me. It locks up mid shutdown and shows weird colors or a white screen. I have to hold down the power button to force it to reboot.

* Then of course there is the age old problem with flash locking up firefox. Annoying as hell sometimes.

Those are three rather big bugs that annoy me all the time. They often happen at the same time. Say I try and take my laptop out of suspend and it locks up. I manually reboot and it comes up with an unresponsive mouse so I re-log in. Now there is no gnome panel so I have to do another reboot. Finally after this reboot I have a working and complete desktop. That exact chain of events just happened to me a few hours ago. It has happened before too and is not uncommon.


I have never encountered bugs this irritating in Windows before that I can recall. Sure it has its bluescreens and lockups but those are fairly rare and can be more easily dealt with.

Could it be that Ubuntu has more bugs then windows XP?

---

### Post by youShotWhoInTheWhatNow on 2008-02-28
There is a good chance that this all stems from the suspend/hibernate problems.  Do the other issues come up if you do not suspend/hibernate?

---

### Post by JaggedOne on 2008-02-28
Hm, I don't know I have never tried it. Maybe I will give it a shot.

---

### Post by sryth on 2008-02-29
Don't give up on Ubuntu just yet.  Hardy is supposed to have a good bit more support for power management, there are a lot of people using the latest alpha that love it, and the fully stable version is only about 2 months away.

---

### Post by ubuntu-freak on 2008-02-29
Your shutdown problem is odd, it's always video card related though. Did you change any bit-depth options? Install startupmanager and make sure the bit-depth is 16-bit. If you're using an open source video driver, try this command;

**sudo dpkg-reconfigure -phigh xserver-xorg**    

If it's an Intel graphics device you have, make sure the driver is "intel" and not "i810". The rest should be autodetected and set up okay.
 
See if the troubleshooting section of my [how-to](http://ubuntuforums.org/showthread.php?t=661833) helps with your flash problem.
 
Nathan

---

