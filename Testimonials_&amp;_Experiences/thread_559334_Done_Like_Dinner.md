---
title: "Done Like Dinner"
date: 2007-09-25
forum: Testimonials &amp; Experiences
---

### Post by uputer on 2007-09-25
That's it for me.   

I am exhausted from typing and trying to get wireless to work.   I  collected notes, tips and tutorials to potentially help progress with my wireless problem in Kubuntu to no avail.  

I'm not going to bother listing all the steps and problems I encountered.  I think that will only invite insults so there's no point.  

Because of that, I will stop here.   The wireless I worked on is just another failed project and problematic task attempted in K/Ubuntu.   For me, too much time is required and too much seems buggy.   Even if it isn't, that is the perception and it seems when you have multiple problems, everyone claims everything works for them but don't offer help.   At least, they're having fun.

---

### Post by Shazaam on 2007-09-25
Sorry for your dilemma. The biggest hurdle you have is the fact that too many hardware companies REFUSE to release Linux drivers for their products making life hard for everbody. I didn't have a failure similar to yours but I feel your pain. $20US for simple Conexant dialup modem drivers is crazy.
Probably not what you want to hear but you could scour the net again to find a wireless card that has the least amount of troubles/difficult installs than the rest and buy it. There HAS to be one out there you can use. Don't rely on testimonials from vendors, make a list of cards and search using the part number and add linux to the search.
If you have Belkin wireless card troubles with Ubuntu more than likely you will have troubles with other version of Linux.

---

### Post by ukripper on 2007-09-25
Well you have already made up your mind then no point asking you about your chipset. Better luck next time if you try Gutsy next month.

---

### Post by uputer on 2007-09-25
The chipset is Zydas (now owned by Atheros) zd1211 (or zd1211b).  

[http://linux-wless.passys.nl/query_part.php?brandname=Belkin](http://linux-wless.passys.nl/query_part.php?brandname=Belkin)

The problem is that it almost worked 'out of the box' but the performance was erratic and the other major problem was the configuration programs.   KNetwork Manager was accessable at first but now I cannot even use it how it was working before.   Now, the only part of any network manager I can use is the manual configuration and in which case, only WEP is available.  No one has commented on this at all, not even in the Kubuntu forums.   The only thing that I gathered from this is the likelihood of a KNetwork Manager bug (which doesn't help). 

I DID research what works easiest and that is why I chose the Belkin.  I read about Linksys adapters (I own a Linksys router) and apparently, you have to complile or build or something.  Or, more accurately, you have to 'blacklist' the driver.

[http://dinomite.net/archives/linksys-wusb54g-in-ubuntu](http://dinomite.net/archives/linksys-wusb54g-in-ubuntu)

I read on here that a Netgear WG111 v.2 works 'out of the  box' but I've learned that there are either two chipsets used in this adapter.   So, how do I verify which adapter has which chipset?  Call around and ask them to open the box or would it be on the box?  :-(

[http://linux-wless.passys.nl/query_part.php?brandname=Netgear](http://linux-wless.passys.nl/query_part.php?brandname=Netgear)

The Realtek apparently works well while the Prism doesn't work well at all.   

But, then like I said, the Belkin's Zydas zd1211 almost worked but a combination of erratic behavior and a sloppy network interface program for configuration prevented the overall experience from:  1) being successful and 2) working relatively smoothly.   Imho, well for me, it was indicative or representative of the overall Linux experience so far.  

Hence, the frustrations and leaning towards throwing in the towel.  Sometimes it's better to walk away.   It's probably a combination of the hardware not fully working but an inability to fix it another way (based on inexperience).   However, if some hardware is reported as working (out of the box) but actually doesn't then how do I know which hardware to go for?   Anyway, I'm leaving it be.

---

### Post by ukripper on 2007-09-25
> **uputer said:**
> 
The problem is that it almost worked 'out of the box' but the performance was erratic and the other major problem was the configuration programs.   KNetwork Manager was accessable at first but now I cannot even use it how it was working before.   Now, the only part of any network manager II can use is the manual configuration and in which case, only WEP is available.  No one has commented on this at all, not even in the Kubuntu forums.   The only thing that I gathered from this is the likelihood of a KNetwork Manager bug (which doesn't help). 

I DID research what works easiest and that is why I chose the Belkin.  I read about Linksys adapters (I own a Linksys router) and apparently, you have to complile or build or something.  Or, more accurately, you have to 'blacklist' the driver.


I personally don't use knetworkmanager..wlassistant is far better app  than that and very powerful.

Can you post output of the folwoing command :
```
lspci -v | less
```

---

### Post by uputer on 2007-09-25
> **ukripper said:**
> I personally don't use knetworkmanager..wlassistant is far better app  than that and very powerful.

Can you post output of the folwoing command :
```
lspci -v | less
```
It's too long.   I am not sure how to obtain the output anyway.   I decided to copy and paste to OpenOffice and it's 6 pages.   There is nothing listed that I could tell that indicates the USB wireless hardware.   

After I installed and configured wlassistant, the attempted wireless connection failed.   I then discovered I couldn't even connect through wired.   I had to exit Kubuntu in order to post and connect to the internet.   

It's hopeless.   I can't even give my opinion of Linux/Ubuntu because the mods cancel anything that gets too negative.   

Have fun.

---

### Post by ukripper on 2007-09-25
> **uputer said:**
> It's too long.   I am not sure how to obtain the output anyway.   I decided to copy and paste to OpenOffice and it's 6 pages.   There is nothing listed that I could tell that indicates the USB wireless hardware.   

After I installed and configured wlassistant, the attempted wireless connection failed.   I then discovered I couldn't even connect through wired.   I had to exit Kubuntu in order to post and connect to the internet.   

It's hopeless.   I can't even give my opinion of Linux/Ubuntu because the mods cancel anything that gets too negative.   

Have fun.

Sorry my bad, I thought it was pci based wireless card...I would never use USB based Wcards as it degrades signal bigtime...

but you can still determine your chipset by using following command```
lsusb
```

---

### Post by uputer on 2007-09-25
> **ukripper said:**
> Sorry my bad, I thought it was pci based wireless card...I would never use USB based Wcards as it degrades signal bigtime...

but you can still determine your chipset by using following command```
lsusb
```
My bad, too.   I should have noticed the command given was for pci.   Duh (on my part).

I already utilized a command that gave the chipset, I think.   It's zd1211b.

---

### Post by uputer on 2007-09-25
Btw, I'll stop posting soon.   I just wanted to give my perspective and experience.  

Good luck.

---

### Post by ukripper on 2007-09-25
Great! I'll look forward to see how you get on with gutsy coming down the line..

Goodluck

---

