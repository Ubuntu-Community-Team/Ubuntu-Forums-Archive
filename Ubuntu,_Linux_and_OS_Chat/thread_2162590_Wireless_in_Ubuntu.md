---
title: "Wireless in Ubuntu"
date: 2013-07-15
forum: Ubuntu, Linux and OS Chat
---

### Post by b3rylord on 2013-07-15
I have recently had a HDD failure with 12.04LTS resident..... A new disc was procured, 12.04 re-installed and updated (298 updates and 339Mb!!!!!!!!!) and then came the fun bit of trying to persuade the wireless to work. My wireless card  uses b43 drivers which appear to be blacklisted by default in 12.04 ISO. This took me AGES to achieve, for want of a sticky about this subject in the forums.......

Out of curiosity this morning I loaded Fedora 17 from a Linux tips tricks apps and hacks CD and was on line in SECONDS, the wireless up and running without my interference.

I do prefer Ubuntu, but cannot see why this problem, which many suffer from, cannot be addressed as a matter of urgency, as if people cannot make it work out of the box, they will just abandon it and stay with their "Windoze"

Not everyone wants to climb under the sheets with a terminal session, and I was lucky to have a mobile dongle to consult on line for a solution, and have the patience to search around amongst the many solutions for the right one........

Happy again now but left confused and baffled.....
Discuss, giving reasons for the above sad state of affairs.....lol

---

### Post by ajgreeny on 2013-07-15
Just in case others with the same problem stumble on this post when looking for answers, here is the most likely site that will point you in the right direction:-

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by mastablasta on 2013-07-15
it's ridiculous that it Wi-fi can work at one pont and not at another. people report that, reports get ignored  and bug just gets closed.  "problem? what problem?"

---

### Post by stalkingwolf on 2013-07-15
lately i have found that getting wifi to work is as simple as using the additional drivers feature.  I run this as a matter of course to check for video drivers.  So usually see at the same time if there is a wireless driver available

---

### Post by varunendra on 2013-07-15
> **b3rylord said:**
> My wireless card  uses b43 drivers which appear to be blacklisted by default in 12.04 ISO. This took me AGES to achieve, for want of a sticky about this subject in the forums.......

If you mean these modules - b43, ssb, bcma, brcmsmac, then none of these are blacklisted by default in any version of Ubuntu. They only get blacklisted if the proprietary driver "wl" (bcmwl-kernel-source package) gets installed.

So I think the case was that you chose to "Install 3rd party packages" during installation, and since the installer gives the proprietary drivers higher priority if they are available, it got installed during Ubuntu installation. Thus you ended up with blacklisted native drivers and the proprietary one installed whose performance is not good with some of the cards it supports, yours most probably being one of them.

I agree with the concerns about having a sticky explaining the possible problems and the solutions. I'm myself ready *(and am sure many others here, including wireless master Chili555)* to create a thread like that, and maintain it to the best of my ability. Or contribute to an existing one if already exists and gets sticky'd.

The wiki page that ajgreeny linked to is a very good source of info about all this, but since it is too wordy (with not much scope to shorten it), I think we do need a summarized version of it and a sticky here can be a perfect solution to that.

---

### Post by b3rylord on 2013-07-15
Thanks guys for seeing my problem or the problem....I wish that I had documented the tortuous path to a working system, but in the heat of the moment all I could do was try the next and often flawed solution.......I did chose to install 3rd party packages, thinking that if I had it all it would work that much better...big mistake......Another distro I tried was Linux mint 15 which also left me high and dry with no direction or help to get started with wireless......just a mess really, especially if it is ones first attempt to move away from Microsoft..

Thanks again for reading without censure!! If it results in a reliable guide to getting started with wireless all the better......

Paul

---

### Post by Tamlynmac on 2013-07-15
> mastablasta
it's ridiculous that it Wi-fi can work at one pont and not at another.  people report that, reports get ignored  and bug just gets closed.   "problem? what problem?" 		

+1

It's sad, but true. Instead of excuses, I think it makes more sense to address the issues. I'm reminded of the sports term: "Just wait until next year".

---

### Post by cariboo on 2013-07-15
> **b3rylord said:**
> Thanks guys for seeing my problem or the problem....I wish that I had documented the tortuous path to a working system, but in the heat of the moment all I could do was try the next and often flawed solution.......I did chose to install 3rd party packages, thinking that if I had it all it would work that much better...big mistake......Another distro I tried was Linux mint 15 which also left me high and dry with no direction or help to get started with wireless......just a mess really, especially if it is ones first attempt to move away from Microsoft..

Thanks again for reading without censure!! If it results in a reliable guide to getting started with wireless all the better......

Paul

This may be a part of the problem, when something doesn't work the way it should many people including myself at one time, throw as many solutions as they can find at a problem, and in most cases the problem never gets solved. My suggestion is to calm down, it isn't the end of the world if something doesn't work as it should. 

[LIST]
[*]There is a solution to your problem, but only try one at a time, and revert the changes you made, if one doesn't work, before going on to the next solution. 
[*]Keep notes, so that if you run into the same problem you already have a solution and don't have to go off in a panic looking for help.
[*]If nothing seems to work, go do something else for a while, you may be missing something that is obvious, and a fresh mind looks at a problem differently.
[*]Make a list of your hardware, and keep it handy, that way you can search for your specific hardware related problem.
[/LIST]

I know this doesn't solve your problem, but it should make things easier, the next time your have one.

---

