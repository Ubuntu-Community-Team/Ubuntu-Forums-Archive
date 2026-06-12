---
title: "Windows 7 disappoints me"
date: 2009-12-06
forum: The Cafe
---

### Post by blueridgedog on 2009-12-06
I had been looking forward to Windows 7 as I hoped that it would make my chief tech support role for my friends and family easier.  Having tested it in virtual machines, I was reserving judgment until I had a chance to do an install.

Last night I did a clean install on a good friends PC (I had put Ubuntu on in the past and he just could not part with his windows applications - all of which I showed him alternatives for).  The install went well and all hardware was recognized, but the OS still suffered from some of the Vista ailments.

File copy and paste was still below what the hardware could do, the OS still had the superfetch process that ate amazing resources, basic locations were obfuscated with "libraries" for pictures, music and the like, DRM was alway lurking in the background (slowing file access times) and it still wanted a USB flash drive to "speed up my computer".

When I re-installed his files drive to copy over his personal items, it advised that I did not have permission to delete some of the junk that came over that was no longer needed.  I had the same frustration all over again that I have had with Vista not letting me manage files.  

After that we had the chore of re-installing at least 10 core applications, none of which came with the OS and all of which required either disks (what a concept!) or archives of downloaded files or new downloads.  I had forgotten what I pain it is to install windows software!  I am so spoiled by my reinstall script that simply apt-gets all my usual applications with one command.  

I had intended to try Windows 7 as an OS myself for a year (my standard MO to learn something) but have cold chills now when thinking about it.  Perhaps I am just getting too old to understand the philosophy of the OS and perhaps such an approach works with younger users, but I was so relieved to get home to my Linux system - where I could manage my files, place them where I wanted, surf the web safely, install applications with just a few key strokes and generally have a happy computing experience.  

What a nightmare.

---

### Post by ElSlunko on 2009-12-06
I think once you have things set up, at least for the larger part of that test year, things would run rather smoothly. Same goes in linux / ubuntu for me. Sometimes things can be tricky on setup.

---

### Post by wilee-nilee on 2009-12-06
I hardly use my W7 setup but it seems pretty straight forward, but I have no history with Vista and only a side glance at XP. W7 on my net book with 2 gigs of ram runs almost as fast as Karmic in general. I have the AV not running constantly though that was slowing stuff down, and making the desktop startup slower and longer to settle down to 2-3 cpu. I only payed 44$ bucks for it though with a student upgrade and have a install DVD and a thumb loaded with the install, and MS just accidentally sent me an extra DVD. go figure. Worth about 44$ in the end as a investment for a little more ease of access to MScentric media and Amazon downloads of movies, no net flicks though they are evil.

---

### Post by pwnst*r on 2009-12-06
Win7 rocks

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-12-06
Win7 is not a bad OS, however Acer need to update their chipset drivers.My laptop hangs in random intervals..Under Ubuntu I have no problems whatsoever :)

---

### Post by Zoot7 on 2009-12-06
To me, 7 is Vista done right. It's got a lot of nifty features I quite like I must say, and I'd definitely rather it to XP now at this stage. It's the first version of Windows I've ever used that I could see myself using on a day to day basis (if I had to) I picked it up with the student offer and I'm glad I did but I'm a long long long way off being blown away by it.
I really don't think it was worthy of all the hype, it is still Windows under the hood after all, and it still suffers from the problems inherent to Windows.

So as for my take, it's good but it's not the revolutionary innovative wonderful OS Microsoft would have you believe.

---

### Post by sports fan Matt on 2009-12-06
Kind of off topic, but you said you had an install script for applications.  Could I take a look at it?  Im curious, since it takes a few hours to just reset everything i put of my machine.

---

### Post by blueridgedog on 2009-12-06
> **sox fan Matt said:**
> Kind of off topic, but you said you had an install script for applications.  Could I take a look at it?  Im curious, since it takes a few hours to just reset everything i put of my machine.

