---
title: "I think my machine is trying to tell me something..."
date: 2008-04-15
forum: The Cafe
---

### Post by missingno on 2008-04-15
Well this is quite strange.

After saving up for a while, I just recently got a shiny new 16 GB iPod Touch  to replace my old 5th gen due to the LCD screen getting shattered (That's a whole different story). It's a pretty nifty piece of hardware, but since it's Apple, the software just thrives on frustrating people who like to tinker.

Now Apple puts different forms of encryption on each model's music library to prevent people from managing music on a device they own without using their proprietary software. And in case you didn't know, iTunes is Windows and Mac only. I run Ubuntu 7.10, but I do have Vista on a separate partition I haven't touched in ages.

There is a Linux library called [libgpod](http://www.gtkpod.org/libgpod.html) for various programs to use that will decode how songs are stored on an iPod, but only libgpod 0.6.0 includes still beta-y support for the Touch. And as Murphy's Law would have it, [Ubuntu 7.10's repositories only contain 0.5.2-2.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?suite=gutsy&searchon=names&keywords=libgpod) (But the really weird part: the beta repositories for 8.04 [*do* contain libgpod 0.6.0.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?suite=hardy&searchon=names&keywords=libgpod))  So using *apt-get install libgpod* to automagically install everything with one command is out of the question. No big deal, I'll just download the source and compile it. But then *make* and *make install* build almost all source directories except one, spitting out some errors not covered in libgpod's troubleshooting guide. So I can't update it to 0.6.0.




Last resort: Reboot, and use Satan's Operating System briefly to just use iTunes. Hopefully just running one application won't consume my soul in burning hellfire. So after not having used Vista, or even rebooting, in ages since I switched to Linux, I reboot my computer. GRUB pops up, I select the Vista bootstrap loader. Vista's shiny little loading screen goes for a few seconds...




...and then my machine reboots. Well that's strange.  I try again a few times with the same results. Somehow Windows is borked.


So is this a sign from above or something trying to keep me away from Windows? Should I just go use my old XP box for now? Or just wait a few days and sort everything out once I upgrade to the next release?
[SIZE=-16]Wall of text scores a critical hit! 184 damage![/SIZE]

---

### Post by Yes on 2008-04-15
Make a topic here (on Ubuntu Forums, not this specific board) and someone should help you out with the libgpod errors.

---

### Post by TeraDyne on 2008-04-15
Missingno... Best. Pokemon. EVAR!

The best thing you could have done is to have bought something better than an iPod, like an iAudio or something similar that works perfectly on Linux.

Your best bet right now is to a) Make a topic in Multimedia\Hardware to see if anyone can help troubleshoot the compiling error, or b) Run the XP machine.

---

### Post by patrickaupperle on 2008-04-16
> **missingno said:**
> Well this is quite strange.

After saving up for a while, I just recently got a shiny new 16 GB iPod Touch  to replace my old 5th gen due to the LCD screen getting shattered (That's a whole different story). It's a pretty nifty piece of hardware, but since it's Apple, the software just thrives on frustrating people who like to tinker.

Now Apple puts different forms of encryption on each model's music library to prevent people from managing music on a device they own without using their proprietary software. And in case you didn't know, iTunes is Windows and Mac only. I run Ubuntu 7.10, but I do have Vista on a separate partition I haven't touched in ages.

There is a Linux library called [libgpod](http://www.gtkpod.org/libgpod.html) for various programs to use that will decode how songs are stored on an iPod, but only libgpod 0.6.0 includes still beta-y support for the Touch. And as Murphy's Law would have it, [Ubuntu 7.10's repositories only contain 0.5.2-2.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?suite=gutsy&searchon=names&keywords=libgpod) (But the really weird part: the beta repositories for 8.04 [*do* contain libgpod 0.6.0.](http://packages.ubuntu.com/cgi-bin/search_packages.pl?suite=hardy&searchon=names&keywords=libgpod))  So using *apt-get install libgpod* to automagically install everything with one command is out of the question. No big deal, I'll just download the source and compile it. But then *make* and *make install* build almost all source directories except one, spitting out some errors not covered in libgpod's troubleshooting guide. So I can't update it to 0.6.0.




Last resort: Reboot, and use Satan's Operating System briefly to just use iTunes. Hopefully just running one application won't consume my soul in burning hellfire. So after not having used Vista, or even rebooting, in ages since I switched to Linux, I reboot my computer. GRUB pops up, I select the Vista bootstrap loader. Vista's shiny little loading screen goes for a few seconds...




...and then my machine reboots. Well that's strange.  I try again a few times with the same results. Somehow Windows is borked.


So is this a sign from above or something trying to keep me away from Windows? Should I just go use my old XP box for now? Or just wait a few days and sort everything out once I upgrade to the next release?
[SIZE=-16]Wall of text scores a critical hit! 184 damage![/SIZE]

You could probably find a .deb somewhere or maybe, I don't know if it would work I have not tried, add the hardy repos temporarily. apt-get update. DONT UPGRADE.  Then install it and get rid of the hardy repose and apt-get update again. This may not work and I don't know if there are side effects. 
edit: 
Scratch that.
Go here:
[http://packages.ubuntu.com/hardy/i386/libgpod-common/download](http://packages.ubuntu.com/hardy/i386/libgpod-common/download)

---

### Post by Tundro Walker on 2008-04-16
I know this sounds a bit "elitists" perhaps, but why purchase hardware from a company that doesn't support Linux?  Sure, there's a lib you can use to get them working, but still, you're putting money in their pocket, which is you providing a positive reward for their negative behaviour.  (Even worse, because Apple makes you use their stupid software.)

I'm not trying to soap-box-preach to you, it's just it seems there's quite a few folks who still like to buy hardware that isn't supported by Linux even though they primarily use Linux with it.  Then they have to find some hackish way to get it to work.

At least with you, you knew what you were getting into and aren't just complaining "OMG!  My new Apple iPod isn't working with Ubuntu!  Linux sucks!"  :)

Do they make Rockbox for your new Apple?  Maybe try that.

---

