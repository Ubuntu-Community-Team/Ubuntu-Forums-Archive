---
title: "New Ubuntu user trying to run games with Wine."
date: 2009-04-06
forum: Wine
---

### Post by Zireth ZH on 2009-04-06
Hello everyone... I just got ubuntu running.. I got both Linux and Vista on the same PC.. I had trouble installing the ATI Catalyst 9.3 linux drivers for my HD  3850... Steps found on most pages arent clear at all for me.. I find some info missing for a newbie in order to understand everything well...
Finally I got the drivers installed with the hardware drivers thingy from System ---> Administration  and Im pretty sure that thats not even the latest drivers.. or maybe im wrong..
But at least desktop effects are working and everything seems fine.

Im not that familiar with any Linux terms, commands.. and not good using the "Terminal".

I got the drivers... I got wine.. I got Fallout 3 installed on C drive... and tried to run it ... but no results... Not even changin the windows versions.

Can someone here please give me the steps for noobs to get all this working? Linux isnt as user friendly as windows but I still like it and want to learn and use it...

Help me out please... And sorry if i wrote something that sounded offensive.. it is not my intention.
Thanks

---

### Post by Cybie257 on 2009-04-06
> **Zireth ZH said:**
> 

Can someone here please give me the steps for noobs to get all this working? Linux isnt as user friendly as windows but I still like it and want to learn and use it...

Help me out please... And sorry if i wrote something that sounded offensive.. it is not my intention.
Thanks

I know what you are saying, but especially compared to Vista, Ubuntu is actually fairly user friendly. You are just too used to Windows and how things work there. Also, if you are stating that by comparing your experience installing Windows programs, Linux is Not windows. Try installing anything Linux in Windows. Not going to work. Install Windows programs into Linux, thanks to WINE, a lot of them will work. :) 

But, I am glad you want to learn Linux and try not to give up to easily as you will find Linux/Ubuntu to be better in so many ways, as long as you don't compare to 'running Windows software'. 


Not to discourage any form of asking for help here in ubuntuforums.org, but you can also check out the WineHQ Forums at [http://forum.winehq.org/viewforum.php?f=2](http://forum.winehq.org/viewforum.php?f=2)

One other thing you can try as I have found some things to work after doing so, is to set a virtual desktop under the Wine Settings/configuration 'Graphics' TAB. Maybe this will get you somewhere?? 

-Cybie

---

### Post by dominiquec on 2009-04-06
Also check the compatibility of your game with Wine over at [http://appdb.winehq.org/](http://appdb.winehq.org/).

---

### Post by twinsmom on 2009-04-09
The other thing that I would suggest to check would be the sound settings in Wine, sometimes those can dork things up too.  Try different things.  

I also just made the switch to Ubuntu a few months ago, don't be discouraged.  It is possible to get a lot of your Windows software running.

---

### Post by NightMKoder on 2009-04-09
Fallout 3 is most definitely not the best windows application to start trying with. 

[small rant]
There is a bug in Fallout's code that does incorrect detection of graphics cards (ie it tries to enable/disable features based on the name of the card, and nothing else). Wine does not normally report the name of your video card to the application, but gives a special list of features that are found instead.
[/small rant]

There is a way to get fallout 3 to run, but it involves compiling your own version of wine, and considering you're not too familiar with the terminal, I wouldn't suggest trying (unless you're feeling brave).

Take a look at [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14322) for instructions.

---

