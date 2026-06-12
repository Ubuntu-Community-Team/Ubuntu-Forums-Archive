---
title: "running windows apps"
date: 2009-10-10
forum: The Cafe
---

### Post by MelDJ on 2009-10-10
what's the best way to run windows apps (without installing windows)?
is it:
1. wine
2. ReactOS: [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)
3. Virtualbox ?

any feedback will be greatly appreciated :)

---

### Post by RichardLinx on 2009-10-10
A mix of wine and virtualbox. Though technically to run Windows applications in virtualbox you'd be installing windows. Just it would be more like an application running through Linux via virtualbox.
ReactOS.. *Laughs*
Just kidding, I've never used ReactOS but I know it's designed to be able to run windows applications. (As well as do some other things I don't know about).

---

### Post by dyingsun on 2009-10-10
Virtualbox is basically like having another PC embedded on your desktop. There do seem to be some limitations though. I was running 7 with all different apps (Office 2007 apps, Dreamweaver, SQL server, Visual Studio, plus various games, all within a Virtualbox (PUEL edition, not OSE). They worked, though they started to slow down a bit, as you can imagine. Ended up building a new machine for the .NET (*spit*) stuff. But yeah it works well, Virtualbox.

WINE doesn't run everything, but what it does run, it runs fast, usually. I'm using Crossover ATM (its commercial, though), which is built on WINE anyway. It's like a user-friendly front end for WINE.

To run everything you want to run, you may need a combination of methods.

---

### Post by Eisenwinter on 2009-10-10
> **RichardLinx said:**
> ReactOS.. *Laughs*
Just kidding, I've never used ReactOS but I know it's designed to be able to run windows applications. (As well as do some other things I don't know about).
Trust me, don't try to depend on ReactOS, it's very bug prone.

Applications always crash, and the system itself crashes every 40 minutes or so, depending on what you're doing.

I'd say the best way is VirtualBox, it's more stable than wine in my experience.

---

### Post by howefield on 2009-10-10
> **MelDJ said:**
> what's the best way to run windows apps (without installing windows)?
is it:
1. wine
2. ReactOS: [http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)
3. Virtualbox ?

any feedback will be greatly appreciated :)

Depends on the application you are trying to run, if it is well supported in wine, it will run perfectly.

You can't use Virtualbox to run windows applications without installing windows, thereby going against your criteria... but this is the best way for certain applications that are not (well) supported by wine. (There are of course higher demands on your system running 2 or more simultaneous operating systems).

Reactos seems to get a laugh every time it is mentioned, appears well intentioned but it seems to me that if it ever gets to be something usable, windows will have moved on to such an extent that Reactos will be somewhat dead in the water in any event.

---

### Post by MelDJ on 2009-10-10
is ReactOS that useless?:smile:

---

### Post by howefield on 2009-10-10
> **MelDJ said:**
> is ReactOS that useless?:smile:

Hmm.. was this your intention ?

(Given that Reactos was the only one you felt the need to post a link for).

---

### Post by cguy on 2009-10-10
> **Eisenwinter said:**
> Trust me, don't try to depend on ReactOS, it's very bug prone.

Applications always crash, and the system itself crashes every 40 minutes or so, depending on what you're doing.

I'd say the best way is VirtualBox, it's more stable than wine in my experience.
Sounds like Windows :P

---

### Post by 3rdalbum on 2009-10-10
> **MelDJ said:**
> is ReactOS that useless?:smile:

It's alpha. Or actually, I think it's pre-alpha.

---

### Post by MelDJ on 2009-10-10
> **howefield said:**
> Hmm.. was this your intention ?

(Given that Reactos was the only one you felt the need to post a link for).

no!! i just found out about it today. and wanted to know what people think. and since i never saw it at the forums, i thought that it would be appropriate to give people the link to it so that they know what it is. and i assume that almost everyone knows about Wine and Virtualbox already so i didn't include theirs

---

### Post by howefield on 2009-10-10
> **3rdalbum said:**
> It's alpha. Or actually, I think it's pre-alpha.

From the Reactos website..

*"Please bear in mind that ReactOS 0.3.10 is still in alpha stage, meaning it is not feature-complete and is not recommended for everyday use."*

---

### Post by howefield on 2009-10-10
> **MelDJ said:**
> no!! i just found out about it today. and wanted to know what people think. and since i never saw it at the forums, i thought that it would be appropriate to give people the link to it so that they know what it is. and i assume that almost everyone knows about Wine and Virtualbox already so i didn't include theirs

OK, I'm glad about that, it just struck me that this might be a disguised bash Reactos thread, with you providing a link which makes it very clear that Reactos is not at a stage where it can be confidently used for everyday use, making your poll a bit of a Hobsons choice.

---

### Post by MelDJ on 2009-10-10
> **howefield said:**
> OK, I'm glad about that, it just struck me that this might be a disguised bash Reactos thread, with you providing a link which makes it very clear that Reactos is not at a stage where it can be confidently used for everyday use, making your poll a bit of a Hobsons choice.

if anybody tries doing that or tries to start a flame war, i wont think twice of asking the mods to close this. SO, please post on what you think is the best way to run windows apps in a civil manner:popcorn:

---

### Post by doorknob60 on 2009-10-10
You can't run Windows apps in Virtualbox without installing Windows, because you need to install Windows to use it :P But I vote for Wine, Virtualbox isn't good for games and stuff, which is what a lot of people want to run Windows apps for. Also Wine runs MS Office pretty well. I do use Virtualbox occasionaly, mainly for transferring stuff to my TI-84+, which only works on Windows x86, so I have XP installed in Virtualbox for that and a few other things.

---

### Post by MelDJ on 2009-10-10
> **doorknob60 said:**
> You can't run Windows apps in Virtualbox without installing Windows, because you need to install Windows to use it :P But I vote for Wine, Virtualbox isn't good for games and stuff, which is what a lot of people want to run Windows apps for. Also Wine runs MS Office pretty well. I do use Virtualbox occasionaly, mainly for transferring stuff to my TI-84+, which only works on Windows x86, so I have XP installed in Virtualbox for that and a few other things.

hm..i read here:[http://forums.virtualbox.org/viewtopic.php?t=16](http://forums.virtualbox.org/viewtopic.php?t=16) that virtualbox only supports directX 8 and not 7 or 9. weird isn't it

---

### Post by khelben1979 on 2009-10-12
I voted [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29").

I don't want to run [VirtualBox]("http://en.wikipedia.org/wiki/Virtualbox") on my computer..

---

### Post by NoaHall on 2009-10-12
Why not run virtual box? You can stop the junk it loads up by itself from starting, and only run them when needed.

---

### Post by khelben1979 on 2009-10-12
> **NoaHall said:**
> Why not run virtual box? You can stop the junk it loads up by itself from starting, and only run them when needed.

I only have 1 GB of RAM and I've seen virtualbox in action a couple of years ago (2004?). I'll probably use it in the future. Don't feel I have a need for it either.

---

### Post by otetiani on 2009-10-12
I started with Crossover Games (with the free give away) and it worked so well for WOW I decided to try Crossover Linux Pro edition ($70.00).

I needed to run Excel and Access for work and open office didn't work for my application.

Only been using for 2 months but has been great, can even run IE.

---

### Post by Simian Man on 2009-10-12
wine is by far the best when it works.  It integrates apps into the desktop fairly well and runs with decent speed and needs no windows installation.

Virtualbox always runs things flawlessly since you are actually running a windows OS when you use it.  However, it can be too much for older machines, doesn't usually run games fast enough to be at all playable and needs a Windows installation.


> **khelben1979 said:**
> I voted [Wine]("http://en.wikipedia.org/wiki/Wine_%28software%29").

I don't want to run [VirtualBox]("http://en.wikipedia.org/wiki/Virtualbox") on my computer..

Thank you so much for your wikipedia links.  I would be lost in this forum without your thoughtful links :\

---

### Post by khelben1979 on 2009-10-12
> **Simian Man said:**
> Thank you so much for your wikipedia links.  I would be lost in this forum without your thoughtful links :\

You're welcome! Some people who reads Ubuntu.org might not always be experts and it also helps if one feels tired as well.

---

### Post by MelDJ on 2009-10-14
> **Simian Man said:**
> wine is by far the best when it works.  It integrates apps into the desktop fairly well and runs with decent speed and needs no windows installation.

Virtualbox always runs things flawlessly since you are actually running a windows OS when you use it.  However, it can be too much for older machines, doesn't usually run games fast enough to be at all playable and needs a Windows installation.




Thank you so much for your wikipedia links.  I would be lost in this forum without your thoughtful links :\

thats why i did not place their links

---

### Post by misfitpierce on 2009-10-14
Other - I don't bother running windows apps. Migrated off them a long time ago :P

---