I just copy and paste the following:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update &&
sudo apt-get install libdvdcss2 &&
sudo apt-get install w64codecs &&
sudo apt-get install wine &&
sudo apt-get install build-essential && 
sudo apt-get install ntfs-config &&
sudo apt-get install k9copy &&
sudo apt-get install gnome-color-chooser &&
sudo apt-get install inkscape &&
sudo apt-get install conky &&
sudo apt-get install lm-sensors &&
sudo apt-get install pypar2 &&
sudo apt-get install pan &&
sudo apt-get install vlc &&
sudo apt-get install vim &&
sudo apt-get install feh &&
sudo apt-get install devede &&
sudo sensors-detect
```

As I find new items that I want to be part of the default setup, I add them to my list.

---

### Post by Paqman on 2009-12-06
> **Zoot7 said:**
> To me, 7 is Vista done right.

I'd say it's just a service pack for Vista. They're pretty similar, really.

That's not a criticism btw, I actually think Vista is a reasonable OS. My wife uses it, and she gets on alright. I just think that releasing Win 7 as a separate OS was more about marketing than any kind of technological leap. Microsoft wanted to ditch the Vista brand.

As a marketing effort, it's been brilliantly successful. You've got to take your hat off to them, really.

---

### Post by LowSky on 2009-12-06
> **blueridgedog said:**
> I just copy and paste the following:

```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update &&
sudo apt-get install libdvdcss2 &&
sudo apt-get install w64codecs &&
sudo apt-get install wine &&
sudo apt-get install build-essential && 
sudo apt-get install ntfs-config &&
sudo apt-get install k9copy &&
sudo apt-get install gnome-color-chooser &&
sudo apt-get install inkscape &&
sudo apt-get install conky &&
sudo apt-get install lm-sensors &&
sudo apt-get install pypar2 &&
sudo apt-get install pan &&
sudo apt-get install vlc &&
sudo apt-get install vim &&
sudo apt-get install feh &&
sudo apt-get install devede &&
sudo sensors-detect
```


Clean up your code
```
sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list \
 --output-document=/etc/apt/sources.list.d/medibuntu.list &&
