---
title: "computer unusually slow"
date: 2006-09-27
forum: The Cafe
---

### Post by maniacmusician on 2006-09-27
I need to know why this is...I don't really see any reason it should be. a summary of what I have is:

processor: Celeron 346 (3.06 GHz / 533 MHz FSB); 256KB L2 cache
ram: 1.5 GBs
chipset: ATI xpress 200

shouldn't it be flying with those specs? I suppose it's reasonably fast, but I don't feel it really flying and being instantaneous. Konqueror takes 6 seconds to open, Kate takes 5, things like that. I feel like at this point, it should be *Click* maybe 2 seconds at the most, for konqueror to pop up. I have the proprietary ATI drivers installed. they kind of suck (i cant enable compositing) but i'm running a screen at 1280x1024 so its not too bad (but System Settings > Display in KDE shows a max refresh rate of 60Hz). Swiftfox can be a bit slow for me  sometimes when I have a large number of tabs/windows open (which i usually do). I also usually run at least these apps all the time: Amarok, Swiftfox, Gaim. those are my basic three.

is it my processor that's slowing me down? I know it's 3.06 GHz, but a 256KB L2 cache seems on the small side. 

so whats going on? is this normal or should I really be faster?

thanks.

edit: output from cat /proc/cpuinfo

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 4
model name      : Intel(R) Celeron(R) CPU 3.06GHz
stepping        : 9
cpu MHz         : 3066.291
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 5
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm pni monitor ds_cpl tm2 cid cx16 xtpr lahf_lm
bogomips        : 6139.69
```

---

### Post by %hMa@?b&lt;C on 2006-09-27
that does seem slow. 
I have the following for a processor(oh, how my celery bottlenecks things), 1 gig of ram and a geforce mx 4000 video card. and My pc seems, from your description, to be running faster.
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.40GHz
stepping        : 7
cpu MHz         : 2392.763
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov
pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr

```

---

### Post by maniacmusician on 2006-09-27
should've included that with my post. edited. 

what's your start time for konqueror/kate, etc.

I find it it odd that your computer with half the cache of mine and not as much ram and a slower processor is running faster. guess you were lucky! 

does anyone have an explanation for it?

---

### Post by NoTiG on 2006-09-27
I have noticed that some programs have memory leaks. Open up your system monitor and look at your ram usage and cpu. close all your windows and programs and look again. THen reboot to see if your ram usage is reduced... (i dont know what system monitor is called in KDE )

---

### Post by maniacmusician on 2006-09-27
RAM isn't really an issue for me, i have 1.5 GBs, more than enough for common everyday applications. also, I use the same programs as many other people, and if their computers are snappy, i don't see a reason mine shouldn't be. top says I still have 50 MBs of RAM that's not being used out of the 1.5 GBs. Also, i'm not really in the habit of restarting my computer too often...

%MEM shows Xorg using 22% of my ram, swiftfox with 18, open office 7, Amarok 7, and then tiny quantities from there. i'm pretty sure my RAM being used is a good thing...that's what i've heard, anyways.

---

### Post by NoTiG on 2006-09-27
I could be wrong but i think you might have a memory leak and its making you use swap. Do you hear your hard drive alot even when you arent moving files around?

Im using 330 MB of 1.2 GB and i have several instances of bon echo(firefox), several gnome terminals , some pdf's... and rhythmn box and gedit. and its pretty snappy especially considering im on a laptop .

to test (i guess) you could just reboot... then open the same exact programs up that you have now. if there is a large discrepancy between the two then i think it means something. although i am no expert.

---

