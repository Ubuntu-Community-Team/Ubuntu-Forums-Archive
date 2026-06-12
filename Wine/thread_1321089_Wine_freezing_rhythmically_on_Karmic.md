---
title: "Wine freezing rhythmically on Karmic"
date: 2009-11-09
forum: Wine
---

### Post by andrew.wja on 2009-11-09
Hi All,
Has anyone noticed that, running on Karmic (up-to-date as of post time) Wine will rhythmically freeze for a very short while every second or two? I'm trying to play Morrowind on Wine, having tried VirtualBox and found it to be far too slow. The game installs and plays fine, but there's this rhythmic freezing which makes it appear very choppy. When Wine isn't freezing, the mouse moves quickly and smoothly and the game is responsive. Any help appreciated.

---

### Post by beastrace91 on 2009-11-09
I am pretty sure the issue you are experiencing is [this one](http://bugs.winehq.org/show_bug.cgi?id=14186). It is a quick fix, just find a native quartz.dll (either through google or off a windows install you may have near by(on your VM perhaps?)) And drop it into your **~/.wine/windows/system32** folder - then open your WineCFG (Applications->Wine->WineCFG or in terminal winecfg) and set your quartz.dll to a native over ride.

Also just as a heads up in the future be sure to use more descriptive topic titles - had this thread had "Morrowind" in its name for example I would have checked it much sooner because I have experience running this program under Wine :). As it was I was just bored and clicked into it on a whim ;)

Cheers,
~Jeff

---

