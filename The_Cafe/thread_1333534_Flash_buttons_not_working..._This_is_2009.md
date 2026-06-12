---
title: "Flash buttons not working... This is 2009"
date: 2009-11-21
forum: The Cafe
---

### Post by Ric_NYC on 2009-11-21
What's the problem?

This is unbelievable.

---

### Post by NoaHall on 2009-11-21
64 bit or 32 bit? Where is the flash installed from?

---

### Post by Ric_NYC on 2009-11-21
> **NoaHall said:**
> 64 bit or 32 bit? Where is the flash installed from?


I have a 64 bit computer. I chose to install the 32 bit version of Ubuntu. I tried to update to the new Flash (10.1)... That's when the problems started.

I fixed it already. I installed and unistalled Flash many times until it started to work again. I don't know how it was solved.

Anyway. I think this kind of thing should not be happening in 2009.

Thank your for your reply.

---

### Post by slakkie on 2009-11-21
you're right, stuff is not supposed to break 2009. Now tell that to airliners, car manufactures, Apple, MS, and all kinds of businesses.

---

### Post by Ric_NYC on 2009-11-21
> **slakkie said:**
> you're right, stuff is not supposed to break 2009. Now tell that to airliners, car manufactures, Apple, MS, and all kinds of businesses.



If I cannot get simple things like a flash plugin working then I'm in trouble. Especially when flash is everywhere on the internet.

---

### Post by slakkie on 2009-11-21
Well, if you are posting in the beginners forum you are not supposed to install software from other sources then the official repo's. Stuff could break if you do.

---

### Post by scradock on 2009-11-21
> **slakkie said:**
> Well, if you are posting in the beginners forum you are not supposed to install software from other sources then the official repo's. Stuff could break if you do.
That's not very helpful - a whole bundle of folk are having problems with the repo version of Flash in Ubuntu 9.10. The sad fact is that integrating closed-source stuff is harder than making open-source programs work together. At the moment it looks as if Flash is a hit-or-miss sort of thing in Linux. See launchpad bug # 410407 for parts of the saga, including some workarounds.

---

### Post by Bios Element on 2009-11-21
Flash isn't hit/miss 99% of the time. Just people don't seem to find the right solution. One idea would be to grab flash player off the adobe website. It's always worked fine for me.

Oh, and complaining about things breaking isn't going to get more people helping you. It'll just annoy people who would otherwise help. >.<

---

### Post by sgosnell on 2009-11-21
+1

Go to the Adobe website, click on the Get Flash Player button, and it will install the proper version for your OS.  You may get a warning that a newer version exists in the software channel, but it's a false warning, ignore it, and continue with the installation, and it should work.  

If it won't, it's Adobe's fault.  It's their proprietary system, and their driver, so it's their responsibility to make it work.

---

### Post by Keyper7 on 2009-11-21
OP, could you please post a link to a site where this is happening?

I want to see if it happens with the version I'm using.

---

### Post by FuturePilot on 2009-11-21
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407")

---

### Post by toupeiro on 2009-11-21
I'm running 64-bit ubuntu as well, not experiencing the problems you are having.

Here's the thing about flash, its not ALWAYS a client problem.  Flash has a server/client relationship.  Are buttons not appearing on other flash enabled sites you go to?  If so, then there is a very, very strong chance its a client issue.  However, if that is the only site you are having an issue with, then there is some realistic chance that its the hosted flash content that could be causing the problem.  It happens.  Linux flash plugins do not necessarily have the best reputations, but it being 2009, almost 2010, really doesn't mean anything other than you're frustrated, you need someone to be frustrated at, and you're aim is a little off.  Linux has really only been mainstream desktop ready for the last 3-4 years tops.  How long has Apple and Microsoft been putting out desktop OSes?  How many years have they been plagued by problems with their own code let alone third party tools?  Ask someone who had the Roxio Easy CD creator suite how well XP worked when XP was released because Microsoft embedded a lightweight roxio agent that conflicted with the full suite of OS integrated CD burning.  