### Post by 3rdalbum on 2006-09-28
Install the 686 kernel and set up Prelinking (you'll need to find a HOWTO). If you don't mind your computer starting up significantly slower, download Preload as well. My computer's so snappy now!

---

### Post by ComplexNumber on 2006-09-28
**maniacmusician**
have you installed lots of packages on your system? if so, that will be a contributing factor. part of this is because more packages also means services tend to be run.

---

### Post by maniacmusician on 2006-09-28
> **ComplexNumber said:**
> **maniacmusician**
have you installed lots of packages on your system? if so, that will be a contributing factor. part of this is because more packages also means services tend to be run.
yup i have tons of stuff installed. I've noticed that when I first started using ubuntu, when i downloaded and installed stuff, it went by really fast. now, it still downloads fast, but it spends a LONG time installing the package. at least 3-4 times as long as before. its ridiculous. what's a solution to this? just stopping services, or what? i dont want to remove all my programs.

@notig:I have Amarok running, along with two swiftfox windows (one with 11 tabs, one with 6), gaim, and a KOrganizer daemon. I guess it could be a memory leak, but i've always heard it said that in linux, any memory that's not being used is being wasted...I'll try rebooting and post back. about the hard drive, it makes a loud sound every once in a while, but it's been doing that for a long time, since before I had linux.

@3rdalbum: i installed the 686 kernel once, but i noticed a major performance hit (especially with GDM...it took about 5 extra seconds than normal to validate my username and password).

---

### Post by PatrickMay16 on 2006-09-28
Just curious... what's the output of this command?

free -m

---

### Post by maniacmusician on 2006-09-28
that would be:

```

             total       used       free     shared    buffers     cached
Mem:          1456       1375         81          0        190        588
-/+ buffers/cache:        596        859
Swap:         3121         19       3102


```

---

### Post by maniacmusician on 2006-10-12
Okay, I agree, i think I have crazy memory leaks as well. it's insane. I have two instances of konqueror open. one, with 13 tabs open. in top, it takes up 159m of VIRT (which i assume is total ram usage). the other one, with 3 tabs open, takes up 106m of VIRT. Xorg takes up 138m. amarok takes up 46, after being on all day long. i only have 47MB free. and things were actually WORSE when i was still using firefox. 

so how do i even start to fix this?

---

### Post by maniacmusician on 2006-10-14
sorry to bump this, guys, but it's getting kind of serious..i dont know why the problem is escalating. I left my computer on at night as i usually do, and this afternoon when I got back on it, I noticed that ram consumption was at 1.44 GB (I have 1.49...so 1.44 is a huge chunk of that. almost all). So this seems to be a fairly serious memory leak?

I havn't had TOO many performance repurcussions yet. I have noticed that konqueror seems to freeze up once in a while and i have to wait about 5 seconds for it to work again.other applications are okay. they still dont fly like i want them to, but its nothing i cant live with for now. what i'm worried about is that my computer is using 97% of its RAM.

---

### Post by mulligan.can on 2006-12-30
just incase your still stuck on this one: linux caches files in ram. type free -m and the value in +/- buffers is the amount of ram thats actually available.

---

### Post by smoker on 2006-12-30
have you checked your ram recently with memtest?

also, a great bootable app for checking your hard drive is 'drive fitness test' from here:

[http://www.hitachigst.com/hdd/support/download.htm#DFT](http://www.hitachigst.com/hdd/support/download.htm#DFT)

i would check both

---

### Post by maniacmusician on 2006-12-31
well since I originally posted this thread, I've been thinking that the problem may be the 533mHz FSB (800 is the standard now, isnt it?) or the 256KB L2 cache. I've no idea what that is but it seems super small.

specs for my computer: [http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00653370&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?docname=c00653370&cc=us&dlc=en&lc=en&jumpid=reg_R1002_USEN)

I think it's just a really pathetic piece of hardware. I bought it on impulse because my old computer fried itself and I really needed a new one. This thing cost me around $300 if I remember correctly. 

I was thinking of building myself a new computer but cash is hard to come by :) I should probably take care of my outstanding debts.... [suddenly remembers that he's living in America] Naaahh.

---

### Post by John.Michael.Kane on 2006-12-31
maniacmusician Try lightening up the load on the machine. Only install what you need remove any services Firefox plug ins etc strip it down to bottom line of your use.

---

### Post by maniacmusician on 2006-12-31
> **SD-Plissken said:**
> maniacmusician Try lightening up the load on the machine. Only install what you need remove any services Firefox plug ins etc strip it down to bottom line of your use.
aw, man, that's no fun! I like it nice and loaded up. I've tried the minimal thing, it wasn't really for me. I can appreciate the speed it brings, but I've seen computers worse than mine running kde more beautifully for long periods of time. 

re-reading your post I see that you're just saying to strip down my current install. I've disabled some services that I didn't need and stuff like that. I love my FF plugins (though I have to say, FF is my laggiest app by FAR, even when I didn't have my extensions installed; it's no doubt due to my 10-14 tabs, but 1.5 ran a lot better with the same number of tabs)

since the OP, i've also gotten an nVidia card and installed beryl, so I guess I've just been beefing up the load on my machine. It's great when it first starts up, but it gets slower as time goes on, and this is the same pattern it exhibited when I didn't have Beryl, so i know that's not the problem.

Here's my theory: 

All the RAM goes to cache memory. This is supposed to be good for the computer and all. But what I think is that it's taking longer for my computer to actually clean out that memory and retrieve it from cache, which is slowing down the response time on my machine.

I can't think of anything else that could be causing it, this machine is definitely in the top end of mid-range computers.

---

### Post by The Noble on 2007-01-01
I have an old laptop that seems to run faster than your rig, even when I am using the equivalent apps. Have your tried using a different desktop environment and other apps temporarily? Maybe QT has a memory leak, so running gnome or XFCE with the equivalent apps (Firefox/Opera/Epiphany, Listen/Banshee, etc) may rule that out. After an hour or so, run the free -m code in the terminal and see if there is any major difference. Otherwise, I have no clue.

---

### Post by riven0 on 2007-01-01
> **maniacmusician said:**
> aw, man, that's no fun! I like it nice and loaded up. I've tried the minimal thing, it wasn't really for me. I can appreciate the speed it brings, but I've seen computers worse than mine running kde more beautifully for long periods of time. 


Maybe it's KDE then, because that's outrageous. I have an athlonXP 3000+ with 512 RAM and Firefox takes, at most, 2-3 seconds to load. With 1.5Gb of RAM you should be flying. Either it's a memory leak, your network is mis-configured, (this can cause huge slowdowns), or you need to add *noapic* to your kernel parameter. Other than that, I'm lost. :confused:

---

### Post by Frak on 2007-01-01
> **maniacmusician said:**
> aw, man, that's no fun! I like it nice and loaded up. I've tried the minimal thing, it wasn't really for me. I can appreciate the speed it brings, but I've seen computers worse than mine running kde more beautifully for long periods of time.

Your desktop enviroment may be corrupt, its happened with me a time or two, especially with QT based (KDE), as it is the only one that has done so, reinstall your desktop enviroment and see what happens.

---

### Post by maniacmusician on 2007-01-01
Thanks for the suggestion, I think I will try that once things quiet down here at home and I have some more time. I hope that's it, though it seems a bit unlikely...this happened when I had dapper too, and I reformatted when upgrading (I was doing the seperate home partition thing)

---

### Post by Frak on 2007-01-01
> **maniacmusician said:**
> though it seems a bit unlikely...

Hey, somethings better than nothing...

---

### Post by RAV TUX on 2007-01-01
> **maniacmusician said:**
> Thanks for the suggestion, I think I will try that once things quiet down here at home and I have some more time. I hope that's it, though it seems a bit unlikely...this happened when I had dapper too, and I reformatted when upgrading (I was doing the seperate home partition thing)
I hate to bring it up but,

Have you tested out different Linux distros, specifically not based on Debian?

I would be interested to see how different OS's work for you.

---

### Post by maniacmusician on 2007-01-01
> **RAV TUX said:**
> I hate to bring it up but,

Have you tested out different Linux distros, specifically not based on Debian?

I would be interested to see how different OS's work for you.
:) No, I havn't really had the time for that. I picked Ubuntu because I found it really easy to use and things fell right into place for me. There's a bunch other I'm planning on trying once I have more time. 

@Frak: Yes, I agree :) Thanks a lot for your suggestion, I'm definitely going to try it.

---

