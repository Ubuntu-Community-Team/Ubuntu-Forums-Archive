---
title: "what about an awareness campaign for windows developers to program for Wine?"
date: 2008-05-26
forum: The Cafe
---

### Post by madjr on 2008-05-26
i think that **Wine 1.0** would be mature enough as a viable platform.

Programming with Wine compatibility would be an excellent way to make apps crossplatform without changing so much the code. In fact some apps just need a few small tweaks from their devs.

a good example is **µTorrent**. **They consider [COLOR="DarkOrchid"]Wine[/COLOR] a windows platform!**

> Download **µTorrent** now - It's Free.
[IMG]http://download.utorrent.com/images/download/win.gif[/IMG][COLOR="DimGray"]**For [COLOR="DarkOrchid"]Wine[/COLOR], Windows 95 (Winsock2), 98/ME, NT/2000, XP, 2003, and Vista**[/COLOR].
[http://www.utorrent.com/download.php](http://www.utorrent.com/download.php)

am speaking about windows only developers, that don't want to change their **programming platform** anytime soon. But would like to target "**another windows platform**": Wine.

the problem with Wine is that there's no campaign going on to make developers aware of it.

Am sure some developers would follow the example of **µTorrent** if they knew what Wine was.

i also would like **native ports**, but programming from **scratch** for linux sometimes is not cost-effective, but tweaking your app for Wine is way faster (i.e: google picassa)

a good campaign might even **double the number of apps currently running in Wine** without over-working the poor Wine devs.

I know i am doing my share. I've spoken to 2 or 3 windows-only app developers and they've shown interest (they didn't even knew it existed)

any thoughts or problems?

---

### Post by tigerplug on 2008-05-26
I don't think there is any chance of this happening.

I mean ... the purpose of Wine is to run apps that were written for Windows. Why would developers change the way they develop for wine specifically.

I think that this would just dig holes for the Ubuntu community. What we need to be asking is for are ports of applications from windows so that they will run on native debian based distros.

---

### Post by fatality_uk on 2008-05-26
> Programming with Wine compatibility would be an excellent way to make apps crossplatform without changing so much the code.

You can't really program for WINE compatibility! WINE is the Windows compatibility layer in Linux, so programming to be compliant with WINE, means programming for Windows, simple as.

---

### Post by daverich on 2008-05-26
what would be more helpful is that when developers ask them for help to support wine,- that they actually did.

Check out reaper - [www.reaperaudio.com](www.reaperaudio.com)

He's one of the few developers who actively tries to make his windows and osx program work with WINE. 

A few times he's come up against stuff thats caused a problem and has asked for help with WINE,- particular to do with the GUI being sluggish under WINE,- and he's not had any help afaik.

In this case I'm pretty sure he's going to work on a linux native version soon-ish anyhow,- but still, a little more help would be , err , helpful.

Kind regards

Dave Rich

---

### Post by Mr. Picklesworth on 2008-05-26
The idea is undoubtedly interesting, but I would prefer it to be implemented in only a parallel universe. The prevalence of Wine apps and Windows-style software that does not fit the platform would only reinforce a notion of desktop Linux being a cheap alternative to Windows. That is something I hope we can avoid!

Besides, would most of those applications really be as good under Linux, anyway? A key advantage of Linux on the desktop is that the platform developers are not in direct competition with all the developers working with their platform. (In contrast to Windows). As a result, we see applications working really well to integrate with platform-specific goodies instead of trying to reimplement them on their own. That, and many other things, makes the style of Windows applications incompatible with Linux - Wine or not.

...Not that it isn't worth a try, for the sake of options. I, for one, will never recommend Wine as a point of entry to the Linux platform, but as another suitable platform worth targetting, it has a place.

---

### Post by klange on 2008-05-26
I'd much rather see them use Mono. That way things are actually ported to Linux rather running in a compatibility layer, they can use native widget toolkits, run faster, etc. Wine was made to make things easier for users, not for developers, whereas Mono was made for developers *and* users.

---

### Post by fatality_uk on 2008-05-26
*Ducks for cover*

---

### Post by smartboyathome on 2008-05-26
From the standpoint of a buisiness owner, this would be what they prefer, as there is less change in the code and thus less to be payed for development. From the user's standpoint, they would rather have it done with Mono or even natively because it would mean that it were faster and looked better.

---

### Post by madjr on 2008-05-26
> **smartboyathome said:**
> From the user's standpoint, they would rather have it done with Mono or even natively because it would mean that it were faster and looked better.

not entirely true.

**as long as it works, users really don't care if it's [COLOR="Purple"]Wine[/COLOR] or mono**

only a linux purist would care more.

just take a look at the **google sketchup** release announcement this month.

[http://209.85.215.104/search?q=cache:SPMCgJ3wAmkJ:sketchupdate.blogspot.com/2007/09/now-even-better.html+sketchup+wine+linux&hl=es&ct=clnk&cd=12&gl=do&client=firefox-a](http://209.85.215.104/search?q=cache:SPMCgJ3wAmkJ:sketchupdate.blogspot.com/2007/09/now-even-better.html+sketchup+wine+linux&hl=es&ct=clnk&cd=12&gl=do&client=firefox-a)

in fact I'll quote some of the users asking for better **Wine compatibility**:


[I]R Adams said...

    Google, thank you for helping to keep Linux viable by porting your killer app, GEarth. Also, nice work with custom wine install for Picasa. **Anxiously awaiting a version of SketchUp Pro that runs flawlessly on Linux, either natively or via [COLOR="Purple"]wine[/COLOR]**.

    Thanks.[/I]
[http://sketchupdate.blogspot.com/2007/09/now-even-better.html#comment-1013523579612138726](http://sketchupdate.blogspot.com/2007/09/now-even-better.html#comment-1013523579612138726)

------------------

[I]I'm not saying this to be annoying, but yeah, I buy a **Linux** version. and don't bother with "Layout"

**You could even do the whole [COLOR="Purple"]wine[/COLOR] thing a la [COLOR="Sienna"]Picasa[/COLOR] and I would live with it**...[/I]


-----------------

[I]I hope Google supports [COLOR="Purple"]**Wine**[/COLOR] since it looks like a few of us depend on it for a variety of Google products...
My dream is
sudo aptitude install sketchup
**Thanks God for [COLOR="Purple"][B]Wine**[/COLOR] and the people who build and support it...[/B]
For that matter, Thanks God the sun is always shining in Sketchup :)[/I]

[http://sketchupdate.blogspot.com/2007/09/now-even-better.html#comment-2081679010238282792](http://sketchupdate.blogspot.com/2007/09/now-even-better.html#comment-2081679010238282792)

---

### Post by MadsRH on 2008-05-26
I'm not sure what the right way to do this "awareness" would be, but there is something very true to this idea and the thoughts posted in this thread. :lol:

---

### Post by phrostbyte on 2008-05-26
How many new software titles (other then maybe video games) are written with Win32? I think the .NET Framework is the new thing now, and that is more to do with Mono.

---

### Post by klange on 2008-05-26
.NET is the current "thing", and programs written for it are some of the least supported through Wine. I really don't care what gets businesses, etc. over to Linux as long as they see the light.
/me goes back to Monodevelop to continue working on his IM client...

---

### Post by billgoldberg on 2008-05-26
> **madjr said:**
> i think that **Wine 1.0** would be mature enough as a viable platform.

Programming with Wine compatibility would be an excellent way to make apps crossplatform without changing so much the code. In fact some apps just need a few small tweaks from their devs.

a good example is **µTorrent**. **They consider [COLOR="DarkOrchid"]Wine[/COLOR] a windows platform!**


[http://www.utorrent.com/download.php](http://www.utorrent.com/download.php)

am speaking about windows only developers, that don't want to change their **programming platform** anytime soon. But would like to target "**another windows platform**": Wine.

the problem with Wine is that there's no campaign going on to make developers aware of it.

Am sure some developers would follow the example of **µTorrent** if they knew what Wine was.

i also would like **native ports**, but programming from **scratch** for linux sometimes is not cost-effective, but tweaking your app for Wine is way faster (i.e: google picassa)

a good campaign might even **double the number of apps currently running in Wine** without over-working the poor Wine devs.

I know i am doing my share. I've spoken to 2 or 3 windows-only app developers and they've shown interest (they didn't even knew it existed)

any thoughts or problems?

Just because an windows app works with wine doesn't make it a cross-platform app.

If you are running utorrent in wine in linux, then you really shouldn't be using linux to begin with. You would be better of downloading an illegal copy of xp.

---

### Post by madjr on 2008-05-26
> **billgoldberg said:**
> Just because an windows app works with wine doesn't make it a cross-platform app.

If you are running utorrent in wine in linux, then you really shouldn't be using linux to begin with. You would be better of downloading an illegal copy of xp.

i don't agree with your statements. Neither would the **google devs**.

Thanks to Wine linux has more users and more apps working.

it works with wine = it works with linux.

i have **picassa** installed, you saying i should leave linux then?

you're incentivating piracy, just because **you feel like it**...

you like it or not am staying.

---

