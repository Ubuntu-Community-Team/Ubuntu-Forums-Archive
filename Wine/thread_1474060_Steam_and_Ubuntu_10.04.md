---
title: "Steam and Ubuntu 10.04"
date: 2010-05-05
forum: Wine
---

### Post by mbuller10 on 2010-05-05
Has anyone installed steam on Ubuntu 10.04. How did it go. If so have you played any games like Half-Life 2 or Left for Dead. Please let me know how its working out. I have nvidia 256 mb 9300 graphics card.

---

### Post by cogadh on 2010-05-05
I haven't got to the point where I've been able to play any games yet (problems unrelated to Wine/Steam), but the Steam client itself installs and runs fine.

---

### Post by mbuller10 on 2010-05-05
thanks so do you think I'll be able to play games fine, assuming my hard ware is strong enough

---

### Post by beastrace91 on 2010-05-05
> **mbuller10 said:**
> thanks so do you think I'll be able to play games fine, assuming my hard ware is strong enough

You are going to be hard pressed to play too many games under Wine with that graphics card. HL2 *maybe* - left 4 dead is going to be choppy like no other though.

~Jeff

---

### Post by camdy on 2010-05-06
yeah i did and i posted the problem i'm having here

 [http://ubuntuforums.org/showthread.php?t=1470935](http://ubuntuforums.org/showthread.php?t=1470935)

but i have read that valve are looking at making a linux version of the steam client

---

### Post by mbuller10 on 2010-05-06
> **camdy said:**
> yeah i did and i posted the problem i'm having here

 [http://ubuntuforums.org/showthread.php?t=1470935](http://ubuntuforums.org/showthread.php?t=1470935)

but i have read that valve are looking at making a linux version of the steam client

I heard that too but haven't they been saying that for years still without doing it

---

### Post by beastrace91 on 2010-05-06
> **mbuller10 said:**
> I heard that too but haven't they been saying that for years still without doing it

But there is an OSX client now :) - At best though I would expect a Steam Linux client before 2010 Q4/2011 Q1

~Jeff

---

### Post by cogadh on 2010-05-06
> **beastrace91 said:**
> You are going to be hard pressed to play too many games under Wine with that graphics card. HL2 *maybe* - left 4 dead is going to be choppy like no other though.

~Jeff
I don't know about L4D (don't own it), but I've been running Half-Life 2 with all the episodes and Portal in Wine for a while (before 10.04) using a 256MB GeForce 7600GS and it handles it fine. I would think that 9300 of mbuller's should be at least comparable to my two generations older mid-level graphics card.

> **beastrace91 said:**
> But there is an OSX client now :) - At best though I would expect a Steam Linux client before 2010 Q4/2011 Q1

~Jeff
Wow, aren't you the optimistic one!:D The existence of an OSX client does nothing to improve or decrease the chances of a Linux client; the odds of that happening are still "slim" to "none" and that has not changed in years. As long as Gabe Newell still views Linux as not a viable platform for gaming, there will never be a Steam client on Linux. I have not seen or heard anything that says he has softened that opinion in the least.

---

### Post by Gary00 on 2010-05-06
where can i go to install Steam...i thought they were still workin on it.

---

### Post by cogadh on 2010-05-06
> **Gary00 said:**
> where can i go to install Steam...i thought they were still workin on it.

What do you mean by "still workin on it"? To install it, all you really need to do is install and configure Wine, then download and install Steam. There may be additional configuration required, but in the most basic sense, that's all you really need to do. If you want the possibly easiest way to install and get Steam running, the get PlayOnLinux and let that install Steam for you.

---

### Post by beastrace91 on 2010-05-06
> **cogadh said:**
> I don't know about L4D (don't own it), but I've been running Half-Life 2 with all the episodes and Portal in Wine for a while (before 10.04) using a 256MB GeForce 7600GS and it handles it fine. I would think that 9300 of mbuller's should be at least comparable to my two generations older mid-level graphics card.

I'd be willing to bet your 7600 performs at the very least equal to (if not better) than the 9300 - X300 series nVidia cards are typically built onto the mother board meaning less performance.

Also system requirements (doubly so under Wine) for L4D source engine are much heavier than HL2 source engine.

~Jeff

---

