---
title: "I have 3GB of ram..."
date: 2009-07-07
forum: The Cafe
---

### Post by CJ Master on 2009-07-07
...and I only ever use around 200-300 megs of it. (I don't have swap.)

Suggestions?

(I'm looking for ways to make apps faster, etc, usefull things. Possibly uploading all the programs I use in ram? *drools*)

---

### Post by accLinux on 2009-07-07
Yeah, I have 2 GB Ram and never max it out on Linux, usually use about 300MB of it. (I tried the windows 7 RC + Crysis demo, used it all.) 


Its not like I have a high-end PC either, P4 3.00Ghz, EVGA Geforce 8400GS 512MB. (and 2 GB Ram, 400Mhz)

---

### Post by Ocxic on 2009-07-07
Ubuntu will use ram as needed, leave your computer on long enough and it will fill up.

---

### Post by michaelzap on 2009-07-07
> **Ocxic said:**
> Ubuntu will use ram as needed, leave your computer on long enough and it will fill up.

No it won't. I have 4GB of RAM and I've never used more than a gig, no matter how long my computer's been on or what I'm doing. I think I should install preload and see if I notice any extra pep.

---

### Post by CJ Master on 2009-07-07
> **Ocxic said:**
> Ubuntu will use ram as needed, leave your computer on long enough and it will fill up.

Well, except for the fact I use Arch and there's no background applications running (that I don't need.)

I heard you had to config preload for it to work, but I'm not quite sure how.

---

### Post by andrewabc on 2009-07-07
install preload.

My recently started ubuntu is using 680mb ram.
Preload is using an additional
[Tue Jul  7 23:52:35 2009] readaheading 2784 files
[Tue Jul  7 23:52:56 2009] 1547660kb available for preloading, using 1444600kb of it

I have 3gb ram.

Read [Utilizing RAM](http://ubuntuforums.org/showthread.php?t=1205154) thread created two days ago for a similar conversation.

You do not need to config preload at all. In ubuntu you install it and that is it. It runs on its own, no need to touch it. You can edit and config it if you want.

---

### Post by MikeTheC on 2009-07-07
Well, I have 4GB of RAM in my MBP. So there!  \\:D/  :tongue:

---

### Post by .Maleficus. on 2009-07-07
> **michaelzap said:**
> No it won't. I have 4GB of RAM and I've never used more than a gig, no matter how long my computer's been on or what I'm doing. I think I should install preload and see if I notice any extra pep.
Yes it will.  From Linux Journal:
[quote=Linux Journal]When extra physical memory is not in use, the kernel attempts to put it to work as a disk buffer cache. The disk buffer stores recently accessed disk data in memory; if the same data is needed again it can be quickly retrieved from the cache, improving performance. The buffer grows and shrinks dynamically to use the memory available, although priority is given to using the memory for paging. Thus, all the memory you have is put to good use[/quote]
[http://www.linuxjournal.com/article/2770](http://www.linuxjournal.com/article/2770)

That article might help you a little OP, but using something like preload would be nice also.

---

### Post by CJ Master on 2009-07-07
Well I DO actually use preload. But I still only use about 300 megs of memory. There has to be some things else?

---

### Post by Gizenshya on 2009-07-07
I don't like pre-loading.  It causes unnecessary hard drive wear.  Hard drive life is far more important than a half a second here and there.

If I want programs to start faster.. I just don't close them.  I use the compiz cube, so I just go to another workspace and then come back later when I need the program.  I can use all the RAM I want :)

---

### Post by sdlynx on 2009-07-07
> **michaelzap said:**
> No it won't. I have 4GB of RAM and I've never used more than a gig, no matter how long my computer's been on or what I'm doing. I think I should install preload and see if I notice any extra pep.

same. I installed preload and same deal so far.

---

### Post by Warpnow on 2009-07-08
Isn't there a boot option that will load the OS files into ram?

---

### Post by Gilabuugs on 2009-07-08
for avid firefox users:

[http://webupd8.blogspot.com/2009/05/speed-up-firefox-by-mounting-profile-in.html](http://webupd8.blogspot.com/2009/05/speed-up-firefox-by-mounting-profile-in.html)

---

### Post by PurposeOfReason on 2009-07-08
What is with all the RAM threads as of late? It's not a problem at all to have free RAM. It's like saying, "my CPU is usually idle, how can I put it to work?". It's not a problem to have unused resources (though folding is cool ;)).

---

### Post by sdlynx on 2009-07-08
> **PurposeOfReason said:**
> What is with all the RAM threads as of late? It's not a problem at all to have free RAM. It's like saying, "my CPU is usually idle, how can I put it to work?". It's not a problem to have unused resources (though folding is cool ;)).

and BOINC.

haha I started the other thread.  you can actually relate it just like folding, its like you have this awesome hardware but no way to put it to use

---

### Post by CJ Master on 2009-07-08
> **PurposeOfReason said:**
> What is with all the RAM threads as of late? It's not a problem at all to have free RAM. It's like saying, "my CPU is usually idle, how can I put it to work?". It's not a problem to have unused resources (though folding is cool ;)).

Because there's no point in having that extra ram if it doesn't do anything. And I barely use virtual machines or anything that takes more then 400megs of ram.

---

### Post by PurposeOfReason on 2009-07-08
> **CJ Master said:**
> Because there's no point in having that extra ram if it doesn't do anything. And I barely use virtual machines or anything that takes more then 400megs of ram.
Really what I'm saying is you shouldn't look for things to use resources on. My RAM on linux almost never gets past 600MB but I have 6GB. Why? When I do need it, it is there. You'll be hard pressed to find a way to be in constant use of more than 1GB of RAM other than always having a VM running. Notice on Windows you never go past 1.5GB unless you open a game, photoshop, or other intensive program? That is because those programs need it. If a program does not need that RAM, don't complain. Look into the basics of programming to see why this is and why it is a good thing.

Better too much than too little.

---

### Post by 3rdalbum on 2009-07-08
The Gnome System Monitor reports only the RAM that is in **active use**. In my case, 623 megabytes.

If you add the System Monitor applet to your panel and set it to show memory use, it will display the **total RAM** in use - including cache. In my case, 100% of it.

Some people don't understand how RAM makes things faster; one poster earlier was complaining that his CPU was at 100% and that only 25% of his RAM was in use, as though the RAM was an extra processor or something. The RAM is only a cache for data that will need to travel to the CPU or to a slower storage device, and it only stores what the CPU tells it to store. It doesn't just suck up data from your hard disk in the hope that the CPU might need it some time down the track.

---

### Post by sdlynx on 2009-07-08
> **3rdalbum said:**
> The Gnome System Monitor reports only the RAM that is in **active use**. In my case, 623 megabytes.

If you add the System Monitor applet to your panel and set it to show memory use, it will display the **total RAM** in use - including cache. In my case, 100% of it.

Some people don't understand how RAM makes things faster; one poster earlier was complaining that his CPU was at 100% and that only 25% of his RAM was in use, as though the RAM was an extra processor or something. The RAM is only a cache for data that will need to travel to the CPU or to a slower storage device, and it only stores what the CPU tells it to store. It doesn't just suck up data from your hard disk in the hope that the CPU might need it some time down the track.

Thanks for the tip about cache, I looked at mine and still only 41% used though (cache + used by programs) of my 4GB lol

---

### Post by Pasdar on 2009-07-08
I tried preload on my 4GB laptop, I didn't notice any difference in anything... making me doubt preload even does anything...

---

### Post by Hallvor on 2009-07-08
> **CJ Master said:**
> ...and I only ever use around 200-300 megs of it. (I don't have swap.)

Suggestions?

(I'm looking for ways to make apps faster, etc, usefull things. Possibly uploading all the programs I use in ram? *drools*)

I only have 512 MB and I hardly use swap at all. There is a limit as to how much RAM your computer can effectively use. I would like to have 3 GB of RAM, 150 gigabytes of hard drive space and a quad core processor. I don`t need it, but it would be nice. :lolflag:

---

### Post by 3rdalbum on 2009-07-08
> **sdlynx said:**
> Thanks for the tip about cache, I looked at mine and still only 41% used though (cache + used by programs) of my 4GB lol

If it's 41% used, then that's the amount of relevant data that can be cached.

Preload needs some time to learn what programs you run after you start up. Remember, there's only benefit in caching what you will use. There's negative benefit to caching what you won't use.

I've ripped some DVDs so my cache is full; but if I tried to rip that last DVD again, the first gigabyte would fly in like nobody's business :-)

---

### Post by sdlynx on 2009-07-08
> **3rdalbum said:**
> If it's 41% used, then that's the amount of relevant data that can be cached.

Preload needs some time to learn what programs you run after you start up. Remember, there's only benefit in caching what you will use. There's negative benefit to caching what you won't use.

I've ripped some DVDs so my cache is full; but if I tried to rip that last DVD again, the first gigabyte would fly in like nobody's business :-)

o lol cool

---

### Post by Firestem4 on 2009-07-08
You may be interested in this. Its a lot of work but you will certainly take your RAM for a walk..

[http://forums.gentoo.org/viewtopic-t-296892.html](http://forums.gentoo.org/viewtopic-t-296892.html)

---

### Post by imlinux on 2009-07-08
ship it to me, i still use 512M.:lolflag:

---

### Post by sdlynx on 2009-07-08
> **Firestem4 said:**
> You may be interested in this. Its a lot of work but you will certainly take your RAM for a walk..

[http://forums.gentoo.org/viewtopic-t-296892.html](http://forums.gentoo.org/viewtopic-t-296892.html)

this is intense!!  looks like too much work for me though...

---

### Post by Blacklightbulb on 2009-07-08
I have 1024 + 256 MB ram and I use it to it's max. Never use swap.

I use a program who loads the binaries of the applications I usually use (kinda cache). Unfortunately I forgot it's name. Can someone else help please!!:confused:

---

### Post by Blacklightbulb on 2009-07-08
Oh yeh right, the name's Preload

---

### Post by evermooingcow on 2009-07-08
and I'm here fighting to reduce resource consumption on my laptop and 512MB.

I got it down to ~70MB idle on a GUI desktop using a minimal WM and I can finally multitask somewhat with firefoxes and open office.

---

### Post by aktiwers on 2009-07-08
Move your Firefox profile into a small partition created in RAM. I did this following this guide:
[http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475)

And firefox is blazing fast!

---

### Post by andrewabc on 2009-07-08
> **aktiwers said:**
> Move your Firefox profile into a small partition created in RAM. I did this following this guide:
[http://ubuntuforums.org/showthread.php?t=1120475](http://ubuntuforums.org/showthread.php?t=1120475)

And firefox is blazing fast!

that means it moves the sqlite database (remembers websites for awesomebar) there as well? And it saves changes to hard drive when done?

*reads thread* hmm , looks like it does both. Thank you for the link!
I had problems with 20mb sqlite slowing down firefox a lot. Also when I go to add a bookmark I can hear hard disk thrashing when selecting different folders to put the bookmark into.

---

### Post by aktiwers on 2009-07-08
> **andrewabc said:**
> that means it moves the sqlite database (remembers websites for awesomebar) there as well? And it saves changes to hard drive when done?

*reads thread* hmm , looks like it does both. Thank you for the link!
I had problems with 20mb sqlite slowing down firefox a lot. Also when I go to add a bookmark I can hear hard disk thrashing when selecting different folders to put the bookmark into.

It makes backup to harddrive, which will be used onload as well. 
And yes it does take the whole profile, cache files, awesomebar, cookies etc..

In post 54 cheesepenguins shows how to make it take backup to HD upon closing Firefox, instead of the every 2 or 5 mins.
[http://ubuntuforums.org/showpost.php?p=7349064&postcount=54](http://ubuntuforums.org/showpost.php?p=7349064&postcount=54)

---

### Post by PurposeOfReason on 2009-07-08
> **evermooingcow said:**
> and I'm here fighting to reduce resource consumption on my laptop and 512MB.

I got it down to ~70MB idle on a GUI desktop using a minimal WM and I can finally multitask somewhat with firefoxes and open office.
If you're fighting for RAM why are you using firefox and OO?

---

### Post by andrewabc on 2009-07-08
> **aktiwers said:**
> It makes backup to harddrive, which will be used onload as well. 
And yes it does take the whole profile, cache files, awesomebar, cookies etc..

In post 54 cheesepenguins shows how to make it take backup to HD upon closing Firefox, instead of the every 2 or 5 mins.
[http://ubuntuforums.org/showpost.php?p=7349064&postcount=54](http://ubuntuforums.org/showpost.php?p=7349064&postcount=54)

Does it save the ram to hard drive when firefox closes?

I mean it is not possible to lose 4:59 if I close it after the tutorial default of sync to hard drive every 5 min?

My wording is bad. Basic question: Every time I close firefox I want it to sync ram to hard drive so next time I open firefox it didn't 'lose' anything from previous session. This happens when following original guide (not the one quoted in this post).

Or does it only sync when you have 'scheduled tasks' time set (default 5 min according to tutorial)?
Or do I need to use the guide in quoted post in order for this to happen?

---

### Post by Saint Angeles on 2009-07-08
I only have about 2GB of RAM and the only way I can ever get Ubuntu to use anywhere near that amount is by running GIMP.

I have a LOT of 3rd party brushes (over 140MB!) and plugins installed that i've found at various websites. ever since I installed that insane amount of brushes, GIMP takes a while to start and it uses a LOT of RAM. I really don't think it should be using this much RAM for 140MB of brushes... does it sound like some sort of bug?

---

### Post by ArtF10 on 2009-07-08
> **PurposeOfReason said:**
> If you're fighting for RAM why are you using firefox and OO?

You shouldn't be using Ubuntu.

> **Saint Angeles said:**
> I **only** have **about 2GB** of RAM....

**HARDLY!**  There are some of us who are struggling with 512 MB!

---

### Post by Hallvor on 2009-07-09
Debian runs very well with 512 MB of RAM and a full Gnome desktop, IMHO. I remember Ubuntu Dapper did the same.

---

### Post by aktiwers on 2009-07-09
> **andrewabc said:**
> Does it save the ram to hard drive when firefox closes?

I mean it is not possible to lose 4:59 if I close it after the tutorial default of sync to hard drive every 5 min?

My wording is bad. Basic question: Every time I close firefox I want it to sync ram to hard drive so next time I open firefox it didn't 'lose' anything from previous session. This happens when following original guide (not the one quoted in this post).

Or does it only sync when you have 'scheduled tasks' time set (default 5 min according to tutorial)?
Or do I need to use the guide in quoted post in order for this to happen?

Yes your right. The tutorial only saves each 5 min. per defualt. 
Afterwards you could follow the guide in the quoted post to make it save whenever Firefox closes.

So basicly you might want to do both guides or set the defualt 5. mins to 60 mins or something like that..

---

### Post by legolas_w on 2009-07-09
> **CJ Master said:**
> ...and I only ever use around 200-300 megs of it. (I don't have swap.)

Suggestions?

(I'm looking for ways to make apps faster, etc, usefull things. Possibly uploading all the programs I use in ram? *drools*)



I have two gig (2  GB) of ram and sometimes it is 80-90% full and usually is 70% full. So if you have some spare module, lend me 2 GB of that 3 GB :D

---

### Post by CJ Master on 2009-07-09
> **legolas_w said:**
> I have two gig (2  GB) of ram and sometimes it is 80-90% full and usually is 70% full. So if you have some spare module, lend me 2 GB of that 3 GB :D

How do you even fill up 2GB of ram?!

---

### Post by legolas_w on 2009-07-09
> **CJ Master said:**
> How do you even fill up 2GB of ram?!


- One VirtualBox instance (OpenSolaris)
- OpenOffice or Ms-Office running in Wine
- FireFox, Thunderbird and Liferea
- SongBird, gmailchecker, 
- Java IDE
- Java EE server

These stuff usually occupy a fair portion of the memory.

---

### Post by mp3_freak_721 on 2009-07-09
I don't think you really need more than 2gb of ram personally. If all you are doing is browsing the internet, listening to music, typing up your english paper than why do you need oodles of ram? Maybe if you are a gamer and needed 4gb for a smooth system then by all means get the 4 gb. I used to have 512 mb myself. My system ran fine until I opened up Firefox. Then I started to run out of ram almost right away. Then upgraded to 2gb and I have a really speedy system. Do note that I am using a single core AMD Athlon 64 3200. :sad: I really need a dual core.

---

### Post by Jeruvy on 2009-07-09
You guys need to play with Blender....that will use your RAM ;)

---

### Post by blueshiftoverwatch on 2009-07-09
> **CJ Master said:**
> Well I DO actually use preload. But I still only use about 300 megs of memory. There has to be some things else?
I don't know if anyone else suggested this because I don't want to read through 5 pages of replies. But the new version of Firefox (3.5) has a secure browsing mode which prevents any data from being cached on the hard drive. I don't know if it instead caches the data onto the RAM, but I would assume it does. If that's the case why not use the secure browsing mode 100% of the time?

---

### Post by ubudog on 2009-07-09
Install preload.  sudo apt-get install preload

---

### Post by Bart_D on 2009-07-09
> **ubudog said:**
> Install preload.  sudo apt-get install preload

After installing updates, that's the first thing I do.  Whether it does anything is irrelevant.....just knowing it is there is all I need.

---

### Post by andrewabc on 2009-07-09
My firefox in ram got corrupted somehow.
I changed sync to HD to 1 min. I restarted computer at some point, and firefox 3.5 was all corrupted and acting very wierd. Had to use backup profile to restore and restart computer.

My guess is that with 1 min sync, that increases chance that when shutting down computer sync gets corrupted if syncing when shutting down?

---

### Post by CJ Master on 2009-07-10
> **blueshiftoverwatch said:**
> I don't know if anyone else suggested this because I don't want to read through 5 pages of replies. But the new version of Firefox (3.5) has a secure browsing mode which prevents any data from being cached on the hard drive. I don't know if it instead caches the data onto the RAM, but I would assume it does. If that's the case why not use the secure browsing mode 100% of the time?

I would assume for secure browsing it wouldn't store a cache at all. But I don't know, I'll try it out.

> Install preload. sudo apt-get install preload

Thanks, but mensioned about 3 times already. And I use Arch, pacman. >.<

---

### Post by arcdrag on 2009-07-10
This thread makes me wonder if car guys ask "hey guys, I have 300 horsepower but I only need 50 hp to go the speedlimit...any suggestions on how to use the rest?" in their forums.

---

### Post by jenkinbr on 2009-07-10
Just load a ton of super-high res images in gimp

Fills my 512 MB of ram and my 3gb swap no problem :)

---

### Post by CJ Master on 2009-07-10
> **jenkinbr said:**
> Just load a ton of super-high res images in gimp

Fills my 512 MB of ram and my 3gb swap no problem :)

Yes, I know how to fill ram, easy. The point is making use of the spare ram to make things faster.

---

### Post by andrewabc on 2009-07-12
> **aktiwers said:**
> In post 54 cheesepenguins shows how to make it take backup to HD upon closing Firefox, instead of the every 2 or 5 mins.
[http://ubuntuforums.org/showpost.php?p=7349064&postcount=54](http://ubuntuforums.org/showpost.php?p=7349064&postcount=54)

That extensions is not compatible with firefox 3.5 :(

So I had to edit install.rdf inside .xpi file and change max version to '3.5'

Also according to that post I am very confused by the 'script'
> The process is simple, edit the file "overlay.js" found in the content folder of the extension to have the full path to the script, e.g. /home/m00z0r/.firefox (where I have mine), highlighted in red below.
As far as I know firefox 3.5 is found in /home/user/.mozilla/firefox-3.5
What is the script and where is it supposed to be found? I opened overlay.js to edit, but not sure what directoty to point to. I am guessing the non rammed 'profile' folder (to backup to hard drive on firefox close)?

EDIT:
Hmm, I'm guessing by 'script' it means path to .tmpfs_firefox.sh file? That seems to work. In overlay.js I have it pointing to /home/myusername/.tmpfs_firefox.sh

Not sure why the person has //home//m00z0r//.firefox location with the // I wouldn't think // would work. And only has path location not even showing file, so that is confusing.

EDIT:
Yah, sync on close is not working good. When I open firefox after restart I get a "well this is embarrassing' tab open saying that firefox tabs did not close properly and I can load tabs or start fresh.

---

### Post by CJ Master on 2009-07-12
Wait, there's a command to mount folders, right? Well, isn't it possible to mount the folder with all the applications as the ram filesystem at bootup?

---

