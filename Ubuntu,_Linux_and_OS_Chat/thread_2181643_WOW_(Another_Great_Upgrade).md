---
title: "WOW (Another Great Upgrade)"
date: 2013-10-18
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2013-10-18
This morning i did my upgrade on my 13.10 development, using the 13.10 Final Iso....Since i run only 1 ubuntu, the automatic part of the installer offered to either totally wipe out everything and re-install OR
Re-install 13.10 with data and programs carried over...It calls it a re-install because i already have 13.10 on there...if i had 13.04 it would have been called Upgrade...

Anyway, it took a zippy 20 minutes for the whole install! (you manually set time zone and log in info as usually done on a clean install) and of course, the same slideshow...

Results was: Once again...EVERYTHING CARRIED OVER (except for the same 3 items as last upgrade) which were my 3 licensed programs...Chrome, Oracle Java, MS Core Fonts...oh yeah and i did have to re-install libdvdcss2 deb file...As far as system settings, everything carried over except for the volume on Sound Settings (went to default) and Rhythmbox went to mute...so i just had to push that back up...

Every little bit of data transferred (music, videos, photos,documents, etc)...and all other settings, apps, even my caches, urls and settings on Chrome were remembered when i re-installed...and my chrome extensions all there...

Just had to spend about 20 to 30 minutes re-tweaking those minor things..instead of spending about 8 to 10 hours, putting everything back again...a terrific time saver!!!

I'm convinced that upgrading from the iso installer (if given as an option for your set-up) is the BEST way to upgrade and the most reliable as well....
Using this method, essentially gets you a Clean Install but with just about everything carried over with it...

An important tip (as many mention) is to uncheck any ppas before you start, so you will get an nice smoooth upgrade...(lol)
They all were gone anyway when i re-booted my new install...

From this point on, i will be using this method to ROLL into each new Ubuntu final when they are released and i highly recommend it :D

---

### Post by Toz on 2013-10-18
[I]Moved to the **Ubuntu, Linux and OS Chat** forum for 2 reasons:
1. Its not a support question
2. Since 13.10 has been released, it is no longer a Development version and doesn't belong in the U+1 forum.[/I]

---

### Post by ventrical on 2013-10-18
@craig10x

Yeah... it's like a system restore/backup all in one .. so pratically any borked system can be recovered/upgraded.

---

### Post by craig10x on 2013-10-18
@ventrical: yeah, that's what so cool about it....it cleaned out all that accumulated stuff from development, and i got a nice FRESH and CLEAN install...yet, at the same time, it brought just about everything over from the old install, saving me hours of extra bother...WOW...love it :D

Now i can finally "roll" into each new final released ubuntu with the minimum of fuss and muss ;)

---

### Post by grahammechanical on 2013-10-18
It is a good way to do it for those who have unreliable internet connections or power supplies or are tempted to shut the lid on a laptop.

---

### Post by craig10x on 2013-10-26
Now that it has been a while since the final of 13.10 was released, if anyone else has specifically used the live iso installer method of doing a UPGRADE, i would like to hear your experience :D

---

### Post by eyTkT7Y on 2013-10-26
> **craig10x said:**
> Results was: Once again...EVERYTHING CARRIED OVER (except for the same 3 items as last upgrade) which were my 3 licensed programs...Chrome, Oracle Java, MS Core Fonts...oh yeah and i did have to re-install libdvdcss2 deb file...As far as system settings, everything carried over except for the volume on Sound Settings (went to default) and Rhythmbox went to mute...so i just had to push that back up...

Every little bit of data transferred (music, videos, photos,documents, etc)...and all other settings, apps, even my caches, urls and settings on Chrome were remembered when i re-installed...and my chrome extensions all there...

It's nice to see someone happy about a good result rather than having issues like so many people who post.

Question... I've had much the same luck if I have a separate partition for /home. Then I can wipe the root partition and install whatever flavor of Linux. My /home directory stays intact as do most of my settings. Do you suppose that what you did simply retained /home? Or did it also retain stuff from /etc?

---

### Post by craig10x on 2013-10-26
That's a good question...i've never manually installed a separate home partition (unless the auto installer does that automatically, perhaps?)...but my experience with the upgrade using the installer option brought over all my personal settings...for example, when i re-installed Google Chrome..my gmail extension was on it already as i had put before, my privacy settings, font settings in the browser, all as i had set them...

The pixel size of my unity icons were the same settings i changed them to, all my mp3s were in my Rhythmbox library as before...my Pidgin messenger settings the same as i had made them, etc etc...
Every little bit of data i had (and i have a LOT) videos, documents, photos, mp3s, etc ALL transferred over and in the same places...even the majority of the system settings were as i had them...

The first time i tried this i had in the back of my mind...well perhaps i may have to re-install with a clean install but instead i sat there with mouth opened, amazed at how well it went...
Only items that got knocked out where things with license agreements (Chrome, MS Fonts and licensed Oracle Java) and the libdvdcss2 codec...and my 2 ppas were knocked out...Chrome's and the Licensed Oracle one...None of which i expected would transfer over....

All other programs (all installed from ubuntu software center) came over with no problems at all...
While you watch it, it looks like a conventional new install with selecting your user name, password, time zone and slide show is the same...but if you watch underneath, different things are going on...

The last thing it does is bring back in all your stuff from the previous install (that it can do)...took 20 minutes...told me to re-boot and DONE....
Only spent about 20 minutes putting back the few missing pieces...instead of spending a day or two like i usually have to do :D

And i have to say, it's running "tip top" for sure...and feels very much like a clean install to me...I did remember the tip i have often read about unchecking any ppas before you start, to help ensure a smooth experience...

---

### Post by help_me2 on 2013-10-26
I've had the same /home for 2yrs now, and just do a clean install of /. It works for me, but hey, if upgrading works for you, go for it. I've just heard too many horror stories over the years to even try it.

---

### Post by craig10x on 2013-10-27
> **help_me2 said:**
> I've had the same /home for 2yrs now, and just do a clean install of /. It works for me, but hey, if upgrading works for you, go for it. I've just heard too many horror stories over the years to even try it.

I often heard the same....and that is why i always avoided it all the years i have been running ubuntu...i took a chance and it paid off (figured, what did i have to lose? i was going to do a clean install anyway and if it didn't work out would just re-do as a clean install)...

Although i never used the software updater option to upgrade and can't speak for that, it seems MOST use that method and it also seems that is where it's kind of a 50/50 deal in terms of how it will turn out (may be great...may not work out great)....I'd love also to hear from anyone else who did it my way and had the same kind of success...

I suspect that when done with the installer option, it has a MUCH higher reliability factor...my friend used it and had the same results as i did...and in fact, i have now done it twice...
first time was to move from 13.04 final to 13.10 development...and then using a 13.10 final iso, i did the upgrade over (which it allows you to do) because i figured it would clear out some of the excess from the development stages...So, both times, results were IDENTICAL...so, those 2 plus my friends (3 altogether) have certainly boosting my faith in using this method...but ONLY using the installer to do it...

---

