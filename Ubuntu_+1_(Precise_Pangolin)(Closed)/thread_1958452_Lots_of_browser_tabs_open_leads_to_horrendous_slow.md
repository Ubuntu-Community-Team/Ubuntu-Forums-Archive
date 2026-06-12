---
title: "Lots of browser tabs open leads to horrendous slowdown"
date: 2012-04-14
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dbd on 2012-04-14
Hi,

I'm not sure if this is a Precise bug or a problem with my system. So I'm posting here mainly to find out what I should do to find out.

The problem I'm having is that when I open more than 5 or so tabs in my web browser (either Chormium or Firefox) the system collapses. The mouse becomes horrendously unresponsive, I can occasionally close tabs or close the browser to stop the system locking up completely, but if I'm not quick enough then I lose all ability to interact with the system. (A jab at Alt+Print+K usually saves me having to press the power button, but also, only if I'm quick.) This also used to happen just when I was watching a youtube video, but that seemed to fix itself when I switched over to the restricted graphics drivers. (I have an AMD card.) (Edit: whenever I have lots of tabs open many of them tend to have flash, so this may be a flash problem.) (Edit,this just happened when I only had six tabs open, which is nut really that many!)

I'm not sure if this is significant, but I don't have a swap partition (I don't have any spare partitions, and don't really want to take the risk of repartitioning as it's not my PC). The computer has 4GB of RAM.

I've done a memory test, and that found no errors.

In Windows the system is stable, but slow (probably because it's not been reinstalled for a couple of years, and there's loads of crap running in the background).

Precise is fully up to date, and this has been happening consistently since I installed Precise earlier in the week. (I've not run a version of linux on this system for a couple of years, so no idea if it would be ok with 11.10.) When I'm not doing much (just running emacs, a web browser with a couple of tabs open and Nuvola) the system seems perfectly stable. 

What should I do to find out the cause of the problem? Or is this just becuase I don't have a swap partition? (And is there a way to have swap, without partitioning?)

Thanks

Paul

---

### Post by 2F4U on 2012-04-14
Both Firefox and Chromium are know to use a lot of resources. The more tabs you open the more resources are used. Additionally, if you don't have a swap partition, the system has not the option, to write unused apps and data to swap. Its no wonder that your system becomes unresponsive.

---

### Post by zombifier25 on 2012-04-14
> **2F4U said:**
> Both Firefox and Chromium are know to use a lot of resources. The more tabs you open the more resources are used. Additionally, if you don't have a swap partition, the system has not the option, to write unused apps and data to swap. Its no wonder that your system becomes unresponsive.
Whoa, last time I checked 5 tabs don't cause that much slowdown in Firefox, left alone Chromium.
About the swap thingy, dunno;

I think the problem is with Flash; the Linux version of Flash are well known for slowing your system down to a crawl.

---

### Post by Gregory Lee on 2012-04-14
I have 18 tabs open in Firefox now with no problem, but then this is a new system with lots of resources.  But with my previous computer, I never noticed any slowdown, either, that I could associate with many tabs open.  I like tabs.  (I certainly did notice, before, big slowdowns caused by the Flash plugin.)

I don't know whether lack of swap could be your problem.  I've always had at least one swap partition.  Did you know you can make a swap file to get swap space without repartitioning?  Read "man mkswap", noting the directions there for using "dd" to create a file without holes.

---

### Post by snkiz on 2012-04-14
I use chrome it wigs outs some times and starts swapping hard idk why. but even when it didn't my whole system was swapping to much. found out stock swappienss is set to 60! changed to 25 and that helped a lot.

---

### Post by Elfy on 2012-04-14
> **dbd said:**
> ...And is there a way to have swap, without partitioning?...

No idea to tell from the information whether it is a lack of swap causing the issue - but you can add a swap _file_.


[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

When it becomes slow - open a terminal and have a look at

```
free -m
top
```

Could even be addons - try running firefox in safe mode - is it the same?

```
firefox -safe-mode
```

---

### Post by NHclimber on 2012-04-14
4GB should be *plenty* for even 20 tabs without swapping.

Run top (press 'M' to sort by memory usage) and see what's sucking it all up. Also, see if you get the same behavior in unity 2D.

*edit: forestpiskie beat me to it...*

---

### Post by philinux on 2012-04-14
Not seeing this here with FF and over 10 tabs.

Install indicator-multiload or conky and see what's causing the problem. Maybe try a unity 2d session too.

---

### Post by Sworddragon on 2012-04-14
Open a video on youtube, right click it and click on "Show video information" on the context menu. Now check which parts are accelerated on your system. For example mine is "software video rendering, software video decoding". There are currently known problems with hardware acceleration enabled in Adobe Flash (especially with version 11.2) which causes even the system to freeze.

---

### Post by dbd on 2012-04-15
> **Sworddragon said:**
> Open a video on youtube, right click it and click on "Show video information" on the context menu. Now check which parts are accelerated on your system. For example mine is software video rendering, software video decoding. There are currently known problems with hardware acceleration enabled in Adobe Flash (especially with version 11.2) which causes even the system to freeze.
I've got the same as you, "software video rendering, software video decoding".

I've done some testing while using top to watch what's going on top at the same time, and it seems to happen the moment the browser goes over using 50% of the RAM. Luckily, if I turn off flash that happens much later, so the system is at least usable now, as long as I'm careful to keep below that number. (But if it does go above 50% the system is utterly unusable, and I normally have to turn it off with the power button.) 

Thanks for all the help!

---

### Post by sgage on 2012-04-15
> **2F4U said:**
> Both Firefox and Chromium are know to use a lot of resources. The more tabs you open the more resources are used. Additionally, if you don't have a swap partition, the system has not the option, to write unused apps and data to swap. Its no wonder that your system becomes unresponsive.

And yet, I use Firefox and often have many, many tabs open, and I have no such problem. I have 4 GB RAM, and though I do have a swap partition, it never gets used. I mean never. I have the system monitor running all the time, and swap never gets touched.

So it is some wonder that his system becomes unresponsive.

---

### Post by dbd on 2012-04-15
> **forestpiskie said:**
> No idea to tell from the information whether it is a lack of swap causing the issue - but you can add a swap _file_.


[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

FIXED! I added a 500MB swap file, and now when chrome hits 50% of the memory the chrome error box pops up to say "these tabs have become unresponsive, do you want to kill them or wait?" (or something along those lines). The system slows a little when I load loads of tabs, but doesn't lock up or freeze any more! And once I've killed them it's all fine again.

So the moral of the story is, never run ubuntu without a swap partition / file!

Thanks for all the help everyone.

---

