---
title: "wine for windows?"
date: 2008-04-13
forum: The Cafe
---

### Post by swoll1980 on 2008-04-13
I went to [www.winehq.org](www.winehq.org) and noticed that they had a wine.exe
installer for Windows xp. Now correct me if I'm wrong here, but 
doesn't Windows xp all ready have a windows compatibility layer
built in?

---

### Post by zmjjmz on 2008-04-13
It's probably for testing purposes...
Maybe one can compare an application's performance in WINE to that of one in actual Windows.

---

### Post by swoll1980 on 2008-04-13
,but since people that are running wine will be doing so on linux it doesn't seem like it would be a very acurate way to test things.

---

### Post by zmjjmz on 2008-04-13
Who knows really :P
I find it more interesting that there's a version for Windows, but not for Mac OSX...

---

### Post by FuturePilot on 2008-04-13
That does make sense. If you're trying to fix a bug or something you can compare how it runs on an actual Windows platform and then how it runs in Wine and maybe see what needs to be fixed.

What if you ran Wine.exe in Wine? :shock:

---

### Post by TeraDyne on 2008-04-13
There is one for OSX: [http://darwine.sourceforge.net/](http://darwine.sourceforge.net/)

---

### Post by TeraDyne on 2008-04-13
> **FuturePilot said:**
> What if you ran Wine.exe in Wine? :shock:

Wouldn't that be like running a virtual machine inside of a virtual machine?

---

### Post by swoll1980 on 2008-04-13
> **FuturePilot said:**
> 

What if you ran Wine.exe in Wine? :shock:

and then ran wine.exe inside of that one and so on and so on

---

### Post by zmjjmz on 2008-04-13
Darwine doesn't seem to run as well as WINE for my cousin's computer, maybe it's an older version?  Actually, the FAQ on the site led me to believe that it was a complete reconstruct of WINE, but is it just WINE ported to OSX (and at the current version, so I can use appdb to check if it will work?)
Also, why don't they put it on that list of binaries? Has it yet to be ported? If they ported it to Solaris, how hard can it be to port it to OSX?
Am I asking too many questions you don't know the answers to?

---

### Post by swoll1980 on 2008-04-13
You would think if they took the time to make a windows version they would have made an osx version

---

### Post by quanumphaze on 2008-04-13
According to the Wine FAQ the Windows version isn't really a usable one and is just for development purposes.

It has something to do with testing the Wine DLL files against the real ones but I'm not an expert.

It's a shame it's not really usable for regular users since Vista needs it to run some older software.

---

### Post by igknighted on 2008-04-13
> **swoll1980 said:**
> You would think if they took the time to make a windows version they would have made an osx version

You throw the word "they" around like one generic blob... remember, this is an open source project, so "they" is hundreds (thousands?) of **independent** contributors from all over.  If someone ambitious enough had a reason to want/need a windows version it would get created, while an OSX version would only exist for similar reasons.

Consider that there are commercial solutions (cider) and virtualization solutions marketed very strongly at Mac users (a user group that has already indicated by their willingness to shell out the money for a Mac in the first place), and I just don't see where the great demand would come from the Mac world.  So in this regard, I am not stunned that there is no really good OSX version.

---

### Post by swoll1980 on 2008-04-13
the word as used ' they' was   plural and refers to a group of people who's sum is more than 1. 
whether it be 2 or hundreds (thousands) (millions) (billions) (trillions)

add: Ive looked at some of your threads, and noticed that you were using the word 'they' in the exact same way. So why you chose to correct me for it is beyond the scope of my imagination [http://ubuntuforums.org/showthread.php?t=753652&page=2](http://ubuntuforums.org/showthread.php?t=753652&page=2)

---

### Post by popch on 2008-04-13
I have tried to find the wine.exe you speak of on the page you mentioned. Can you be a bit more specific on how to find it?

---

### Post by swoll1980 on 2008-04-13
[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

---

### Post by CarpKing on 2008-04-13
I don't know for sure about this file, but I have heard them talk about testing Wine components in Windows.  The idea is that, since they're essentially rebuilding pieces of a Windows install, they can test to see how well they've done and where they need work by replacing a piece from a real Windows install with one of their own.  This is much more reliable than just using Wine on Linux to run a bunch of random programs, most of which have their own bugs and idiosyncrasies.

---

