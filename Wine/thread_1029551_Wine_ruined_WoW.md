---
title: "Wine ruined WoW"
date: 2009-01-03
forum: Wine
---

### Post by Gorechilde on 2009-01-03
hello    my first post   i had a friend DL ubuntu on my desktop  i love it. however, wine is not working so well.  today my wine updater said i had to DL a new thing for it     i dont remember what it was, didnt really read it.  after it was downloaded i found i cant open anything besides the internet    Starcraft, Ventrilo .and my World of Warcraft will not open.   Im dieing here   help me out plx .

---

### Post by EnderEcho on 2009-01-03
Were going to need a whole lot more info. What ubuntu version are you running.

What version of wine do you have. Go to configure wine and click the about section and look to see the version.

Reading the forums will be infinitely helpful. Get familiar with why its not working and try some troubleshooting before posting.

---

### Post by efexD on 2009-01-04
You know, you can always downgrade your wine... Check the site.

---

### Post by Gorechilde on 2009-01-06
I have Ubuntu 8.04.    i tried to uninstall and install a new version of wine but it still wont work    i followed the install directions but it doesnt seem to want to run.   Im not very capable with things like this i always seem to be 1 stage off from getting things to work.     when i click on configure wine   it does nothing     nothing opens  nothing closes  just  nothing lol

---

### Post by hikaricore on 2009-01-06
Open a terminal and type:

> wine --version

If it say 1.1.12 download and install this version:
[http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/intrepid/wine_1.1.11~winehq0~ubuntu~8.10-0ubuntu1_i386.deb)
Assuming you're using 32bit Ubuntu of course.

If it doesn't say 1.1.12 please try launching WoW from a terminal window instead of a launcher and post the error/fixme output here.


In the future you may want to think about considering perhaps reading things when you're presented with updates.
If you can't be bothered to read them you don't really need to update them imho.  Especially since you claim to be incapable of things.

---

### Post by bunty on 2009-01-06
yeah well that's what happens when you make Linux distros accessible to windows users , they install linux but carry on being windows users. 

Windows has trained people to ignore everything that is shown to them by spamming them with so many "are you sure" messages they just turn off.

The sad truth is that windozey distros like *buntu think they have to copy this insanity. Not only does this degrade the whole linux experience it reinforces the "yeah, yeah, just get on with it .... oh **** what happened?" mentality.

:-x

---

### Post by Zeroberry on 2009-01-06
Also try just navigating to the wow.exe file by Nautilus or similar program and manually running it with Wine. Sometimes links just get crazy on you, happened to me a bunch already and I'm pretty new to Ubuntu.

---

### Post by Gorechilde on 2009-01-06
Ok, my version is 1.1.12   but the installer from your link says Error: Dependency is not satisfiable:libsound2.    I Googled libsound2 and got many different things to come up    im just not sure on what specific one to DL.   And btw  i didnt ask him to DL this on my comp, my windows was hacked from my brother goin to unsafe sites. I aoplogize for being new, I didnt think an "update" would be a bad thing.

---

### Post by hikaricore on 2009-01-07
I guess I just assumed you were using Intrepid.

What version of Ubuntu are you running?
If you're using Hardy you'll need to downgrade to 1.1.10: [http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.10~winehq0~ubuntu~8.04-0ubuntu1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/hardy/wine_1.1.10~winehq0~ubuntu~8.04-0ubuntu1_i386.deb)

Generally updates are not a bad thing, however when updating there is always a chance of bugs.
Especially when you're using a nonstandard repo such as the one for WINE which is not directly supported like the standard repos.

---

### Post by Zackie on 2009-01-07
I have version 1.1.12 wine and when i start wow now i get this:

This App has encountered a crit error:

Error #132(0x85100084) Fatal Exception
Program                   C:/wow/World of Warcraft/Wow.exe
Exception                 0xC0000005 (Access_Violatioin) at 0073:00000000

The instruction at "0xC00000000: referenced memory at "0x00000000".
The memory couldnot be "read".


Press OK to terminate the application.



Then the Wowerror.exe pops up to send a message.. any ideas?

using intrepid also.

---

### Post by hikaricore on 2009-01-07
Did you read this post at all or the sticky I posted in the WINE forum?

---

### Post by Gorechilde on 2009-01-07
downgrading isint working for me   ive tried it a few times already. The package installer tells me that theres an error, because a later version is already installed.   Whats the correct way to uninstall the original version, if i need to uninstall it first

---

### Post by Gorechilde on 2009-01-07
> **Zackie said:**
> I have version 1.1.12 wine and when i start wow now i get this:

This App has encountered a crit error:

Error #132(0x85100084) Fatal Exception
Program                   C:/wow/World of Warcraft/Wow.exe
Exception                 0xC0000005 (Access_Violatioin) at 0073:00000000

The instruction at "0xC00000000: referenced memory at "0x00000000".
The memory couldnot be "read".


Press OK to terminate the application.



Then the Wowerror.exe pops up to send a message.. any ideas?

using intrepid also.
I get this all the time also     WoW forums say its a video card error  a new video card is needed or drivers need to be updated. Can also be  caused by a lack of ram.

---

### Post by notwen on 2009-01-07
Perhaps contact your friend who helped you get Ubuntu installed and setup?  =]

---

### Post by Zackie on 2009-01-07
> **Gorechilde said:**
> I get this all the time also     WoW forums say its a video card error  a new video card is needed or drivers need to be updated. Can also be  caused by a lack of ram.


Figured out what it was.. For some reason my video card driver wasn't being used had to Activate it... Works Great now!

---

