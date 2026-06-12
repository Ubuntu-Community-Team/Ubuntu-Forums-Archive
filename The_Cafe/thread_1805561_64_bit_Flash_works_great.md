---
title: "64 bit Flash works great"
date: 2011-07-16
forum: The Cafe
---

### Post by SlappyPappy on 2011-07-16
Found this 64 bit Flash, it works great.

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-11-04-211737.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-11-04-211737.shtml)

---

### Post by Frogs Hair on 2011-07-16
Good news !  I Installed Via Flash-Aid  using quick mode . I have not used 64 bit  enough to notice a difference .

---

### Post by haqking on 2011-07-16
> **SlappyPappy said:**
> Found this 64 bit Flash, it works great.

[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-11-04-211737.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-11-04-211737.shtml)


though the tut is for 11.04 i would like to make sure people know that 64bit flash works fine on 10.04 and 10.10 also, well it does on my machines and builds anyways

---

### Post by bodhi.zazen on 2011-07-16
I moved your thread to the cafe as it does not seem a request for support. Although that flash driver works, keep in mind it is in Beta still ;)

---

### Post by OldBoy44 on 2011-07-20
Hi all, 

Beta version works fine for me too, previously this site was completely messed up, now much better -

 [http://24timezones.com/](http://24timezones.com/)

Hope that Beta version stands the test of time - :)

---

### Post by BrokenKingpin on 2011-07-20
I may give this a try. I sometimes get choppy video playback with flash. hopefully this resolves the issue.

---

### Post by wolfen69 on 2011-07-20
Works good for me.

---

### Post by SeijiSensei on 2011-07-20
I've been running the Flash 11 64-bit beta for a week or so now.  I notice that it can occasionally hang the browser (Firefox) or render it unresponsive.  Closing Firefox and reopening generally cures the problem.  

This is on a quad-core Q6600 with 4GB of memory and an NVIDIA 9500GT so I don't think it's a problem with hardware resources.  Perhaps it's an overflow bug in the binary?

I ran the 64-bit "Square" beta of Flash 10 for about a year and didn't have this problem.

---

### Post by Foxcow on 2011-07-20
> **SeijiSensei said:**
> I've been running the Flash 11 64-bit beta for a week or so now.  I notice that it can occasionally hang the browser (Firefox) or render it unresponsive.  Closing Firefox and reopening generally cures the problem.  

This is on a quad-core Q6600 with 4GB of memory and an NVIDIA 9500GT so I don't think it's a problem with hardware resources.  Perhaps it's an overflow bug in the binary?

I ran the 64-bit "Square" beta of Flash 10 for about a year and didn't have this problem.



My experience has been opposite.  With Flash Square, my laptop didn't like to maximize/fullscreen youtube or any other flash but no problem with 11 Beta.  I find this beta to be much less resource intensive as well.

---

### Post by Foxcow on 2011-07-20
I didn't use flash Air or anything to install the new beta.

Download from here:
[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

extract the plugin and copy it to:

/usr/lib/mozilla/plugins

Restart browser and done!

---

### Post by wolfen69 on 2011-07-20
> **Foxcow said:**
> I didn't use flash Air or anything to install the new beta.

Download from here:
[http://labs.adobe.com/downloads/flashplayer11.html](http://labs.adobe.com/downloads/flashplayer11.html)

extract the plugin and copy it to:

**/usr/lib/mozilla/plugins**

Restart browser and done!

*Or* to ~/.mozilla/plugins ;)

---

### Post by Foxcow on 2011-07-20
> **wolfen69 said:**
> *Or* to ~/.mozilla/plugins ;)



Cool, I didn't know that would have sufficed.  Maybe for the next version.  :D

---

### Post by wolfen69 on 2011-07-20
> **Foxcow said:**
> Cool, I didn't know that would have sufficed.  Maybe for the next version.  :D

Yeah, I used to do it your way, but it takes a few seconds less time to just drag and drop it into ~/.mozilla/plugins Hey, whatever works.

---

### Post by Perfect Storm on 2011-07-20
Haven't noticed any hangs or lags with the new 64-bit flash (browser: Chrome latest stable). Very smooth even in fullscreen.

---

### Post by SamD42 on 2011-07-20
Had to switch away from the latest 64 bit flash after it repeatedly caused the computer the lock up for 10-20 seconds every time a video first started playing, even with the 275.19 graphics driver. This is using a T6500 cpu and nvidia g105m graphics card.

That said, after it got over the lock-up playback was absolutely fine.

---

### Post by SeijiSensei on 2011-07-20
> **wolfen69 said:**
> Yeah, I used to do it your way, but it takes a few seconds less time to just drag and drop it into ~/.mozilla/plugins Hey, whatever works.

Plugins installed to your home directory will not be available to other users of the computer.  If that matters to you, you need to install libflashplayer.so to /usr/lib/mozilla/plugins.

---

### Post by zinadork on 2011-07-20
Does it have the gray box in place of flash video?  I downgraded to 32 bit after being tired of terrible flash support.

---

