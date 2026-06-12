---
title: "Put Vista on a diet!"
date: 2008-01-30
forum: Windows
---

### Post by angryfirelord on 2008-01-30
Since I've noticed quite a fair amount of Vista bashing (myself included), I though I would help give a better image of this community by showing some tweaks I've been working to get Vista much more usable.

**Note: I am not responsible if you bork your system. Back up your data first!!!!**

First, the obvious. Update the drivers and replace any Microsoft ones if possible.
 
Next, go to this article: [http://www.extremetech.com/article2/0,1697,2110595,00.asp](http://www.extremetech.com/article2/0,1697,2110595,00.asp) TFA works through the services and seems to work well.
 
However, the hard disk thrashing still continues. Here's what I'm trying to do to make it stop:
 
-Disable Windows Search. It sucks, it eats RAM and doesn't even do it well. Kill and disable it in services.msc.
-Kill System Restore. Unfortunately in Vista, when you disable it, you disable it altogether, but Vista insists on making a restore point every 5 seconds. Disable it by going to Control Panel --> Classic View --> System. On the left hand side, click System Protection. Uncheck the box for Automatic Restore points for your drive(s).
-Disable SuperFetch. I'm still experimenting on this, but that seems to be the biggie here along with System Restore. It's supposed to speed things up by caching them, but in the process SuperFetch gobbles up RAM and disk access, thus defeating the purpose it was designed for.
-Disable Windows Defender auto scans. You can kill that by going to Tools-->Options and uncheking the box. Real-time protection is still enabled.
 
Hopefully this helped someone with their Vista troubles.

---

### Post by karellen on 2008-01-30
I've found out that one of the greatest tweaks is if you disable the aero effects and just keep the vista basic theme. of course, many will argue that you lose one of vista's pluses, though for not so new pcs it's worthy

---

### Post by kool_kat_os on 2008-01-31
Ya....it needs a diet alright...i have it and there are alot of stuff i dont use

---

### Post by angryfirelord on 2008-01-31
The Windows kernel is written quite well and personally, I believe Microsoft can write a kick butt OS. However, until the monopoly is broken, we'll have to deal with the extra unnecessary crap that goes with it.

Of course, Ubuntu kicks butt already, so it'll take some good convincing to make me go back to 100% Windows.

---

