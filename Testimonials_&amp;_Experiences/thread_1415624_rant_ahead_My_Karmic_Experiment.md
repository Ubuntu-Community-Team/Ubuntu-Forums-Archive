---
title: "*rant ahead* My Karmic Experiment"
date: 2010-02-25
forum: Testimonials &amp; Experiences
---

### Post by Thanh-BKK on 2010-02-25
Hi.

As some of you may know, i am one of those guys that says "never upgrade a running system" and yet, i do have more than one computer and one of them is for experimentation.

And one such experimentation i started today - booted that machine (Jaunty), grabbed the latest updates, then - upgraded to Karmic!

I just wanted to know how it is like, no more.

Now first i was surprised about the ginormous amount of data to be downloaded - 1.3 GB (Gigabytes!) even though i had just installed another 390 MB of Jaunty updates?? Way much data.... but then i have Gnome, KDE and XFCE in that system...... 

So it sat there downloading for quite some time and then went on installing. All looked good.

Until there came a window asking me if i want to install some new Network Manager config - something, or keep the old one? And i found out that i could not click anything because the mouse didn't work. Neither did the keyboard. There was no HDD activity - machine was hard frozen. 

I had it sit there for 15 minutes thinking it migh tjyst be very busy doing something in the background but nope - only the reset button could help me. 

Upon restart i was looking at some strange splash screen - a simple white Ubuntu logo on black background. Not nice at all. And, even worse - next came a text prompt for me to login. Which i did - no GUI, but logged in. 

Ok so the machine wasn't dead despite the bombed upgrade, so i tried a simple "startx" and so it did - went into KDE though, but working. I shut down from there, no problem, restarted - same again. 

So i tried, from the command line, a "sudo apt-get dist-upgrade" and Ubuntu, intelligent as it is, told me what a fool i am and which command it wanted to see :) Something involving dpkg, i did exactly what Ubuntu told me to do and it started rummagin in text mode, installing a bunch of stuff and in the end sat there waiting for me to log in.

Which i did.

And still command line?? "startx". And there was my Gnome again :) However - no internet (network manager not working) and neither "shutdown" nor "restart" were available. Reset button again.

Next restart then there was internet, so i ran Update Manager and that told me that a previous upgrade was not completed however it offered me to do that for me. Sure, do it then.

Another 10 minutes later then it was done, i wanted to shut down - which was now available, however i was greeted by yet another command line asking me to log in?? 

I logged "in" and the system shut down. Weird.

Started again! You see i don't give up. It booted straight into Gnome, all looked fine, internet, Awn, all programs were there..... i ran out of time and had to go to work, just one more test - restart? Nope, get a CLI login prompt yet again. Logged in and the system rebooted.

The final shutdown then went normal, i.e. without a login prompt.....

Now i do understand that this is my fault for hard-resetting the machine during an upgrade but hey, the machine froze on me first! I am not using the "restart" feature all that often and, apart from the unusual login prompt, it works..... but i hope i will find a fix for that.

And here comes the rant now, as promised in the title:

Why in the world has the beautiful, functional boot splash from Jaunty been replaced by a single, static, dead-looking white Ubuntu logo on a black background that appears upon start and shutdown???? Come on... at least a progress bar could have been there....... yes, i use auto-login as i am the sole user and it's a personal computer of mine, no need for passwords. 

And why, if Ubuntu knows exactly what command to use after a botched upgrade, can't it do that by itself? I.e. auto-repair or auto-continue or something like that? 

One thing for sure - all my other (own and at my office) machines will stay on Jaunty, i won't touch the "upgrade" function again in this life :) Now if i only find a way to stop that barrage of beeps when shutting any of them down....... 

Best regards.....

Thanh

---

### Post by 3rdalbum on 2010-02-25
Karmic has switched entirely to the Upstart bootup system.

Under the old system (called System V Init), there were a specific number of scripts to execute before the system was considered "fully booted", so a progress bar could be drawn based on how many of those scripts had been run.

Under Upstart, services are only started if they are actually needed and their dependencies are available. The system is considered "fully booted" when all the dependencies are met, which can change depending on your configuration. So basically the system doesn't know exactly how far it is through the bootup sequence, and it can't draw a progress bar.

Upstart makes it possible to have quicker, more intelligent boots, so it's a worthy trade-off. If you fresh-install Karmic and it works right, you could well get a bootup that's so fast you don't need a progress bar. I'm on Lucid at the moment and it's ridiculously quick to boot.

---

### Post by caravel on 2010-02-25
Distribution upgrades have always been hit and miss.  Use a seperate /home partition and clean install next time.

Personally I find startup splash screens/quiet boot annoying on the whole and disable them in grub.cfg/menu.lst.

---

### Post by ndefontenay on 2010-02-25
I've tried upgrading 3 times in the fast. Always a big failure.

Try a clean install it is much much better.

Nico

---

### Post by stalkingwolf on 2010-02-25
I personally have never done an upgrade, for all the reasons mentioned.
If I want to try "the latest and greatest" I run first the live disc then 
if i am inclined a fresh install.

---

### Post by Thanh-BKK on 2010-02-25
Hi.

The only one time that i attempted a fresh install where a system was already installed it ended in failure as well - despite having chosen NOT to format the home partition it did so regardless during the install - i had to reinstall and reconfigure all my apps. 

I do not mind to do a fresh install of Ubuntu - after all it takes only 20 minutes at the most. However it takes me days to get all my applications back in and customizations to where they were before :)

This is why i did the upgrade... after all that computer serves that one purpose, testing stuff before implementing it on a production machine. I know, now, that i won't have Karmic on my main machine, after all Jaunty performs absolutely flawless there..... maybe the next one, Lucid, will be replacing it - if at all :)

Kind regards.....

Thanh

---

### Post by DeusExM1 on 2010-02-25
i always install from scratch and i always have the startx problem. My pc just boots into a black screen... i have to log in just like you, then type startx to make the machine boot. 

What is funny is that i have configured it to not require a a log in at all... but i guess it doesnt listen. 

Furthermore, as soon as it boots up and i start doing my work, the ubuntu splash screen appears out of nowhere, and the desktop loads again. All of the apps are gone from the tray, but are still running in the background. I have to kill the processes and then start them again.

I have only used Jaunty and Karmic, and for me personally, Karmic is not half of what jaunty was. I couldnt find help on the forums about this problem, and im too lazy to reinstall... So im patiently waiting for lucid lynx, hoping that since it is an LTS release, that it will be more stable.

---

### Post by Tamlynmac on 2010-02-25
Thanh-BKK

Thank you for sharing your experience.

I recall the words of a recently departed member who constantly reminded us to always do a clean install from disk or stick. Never to use the net upgrade. His words rang true for me numerous times. I also use a separate (used) HDD to install and test new upgrades prior to commitment. Testing before installing on all our primary HDD's has proven to be an effective solution.

Since this isn't a debating section of the forum, I will not debate the issue. Only remind all that testing is a simple and inexpensive solution to assuring upgrades will be fully functional on your systems prior to installation.

Good Luck

---