### Post by mbuller10 on 2010-05-06
> **beastrace91 said:**
> I'd be willing to bet your 7600 performs at the very least equal to (if not better) than the 9300 - X300 series nVidia cards are typically built onto the mother board meaning less performance.

Also system requirements (doubly so under Wine) for L4D source engine are much heavier than HL2 source engine.

~Jeff

Well technically its a discrete Nvidia GeForce G 105M (a higher clocked 9300) L4D ran fine under XP, but not under 9.10 so I dunno.

---

### Post by handy on 2010-05-06
You can also use Crossover Games; type steam in the **Application Name:** field in the following search page to see an honest medal rating on how those Steam games run via CX Games:

[http://www.codeweavers.com/compatibility/search?name=steam&company=&medal=&date_start](http://www.codeweavers.com/compatibility/search?name=steam&company=&medal=&date_start)

---

### Post by mbuller10 on 2010-05-06
Okay so I installed PlayonLinux in Lucid. Then I installed steam which seemed to go okay. Now when I try to click on Half Life 2 install through play on Linux it keeps saying incorrect steam username. When I try to start half life 2 directly though steam theres no sound and when I quit the resolution is all messed up. Can anyone help.

---

### Post by Schuby007 on 2011-01-03
I like how no one has posted anything actually useful to someone trying to get Steam running in 10.04.

---

### Post by cogadh on 2011-01-03
I like how you resurrected a thread that hasn't seen a post in almost a year just to pointlessly say that.

---

### Post by mbuller10 on 2011-01-23
I like how you both seem so interested in steam still, well here's an update, I built a new computer with a 1 Tb hard drive, and just install windows and linux, and use windows for all my non-free games and school stuff, I still use linux for downloading torrents, cracking passwords with aircrack, browsing web, but steam with wine just weren't meant to be

---

### Post by Halzen on 2011-01-23
I dunno about that. I'm running Steam silky smooth on my Linux Mint 10 setup. I used winetricks to install the dependencies it needed, and have had no problems at all. I even have most of my games (Half Life 2 and all Source games I own, for starters) running smoothly.

I should hope that everyone here has found Steam's WineHQ page and followed the installation steps included: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

Also, it should be noted that Source Engine games do not scale as well on Linux as they do for Windows for those of you with ancient hardware. The only reason I'm running everything on high settings is because I built this computer for gaming last year. Overclocked Core 2 Quad, overclocked GTX 260, 4GB of overclocked RAM, etc.

---

### Post by Schuby007 on 2011-01-29
> **Halzen said:**
> I dunno about that. I'm running Steam silky smooth on my Linux Mint 10 setup. I used winetricks to install the dependencies it needed, and have had no problems at all. I even have most of my games (Half Life 2 and all Source games I own, for starters) running smoothly.

I should hope that everyone here has found Steam's WineHQ page and followed the installation steps included: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444)

Also, it should be noted that Source Engine games do not scale as well on Linux as they do for Windows for those of you with ancient hardware. The only reason I'm running everything on high settings is because I built this computer for gaming last year. Overclocked Core 2 Quad, overclocked GTX 260, 4GB of overclocked RAM, etc.

Hey,

Nice rig. I have a fairly powerful laptop (Core 2 Extreme x9000, 4GB DDR2, GeForce 8800M GTX) and I can't play Counter Strike: Source on dx9; I get about 15-20fps, I have to use the terminal to open the game under Direct X8 to get about 60fps. Is this a problem with Wine trying to emulate Direct X? Because under Windows Vista, using Direct X 10 I get about 80fps with all settings maxed.

Thanks.

---

### Post by Halzen on 2011-01-29
> **Schuby007 said:**
> Hey,

Nice rig. I have a fairly powerful laptop (Core 2 Extreme x9000, 4GB DDR2, GeForce 8800M GTX) and I can't play Counter Strike: Source on dx9; I get about 15-20fps, I have to use the terminal to open the game under Direct X8 to get about 60fps. Is this a problem with Wine trying to emulate Direct X? Because under Windows Vista, using Direct X 10 I get about 80fps with all settings maxed.

Thanks.

This sounds like something that belongs in its own thread, but it might be a quick fix. To get a good CS:S framerate, I had to disable motion blur and color correction. I also left the dynamic light setting on Bloom since CS:S doesn't use HDR anyway. Check the WineHQ page for some other tweaks that ought to help you.

---

