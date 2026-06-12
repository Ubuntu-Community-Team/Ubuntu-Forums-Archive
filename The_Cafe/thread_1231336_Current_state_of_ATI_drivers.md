---
title: "Current state of ATI drivers?"
date: 2009-08-04
forum: The Cafe
---

### Post by Phreaker on 2009-08-04
I am going to  buy a laptop with an ATI card, what is the current state of their drivers?
I need the laptop to play world of warcraft

---

### Post by Skripka on 2009-08-04
The current driver state?

I'll put it this way--I'd say get a different laptop.

---

### Post by Pasdar on 2009-08-04
Don't expect best performance in Linux, but you get great performance in Windows. Not surpassable by NVIDIA with the same price. My previous laptop had an ATI 3470, and now I bought one with ATI 3650. The ATI drivers are getting better with the month anyway, I have patience.

---

### Post by CharmyBee on 2009-08-04
If it doesn't start with HD, then it's a no-go with the current fglrx drivers.

---

### Post by aaaantoine on 2009-08-04
The FOSS ATI driver stack is undergoing a complete overhaul, and in a year or so should be good for 2D and 3D applications.  But currently, no 3D support for R600/700 (this may change very soon), and not-so-good 3D support for other chipsets.

The proprietary ATI driver (fglrx) works with 3D now, but it...
- only supports modern GPUs (pretty much only Radeon HD as CharmyBee said)
- generally lags behind kernel and xserver updates.
- has some pretty wild bugs of its own.

---

### Post by realzippy on 2009-08-04
You have no choice,if you want linux with gaming and the fancy stuff running fine:
nvidia.

---

### Post by Can+~ on 2009-08-04
+1 to nvidia, ATI drivers never fail to disappoint me.

---

### Post by gravity_blast on 2009-08-04
for my x1950 they suck hard

---

### Post by binbash on 2009-08-04
Don't buy ATI if you are planning to play via wine.

---

### Post by alexandari on 2009-08-04
ATI fails in every way -_-"

---

### Post by doas777 on 2009-08-04
better, but still not even close to nvidia. I've had to install the version from their site every time, and spent days trying to do 20 minutes of configuration, becasuse every time I got the res up on the second monitor, or enabled 3da or whatever, I'd get blackscreen on teh next reboot.

---

### Post by CharmyBee on 2009-08-04
> **realzippy said:**
> You have no choice,if you want linux with gaming and the fancy stuff running fine:
nvidia.

Are we out of the year 2006 yet?

---

### Post by Blu Fox on 2009-08-04
Well that blows. I have an HD 4830, does that mean I'm screwed?

---

### Post by spoons on 2009-08-04
> **Blu Fox said:**
> Well that blows. I have an HD 4830, does that mean I'm screwed?

