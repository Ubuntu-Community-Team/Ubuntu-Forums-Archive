---
title: "Got sick of Windows in general and so I Ubuntu my system..."
date: 2014-08-02
forum: Ubuntu, Linux and OS Chat
---

### Post by JCole81 on 2014-08-02
Got tiered of fighting back hackers on my system, dealing with registry problems, viruses, Trojans, Malware etc, My system was at a critical rate, interfering with my gaming I've just got back into from PS3. The installing of Ubuntu was a breeze, a breath of fresh air, my system became quite at peace, everything went well, love the smooth interface and easiness on the eyes but since I was about security first and then gaming second I run into a problem.

After installing all the needed components to be able to run MMO games like Neverwinter online and getting it running everything just went to a crawl via the logon screen and my question is: How much RAM I need to run MMO games via Playonlinux/wine? I have a 2GB system with Nvidia Geforce GT 355M. I really want to play that game on sweet Ubuntu and by the way I am typing this from window 7 :( I had to go back, well.. more like forced back:mad:

After installing Ubuntu I download Wine and then I downloaded Playonlinux, downloaded Arctorrent for Neverwinter, set up the needed window configuration and that was it but did I only needed Playonlinux and not wine?

---

### Post by s-l-425434 on 2014-08-02
Not many games run on linux, even with wine. Though it´s getting better and with the steam OS coming out, I suspect we are going to see a whole lot more of it.
If you look under steam, neverwinter is not supported for linux based OS or mac, only windows.
Actually played around with neverwinter and tried getting it to run on ubuntu (that and perfect world international) a couple of years back. Never got it to work though, but perhaps it´s time to give it a try again. 
I´ll look into it and keep you posted if I should fall upon a solution, but I doubt it.

---

### Post by grier-devon on 2014-08-02
Here is a guide of how to install the game natively I believe
[http://robotbutler.org/article/13](http://robotbutler.org/article/13)

Never Winter Nights I believe was ported to Linux some years ago. However understand that gaming on Linux is no where it is on Windows. We are getting there in time but still a ways off. I believe there are some MMO on steam and another one to try is Ryzom which has a native Ubuntu port in your software center.

---

### Post by s-l-425434 on 2014-08-02
Here´s a video guide to PWI, haven´t tried it myself, but looks decent and simple. Will probably try tomorrow.

[https://www.youtube.com/watch?v=C3vbsA15iOc](https://www.youtube.com/watch?v=C3vbsA15iOc)

---

### Post by Rob Sayer on 2014-08-03
PlayOnLinux is nothing but a GUI front end for Wine.  In other words it *is* Wine, it just looks different.  And I doubt it's as recent a version of Wine as the one you'd get from the repos.

So you're never going to get better results with it.

Wine is not reliable, and there is a ton of documentation on the web on which programs will work.  Anything rated less than Gold will be unreliable, and be careful updating those programs.

Running Windows in a VM would be more reliable but would also be a more power hungry solution.

---

### Post by V_Lnh_Ti on 2014-08-03
> **s-l-425434 said:**
> Here´s a video guide to PWI, haven´t tried it myself, but looks decent and simple. Will probably try tomorrow.

[https://www.youtube.com/watch?v=C3vbsA15iOc](https://www.youtube.com/watch?v=C3vbsA15iOc)

its done. i tried it

---

### Post by JCole81 on 2014-08-05
> **V_Lnh_Ti said:**
> its done. i tried it

Okay, I watched like 31 videos on MMO gaming via ubuntu and all of them are shady! When they show the game running on ubuntu they never move, they just logon and be like see it works. The guy that got PWI working and log in, all he did was open inventory and then that was the end of the video and in another video running Neverwinter online, the video just shows him log on already in an instance with no other players around to hide the fact that lag is heavy in towns around players and unplayable, why the shady BS, why they can't just say it works but unplayble? all the videos I watched is just a gimic:evil:

I mannage to get Neverwinter online working but the lag was bad af at first and then few more tweaks I was able to explore the city a bit but still the lag was there. The game started playing on it's own half the time, sound kelpt going off like bombs and random crashing but hey like I said I got it running and was able to move in the city around 100s of players, I am going to keep trying different tweaks etc, it is actually fun trying to get this MMO running with playabilty.

---

### Post by mastablasta on 2014-08-05
> **Rob Sayer said:**
> PlayOnLinux is nothing but a GUI front end for Wine.  In other words it *is* Wine, it just looks different.  And I doubt it's as recent a version of Wine as the one you'd get from the repos.

So you're never going to get better results with it.


since it is only a front end it allows you to easily install (via menu and a few clicks) different versions of wine. including the latest dev version, as well as standard and older versions. you can easily run multiple version at the same time. this is good in case newer wine version doesn't support the game as good as the old.

aside from that you can also use the preset setups that people as PoL prepared. they include various scripts that will tweak the game in order for it to run faster/smoother/with no crashing .... same goes for programs. the presents will use older wine version if necessary or if game/program performs better with it. while some may criticize some of the scripts they did try to make the experience as easy as possible for new users. so those that complain about scripts should do better in trying to improve them instead. :P 

one other thing is that some games do give better performance in wine. again this is connected to the GPU used, drivers used.... but yeah some actually do give better performance than in windows.

> **JCole81 said:**
> 
I mannage to get Neverwinter online working but the lag was bad af at first and then few more tweaks I was able to explore the city a bit but still the lag was there. .

as mentioned above it seems Neverwinter has a Linux port. you might try that first.

if you insist on going wine you need to search for info here first: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=870](https://appdb.winehq.org/objectManager.php?sClass=application&iId=870)
and you see things like: 
> [TABLE="width: 100%"]
[TR="class: notetitle"]
[TD]Getting Neverwinter Nights to work on ATI Cards[/TD]
[/TR]
[TR]
[TD="class: note"]Multiple users reported that Neverwinter Nights might present problems when running it on a machine with an ATI card.
In order to avoid that, rename the main program file **nwmain.exe** to something else, like **nwmain2.exe**. The driver seems to try some optimizations otherwise, which are actually backfiring and causing issues with the game.
[/TD]
[/TR]
[/TABLE]


check for bugs & possible complicaitons. as I see the latest patch has platinum rating but with latest wine dev version not the wine in repo. might be good time to use PoL to install the dev wine version just for neverwinter.

---

### Post by JCole81 on 2014-08-05
> **mastablasta said:**
> since it is only a front end it allows you to easily install (via menu and a few clicks) different versions of wine. including the latest dev version, as well as standard and older versions. you can easily run multiple version at the same time. this is good in case newer wine version doesn't support the game as good as the old.

aside from that you can also use the preset setups that people as PoL prepared. they include various scripts that will tweak the game in order for it to run faster/smoother/with no crashing .... same goes for programs. the presents will use older wine version if necessary or if game/program performs better with it. while some may criticize some of the scripts they did try to make the experience as easy as possible for new users. so those that complain about scripts should do better in trying to improve them instead. :P 

one other thing is that some games do give better performance in wine. again this is connected to the GPU used, drivers used.... but yeah some actually do give better performance than in windows.



as mentioned above it seems Neverwinter has a Linux port. you might try that first.

if you insist on going wine you need to search for info here first: [https://appdb.winehq.org/objectManager.php?sClass=application&iId=870](https://appdb.winehq.org/objectManager.php?sClass=application&iId=870)
and you see things like: 


check for bugs & possible complicaitons. as I see the latest patch has platinum rating but with latest wine dev version not the wine in repo. might be good time to use PoL to install the dev wine version just for neverwinter.

Just to be more clear, I am not talkig about Neverwinter knights I am talkig about Neverwinter online. You just gave me more room to tinker with when you metion that using differrent versions of wine could run games better than even the newer version of wine. I also have only 2GB of RAM and strongly believe that could be the problem.

---

### Post by mastablasta on 2014-08-06
in that case this might be it: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=27906](https://appdb.winehq.org/objectManager.php?sClass=version&iId=27906)

1. make sure you have wine 32 prefix. -- I was just struggling with getting Morrowind to work well until I figured out I had a wrong wine prefix (among others).
2. Online games are problematic as they are often patched. and what is one version works in wine another patched version might not work.

not sure what the system specs are for this game but you should have proper specs to play games. wine is not an emulator so similar specs as in windows should do more or less.

otherwise these MMORPG games are all more or less the same to me. the way they work you can see how static they actually are. and not that much different from MUDs (well aside from the gui). it's the only way they can get so many players into one spot. the funny thing is when one compares attest games with some major graphics in play and then some old or free ones you can see how similar they actually are.

---

