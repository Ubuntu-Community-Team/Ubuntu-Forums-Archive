---
title: "uTorrent not working with Wine??"
date: 2011-01-08
forum: Wine
---

### Post by mufc on 2011-01-08
hello,
I am new to the forum so I opened the thread in general section.

I wanna use utorrent in ubuntu, I downloaded the wine, I downloaded the utorrent, I did everything they said in here [http://www.blogsolute.com/install-utorrent-client-server-ubuntu-10-maverick/12213/ ]("http://www.blogsolute.com/install-utorrent-client-server-ubuntu-10-maverick/12213/")but it's not working! so i tried to create launcher for it like they say in here [http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml](http://news.softpedia.com/news/uTorrent-under-Ubuntu-in-3-Easy-Steps-49037.shtml) . still not working! i mean it's not opening, when i click on the launcher, it says "utorrent is already running but not responding..." even when I've just turned on the computer! why is it not working? please help :(

---

### Post by cascade9 on 2011-01-08
Why not just use a linux native torrent client?

---

### Post by Bucky Ball on 2011-01-08
Tried Azureus? It's in the repositories and quite similar and guaranteed to run without the hassle of Wine. As cascade9 mentions you're better off with something native if you can find it. It you find you need to use a lot of Windows software it might be a better idea to dual boot or forget Linux. 

System >Admininstration >Synaptic Package Manager, search for and install Azureus. If you don't like, uninstall the same way. Transmission is the default torrent client in Ubuntu (which you already have installed in Applications >Network from memory) but I don't dig it much. ;)

---

### Post by mufc on 2011-01-08
i don't wanna offend you but i wanna use utorrent not anything else. so if you know something about my problem please help.

---

### Post by Bucky Ball on 2011-01-08
No probs. You should have posted this in the appropriate Wine forum and you'd probably have gotten more help:

[http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

A kind mod might move it for you as it is against forum rules to double-post.

---

### Post by Elfy on 2011-01-08
Please post threads about windows apps in the wine forum.

Moved to wine

Found a mod - not sure if it's a kind one ;)


> i don't wanna offend you but i wanna use utorrent not anything else. so if you know something about my problem please help.
__________________
UBUNTU IS THE BEST! This made me laugh a bit, in a not taking the mickey way  - if ubuntu is best why use a non-ubuntu torrent client :)

---

### Post by mufc on 2011-01-08
well i don't know if the problem here is wine or something else but anyway, waiting for your help people!

---

### Post by dino99 on 2011-01-08
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22031](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22031)

---

### Post by mufc on 2011-01-08
> **forestpiskie said:**
> Please post threads about windows apps in the wine forum.

Moved to wine

Found a mod - not sure if it's a kind one ;)


This made me laugh a bit, in a not taking the mickey way  - if ubuntu is best why use a non-ubuntu torrent client :)

i said ubuntu is the best i didn't say transmission is better than utorrent LOL ubuntu>windows&mac utorrent>others LOL

---

### Post by mufc on 2011-01-08
> **dino99 said:**
> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=22031](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22031)

i tried with utorrent 2.0.4 still says the same thing :(

---

### Post by cascade9 on 2011-01-08
@ forestpiskie- same here, but I didnt know if it was a good idea to post that.....obviously its fine :) 

> **mufc said:**
> i don't wanna offend you but i wanna use utorrent not anything else. so if you know something about my problem please help.

May I ask why? 

BTW, transmission is just the defualt torrent client.

---

### Post by Bucky Ball on 2011-01-08
> **cascade9 said:**
> 

BTW, transmission is just the defualt torrent client.

Yea, there's a few other options:

[http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html](http://www.ubuntugeek.com/list-of-bittorrent-clients-available-in-ubuntu.html)

As I mentioned, Azureus (now Vuze) is virtually the same as utorrent (was a heavy user of utorrent once upon a time in Windows world), main difference being there is no search function to find torrents. ;)

---

### Post by dondiego2 on 2011-01-08
I liked uTorrent too, having moved from Windows last year and using a private torrent site that required it.  I did get it to work but I don't remember if I did anything special.  Now I use Deluge as it is native to Linux, is a lot like uTorrent and the private torent site I am on now supports it.  So now I don't miss uTorrent at all.

I do recall when I had it running in Wine I could never get to show up in the programs on the menu.  I had to always search for it in "Wine HD" and click on the program to run it.  I don't remember exactly, I don't even have Wine on my computer now as that was the only thing I used it for.

---

### Post by alaukikyo on 2011-01-09
> **mufc said:**
> i said ubuntu is the best i didn't say transmission is better than utorrent LOL ubuntu>windows&mac utorrent>others LOL

try [deluge]("apt://deluge") (just try it) 
it blows utorrent.

---

### Post by marl30 on 2011-01-09
Utorrent alpha is available for Linux:[http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux).

However, there is no PPA or deb file available as yet, so it has to be compiled. It's also only available in 32 bit for now. It should be very buggy at this stage, being at the alpha stage. 

I also felt like nothing else could replace Utorrent when I just switched to Ubuntu, but after using Transmission, Deluge, and even Ktorrent, I felt satisfied.

---

### Post by tuahaa on 2011-01-10
I want to use utorrent via WINE ONLY because if I run any native linux client, the speed is 4-5 less than what I would have gotten on windows. I really love linux but I also want to torrent effectively so I'd rather use wine. Apparently, this fixes the problem.

---

### Post by cascade9 on 2011-01-10
I've run both utorrent and a few of the linux native torrents, and speeds are pretty much the same. 