sudo apt-get -q update &&
sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get -q update && sudo apt-get install libdvdcss2 w64codecs wine build-essential ntfs-config k9copy gnome-color-chooser inkscape conky lm-sensors pypar2 pan vlc l vim  feh  install devede sensors-detect
```

---

### Post by Paqman on 2009-12-06
sensors-detect isn't a package, it's a command you run after installing lm-sensors. So the last line should be:
```
sudo apt-get -q update && sudo apt-get install libdvdcss2 w64codecs wine build-essential ntfs-config k9copy gnome-color-chooser inkscape conky lm-sensors pypar2 pan vlc vim feh devede && sudo sensors-detect
```

You can also automatically create a list of all installed packages and reinstall them with two commands. [Howto create a list of all installed packages]("http://ubuntuforums.org/showthread.php?t=261366").

---

### Post by autonomy on 2009-12-06
> **blueridgedog said:**
> my reinstall script ... simply apt-gets all my usual applications with one command.
nice

thanks everyone for the fixes and the link

I haven't had any technical problems with my virtual Windows 7, but it's an ugly step backwards from Vista. I saw a real Win7 on a laptop this week, and it looked a lot like Vista; so that solves my gripe. The desktop backgrounds are still very fake, but I mostly like 'em.

---

### Post by Tipped OuT on 2009-12-06
Why isn't this in Recurring Discussions yet?

---

### Post by vader95 on 2009-12-06
I have use Windows since 95 and am just getting into Linux with booth ubuntu and openSUSE. I didn't like vista, but windows 7 is much better. I think the three best windows OS are 
1. Windows 7
2. Windows XP
3. Windows 95


Windows is still my primary computer, especially considering all of my family uses them and it would be hard to switch them to linux. I still think windows is a little better with some software though.

---

### Post by Ylon on 2009-12-06
The Windows 98 (before SE) send a curse over Microsoft:


Any new Windows from that to next new one suffered always bad fame... usually in favor of the previous windows.

I think that the "best remembred Windows are" (in order)


1. Windows 98SE
2. Windows XP(sp2~3) (or 2000 sp 4~5+)
3. Windows 95/NT
...
...(counting beta e service pack)
..
143: Windows Me

---

### Post by blueridgedog on 2009-12-06
> **LowSky said:**
> Clean up your code[/CODE]

True!  I sort of just add them as I decide they should be part of the standard build...you cleaner version is better!

---

### Post by Zoot7 on 2009-12-06
> **Paqman said:**
> I'd say it's just a service pack for Vista. They're pretty similar, really.

That's not a criticism btw, I actually think Vista is a reasonable OS. My wife uses it, and she gets on alright. I just think that releasing Win 7 as a separate OS was more about marketing than any kind of technological leap. Microsoft wanted to ditch the Vista brand.
Yeah, they are very similar. If they really wanted to go with the number naming convention, then 6.1 would be the proper version.

> **Paqman said:**
> As a marketing effort, it's been brilliantly successful. You've got to take your hat off to them, really.
Agreed, it was hard enough to get away from the Windows 7 marketing at times.

---

### Post by mmix on 2009-12-06
i had tried win7 about 6 months. 

win7 == (winxp + GDI replacement with Direct2D/DirectDraw)

---

### Post by Cardale on 2009-12-06
> **mmix said:**
> i had tried win7 about 6 months. 

win7 == (winxp + GDI replacement with Direct2D/DirectDraw)
ReactOS is good as a windows replacement.  It is still beta though.

---

### Post by the8thstar on 2009-12-06
The upgrade price is an absolute scandal if you're not a student. 

I tested several betas, the RC and Windows 7 Enterprise Edition. The price of the upgrade from Vista is not justified simply because the new features don't overcome the hefty price of the OS.

It looks like Vista. I'll admit that Windows 7 behaves a little better and faster on the hardware I have but it's not worth it ([119.99&#8364;]("http://emea.microsoftstore.com/fr/Microsoft/Mise-a-jour-Windows-7-Edition-Familiale-Premium")).

so yeah, Windows 7 disappoints me too.

---

### Post by Paqman on 2009-12-06
> **Zoot7 said:**
> 
Agreed, it was hard enough to get away from the Windows 7 marketing at times.

I don't just mean the volume, but it's effectiveness. The general public thinks that Win7 is both substantially different from and substantially better than Vista.

XP suffered from a fair amount of suckage when it first came out. It wasn't until SP2 that it became a good OS. Win7 is to Vista what SP2 was to XP, really. But by rebranding it as a completely new system they've managed to pull off a marketing switcheroony, and salvaged their reputation.

---

### Post by getaboat on 2009-12-06
I've just upgraded this laptop from Vista (which I loathed) to W7 - which was a painless exercise - and I'm quite liking it. I was rather hoping for a bigger performance gain give the spec of the laptop, but it is a more relaxing experience than Vista.

My personal computing though stays with Ubuntu.

---

### Post by BuffaloX on 2009-12-06
I'm very disappointed with Windows 7, there hasn't been nearly as many funny stories about it as with Vista. :(

---

### Post by cmat on 2009-12-06
I have Windows 7 on my desktop since software I need for work now required 64-bit support and there is no linux alternative. I have to admit that it is better than XP by all accounts even though I've been charged for a service pack of Vista. Not the "Jesus OS" MS makes it out to be but surely a good step forward.

---

### Post by alexfish on 2009-12-06
Don't care 

I would not even open the box, even if it were a present

XP was the last STRAW

  and as usual I picked a short one < Not any more

---

### Post by autonomy on 2009-12-06
> **Paqman said:**
> Win7 is to Vista what SP2 was to XP, really. But by rebranding it as a completely new system they've managed to pull off a marketing switcheroony, and salvaged their reputation.
This isn't the first time Microsoft has done this. Basically, Windows 3 was a piece of crap, so they made a new OS; and instead of starting over at 1, they called it Windows NT 3.1 because more people would buy the third release than an initial release.

---

### Post by witeshark17 on 2009-12-06
> **autonomy said:**
> This isn't the first time Microsoft has done this. Basically, Windows 3 was a piece of crap, so they made a new OS; and instead of starting over at 1, they called it Windows NT 3.1 because more people would buy the third release than an initial release. Isn't it just amazing!? 
:popcorn:

---

### Post by the8thstar on 2009-12-07
> **BuffaloX said:**
> I'm very disappointed with Windows 7, there hasn't been nearly as many funny stories about it as with Vista. :(

Hahaha, that's a good one! :p

---

### Post by kerry_s on 2009-12-07
i actually dig win7, it's just so simple. i'm currently running it on a atom 1.6 512mb ram nettop, surprisingly it works great even when i max out the ram 99%, no freezing, no lockup, no stutter, it just finds a way to release more ram. ;)

i spent most of the day upgrading the kids xp machines to win7, currently downloading a driver pack so i can finish. :lolflag:
dang things are so old, i don't even no what type of drivers to look for, there all a mix of parts.

---

### Post by julianb on 2009-12-07
> i actually dig win7, it's just so simple. i'm currently running it on a atom 1.6 512mb ram nettop, surprisingly it works great even when i max out the ram 99%, no freezing, no lockup, no stutter, it just finds a way to release more ram.

I'm surprised. It must do a good job of handling the swap file.

I use tiny-core-linux on two netbooks with similar specs in terms of processor & ram (eee pc). I can have my spreadsheet program,* my word processor,* and Opera web browser open and still have less than 64mb ram used. 

*gnumeric and abiword

---

### Post by fromthehill on 2009-12-07
I don't notice any speed difference between vista and 7 on fast systems like my dual core 2ghz laptop.

in a virtual machine however win7 runs smoother than vista
I still disable things like libraries, homegroups and the superbar so it looks end works exactly like vista

---

### Post by Uncle Spellbinder on 2009-12-07
Win XP was better than Vista and 7 is leaps and bounds better than Vista.

But if I could get sound working with TVTime on Karmic, and could get to my router settings. I'd ditch Windows alltogether. 

Just my 2 cents.

---

### Post by forrestcupp on 2009-12-07
> **blueridgedog said:**
> 
When I re-installed his files drive to copy over his personal items, it advised that I did not have permission to delete some of the junk that came over that was no longer needed.  I had the same frustration all over again that I have had with Vista not letting me manage files.If you're advanced enough to even care about that, then you should be advanced enough to turn off the UAC and never have that problem again.  They made the UAC settings a lot easier and more customizable in 7 than it was in Vista.

> **fromthehill said:**
> 
I still disable things like libraries, homegroups and the superbar so it looks end works exactly like vista
What?  Homegroups are awesome.  They make it extremely easy to set up a home network of computers, assuming all your computers have 7 on them.  I like them because the password is built in and I don't have to keep logging in to other computers, even after a restart.

---

### Post by kerry_s on 2009-12-07
> **julianb said:**
> I'm surprised. It must do a good job of handling the swap file.

I use tiny-core-linux on two netbooks with similar specs in terms of processor & ram (eee pc). I can have my spreadsheet program,* my word processor,* and Opera web browser open and still have less than 64mb ram used. 

*gnumeric and abiword

yeah, i average between 50->70 percent most of the time, it's when i use the big programs like openoffice or watch movies while browsing the ram use climbs, other then that runs like a champ.
i switched to using the basic mode though, cause the aero stuff just got boring, i figured might as well save some memory. :lolflag:

here's a pic:

---

### Post by autonomy on 2009-12-07
> **kerry_s said:**
> upgrading the kids xp machines to win7, currently downloading a driver pack so i can finish. :lolflag:
dang things are so old, i don't even no what type of drivers to look for, there all a mix of parts.
printer drivers took some trickery: let 7 install, install dell's, delete the printer and let 7 reinstall
> **julianb said:**
> I use tiny-core-linux on two netbooks with similar specs in terms of processor & ram (eee pc). I can have my spreadsheet program,* my word processor,* and Opera web browser open and still have less than 64mb ram used. 

*gnumeric and abiword
abiword was a processor hog on my old laptop that ran xubuntu.
> **Uncle Spellbinder said:**
> if I could get sound working with TVTime on Karmic
yeah, tv is a pita

---

### Post by fela on 2009-12-07
To be fair you can't expect software to work 100% of the time. It's not possible.

---

### Post by Miguel on 2009-12-07
I find Windows 7 is an almost decent OS. It is halfway usable: the new taskbar is great (well, for what I do on Windows), but not having multiple workspaces is just awful. I can't work with less than 4 virtual desktops. I find I actually like libraries, and the behaviour of explorer is okay. One of the great features of 7 is being able to recover from a graphics crash with almost no losses. But the best feature of all is... the Windows Picture Gallery screensaver. I'm not joking, seeing your pictures appearing like in an album is unbelievably addictive. The current gnome equivalent is dead simple and miles from it.

> **forrestcupp said:**
> If you're advanced enough to even care about that, then you should be advanced enough to turn off the UAC and never have that problem again.  They made the UAC settings a lot easier and more customizable in 7 than it was in Vista.


I disagree there. The defaults of UAC in 7 are insecure. Period. Any program could lower the UAC settings in its default position (I'm not 100$ sure MS actually fixed this) without permission. In any case, using Windows without UAC is (more or less) like running Ubuntu without sudo.

---

### Post by drawkcab on 2009-12-07
I might try it on my htpc if I decide to get a netflix account but only because I can get a university discount.

---

### Post by froggyswamp on 2009-12-07
Deleting a file is still a problem, especially if it's a resource or dll and used by some (daemon) crapware, the system just says no (some crapware that comes with windows doesn't have an obvious way to remove it).
Also the app icons on the bottom panel are pretty big + open a few windows and you run quickly out of space - how do people deal with this?

---

### Post by autonomy on 2009-12-07
> **froggyswamp said:**
> the app icons on the bottom panel are pretty big + open a few windows and you run quickly out of space - how do people deal with this?
[FONT=Verdana]Someone on this thread gave me the idea to right-click the taskbar and change it to the slick Vista look, but the best I could do was change the icons to smaller ones; so another one of my gripes is somewhat gone -- the gawky taskbar is cut down to size. Maybe the bland color is particular to Pro, and the sexy look may be in Home Premium or something.[/FONT]

---

### Post by alphaniner on 2009-12-07
> **froggyswamp said:**
> Also the app icons on the bottom panel are pretty big...

That's a new feature called pinning, I think.  When you have any of those apps open, the window will not have a normal rectangular window entry, so it actually saves space.  At least, that's how I remember it... I went back to the old quick-launch toolbar.

---

### Post by murderslastcrow on 2009-12-07
Just install dockbarX- it resizes with your gnome panel, and also supports all the functions of the superbar besides jumplists.

P.S. What's Windows? Apparently there have been 7 versions of it and I'm just now hearing about it. Is it any good?

---

### Post by kerry_s on 2009-12-07
> Maybe the bland color is particular to Pro, and the sexy look may be in Home Premium or something.

if you use aero, you can use what ever color you want.

---