Finally, all that said, flash is not an open standard, it is a proprietary standard.  Macromedia once owned it, now Adobe does.  If you are using an Open Source flash player, and adobe updates flash code, that doesn't mean that third party players will be able to use it right away.  Things are going to break until they can all be identified and updated.  This is true with any player in linux, windows, OSX, or otherwise.  Adobe releases a flash player for linux, and if you are using it, you are relying on adobe to be making sure it works well.  If you want to direct your frustration for an adobe flash player not working well, the appropriate target would be adobe.

---

### Post by Psumi on 2009-11-22
> **FuturePilot said:**
> [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407")

Seems like we will have to wait for lucid, as the fix was declined for karmic and LTS.

---

### Post by Regenweald on 2009-11-22
Yes it is 2009. and mine work.

---

### Post by Psumi on 2009-11-22
> **Regenweald said:**
> Yes it is 2009. and mine work.

Mine did work until today or so, then I had to apply the GDK NATIVE WINDOW fix.

---

### Post by Regenweald on 2009-11-22
> **Psumi said:**
> Mine did work until today or so, then I had to apply the GDK NATIVE WINDOW fix.

Updates broke it ? :D

---

### Post by ZankerH on 2009-11-22
> **Ric_NYC said:**
> If I cannot get simple things like a flash plugin working then I'm in trouble. Especially when flash is everywhere on the internet.

If you rely on a piece of proprietary software like flash, you're in trouble regardless of whether or not it happens to work on your machine.

---

### Post by Psumi on 2009-11-22
> **Regenweald said:**
> Updates broke it ? :D

Nope, installing xdm/wdm did apparently. Or removing firefox-gnome-support as I use xfce.

<snip>

---

### Post by ZankerH on 2009-11-22
> **Psumi said:**
> You know, you are really starting to get on my nerves. I should slice you with my scythe.

That strikes me as not a very civil way to respond to an advice given to a third person with the best of intentions.

---

### Post by Psumi on 2009-11-22
> **ZankerH said:**
> That strikes me as not a very civil way to respond to an advice given to a third person with the best of intentions.

You surrender to free and open source, therefore you are lost.

---

### Post by ZankerH on 2009-11-22
> **Psumi said:**
> You surrender to free and open source, therefore you are lost.

I'd say it's the other way around, the ones surrendering are the people who give validity to proprietary software and encourage its use.

Also, "Free and open source software" is redundant, because Free Software is open source by definition.

---

### Post by Psumi on 2009-11-22
> **ZankerH said:**
> I'd say it's the other way around, the ones surrendering are the people who give validity to proprietary software and encourage its use.

Also, "Free and open source software" is redundant, because Free Software is open source by definition.

Flash is "free to download and use for personal use" so I would think it would be considered free, but not free and open source.

---

### Post by ZankerH on 2009-11-22
> **Psumi said:**
> Flash is "free to download and use for personal use" so I would think it would be considered free, but not free and open source.

free != Free

---

### Post by RiceMonster on 2009-11-22
> **ZankerH said:**
> If you rely on a piece of proprietary software like flash, you're in trouble regardless of whether or not it happens to work on your machine.

Must you try to turn EVERY thread into Free vs Proprietary or GNU/Linux vs Linux? You are so predictable.

> **ZankerH said:**
> free != Free

[img]http://i12.photobucket.com/albums/a218/japongt/Others/AttemptingtoCare.gif[/img]

---

### Post by Dharmachakra on 2009-11-22
> **ZankerH said:**
> free != Free

I find myself using this similie quite often...

](*,)

---

### Post by Regenweald on 2009-11-22
> **RiceMonster said:**
>  
[img]http://i12.photobucket.com/albums/a218/japongt/Others/AttemptingtoCare.gif[/img]

Thanks for this :), reminds me of an article I read recently, the title of which would really ruffle some feathers in here so that will remain unspoken. Anyway, the person was running through the history of some aspects of the Linux desktop in general. Some things I learned, disagreed with and agreed with, but one line really made my day, describing some crossroads in the path that the desktop took there was this line: "....and while the free software community achieved much that was moral and little that was useful...."
I'm reminded of that line everytime I visit the forums :D

---

