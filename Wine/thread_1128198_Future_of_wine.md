---
title: "Future of wine"
date: 2009-04-17
forum: Wine
---

### Post by Rackstar on 2009-04-17
Hi,

I'm really amazed by the wine project. Not flawless yet, but I don't know what I can expect of it in the future?

I installed Ableton Live 7 without any issues. (Low latency!) That was a real thumbs up. Because this was one reason for me to have another windows computer next to me, almost only for music production.

I was a bit too excited, and hoped to get rid of my windows for ever. Tried installing photoshop and flash. But CS3/4 not working. Which is really sad.

I'm not asking help in this thread for the adobe products, (Another thread running on that) But a little discussion about what wine could do for us.

Will we be able to run some window programs on wine, without having to wait approx. 2 years? Should we encourage wine to create support for adobe products, or should we encourage adobe to port to ubuntu (and other distro's)?

---

### Post by cogadh on 2009-04-17
Encouraging native ports is always preferable, but that doesn't mean you should remove your encouragement from Wine. There will always be some Windows applications that will never get ported to Linux and may be wanted or needed by a Linux user, so in order to keep that functionality available to him/her, Wine needs to continue to develop.

As for when you might be able to run something specific in Wine, that is really a moving target and no one can say for certain when it might happen. Wine has been under development for about 16 years now and during that time it has seen massive bursts in functionality as well as long droughts where it seemed development was dragging on with no discernible results. The best you can do is follow the specific bugs that affect your application in Wine (check the application's [AppDB page]("http://appdb.winehq.org/")) and follow Wine's [general development]("http://www.winehq.org/devel/").

BTW - Some of the bugs that directly affect Adobe products are already on the list of bugs that must be fixed before Wine 1.2 (the next stable release) can be released. Details on when that is supposed to happen can be found [here]("http://wiki.winehq.org/WineReleasePlan").

---

### Post by asdfoo on 2009-04-17
> **Rackstar said:**
> Hi,

I'm really amazed by the wine project. Not flawless yet, but I don't know what I can expect of it in the future?

I installed Ableton Live 7 without any issues. (Low latency!) That was a real thumbs up. Because this was one reason for me to have another windows computer next to me, almost only for music production.

I was a bit too excited, and hoped to get rid of my windows for ever. Tried installing photoshop and flash. But CS3/4 not working. Which is really sad.

I'm not asking help in this thread for the adobe products, (Another thread running on that) But a little discussion about what wine could do for us.

Will we be able to run some window programs on wine, without having to wait approx. 2 years? Should we encourage wine to create support for adobe products, or should we encourage adobe to port to ubuntu (and other distro's)?

Wine is an enormous project and has many outstanding bugs, however bugs are being squashed every day and with each release Wine becomes more reliable and less prone to regressions thanks to the work of both volunteers and people who are paid to work on Wine.  

That said, there's nothing stopping giant companies like Adobe from spending some pocket change to hire knowledgeable people to investigate and submit fixes for bugs affecting their products.  I've seen smaller software companies take an interest in Wine and help out by fixing bugs and doing translations.

---

### Post by Rackstar on 2009-04-17
I really didn't know that wine has been in development for 16 years! How about when windows 7 apps start coming. Will current versions of wine be able to handle this?

I can understand that MS Office & Adobe products aren't easy to support, but how come some smaller apps like MS IE7 have so much trouble?

---

### Post by Rackstar on 2009-04-17
> **cogadh said:**
> 
BTW - Some of the bugs that directly affect Adobe products are already on the list of bugs that must be fixed before Wine 1.2 (the next stable release) can be released. Details on when that is supposed to happen can be found [here]("http://wiki.winehq.org/WineReleasePlan").

Alright, earlier this day I was searching where I could find more info about the next stable release of Wine.

> Ideally, this would be done by February or so, in order to stabilize Wine in time for a March/April release, which would in turn allow Wine 1.2 to ship with the next wave of distros based on the new Gnome and X. If we miss April, most users wouldn't see Wine 1.2 until November 2009. 

I guess we won't see this in Jaunty then. I really feel like Ubuntu 9.10 will be a big step forward. I like the upcoming 64-bit support in wine.

---

### Post by NightMKoder on 2009-04-17
M$ IE7 is very strongly integrated into windows. What you know as the "explorer" (for files) on windows and "internet explorer" are really (almost) the same thing. It's not actually a very small app.

Strangely, MS office works rather well at this point.

As for windows 7 - I doubt any (large) company try to explicitly break compatibility with windows xp in the near future, so there is a good chance that wine will be able to run new apps for the next few years. However, this doesn't apply to games using DirectX10 exclusively.

For the future - I just hope wine finishes the graphics implementation. After the DIB engine is done (if ever) and directx9 is fully (and well) implemented, life will be wonderful.

---

### Post by Rackstar on 2009-04-17
> **NightMKoder said:**
> 
Strangely, MS office works rather well at this point.


Is it already possible to use Office 2007 on ubuntu without too much problems? I know you can read on wineHQ, but they always seem very very optimistic.

Let me rephrase it: can a non-tech, but educated person do it?

I understand the IE7 problem now, I sometimes need it to check compatibility, because I'm also a webdeveloper. But that's not a regular base, so that won't stop me.

---

### Post by zami on 2009-04-17
I also wanted to encourage you to look into Crossover Linux by Codeweavers.

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

It's basically a pay-for (purchase, not a subscription) Wine program, but I've found a lot of things I can't get to run under vanilla Wine, I'll get going under Crossover - with the reverse being just as true.

Along with the Wine Application Database (referenced in previous posts)
[http://appdb.winehq.org/](http://appdb.winehq.org/)

you can look up programs in the Crossover Compatability database
[http://www.codeweavers.com/compatibility/](http://www.codeweavers.com/compatibility/)

Often you'll find a tip at one site or the other that's just what you needed to get a program running, regardless of if you're using Wine or Crossover.

Lastly, if you're a customer of Codeweavers, you can "vote" for applications you want to run - I think you can have one active vote at any time - and you can pledge for specific applications as well.  For example, there are 77 votes and 18 pledges totaling $1153.39 for "Lord of the Rings Online" right now (oddly that's a game that runs pretty nicely under both Crossover and Wine!)  I don't know how much the voting/pledging actually affects anything, but I appreciate getting a vote.  :D

Also, never fear asking "whats an alternative to ____ " for your favorite programs, especially if you've got some less than common favorites.  

I don't want to side track the thread but you mentioned Office 2007 and web editing - you might like Open Office, and for web editing I lurve me some Quanta+  (I am not a fan of WYSIWYG editors - but there are plenty of those available too!)

Good luck!

-zami

---

### Post by Flareside on 2009-04-17
> **Rackstar said:**
> Is it already possible to use Office 2007 on ubuntu without too much problems?

I run office 2007 without any problems. You just need to get as more recent version of wine than what's available in the package manager. I run it just fine with version 1.1.9, but the tutorial on installing it in Ubuntu calls for 1.1.16, so i would go with that version first if your interested in installing office.

---

### Post by Rackstar on 2009-04-17
Hi,

Thanks for your comment. I'll take a look at CrossOver. If the prices are ok, maybe I will. I was looking to give a (little) donation to Wine also. I love those projects.

Yes I use OpenOffice for now. But I sometimes need Office 2007 PowerPoint for presentations I give on pc's without OO. Or sometimes I need to exchange Word documents, and I often notice documents getting little corrupt. (There not standard documents, use a lot features)

For web editing I really like the netbeans 6.5 with PHP support. So that's no problem.

Adobe products just can't be replaced for people who need it on almost a daily basis.

If somebody here has experience with Wine. (If not, you would not be here ;) ) And able to help me with this thread, don't hesitate!

[http://ubuntuforums.org/showthread.php?t=1128083](http://ubuntuforums.org/showthread.php?t=1128083)

But back to topic. What can regular software developers do to give maximum compatability to Wine? Are there guidelines? I'm not that big of software engineer, and if I do some software development, it's in Java, so no problem there ;)

Sorry for all the questions, but this really got me interested, but there isn't that much to read about it, or I just look over it.

---

### Post by Rackstar on 2009-04-17
> **Flareside said:**
> I run office 2007 without any problems. You just need to get as more recent version of wine than what's available in the package manager. I run it just fine with version 1.1.9, but the tutorial on installing it in Ubuntu calls for 1.1.16, so i would go with that version first if your interested in installing office.

I will take a look at this! Thank u, where did you find the tutorial? Or just in the appDB? I'm at version 1.1.19. I also have a question about this: Is it always wise to upgrade to the latest development release? I normally just go for stable releases, but last stable release was a long time ago.

---

### Post by Rackstar on 2009-04-17
Had to use wine 1.1.16 and office 2007 installed with no errors!

Word en Excel run perfectely till now. But Powerpoint doesn't, I'll have a look around. But I'm pleasantly suprised.

EDIT: Ok, I made Powerpoint run with only one override in winecfg.

Ok this answers my question. This is really perfect! One donation coming up!

Only only if Photoshop CS4 would run (still have a license for it).

This was a bit off-topic. But really happy to see this is possible.

---

### Post by cogadh on 2009-04-17
One minor note that should be mentioned: Codeweavers is the primary financial backer of Wine and much of the code they create for CrossOver ends up enhancing Wine (and vice versa). If it comes down to a choice between buying CrossOver and making a small donation to Wine, you should buy CrossOver. Not only will you get an excellent product for running many of your Windows applications, your purchase will directly benefit the Wine project.

---

### Post by simtaalo on 2009-04-17
i'm quite impressed you got ableton 7 to work perfectly through wine

---

### Post by Rackstar on 2009-04-17
> **simtaalo said:**
> i'm quite impressed you got ableton 7 to work perfectly through wine

I haven't tried everything. But it runs, low latency, and low CPU usage. I run intel centrino duo, 1.66. 2GB ram. Not state of the art.

Only the function to use the keyboard as midi keyboard will only start if I first have renamed a track or something.

---

### Post by asdfoo on 2009-04-17
> **cogadh said:**
> One minor note that should be mentioned: Codeweavers is the primary financial backer of Wine and much of the code they create for CrossOver ends up enhancing Wine (and vice versa). If it comes down to a choice between buying CrossOver and making a small donation to Wine, you should buy CrossOver. Not only will you get an excellent product for running many of your Windows applications, your purchase will directly benefit the Wine project.

Donations to the Wine project go towards helping Wine volunteers with travel costs to get to conferences I think.  So, it's still a worthy cause.

---

### Post by NightMKoder on 2009-04-17
> **Rackstar said:**
> I will take a look at this! Thank u, where did you find the tutorial? Or just in the appDB? I'm at version 1.1.19. I also have a question about this: Is it always wise to upgrade to the latest development release? I normally just go for stable releases, but last stable release was a long time ago.

[self promotion]
[http://ubuntuforums.org/showthread.php?t=1102840](http://ubuntuforums.org/showthread.php?t=1102840)

Wrote this up a while ago so that people would stop doing 21.5 winetricks to get office running (and probably hose their wine prefix).

Also just added the bit about powerpoint - I suggest adding the riched20 override regardless, but if you don't powerpoint will crash at start.
[/self promotion]

Rackstar: development releases are actually rather stable (there are some regressions, but in the worst case you can always downgrade). There is a pretty high chance that with each development release something will begin to work.

In terms of development, the best thing actual developers can do is test the apps with wine. Since they have the source code, they can at least tell what they're expecting and what wine is doing wrong. Sadly...that's just not happening in the big companies.

---

### Post by Skerit on 2009-12-13
Codeweavers also employs Wine's maintainer Alexandre Julliard and many other developers.

I've read Photoshop cs4 is starting to work on wine, although the installer is currently failing because of regressions (so you'll need to install using wine 1.1.16)

I believe Adobe applications are desperately needed. There still isn't a decent, professional Video NLE for Linux. Getting Adobe Premiere Pro to work would be fantastic!

I've alreayd bought a copy of Crossover Office Pro and pledged $192 to it :)
I've also voted for it on the AppDB

---

### Post by Ghost|BTFH on 2009-12-13
I'd like to offer the simple and logical recommendation that, since you already have a Windows box running next to you, why not put it safely inside your Linux box?

I know, I know, I'm talking crazy - but hear me out...

Install VirtualBox by Sun.

Take your Legit Windows CD, plug it right on into the CD drive, configure your VirtualBox to use it, install Windows via a VirtualBox.

From there, install your photoshop, flash, whatever.  Run it.

Unless you're trying to get a game to run (which ironically works better using WINE usually) you should be able to get almost any program working just fine in a Virtual Machine.

Problem solved, now go turn that other system into your Jukebox server.  You know you want to, go on.

Cheers,
Ghost

---

### Post by del_diablo on 2009-12-14
> **Ghost|BTFH said:**
> I know, I know, I'm talking crazy - but hear me out...

Install VirtualBox by Sun.

Remember that there is a performance loss on emulation, how much is not quite known.

---

### Post by Ghost|BTFH on 2009-12-14
> **del_diablo said:**
> Remember that there is a performance loss on emulation, how much is not quite known.

This is true, but I've run Photoshop and Rosetta Stone both very well on VirtualBox - the only issue with Photoshop, if I recall correctly was some of the keyboard shortcuts act up.  Aside from that, it works like a champ - just make sure to give your Virtual Machine plenty of ram and video ram.

Cheers,
Ghost

---