Well, only sort of. Compositing is pretty slow because of bugs, and Running DirectX games in Wine is a total and utter failure (don't even bother trying), but OpenGL applications work okay. PREY, for example, ran fine for me in Wine and Nexuiz, Open Arena work okay. The drivers are pretty damn awful to be honest though. Sometimes I can install Ubuntu, and install the ATi drivers, and resetting the X server will always cause a kernel panic. Other times, I can install Ubuntu and install the ATi drivers and this does not happen. ATi also beat the crap out of Nvidia in performance below the £200 bracket so it's a shame that the cards work so badly in Linux. I'm typing this on an ATi machine but I wish so much I had got an Nvidia card. If by the time I get a new card ATi haven't got their act together, I'm buying Nvidia.

I hope this helps.

---

### Post by Blu Fox on 2009-08-04
So if I want to use wine, a nvidia card is highly recommended?

---

### Post by racerraul on 2009-08-04
I had 3 computers with nvidia and 2 with onboard ATI HD3200.
I now have 5 computers with nvidia, two of those have the ATI HD3200 disabled.

I want to support open source as much as the next guy... but ATI at the moment sucks if you need more than the average 2D desktop functions.

---

### Post by gravity_blast on 2009-08-04
> **racerraul said:**
> I had 3 computers with nvidia and 2 with onboard ATI HD3200.
I have have 5 computers with nvidia, two of those have the ATI HD3200 disabled.

I want to support open source as much as the next guy... but ATI at the moment sucks if you need more than the average 2D desktop functions.

whats with all the pcs?

---

### Post by spoons on 2009-08-04
> **Blu Fox said:**
> So if I want to use wine, a nvidia card is highly recommended?

Not just recommended, but essential. Make sure, if you're constrained to a budget, the Nvidia card is comparable to the ATi card in performance and is fast enough for your needs.

Good luck.

---

### Post by Blu Fox on 2009-08-04
Well that sucks real hard since I'm kinda stuck with my card. Can't afford to go out and buy a new card at all.

---

### Post by racerraul on 2009-08-04
> **gravity_blast said:**
> whats with all the pcs?

I have a family.  Each of my kids has their own and I have two... 


Well three if I include the Windows XP laptop assigned to me by my employer.

---

### Post by doas777 on 2009-08-04
in all fairness, I have my HD3870 going alright, so your not screwed, unless you give up. it prolly took me 18 hours to get it going correctly, with dual monitors as ful res, 3da, and "big desktop".  the card was a bit of a pain in windows as well.

it'll prolly be fine unless you want dual monitors/tvouts or special color and 3D configurations.

---

### Post by gravity_blast on 2009-08-04
> **racerraul said:**
> I have a family.  Each of my kids has their own and I have two... 


Well three if I include the Windows XP laptop assigned to me by my employer.

hehe kk

---

### Post by 3rdalbum on 2009-08-04
I wouldn't look at ATI until:

1. They submit patches to Mplayer and VLC to add support for video acceleration, and this support is as good as Nvidia's VDPAU (or they support VDPAU on their cards)

2. Performance gets as good as Nvidia, on Linux.

---

### Post by Jackelope on 2009-08-04
For all the scary talk about terrible ATI drivers, my HD3450 runs pretty well. I can composite and play games just fine...it just has a lot of glitches here and there. Not unusable by any means, tho.

---

### Post by racerraul on 2009-08-05
> **doas777 said:**
>   **the card was a bit of a pain in windows as well.**


aint that the truth... I'm actually not surprised it's as big a deal in Linux since even with Windows they can't seem to get everything right.

---

### Post by magmon on 2009-08-05
It depends on what model of card it is. The newer ones have ati drivers available from the amd site.

---

### Post by stwschool on 2009-08-05
ATI + Games in linux (be it Wine or otherwise) fail pretty badly. I have a number of linux machines. My Intel machines will run Popcap games ok, but not much else. My NVIDIA machine plays anything. My ATI (very modern card) machine makes a right mess of anything gaming. That said, there is a clear improvement in the drivers, and the open-source drivers show some promise.

So, you have:
NVIDIA: Brilliant Linux performance.
Intel: Even in Jaunty not too bad, though far short of Windows performance (much slower)
ATI: A mess, but potentially could be good.

---

### Post by Private_Ops on 2009-08-05
> **stwschool said:**
> That said, there is a clear improvement in the drivers, and the open-source drivers show some promise.


The open source ATI drivers show a lot of promise. I'm currently running an AGP ATI X800 (r420) with Jaunty and the open source drivers have given me no problems at all since the installation. I haven't tried any games yet but Compiz works wonderfully.


I also have an ATI 4830 in another rig (hence, why it runs windows) and when I had Ubuntu on it the drivers were horrible. I couldn't run Compiz, videos flashed or didn't display, anything in wine (like CS:S) would hard lock the system after a random amount of time. The drivers were just a complete mess.

---

### Post by ssam on 2009-08-05
the developers have just got compiz working on the opensource drivers for r600/r700 [http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)

---

### Post by Blu Fox on 2009-08-05
> **Private_Ops said:**
> The open source ATI drivers show a lot of promise. I'm currently running an AGP ATI X800 (r420) with Jaunty and the open source drivers have given me no problems at all since the installation. I haven't tried any games yet but Compiz works wonderfully.


I also have an ATI 4830 in another rig (hence, why it runs windows) and when I had Ubuntu on it the drivers were horrible. I couldn't run Compiz, videos flashed or didn't display, anything in wine (like CS:S) would hard lock the system after a random amount of time. The drivers were just a complete mess.

That's weird. I have the exact same card but compiz/video work absolutely fine. I do have to change the video output to x11 on vlc but that's about it so far. Hadn't really tried out wine yet.

---

### Post by xir_ on 2009-08-05
i have a nvidia system and ati system.

nvidia really does just win, performance is far better and has far more features.

unfortunately i wont be buying ati again untill this is all fixed

---

### Post by AllRadioisDead on 2009-08-05
I have a HD 4850 and it's brutal in linux. I can't run anything WINE, my screen flickers for half a minute before opening any WINE app, it does this at boot as well. Resizing windows is also especially slow with KDE compositioning on. I'm probably going to sell it on craigslist and buy a Nvidia card.

---

### Post by Martje_001 on 2009-08-05
[http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)

ATi haters here..

---

### Post by Skripka on 2009-08-05
> **Martje_001 said:**
> [http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg](http://www.phoronix.com/scan.php?page=news_item&px=NzQyNg)

ATi haters here..

It is a good first step.  But running Compiz, and being able to run OpenGL2 and OpenGL3 games are 2 very different things.  Radeon still has a long way to go.

---

### Post by Phreaker on 2009-08-05
I am going to run WOW in wine, so I will get a nvidia then.
Thanks for posting everyone!

---

### Post by realzippy on 2009-08-05
Wise decision.Also it might be very usefull to have a look at the WLAN adapter thats built in...

---

### Post by Blu Fox on 2009-08-05
Yep. Within the next month or so (hopefully) I'll have a nvidia replacement. Looking into a 9800gt, nothing fancy or anything but gets the job done.

---

### Post by ssri on 2009-08-06
> **Skripka said:**
> It is a good first step.  But running Compiz, and being able to run OpenGL2 and OpenGL3 games are 2 very different things.  Radeon still has a long way to go.

From the comments, it seems like it was a proof of concept, something to build upon.  As if now, both Compiz and glxgears run slowly.  Still, all of this is good news.  However, I hope people do not go out and start purchasing ATi cards expecting to play the latest games.  It is not going to be next week or next month.  As everyone in phoronix knows, OpenGL2+ implementation will not come until gallium3d is stabilized sometime next spring or summer.  Also, there are other showstoppers for me from the opensource drivers.  I know I won't be leaving fglrx land for my legacy card until the wonky TV-Out is fixed for R500s, and to a lesser extent OpenGL2 support in mesa.  As shocking as it may sound, Catalyst 9.3 is running very smooth for me in Intrepid.  I can easily connect to my TV through S-Video.  Video playback exhibits tearing on very rare occasions if at all.  KWin desktop effects are fast and snappy.  The only negative thing is resuming from suspend, as it is a tossup affair.

---

### Post by Hallvor on 2009-08-06
Buy nvidia.

---

### Post by stwschool on 2009-08-06
> **Phreaker said:**
> I am going to run WOW in wine, so I will get a nvidia then.
Thanks for posting everyone!
Good decision, and really the only one available to you. So, install, add wine, winetricks to put on a few essentials like directx9, vcrun2005, vcrun2005sp1, msxml3, msxml6, vb6run and a few others and you should find most Windows stuff runs just fine.

---