tuahaa, you could be having a UPnP/portforwarding issue, that would explain slow speeds.

---

### Post by alaukikyo on 2011-01-10
> **tuahaa said:**
> I want to use utorrent via WINE ONLY because if I run any native linux client, the speed is 4-5 less than what I would have gotten on windows. I really love linux but I also want to torrent effectively so I'd rather use wine. Apparently, this fixes the problem.

i would say that is IMPOSSIBLE.
which linux native client you are talking about?

---

### Post by mufc on 2011-01-11
transmission doesn't have transfer cap which i needed most, but i'll try azureus.

---

### Post by cascade9 on 2011-01-11
Are you sure transmision doesnt have a bandwidth setting, any decent torrent client should. I though it used to (preferences-> bandwidth). I know deluge does, thats what I use.

---

### Post by Yeeha on 2011-01-11
Transmission has bandwidth settings. Azureus from time to time feels unresponsive so if you are used to things opening and closing in a blink then its not good choice.

---

### Post by mufc on 2011-01-11
i need transfer cap, it's not bandwidth, if you enable transfer cap it stops downloading when it reaches a limit, file size limit not speed limit. transmission and deluge doesn't have one.

---

### Post by cascade9 on 2011-01-11
> **mufc said:**
> i need transfer cap, it's not bandwidth, if you enable transfer cap it stops downloading when it reaches a limit, file size limit not speed limit. transmission and deluge doesn't have one.

I dont know about transmission, but deluge does (via a plugin) 

[http://dev.deluge-torrent.org/wiki/Plugins](http://dev.deluge-torrent.org/wiki/Plugins)

[http://forum.deluge-torrent.org/viewtopic.php?f=9&t=34343](http://forum.deluge-torrent.org/viewtopic.php?f=9&t=34343)

---

### Post by mufc on 2011-01-12
bottom line uTorrent is the best *for me* and i want *it*, so anyone who can solve my real problem please?

---

### Post by _outlawed_ on 2011-01-12
uTorrent in wine sucks. You can't delete torrents, so your main torrent download screen gets cluttered with junk you can't remove.

I suggest using Deluge until uTorrent comes out with a full stable release of a linux native client for it.

---

### Post by Skapunker on 2011-02-08
Any luck with this?  I've been having the exact same problem.  I want to use utorrent because I have not been able to get the same speeds with ubuntu clients (I've been using mostly Deluge) that I can with utorrent in Windows.  Ports are forwarded, but it's still a lot slower.  So I want to try utorrent to see if it helps with the speed.  When I try to run utorrent it looks like it's going to start, but then does nothing.  The process for utorrent is running but it's status is sleeping, which is why when I try to run it again wine says it's already running, like it was for the op.  I'm thinking it's a problem with the wine installation because I was having a similar problem with black ops trying to install it with playonlinux and it would do nothing.  I got that working by messing with and installing a new version of playonlinux.  I've tried with both the beta and the stable versions of wine, but it hasn't made a difference.

I'm going to keep on working on it and I'll post if I have any luck.  If anyone has any ideas let me know, I'll try anything, really want to fix this.

---

### Post by YokoZar on 2011-02-10
I believe uTorrent is aware of the problem and are actually releasing a new version of uTorrent to fix it.

You can also try the uTorrent 1.3x alphas, which should work in Wine.

---

### Post by schtufbox on 2011-02-10
I used to use uTorrent in Linux, but when it stopped workign properly I switched to using qBittorrent, and found it to be better, IMO.
So much so I even use the windows version on one of my windows PC's

---

### Post by kelvin spratt on 2011-02-10
> **schtufbox said:**
> I used to use uTorrent in Linux, but when it stopped workign properly I switched to using qBittorrent, and found it to be better, IMO.
So much so I even use the windows version on one of my windows PC's

Use a older versions for now as there is a problem with high CPU in the last couple of releases in wine. and yes Utorrent is by far the leader at present but Deluge and others are catching up very fast.
To those saying you should only be using Linux apps in Linux stop trying to dictate that's what is wrong with the world today people think they have the right to force others to think the same rather sad really.

---

### Post by Skapunker on 2011-02-12
> **YokoZar said:**
> I believe uTorrent is aware of the problem and are actually releasing a new version of uTorrent to fix it.

You can also try the uTorrent 1.3x alphas, which should work in Wine.

Thanks for the info, but did you mean 2.3x alhphas?  I only see the 2.2 beta which I tried with the same results.

I used Windows again to download a bunch of stuff and the speed difference was huge, but I just tried some of the same torrents again in Ubuntu and now I'm getting the full speed using Deluge and I didn't change anything, so for now I'm not so worried about it, but will continue to see if I can get uTorrent to work and hopefully they'll release a new version that works better.

---

### Post by DoktorSeven on 2011-02-12
According to WineHQ there is an "unresolved bug" with uTorrent 2.2 and current Wine, so it will not work at all.  3.0 beta seems to work though, get it from here:
[http://forum.utorrent.com/viewtopic.php?id=63247](http://forum.utorrent.com/viewtopic.php?id=63247)

---

### Post by jrz on 2011-02-21
> **mufc said:**
> bottom line uTorrent is the best *for me* and i want *it*, so anyone who can solve my real problem please?

Have you tried the Linux version of utorrent yet? It works much better than the Windows version under wine for me, and although still an Alpha I've not experienced any problems with it.
It took a small amount of effort to install it and run it, but worth the effort.

---

### Post by Skapunker on 2011-04-06
I did finally get uTorrent working.  I had to run winetricks and use the install an app function and that got it working.

---

