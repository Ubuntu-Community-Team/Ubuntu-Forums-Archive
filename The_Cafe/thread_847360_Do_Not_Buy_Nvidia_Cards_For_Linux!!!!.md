---
title: "Do Not Buy Nvidia Cards For Linux!!!!"
date: 2008-07-02
forum: The Cafe
---

### Post by GrantsV on 2008-07-02
I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.

---

### Post by iheartubuntu on 2008-07-02
Maybe it depends on your system. I have 8600 on my computer at home. It also has 4GB RAM and a single 3.6 ghtz processor. It kicks butt. I installed World of Warcraft on it for my sister to prove it would work on Ubuntu/linux systems and she was impressed. The game runs much faster with higher amount of detail and framerates as the same system with XP (its dual boot).

I dont know what youre talking about, other than "your mileage may vary". I think it sucks you are going around "warning" people of nVidia like this instead of going around asking more questions and being more informed about it.

An Intel card is never going to get the power of nVidia... SORRY!!!!

---

### Post by GrantsV on 2008-07-02
Sorry I wasn't being 100% clear.  3D works marvelous on Linux with NVidia.  Urban Terror with AntiAliasing etc works fantastic at over 100fps.

But general 2D desktop is really laggy.  For example I drag a window or scroll, it leaves a trail.  On very low spec Intel integrated motherboard video card, and on ATI cards, this is not an issue.

Please appreciate I spent months wondering what on earth was wrong with my laggy Linux desktop.  Dual booting to Windows confirmed Win offers instant response to desktop movements.  I have tried various drivers and am now on 173.14.05.

If I had spend my £100 on equivalent ATI card, all that time distro hoppy and trying to optimise the desktop would not have happened.  Had I not stumbled upon the Nvnews forums and saw all the others with the same problem I would still be thinking its Ubuntu being "bloated".

Nevertheless, NVidia is proclaimed the choice for Linux and that just simply isnt true in my recent experience of all 3 major makers of video cards.

Best regards,
Colin

---

### Post by chalewa on 2008-07-02
strange, never heard anything like this before.

---

### Post by Steveway on 2008-07-02
Yup, you propably mean the miserable Xrender performance of Nvidia-cards.
Those cards can do good 2D acceleration but it's mostly a driver-issue.
Nvidia knows about it but refuses to fix it. I'll change to the nouveau-driver as soon as I can. (Hope we get proper Ubuntu-packages.)

---

### Post by stchman on 2008-07-02
> **GrantsV said:**
> I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.

I have two nvidia cards (8800GT and 7600GT) running the 169.12 nvidia-glx-new drivers in Ubuntu Hardy 64 bit.  They both run Compiz perfectly.  If I switch Compiz off, the desktop is still super responsive.

I don't know what the problem with your system is.

Nvidia is the best choice of video card for Linux.  You will find that opinion shared by many on this forum.

---

### Post by Joshuwa on 2008-07-02
Running the 9600gt without problems.

I *specifically* bought this card for linux use, and it has been a dream. Getting the driver properly installed was a trial and error process, but I found a script that did it with ease, and it works perfectly now.

I'd personally have trouble recommended anything *other* than NVidia for linux.

---

### Post by wdaniels on 2008-07-02
> **GrantsV said:**
> ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I don't know anything about this issue since I've never had cause to look up any problems with NVIDIA cards - my 7600GS works brilliantly and always has done. So whatever trouble you're having, it doesn't seem to affect "anything beyond 6 series"...perhaps you have misidentified a more specific problem as this general Xrender performance issue?

There may well be poorer Xrender performance than there ought to be, but not to the extent you're describing I'm sure (unless the problem worsens somehow with faster cards?). I suggest you look at other potential problems before deciding that it's just something in the driver that can't be fixed.

---

### Post by GrantsV on 2008-07-04
I am hearing a few 8800 owners who are very happy, so my statement its all 6+ series appears to be wrong.

Let me illustrate my situation.  I just switched back to VESA drivers and my desktop is perceptable twice as quick than NVidia drivers with my 8600GT.  I measure this by scrolling around bloated web browser pages, and dragging window around with contents displayed.  With Vesa drivers, the CPU isn't getting slammed either.

Under a selection of NVidia's drivers, I get lag where the windows literally trail behind as they redraw, its that slow.  You can see Gnome menus being drawn on screen, its like having a 5 year old computer.  With Vesa drivers, is only just perceptible, however its still nowhere near as good as Windows, which for all purposes is instantaneous on the Desktop so long as you have the RAM and no other bottlenecks (e.g. clean install).

It is definitely a driver bug, and GTK cant be blamed because I am getting instantaneous reponse with ATI and Intel cards.  The ATI machine is identical in software and other hardware beyond the video card.  Its NVidia's drivers alone causing this.

Btw, I have Render enabled and other XORG options switched on.

---

### Post by regomodo on 2008-07-04
> **GrantsV said:**
> I am hearing a few 8800 owners who are very happy, so my statement its all 6+ series appears to be wrong.

I had a 6800gt for about 1.5yrs. No problems there even if it was overclocked a bit much.Have a 8800gt now, still no issues.

I have heard of this xrender issue and also look forward to the nouveau driver.

---

### Post by Lster on 2008-07-04
I have a NVidia 8600M GS graphics card on my laptop and it runs fine with Compiz enabled or not. I can't really see any difference to my older laptop that has an ATI Mobility Radeon x1400 in terms of desktop performance...

---

### Post by Polygon on 2008-07-04
uhh, running a nvidia 7000m here and no visible impact on 2d performance then my other comp with an ati card.

---

### Post by BlueSkyNIS on 2008-07-04
I agree with OP. To see what he is talking about you MUST turn off compiz, System -> Preferences -> Appearance -> Visual Effect : None, and you will see lagging while moving windows...


By the way, GrantsV, what is your graphics type and model? Mine is Gigabyte 8600GT.

---

### Post by HansKisaragi on 2008-07-04
I used to have a 8400 everything ran smoothly .. no problem what so ever .. tho i know that the latest nvidia cards have heating problem ..

I use ATi now tho, and couldn't be happier .. :)

---

### Post by dacorr on 2008-07-04
i got he 8500GT with envy drivers and not a problem

Dac

---

### Post by BlueSkyNIS on 2008-07-04
I want to add to my post: lagging effect is visible only when moving windows above Firefox.

---

### Post by Extreme Coder on 2008-07-04
I got to agree with the OP..
I had a 8600 GT, and while it was working well in 3D, I sold it because the desktop didn't feel responsive enough :/
Now I couldn't be happier with my ATI x1650 Pro.
The fact that nVIDIA knows that the latest 8 series doesn't support X Render and do not plan to, is reason enough for me to not recommend nVIDIA and buy ATI instead. Also, they recently said they will not open souce their drivers or give out documentation anytime soon, unlike ATi.

---

### Post by geoken on 2008-07-04
But if you do use compiz, won't you get significantly worse performance and more buginess by switching to ATI.

---

### Post by Chame_Wizard on 2008-07-04
I have a Nvidia Gforce 7600 GS,some problem with the monitor.

Having problem with it on Kubuntu(Compiz don't work:?:cry:)

---

### Post by OldTimeTech on 2008-07-04
I run Nvidia 8800GTS on both a laptop and a desktop and I haven't noticed any lag...either in doing regular work on desktop or with Firefox...and I don't use Compiz at all...

I think every machine has it's own attitude to parts and drivers....kind of like every car has it's own attitudes...LOL!

---

### Post by Enthralled on 2008-07-04
Is GeForce 9600GT running good on Linux? I'm buying it tomorrow, so it would be helpful if someone told me. :)

---

### Post by Tomatz on 2008-07-04
The 8800 is notoriously buggy with the latest drivers in Linux. My 8600 works like a charm though ;)

---

### Post by Crusty Juggler on 2008-07-04
> **GrantsV said:**
> I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.

I also must beg to differ.  I am having heaps of problems with an Intel 945GM integrated card on my wife's laptop.  I am resorting to using the Vesa driver because the performance of the intel and i810 drivers are so rubbish.  The nVidia card I bought for my Mythbuntu box is much better, even though it's a low end 8400GS.

---

### Post by Xanatos Craven on 2008-07-04
Hm, I thought something weird was up with my machine... I just thought X was the only culprit, since Windows had better graphical performance on the same hardware and because I heard nVidia drivers on linux were great. Got a 7800GS, my desktop is laggy too. Though not quite as horrible as OP's sounds. ATI drivers were unusable for me at the time I got the card, but I may find myself switching back to one of ATI's at this rate.

---

### Post by days_of_ruin on 2008-07-04
The newer ati cards are going to have linux drivers in the box(if they
haven't started already) so it looks like nvidia is not the only
choice anymore.

---

### Post by Riffer on 2008-07-04
A 7300 gs here and I have the opposite problem.  2d sreams its so fast but there is a noticeable lag when compiz is enabled.

---

### Post by KillerSponge on 2008-07-04
I have a 6600GT, 8800GT and a 8400M G, and I haven't experienced any 'lag' at all. Everything is very responsive, with of without compiz. Except for when I don't install the nVidia driver, then Firefox lags the hell out of me :P

---

### Post by FuturePilot on 2008-07-04
I've never seen this lag. :confused:
GeForce 6600, and GeForce 8400M GS both work great.

---

### Post by barney385 on 2008-07-04
My 8600 mobile GT works great. Have never had a problem.

---

### Post by lnxnut on 2008-07-04
I built my computers right before I started using Linux using ATI Radeon 9600 Pro's 4 1/2 years ago.  The drivers have always been behind Nvidia's.  I'm upgrading now and I'm looking mainly at Nvidia.  What am I doing?  Am I going behind the curve again or what?  Should I stay with ATI?

---

### Post by swoll1980 on 2008-07-04
I have a nvidia 6200, and a Intel 845. I use compiz. The nvidia works perfectly. The Intel 845 crashes like 5 times a day if I try to run compiz, so I have to keep it disabled.

---

### Post by kripkenstein on 2008-07-04
> **Enthralled said:**
> Is GeForce 9600GT running good on Linux? I'm buying it tomorrow, so it would be helpful if someone told me. :)
I am running a 9600GT right now, it works great. Had to set up the driver from NVidia, not the one in the repos though, but a howto on these forums was easy to find.

3D is **very** fast, 2D looks fine to me. Main problem with the card is that without binary drivers the fan runs at 100% all the time, but with the binary drivers it's fine.

Regarding the original complaint of slow 2D on new NVidia cards - it seems all people are saying in this discussion is "it's slow" and "it's not". How about if the people claiming it's slow provide evidence, that is, a video (with sufficient framerate, and taken from an external camera presumably) that shows the problem. Then we can understand the issue.

---

### Post by YaroMan86 on 2008-07-04
I use an onboard 6150SE. 3D is fantastic, and 2D is perfectly fine. Driver from the Restricted Drivers Manager worked no problem.

---

### Post by geoken on 2008-07-04
> **kripkenstein said:**
> 



Regarding the original complaint of slow 2D on new NVidia cards - it seems all people are saying in this discussion is "it's slow" and "it's not". How about if the people claiming it's slow provide evidence, that is, a video (with sufficient framerate, and taken from an external camera presumably) that shows the problem. Then we can understand the issue.

I think the problem is that a lot of people have never ran anything else, or at least haven't had two configurations close enough to make an accurate comparison. Also, people might be using computers where UI elements are being bottlenecked by other things. 

I don't personally consider the desktop slow, but there are certain areas where I could see it being faster but I've never used anything else so I always thought it was simply a gnome thing. It's mostly little things like how I can see the icons coming in when I click a menu, or how my resize method is 'outline' because I used to get serious lag resizing windows with any other method. I've also noticed extreme slowness while using inkscape with many items on the canvas, but I always assumed this was an inkscape issue.

---

### Post by kripkenstein on 2008-07-04
> **geoken said:**
> 
I don't personally consider the desktop slow, but there are certain areas where I could see it being faster but I've never used anything else so I always thought it was simply a gnome thing. It's mostly little things like how I can see the icons coming in when I click a menu, or how my resize method is 'outline' because I used to get serious lag resizing windows with any other method. I've also noticed extreme slowness while using inkscape with many items on the canvas, but I always assumed this was an inkscape issue.

The problem is, such descriptions don't help other people understand the issue. And certainly this might be an actual problem, even though I haven't seen it on any Linux desktop I've used - maybe I don't have a good enough eye for these things. So, concrete evidence is needed.

Movies or it didn't happen ;)

---

### Post by reyfer on 2008-07-04
Nvidia GeForce FX5500 128 MB, running smoothly, with or without Compiz

---

### Post by BlueSkyNIS on 2008-07-04
> **kripkenstein said:**
> Regarding the original complaint of slow 2D on new NVidia cards - it seems all people are saying in this discussion is "it's slow" and "it's not". How about if the people claiming it's slow provide evidence, that is, a video (with sufficient framerate, and taken from an external camera presumably) that shows the problem. Then we can understand the issue.

Here: [http://www.youtube.com/watch?v=OHUslzXTzDQ](http://www.youtube.com/watch?v=OHUslzXTzDQ)

Notice how the effect is visible only while moving a window over Firefox.

---

### Post by GrantsV on 2008-07-04
There is a program to measure response.  Gtkperf I think??
On the nvnews and nvidia forums there are many how have tested this and proved the dreadful 2d performance with NVidia 8 series.

I have to say, if I didnt have the ATI and Intel machines sat here to compare I might not have even noticed.  Also dual booting daily for Illustrator etc shows me constantly how slow NVidia 2d is on the desktop.

Those with higher spec cards may be brute forcing through the issue.

This thread is not about an issue of installation/compatibility etc.  Intel video might be harder to get going!  But my issue is that once everything is up and running, the x-render performance is poor on NVidia 8600GT and there are many reports of it effecting 8 series +.

My main reason for posting this is because people all over the net are blaming "bloated" distros, Linux and everything else, for sluggish performance when it may just be NVidia at the root!

Take care

---

### Post by FuturePilot on 2008-07-04
> **geoken said:**
> I think the problem is that a lot of people have never ran anything else, or at least haven't had two configurations close enough to make an accurate comparison. Also, people might be using computers where UI elements are being bottlenecked by other things. 

I don't personally consider the desktop slow, but there are certain areas where I could see it being faster but I've never used anything else so I always thought it was simply a gnome thing. It's mostly little things like how I can see the icons coming in when I click a menu, or how my resize method is 'outline' because I used to get serious lag resizing windows with any other method. I've also noticed extreme slowness while using inkscape with many items on the canvas, but I always assumed this was an inkscape issue.

I have run an ATI card with the fglrx driver and it sucked big time.

The thing with the menu has nothing to do with the graphics card. It's the way the menu works. It doesn't preload the icons, instead it loads them on the fly the first time you open the menu. Are you using Compiz when you see this lag when resizing windows? If so that problem happens even in Vista. I'm guessing it's just a compositing thing.

> Here: [http://www.youtube.com/watch?v=OHUslzXTzDQ](http://www.youtube.com/watch?v=OHUslzXTzDQ)

Notice how the effect is visible only while moving a window over Firefox. 

That's just how stuff is when you don't use a composite layer. A composite layer eliminates that behavior because it draws to a buffer, whereas without a composite layer you're pretty much drawing directly to the screen. I can reproduce that behavior on Windows too so it's not a Linux thing. Also I think Firefox may be partly to blame too.

---

### Post by Steveway on 2008-07-04
> **BlueSkyNIS said:**
> Here: [http://www.youtube.com/watch?v=OHUslzXTzDQ](http://www.youtube.com/watch?v=OHUslzXTzDQ)

Notice how the effect is visible only while moving a window over Firefox.

Firefox is one of the more heavy users of x-render. So this behavious is explainable by the lousy x-render performance of Nvidia-cards.

---

### Post by grossaffe on 2008-07-04
my nVidia Geforce 5500 FX runs flawlessly with in Gutsy Gibbon with Compiz, and my nVidia 8400 GS runs flawlessly in Hardy Heron 64-bit with Compiz.  I don't know what problems you're having, but its certainly not giving me any problems with my nVidia cards.

---

### Post by Steveway on 2008-07-04
> **grossaffe said:**
> my nVidia Geforce 5500 FX runs flawlessly with in Gutsy Gibbon with Compiz, and my nVidia 8400 GS runs flawlessly in Hardy Heron 64-bit with Compiz.  I don't know what problems you're having, but its certainly not giving me any problems with my nVidia cards.

You have to turn off compiz and start some x-render heavy applications like firefox to see this.

---

### Post by grossaffe on 2008-07-04
> **Steveway said:**
> You have to turn off compiz and start some x-render heavy applications like firefox to see this.
wait, so I have to disable compiz to have problems with my computer?  well hot damn, let me go and do that now!:)

---

### Post by BlueSkyNIS on 2008-07-04
> **Steveway said:**
> Firefox is one of the more heavy users of x-render. So this behavious is explainable by the lousy x-render performance of Nvidia-cards.

I use Compiz anyway, so it's not a big issue for me. I just wanted to confirm OP statements about possible performance issues with nv8600 cards...

---

### Post by Hells_Dark on 2008-07-04
Well, i have a **8800GT**, i use compiz, all works well :).

But i have to agree : moving a window is **not** as smooth as it should be.

---

### Post by kripkenstein on 2008-07-04
> **BlueSkyNIS said:**
> Here: [http://www.youtube.com/watch?v=OHUslzXTzDQ](http://www.youtube.com/watch?v=OHUslzXTzDQ)

Notice how the effect is visible only while moving a window over Firefox.
Thanks for the video. And yes, that does look quite bad.

However, I've never noticed that myself, but if it only occurs over Firefox windows then perhaps I just never noticed. On my current machine, with a 9600GT, this doesn't happen.

Perhaps it's an issue with Firefox?

---

### Post by GrantsV on 2008-07-05
Everyone is blaming Firefox3 for poor performance. I think its only in webpages with lots of graphics you can see the issue very clearly while most people aren't inconvenienced by the issue dragging windows around and dont identify theres a problem.

I have tried Kazehakase and Firefox2 web browsers and the issue still remains. As you quite rightly say Firefox on Win flies!

I have installed so many distros, even the IceWM/Rox 80mb "Puppy Linux" and the issue is still there despite tiny resources being used.

Using Compiz with the window contents being dragged is just fine under the ATI, Intel and Windows.  Not perfect, but like the guy above said, its by nature not perfectly smooth due to the amount of redraws.  But on NVidia

---

### Post by GrantsV on 2008-07-05
PROOF!

Snapped with my camera just pulling a Window across the desktop.  Takes about 1/2 second to clear with Vesa drivers but a whopping 1 second to redraw with NVidia drivers.  No matter which distro, Xorg settings, or Window manager this same thing happens.

This does not happen on ATI/Intel.

Of course on the same machine in Windows dual boot it files with or without eye candy.

---

### Post by kripkenstein on 2008-07-05
> **GrantsV said:**
> PROOF!

Snapped with my camera just pulling a Window across the desktop.  Takes about 1/2 second to clear with Vesa drivers but a whopping 1 second to redraw with NVidia drivers.  No matter which distro, Xorg settings, or Window manager this same thing happens.

This does not happen on ATI/Intel.

Yeah, that's very bad, I agree.

---

### Post by Redache on 2008-07-05
This is why my next video card will be an ATI HD 4850 or 70 (can't decide if i want to fork out extra for the 70.). Nvidia took something out of the Windows Driver in the 8 series that renders Medieval Total War unplayable and that is one of the most annoying things for a company to do imaginable.

---

### Post by Lster on 2008-07-05
[QUOTE=BlueSkyNIS]I agree with OP. To see what he is talking about you MUST turn off compiz, System -> Preferences -> Appearance -> Visual Effect : None, and you will see lagging while moving windows...


By the way, GrantsV, what is your graphics type and model? Mine is Gigabyte 8600GT.[/QUOTE]

I don't get any lagging with Compiz enabled or not.

---

### Post by BlueSkyNIS on 2008-07-05
> **GrantsV said:**
> Everyone is blaming Firefox3 for poor performance. I think its only in webpages with lots of graphics you can see the issue very clearly while most people aren't inconvenienced by the issue dragging windows around and dont identify theres a problem.

It was Ubuntu forums.

---

### Post by GrantsV on 2008-07-05
Running CounterStrike Source on Wine with my 8600GT rendered terrible, 10 FPS.  I see on the Wine database some people get 10-15fps, others 80+ and they cant work out why when the cards are similar power/generation!

Swap to the ATI card 1950Pro with everything else the same and it runs just like Windows (80FPS).  I dont know the details of how Wine renders but the driver problem effects this type of 3d as well as the desktop 2d.

All the best

---

### Post by BlueSkyNIS on 2008-07-05
> **Lster said:**
> I don't get any lagging with Compiz enabled or not.

It's only visible with _Firefox running and Compiz off_; at least at my computer. Try to move a window over the Firefox window and you should see the lagging.

While Compiz is on there are no issues and no lagging effects. 

Maybe only 8xxx users are affected? No one here with nv9600 reported the problem?

---

### Post by SoberWarlock on 2008-07-16
I got to admit I noticed this too. I had a working 8800GTS 320mb and it was pretty bad with 2d rendering. Using firefox was pretty hard :P On this other cmoputer that belongs to my dad that has an ATI card seemed to have better 2d rendering performance, but I just like playing games and I don't want to get an ATI. I can't even run Counter-Strike 1.6 (steam) on an ATI card in Linux without it freezing or flickering all the time.

---

### Post by toupeiro on 2008-07-17
Can't say I can corroborate this at all...  I have over 100 linux desktops each running Quadro FX Nvidia cards for 3d modeling that blow the doors of the windows boxes attempting to do the same thing...  Windows needs a lot more out of the system, using identical hardware, to push the models I push on Linux fluidly.    I highly suspect a configuration problem.

---

### Post by tuxxy on 2008-07-17
Im running the 8600GTS and its superb, the drivers are much better than ATI and would recommend nVidia cards over ATI to Ubuntu users based on my experience definitely.

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsNvidia)

---

### Post by screaminj3sus on 2008-07-17
> **FuturePilot said:**
> I have run an ATI card with the fglrx driver and it sucked big time.

The thing with the menu has nothing to do with the graphics card. It's the way the menu works. It doesn't preload the icons, instead it loads them on the fly the first time you open the menu. Are you using Compiz when you see this lag when resizing windows? If so that problem happens even in Vista. I'm guessing it's just a compositing thing.



That's just how stuff is when you don't use a composite layer. A composite layer eliminates that behavior because it draws to a buffer, whereas without a composite layer you're pretty much drawing directly to the screen. I can reproduce that behavior on Windows too so it's not a Linux thing. Also I think Firefox may be partly to blame too.

No the window resizing slowness is a very well known bug and is a problem with the way compiz handles window resizing, this does not happen in aero. I recommend you use the "stretch" plugin, provides a nice compromise, it isn't horribly slow and looks good.

I can confirm the windows lagging when you drag them over firefox with my 9600GT. and also firefox's xrender performance is simply awful, the animations lag horribly, like when the remember password thing comes down, not anywhere as close to as smooth as firefox in vista.

---

### Post by FuturePilot on 2008-07-17
> **screaminj3sus said:**
> No the window resizing slowness is a very well known bug and is a problem with the way compiz handles window resizing, this does not happen in aero. I recommend you use the "stretch" plugin, provides a nice compromise, it isn't horribly slow and looks good.

I can confirm the windows lagging when you drag them over firefox with my 9600GT. and also firefox's xrender performance is simply awful, the animations lag horribly, like when the remember password thing comes down, not anywhere as close to as smooth as firefox in vista.

Interesting. However when resizing windows in Vista I see huge CPU spikes. But either way it is a Compiz bug and has nothing to do with Nvidia. I also have found that using the stretch resize is a good workaround. I actually like it better than just plain resizing, it's cool the way it distorts everything. :p

---

### Post by geogur on 2008-07-17
I am building a pc using an intel media (dp35dp)mother board core duo chip and plan on purchasing a nvidia 9600 (alu heat sink cooling) putting it all in an antec 900 gaming case (on back order) . the reason I am planning on the 9600 is try and get one $170.00 as apposed to $550.00 for the 9800 gtx . The three hundred I save on a vidio card will buy a tb hd. with $100.00 left over .

---

### Post by EdThaSlayer on 2008-07-17
I have a sweet Nvidia 9500m with 512m of vram. Everything works just the way I want to. Now I can even play Guild Wars in Wine with the highest graphics(something I couldn't do with a ATI Radeon 9600/9700m). It's just a small problem, will take Nvidia with slow 2d but fast 3d over ATI with slow 3d and fast 2d. :)

---

### Post by Cresho on 2008-07-17
> **GrantsV said:**
> I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.

you really need to tell us what you are talking about.  My system runs fine and I see no problems at all.  Even the video has no problems.  My desktop looks like 200fps.  No tear no nothing.  I am assuming that you are talking about refresh problems.

---

### Post by the_darkside_986 on 2008-07-17
I usually don't have this problem, but the suggestion makes no sense as there are no better hardware vendors. I mean, I cannot just go out and buy a PCI-e Intel card, I don't think they sell their gfx devices separately. And ATI Linux support is still far from decent. Anyway, I think the experimental free software "nouveau" driver has better 2D support for Nvidia cards but limited 3D ability.

---

### Post by eragon100 on 2008-07-17
> **the_darkside_986 said:**
> I usually don't have this problem, but the suggestion makes no sense as there are no better hardware vendors. I mean, I cannot just go out and buy a PCI-e Intel card, I don't think they sell their gfx devices separately. And ATI Linux support is still far from decent. Anyway, I think the experimental free software "nouveau" driver has better 2D support for Nvidia cards but limited 3D ability.

NouCrab has no 3d at all :(

I am happily using the official nvidia drivers on a 512 MB GeForce 7 7500 LE.

Fast 2d and 3d! :popcorn:

---

### Post by diffuze on 2008-07-17
I have a 7900GS and it's super smooth, both in 3D and in 2D.
"2D desktop" without any 3D loaded is fast and snappy, I've never had issues with it.

I normally use Compiz though. ;)

---

### Post by Corvair on 2008-07-17
I have recently built a system around an EVGA nForce 680i with Heron Hardy.
I am using an XFX GeForce 7300 GT 512 MB PCIe graphics board and OCZ SLI 4096MB PC6400 DDR2 800MHz (2 mem. strips). I have had no issue with this system, very fast, works beautifully. I would recommend it to anyone.
Nvidia is great.

---

### Post by Redrazor39 on 2008-07-17
Damn I have an Nvidia Geforce Go 7400... No wonder there are some response quirks :(

I hope this gets fixed!

---

### Post by grossaffe on 2008-07-17
yeah, I did notice that my laptop with an 8400 was slower with 3d effects at times than my desktop with a 5500 FX

---

### Post by FuturePilot on 2008-07-17
> **grossaffe said:**
> yeah, I did notice that my laptop with an 8400 was slower with 3d effects at times than my desktop with a 5500 FX

That's because of Powermizer. Anything prior to the 8 series cards do not have this feature. It basically scales your GPU which can make Compiz and other 3D things seem sluggish sometimes until it decides to scale the GPU up to full.

---

### Post by grossaffe on 2008-07-17
> **FuturePilot said:**
> That's because of Powermizer. Anything prior to the 8 series cards do not have this feature. It basically scales your GPU which can make Compiz and other 3D things seem sluggish sometimes until it decides to scale the GPU up to full.

ok, that makes sense since it seems unsure of itself at first and then works at full speed.  is that a power-saving feature or something?

---

### Post by Extreme Coder on 2008-07-17
First of all, people who DO NOT have a GeForce 8/9 Series card should not be posting here. If you just did a little bit more effort, you would've seen this:
[http://www.nvnews.net/vbulletin/showthread.php?t=115916](http://www.nvnews.net/vbulletin/showthread.php?t=115916)
Which clearly states there is a problem with 8/9 series ONLY in Linux, and nVIDIA acknowledges that. Because this thread is just turning into lots of posts that say:" I have nVIDIA card blablabla, and everything is as good as it can be", even though you don't have a card of 8/9 Series!
Second, if you don't believe the OP, then try using KDE 4 on a GeForce 8/9, and tell me how fast it was. The reason KDE 4 will be slow because it heavily depends on XRender, and XRender depends on the 2D acceleration of the card's driver!
> I have a sweet Nvidia 9500m with 512m of vram. Everything works just the way I want to. Now I can even play Guild Wars in Wine with the highest graphics(something I couldn't do with a ATI Radeon 9600/9700m). It's just a small problem, will take Nvidia with slow 2d but fast 3d over ATI with slow 3d and fast 2d.
Comparing a card of the latest generation with a card from over 4 generations ago isn't very smart ;)
And can you prove ATI has slow 3D? Since the new drivers with the updated and shared codebase(they use the same base for Windows and Linux) speed has greatly improved, and ATI cards easily outperform nVIDIA cards of the same price. Look on phoronix.com and see the benchmarks yourself.

---

### Post by timzak on 2008-07-17
deleted

---

### Post by stchman on 2008-07-17
> **GrantsV said:**
> I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.

I run two different machines using a 7600GT and an 8800GT.  They both run the desktop very well and have excellent response.

I have never come across what you speak of.  Nvidia is the best video card for Linux.

---

### Post by edfish on 2008-07-17
[URL="http://ubuntuforums.org/edfish@live.co.uk"]i have Nvidia graphics card. works a treat!
i run windows xp and linux on my refubbished packard bell laptop!
1.6 GHz 1gb ram nividia graphics card ??????? 258mb video ram

edfish@live.co.uk[/URL]

---

### Post by Ioky on 2008-07-17
are you sure it is not your problem? I have use 7600 for like a year and so. It doing it's job beautifully, And as you see, you seem like the only one here have this problem. So maybe it is nice for you to ask, instead of warning people. I know nvidia is not perfect yet for linux, well so did the other one. But as what it is, it do have a better rendering/display than ATI, yes, ATI do have the speed, but there isn't many thing in linux need that kind of speed. So nvidia is still the first reasonable choice for linux user. (I think)

---

### Post by geekygirl on 2008-07-17
You must have other hardware issues as I am running an XFX 9600GT 512MB GPU (system specs in sig) and my desktop runs like a dream. Compiz on or off, Gnome, KDE and XFCE ALL run very nice - far better than my old Intel Intergrated graphics did on an older notebook I had....2D performance is amazing with the 9600GT..sorry to crush that theory....(works better in Ubuntu than it did under Vista or XP....)

I think you need to change the thread title as someone might actually beleive what you are saying rather than noticing how many people have had success with Nvidia cards...

*sigh*

---

### Post by zachtib on 2008-07-17
Yeah, my Quadro 570M (8600M GT) works great.  As for the 2-d issue, I wouldn't know, I run compiz, so it's always utilizing the 3-d acceleration on my card.  In 3 years or so, when it's time for a new laptop, I'll reevaluate Intel and AMD/ATI's offerings, but at the moment, this was the best choice for what I needed it to do.

---

### Post by d3drocks on 2008-07-17
i have a factory overclocked gforce 7800 GT in my pc, and have no issues on ubuntu with it. i just install the closed source drivers, and im good.

---

### Post by screaminj3sus on 2008-07-17
lol did any of you read the post saying it is an issue with 8/9 seriies cards only? This DOES happen with my beefy 9600GT, firefox's animations are ridiculouslously laggy for a card of this power, my radeon x300 is smoother in firefox.

---

### Post by Mizzou_Engineer on 2008-07-18
> **Crusty Juggler said:**
> I also must beg to differ.  I am having heaps of problems with an Intel 945GM integrated card on my wife's laptop.  I am resorting to using the Vesa driver because the performance of the intel and i810 drivers are so rubbish.  The nVidia card I bought for my Mythbuntu box is much better, even though it's a low end 8400GS.

Hmm, I have the opposite experience. My laptop with its 945GM hasn't given me any trouble since the old xserver-xorg-i810 driver got phased out for the newer xserver-xorg-intel driver that eliminates the 915resolution VBIOS hack to get the panel's native 1280x800 resolution. Also, XvMC on the 945GM with the xserver-xorg-intel-2.3.0+ drivers actually works well with MythTV, as opposed to the GeForce 6200 in my actual MythTV box. XvMC there actually causes *higher* CPU usage than with plain old XVideo. I have a hunch that it's something with MythTV's implementation of XvMC as I can use MPlayer with the "-vf ffmpeg12mc" option and see the big dip in CPU usage, but whatever it is, the NVIDIA card doesn't play nicely but the Intel one does. I have an ATi card in my desktop and it doesn't have XvMC (no ATi cards do at the present time) but it works very well doing everything else.

EDIT: To reply to the OP's statement, 2D performance looked fine- it was XvMC that was acting funky on the 6200. I can't say that I really did a lot of window dragging on that machine when it was hooked up to a monitor (a 720x480 TV screen doesn't really allow much window dragging) but I didn't notice anything funny and I would certainly notice something that was obviously wrong like 1-second refresh times.

---

### Post by bigbrovar on 2008-07-18
i can confirm this .. before when i started linux i my laptop was an intel 945 GMA but my Linux mento kept telling me that Nvdia was the best graphic card for LInux  .. and even though My intel card ran compiz like it was liquid i decided to go for a nvdia card the i changed notebook .. it was the biggest Mistake i ever made .. i got a sony viao fz21e which came with nvidia 8400gt .. i still swear  at it till this very day .. the card was crap and i went through hell with it .. if i want to be productive i would just switch off compiz .. cus it would just slow down my system to a crawl .. this doesnt happen often but when it does .. i have to restart the system .. although with time nvidia released better drivers for it ... it wasnt in any as good as the intel card on my brother notebook.. that one runs like liquid .. to break.. no slow down ... all the transition is flawless .. i had to sell the laptop when i couldnt take it anymore .. am in the market now for a new notebook with intel card .. am done messing with closed source hardware that **** on the community ..
also nvidia as an age old bug with kopete that crashes x .. sigh

---

### Post by Delever on 2008-07-18
My experience with Compiz and ATI card was horrible.
My experience with Compiz and NVIDIA card IS perfect.
How can I listen to your "don't buy" advice?

---

### Post by o.besner on 2008-07-18
Don't let Ubuntu configure your X.org with Nvidia and you'll be allright. I've always had terrible performances with my 7600GT card until this : 

```
sudo apt-get install nvidia-settings nvidia-xconfig
```

then : 

```
sudo nvidia-xconfig --composite --twinview --dynamic-twinwiev
```

That's what I need. If you have other needs, simply check the choices under ```
nvidia-xconfig -A
```

once it's done, finish the job with :

```
sudo nvidia-settings
```

and configure the rest. Voilà. :)

---

### Post by jespdj on 2008-07-18
The 8600M GT in my XPS M1530 works without any performance problems. I've never noticed the slow scrolling in Firefox or any other graphics performance problems.

I'm using the nvidia restricted driver that comes with Ubuntu 8.04; that's version 169.12.

The only thing that seems slow is Youtube videos in full screen mode, but I think that's a problem in the Flash player, because videos in other applications in full screen mode work nicely.

---

### Post by OffHand on 2008-07-18
> **jespdj said:**
> the 8600m Gt In My Xps M1530 Works Without Any Performance Problems. I've Never Noticed The Slow Scrolling In Firefox Or Any Other Graphics Performance Problems.

+1

---

### Post by damis648 on 2008-07-18
> **jespdj said:**
> The 8600M GT in my XPS M1530 works without any performance problems. I've never noticed the slow scrolling in Firefox or any other graphics performance problems.

I'm using the nvidia restricted driver that comes with Ubuntu 8.04; that's version 169.12.

The only thing that seems slow is Youtube videos in full screen mode, but I think that's a problem in the Flash player, because videos in other applications in full screen mode work nicely.

+1...

PS. How did you get 64-bit on your M1530? I couldn't even boot up the liveCD.

---

### Post by OffHand on 2008-07-18
> **damis648 said:**
> +1...

PS. How did you get 64-bit on your M1530? I couldn't even boot up the liveCD.

Nah...32bits OS. Little reason to use the 64bits for me.

---

### Post by Steveway on 2008-07-18
> **geekygirl said:**
> You must have other hardware issues as I am running an XFX 9600GT 512MB GPU (system specs in sig) and my desktop runs like a dream. Compiz on or off, Gnome, KDE and XFCE ALL run very nice - far better than my old Intel Intergrated graphics did on an older notebook I had....2D performance is amazing with the 9600GT..sorry to crush that theory....(works better in Ubuntu than it did under Vista or XP....)

I think you need to change the thread title as someone might actually beleive what you are saying rather than noticing how many people have had success with Nvidia cards...

*sigh*

It's not a theory, it's a fact and it has been said several times that the nvidia-developers know about that and acknowledge that officially.

---

### Post by drascus on 2008-07-18
you are absolutely correct. I have an Nvidia card in my laptop and it performs terribly. especially when on battery power. I think this is mainly due to Nvidia not being very good at working with the Free and Open source communities. The refuse to release specs that would allow developers to come up with good Free Drivers that would run the hardware better then their proprietary drivers due under Gnu/Linux. The result is very crappy performance. Intel on the other hand is good at working with us. ATI and AMD are beginning to catch on and their performance is slowly improving. My suggestion is complain like crazy to Nvidia and on top of it try to not get a computer with one. maybe if their stock drops a few points they will listen to the community a bit more.

---

### Post by jespdj on 2008-07-18
> **damis648 said:**
> PS. How did you get 64-bit on your M1530? I couldn't even boot up the liveCD.
It just works, I didn't have to do anything special - the live CD works normally on my XPS M1530. Are you sure your live CD doesn't contain errors? Try burning a new CD, or downloading the ISO image and burning it again, and check the checksum.

See [Ubuntu on the Dell XPS M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

---

### Post by pound_forthesound on 2008-07-18
There seems to be a lot of doubting thomas's here, but this is a real problem, even the KDE4.1rc1 release announcement mentions it - [http://kde.org/announcements/announce-4.1-rc1.php](http://kde.org/announcements/announce-4.1-rc1.php)

---

### Post by screaminj3sus on 2008-07-18
> **geekygirl said:**
> You must have other hardware issues as I am running an XFX 9600GT 512MB GPU (system specs in sig) and my desktop runs like a dream. Compiz on or off, Gnome, KDE and XFCE ALL run very nice - far better than my old Intel Intergrated graphics did on an older notebook I had....2D performance is amazing with the 9600GT..sorry to crush that theory....(works better in Ubuntu than it did under Vista or XP....)

I think you need to change the thread title as someone might actually beleive what you are saying rather than noticing how many people have had success with Nvidia cards...

*sigh*
Quite the opposite with my 9600GT, while compiz and all the fancy effects run flawlessly scrolling in the firefox addons window for example feels like I'm running a pentium II.

When the remember password thing comes up in firefox the animation is like 3 fps.

scrolling pages is generally much less smoother than windows.

I'm just going to make a video and put it on youtube later as visual proof.

I get none of these problems with the open source "nv" driver.

The vista nvidia driver CRUSHES the linux one for me in general 2d/3d performance, there is definitely an issue with the nvidia driver, although obviously it does not affect every single person it is there and obviously affects a lot of users. I am running the very latest driver from nvidia.

---

### Post by Nebutron on 2008-07-18
Seems there are sufficient numbers of people who clearly experience this problem to support the notion that there really is a problem out there.  I am an Nvidia fan and quite disappointed to hear that they have no plans to improve their drivers or offer any open source drivers for their hardware.  That alone is enough to make me seriously consider going with ATI for my next build.  I am glad this thread was posted.  It would be a disservice to Ubuntu and the community if we went on thinking it was Ubuntu causing the poor performance.  Thanks GrantV!

---

### Post by Extreme Coder on 2008-07-19
Yet even after I post, people plug their ears and say: "lalalala, I don't hear you. I'm working fine." Even though no one of them has even cared to try KDE 4. Why does KDE 4 run like a snail on nVIDIA? It must be ATI and NVIDIA that are horribly messed up to run it at decent speed!

---

### Post by fwojciec on 2008-07-19
I can confirm this on my hardware.  I'm using 7900GS card with the latest nvidia drivers and I can tell, for sure, that there is something seriously wrong with 2d rendering performance, though the artifacts on my system are not nearly as obvious as on some pictures/videos earlier on in this thread.  For me, if I open empty firefox window (about:blank) and move it around fast I can see how the window is being redrawn around the edges -- it kind of looks like tearing.  This is annoying, moving a flat, mono-colored rectangle (essentially) should not be pushing my video card to the limit.

3d performance -- no complaints.

---

### Post by gaspard.leon on 2008-10-08
Summary:

Linux Xorg Video Cards/Drivers:

NVidia
Pros: Generally considered the best supported, good 3d performance, "easy" to install with most distros, sometimes has ok 2D performance... for some users, great Windows driver support, supports VSync so videos don't look rubbish, compiz generally works ok
Cons: Crappy 2D performance in a lot of cases, different 2D hardware in 8 series and above, not supported xrender extensions, proprietary driver, no open-sourcing plans, no support for "legacy" products once they reach a certain "age", various levels of suspend support.

ATI
Pros: Great xrender / 2d acceleration support in some drivers, multiple open-source drivers available, great 3d performance in some applications, at some times, when it works, recently open-sourced their specs, so it should get better...
Cons: Currently rubbish support for a lot of items, such as NO VSync support means videos look rubbish, a lot of 3D apps just crash out and don't work, can be hard to install or confusing, the open source teams are devided into 2, overall not considered to have that great Linux support, weird website for support using a enterprise-y knowledge base system, compiz generally doesn't work well if at all...

Intel
Pros: Great xrender / 2d acceleration when it works, often considered to have good driver design, open-source drivers, often working suspend/resume...
Cons: Often hard-to-install or doesn't work properly out of the box, not very good 3d performance, all are low-end integrated parts, compiz can work, but will usually be slow...

Does this sound accurate?

---

### Post by david_lynch on 2008-10-08
> **gaspard.leon said:**
> Summary:
Intel
Pros: Great xrender / 2d acceleration when it works, often considered to have good driver design, open-source drivers, often working suspend/resume...
Cons: Often hard-to-install or doesn't work properly out of the box, not very good 3d performance, all are low-end integrated parts, compiz can work, but will usually be slow...

Does this sound accurate?
The nvidia/ati descriptions sound accurate, but I would disagree with the intel description. There's nothing to "install" with the intel drivers, they are part of the kernel. They are there already, "out of the box". The intel video works well, supporting the compiz desktop eye candy and some games, but it lacks the raw horsepower needed for the newer, more demanding 3D FPS games.

---

### Post by albertz on 2008-10-10
That is a known problem in the driver. I read about this in relation to KDE4, because they figured out the same problem. They also have some solutions. Read about this here:
[http://techbase.kde.org/User:Lemma/KDE4-NVIDIA](http://techbase.kde.org/User:Lemma/KDE4-NVIDIA)

This is *not* a hardware problem and beside this performance problem in the driver, I would still say that the nVidia X11 driver is by far the best available driver out there (compared to ATI and Intel at least, don't know about more exotic hardware).

So, I would still give everybody the advise to bye a nVidia if somebody asks me for a good card for Linux. The 2D performance issue will probably be fixed soon.

---

### Post by Raffles10 on 2008-10-10
Funny, I guess I should be experiencing problems as I have an Nvidia Geforce 8600 GTS, but I'm not.

I never use compiz, it's been turned off since I installed Mint 3 months ago. I haven't seen any lagging or unresponsiveness. I've also tried Kubuntu kde 4 live cd and didn't experience any slowness etc.

This must be a more complex problem than simply saying "Do Not Buy Nvidia Cards For Linux!!!!" Some are having problems, some not, hardware & configuration must be an contributing element to the issues described here.

But simply saying "Do Not Buy Nvidia Cards For Linux!!!!" is an outrageously generalized statement.

---

### Post by fatality_uk on 2008-10-10
> **Raffles10 said:**
> But simply saying "Do Not Buy Nvidia Cards For Linux!!!!" is an outrageously generalized statement.

[SIZE="3"]**Of course it is**[/SIZE]. Just as "Linux is too hard for ordinary desktop users" and my personal favourite at the moment "The Credit Crunch is because people borrowed too much"

I have amazing performance from my GeForce 8800 GT, some awesome benchmark figures and 2d is blistering.

---

### Post by presence1960 on 2008-10-10
I have an EVGA GeForce 8600 GT and have had no problems with it. Used EnvyNG and voila! never had to tinker with it. I do not doubt there is some type of problem with some people's cards, but I would say the problem is just a symptom of whatever is the issue. Until it is factually determined what the problem is it is really not prudent to make generalizations about hardware, software or drivers. Just my 2 cents  :)

---

### Post by bigbrovar on 2008-10-11
i can confirm from experience that the Nvdia 8 series cards  do suck on Linux. yeah it works fine with 3D graphics but drags and lags when it comes with 2D. switching tabs on firefoxs,draging items on your desktops and draging a page across the screen are a pain compared with the snappy response you get when you use a lower card like intel. eventually gave out the computer and ordered a dell ubuntu with intel card . am not a gamer so i wont miss a thing.

---

### Post by techmarks on 2008-10-11
I think it is true in my experiences.

ATI are better all around cards for Linux.

They seem to just work.

With Nvidia you take more a chance of getting the unlucky troubles on some machine.

---

### Post by epidemiks on 2008-10-11
hmm.
i've got a pretty povo 6700GS and it works fine for me on a 2900x1050 dual setup with full compiz.

---

### Post by forrestcupp on 2008-10-11
Well, this debate has been going on for a long time, but my experience is the opposite of the OP.  

I have a geforce 8600GT and I love it.  I had a Radeon HD 2600 and it totally sucked for the desktop.  In Firefox, pulling the vertical scroll bar down lagged by probably almost half a second.  When I switched to a geforce 8600, my desktop was snappy.

---

### Post by Canis familiaris on 2008-10-11
I prefer ATI but then I only have ATI and it works almost perfect. (only few niggles with Compiz)

---

### Post by BLTicklemonster on 2008-10-11
I've used both ATI and NVIDIA cards on several different machines and find that NVIDIA cards blow ATI cards out of the water in Ubuntu in general and in 3d gaming. My laptop has ATI, and it drives me crazy. I wish I could drop an NVIDIA card in that thing and be done with it. Oh, anything from GeForce 5600 to 8500, and ATI 9200 among others I've tried and which all have ended up in a cardboard box in my utility room. I'd bury them in the back yard but I don't want the dogs to dig them up and have a neighbor accidentally find them and think they are usable video cards... lol.

---

### Post by KOld Iron on 2008-10-11
Thread Template:

Original Poster:
Option 1: I have this *hardware*, that really sucks on Linux. Don't buy it.
Option 2: I have this *hardware* and it is really lousy on Linux. Linux sucks, I am going back to Windows.

Multiple responses to OP (pages over pages):
- Never heard of that problem. Mine is working fine.
- Can't confirm, why don't you provide more info on your problem, so we can help you.

Occasionally:
- Yep, I have a similar problem.

I am not sure, how many threads we already had following this pattern. Have people not understood yet, that very often a specific problem they have is just that: A specific problem with their specific configuration and combination. It is of course okay, to post it and then maybe something can be done about it. If not, okay, not so good, but the experience should absolutely be shared here.

But, why on earth is it necessary in such cases to shout very unspecificially: Do not do this or do not do that. It is neither helpful nor even true in many cases. I mean, wouldn't it just be a lot better to say:
- I have this problem
- Can anybody confirm it?
- Is there a workaround or even a fix?
- If not, can we do something about (file a bug, ...)

Just my 2 cents.

---

### Post by bigbrovar on 2008-10-11
> But, why on earth is it necessary in such cases to shout very unspecificially: Do not do this or do not do that. It is neither helpful nor even true in many cases. I mean, wouldn't it just be a lot better to say:
- I have this problem
- Can anybody confirm it?
- Is there a workaround or even a fix?
- If not, can we do something about (file a bug, ...)

Just my 2 cents. 
works mostly when dealing with software especially .. with hardware its a different case and i think its important that people be warned before getting any hardware especially if that hardware has been known to have issues. True the Nvidia issue doesn't affect everyone.and so far only the **8 series cards** are affected but the problem does exist. its real . i experienced it and so have many other people. heck if 20 percent of 8 series card users experience the problem then its bad enough .. i got a laptop with Nvidia cards because i heard that it was the best for Linux. and when i starting experiencing performance issues i assumed it was gutsy till i read about the problem [http://www.google.com.ng/search?hl=en&client=firefox-a&rls=com.ubuntu:en-GB:unofficial&hs=0KM&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=Nvidia+8+series+cards+Linux+performance+issues&spell=1](http://www.google.com.ng/search?hl=en&client=firefox-a&rls=com.ubuntu:en-GB:unofficial&hs=0KM&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=Nvidia+8+series+cards+Linux+performance+issues&spell=1)

Now i know better than to go for a Nvidia 8 series card. but a friend got it recently and his system its working fine. i warned him about it but he still went ahead which proofs my point. its better to warn people about this problem so that should they decide to Buy Nvidia 8 Series cards they would do so knowing the risk involved

---

### Post by xeriouxi on 2008-10-11
Is this bad 2D performance what I'm seeing in Firefox? When I click and drag highlighted text or an image and then let it go, it stutters back to where it came from and looks awful.

---

### Post by forrestcupp on 2008-10-11
> **bigbrovar said:**
> 
Now i know better than to go for a Nvidia 8 series card. but a friend got it recently and his system its working fine. i warned him about it but he still went ahead which proofs my point. its better to warn people about this problem so that should they decide to Buy Nvidia 8 Series cards they would do so knowing the risk involved

But there are countless people, even in this thread, who don't have any trouble whatsoever using an nvidia 8 series card.  <snip>

---

### Post by Canis familiaris on 2008-10-11
> **forrestcupp said:**
> But there are countless people, even in this thread, who don't have any trouble whatsoever using an nvidia 8 series card.  My experience is that you're crazy if you buy anything *other* than nvidia for linux.

Not for long... ;). Rather not any more...

---

### Post by Twitch6000 on 2008-10-11
This is odd because my nvidia 8200 m card works just fine after enabling the restricted drivers <.<.

It sure as hell works better then my old intel 945gm card on my old laptop..

---

### Post by bigbrovar on 2008-10-11
> But there are countless people, even in this thread, who don't have any trouble whatsoever using an nvidia 8 series card. My experience is that you're crazy if you buy anything other than nvidia for linux.

what exactly is your point? .. and why do you have to call people crazy just because they dont agree or do what you perceive as the right thing for Linux. I don't deny that lots of people have no issues with the Nvidia 8 series cards. but that dont mean that the problem doesn't exist. there are countless of people u have problems with their 8 series Nvidia card. maybe they are a small 10% of  users but 10% is bad enough.. and the problem does exist. i experienced it first hand and the reason why i went for Intel in my new laptop order is because am now the wiser than to gamble my hard earned money on another Nvidia card when i would be sure what side of the percentage i would fall into.

---

### Post by Perfect Storm on 2008-10-11
> **forrestcupp said:**
> But there are countless people, even in this thread, who don't have any trouble whatsoever using an nvidia 8 series card.  <snip>

+1

I'm with a 8800GTX (PCI Express 16x) 768MB, it runs stuff smooth, 2D as 3D.

I wouldn't switch to ATI in the near future as I am a gamer on Ubuntu. Reading all the problems/issues/poor performance that ATI cards gives it's not an option (or Intel for that matter).

---

### Post by lyceum on 2008-10-11
I use NVIDIA on my laptop, I have 2 hard drives, one has Vista installed and the other is dual booted with Ubuntu 8.04 & Kubuntu 8.10 beta. Today, for the fist time my graphics card is acting buggy on Kubuntu 8.10, but it seems to work better on Ubuntu 8.04 (and Kubuntu 8.10 beta until this morning when I re-started after running the update manager) than on Vista. I think it must depend on the PC. I have been building Ubuntu PCs for 2 years now. I have used ATI or NVIDIA in all of them, with no issues. There may be a problem, but I do not think it is universal.

---

### Post by KOld Iron on 2008-10-12
> **bigbrovar said:**
> .. with hardware its a different case and i think its important that people be warned before getting any hardware especially if that hardware has been known to have issues. ...

You are absolutely right and I never argued that. On the contrary, that's what this forum is all about. To share your experience with other's so all can profit from it. All I wanted to point out, that it is not helpful to generalize from a single incident as is done so often.

I mean this thread just proves it. Some people have a problem with a specific hardware, so there is apparently some configuration that does not work well. So that's good to know. But at the same time many have no problem at all and it is just as important to know, which configuration DOES work.

But yelling in the title (with exclamation marks galore) "don't buy these cards" implies that NONE of these cards is working with Linux and that is simply wrong and definitely is not helping the cause of the OP either.

---

### Post by eragon100 on 2008-10-12
> **KOld Iron said:**
> You are absolutely right and I never argued that. On the contrary, that's what this forum is all about. To share your experience with other's so all can profit from it. All I wanted to point out, that it is not helpful to generalize from a single incident as is done so often.

I mean this thread just proves it. Some people have a problem with a specific hardware, so there is apparently some configuration that does not work well. So that's good to know. But at the same time many have no problem at all and it is just as important to know, which configuration DOES work.

But yelling in the title (with exclamation marks galore) "don't buy these cards" implies that NONE of these cards is working with Linux and that is simply wrong and definitely is not helping the cause of the OP either.

My 512 MB GeForce 8600 GT works great, 2d and 3d.

---

### Post by Torgas Prim on 2008-10-12
Hmmm, I have have an ATI HD2400 for sale if anyone wants it. :-\"
My nVidia GF5600 runs games, Linux, and Firefox3 better than any of my ATI cards I have had. And it is nVidia's worst card evar!

---

### Post by bigbrovar on 2008-10-12
> You are absolutely right and I never argued that. On the contrary, that's what this forum is all about. To share your experience with other's so all can profit from it. All I wanted to point out, that it is not helpful to generalize from a single incident as is done so often.

I mean this thread just proves it. Some people have a problem with a specific hardware, so there is apparently some configuration that does not work well. So that's good to know. But at the same time many have no problem at all and it is just as important to know, which configuration DOES work.

But yelling in the title (with exclamation marks galore) "don't buy these cards" implies that NONE of these cards is working with Linux and that is simply wrong and definitely is not helping the cause of the OP either.

very true i think we would be more constructive when dealing with such issues as this. Although sometimes its hard especially when the company wont even admit the problem. and when its been on for quite a while now. but like you said going about it in a constructive manner wont hurt anyone.

---

### Post by forrestcupp on 2008-10-12
> **bigbrovar said:**
> what exactly is your point? .. and why do you have to call people crazy just because they dont agree or do what you perceive as the right thing for Linux. I don't deny that lots of people have no issues with the Nvidia 8 series cards. but that dont mean that the problem doesn't exist. there are countless of people u have problems with their 8 series Nvidia card. maybe they are a small 10% of  users but 10% is bad enough.. and the problem does exist. i experienced it first hand and the reason why i went for Intel in my new laptop order is because am now the wiser than to gamble my hard earned money on another Nvidia card when i would be sure what side of the percentage i would fall into.

I apologize.  That wasn't really what I meant for my point to be.  My original wording was more harsh than intended.

I know that the Intel GMA's are great for open source drivers.  I just wish they would come out with something that could compete in the 3D realm.

I'm also happy for anyone who is satisfied with ATI stuff.  Radeons kick hiney in Windows, and I applaud their advancements in Linux drivers.  Hopefully, they will fix their X/glx issues soon so that we can run opengl stuff while Compiz is running without the "flickering" phenomenon.  After that, it won't even be an issue for me anymore.

It's just been my personal experience, having used both nvidia and ATI, that nvidia has worked much, much better for *me* in Linux.  I also personally like nvidia because they have a long history of being good to the Linux community.  I know that there are people that have had trouble with them. But in my mind, if it works flawlessly for some, there have to be fixable reasons for the problems other people have.

I apologize for my overly harsh wording, and am more than happy to have those words snipped.

---

### Post by BlueSkyNIS on 2008-10-13
I can see many answers regarding compiz. Compiz works great on Nv hardware, there is no question about it, but 2D performance is the issue here. The OP, as explained later, was referring to very bad performance of Nvidia chips in 2D mode with restricted drivers installed. Someone posted later in the thread that 8x00 series got the biggest performance hit and pointed to the Nv forum regarding the issue.

So can I propose test method in order to end this silly discussion of work/not work for me?

**How to reproduce this issue?** 
*Step 1*: First to turn of Compiz: go to System -> Preference -> Appearance, then go to Visual Effects tab and choose option "None", click Close. 
*Step 2*: Now open Mozilla Firefox and maximize it. Open a Nautilus window, like Places -> Home. It will open in front of Mozilla windows, ensure it is not maximized so you can see Mozilla window in the background. 
*Step 3*: Move Nautilus window left and right in front of Mozilla and you should see old traces of window while dragging. 

This lagging effect is clearly visible only in inside of Mozilla Firefox window and outside of the window there is no any lagging. 

Please have a look at [this clip]("http://www.youtube.com/watch?v=OHUslzXTzDQ") so you can see what I am talking about. Post your opinion/results.

---

### Post by presence1960 on 2008-10-13
> **BlueSkyNIS said:**
> I can see many answers regarding compiz. Compiz works great on Nv hardware, there is no question about it, but 2D performance is the issue here. The OP, as explained later, was referring to very bad performance of Nvidia chips in 2D mode with restricted drivers installed. Someone posted later in the thread that 8x00 series got the biggest performance hit and pointed to the Nv forum regarding the issue.

So can I propose test method in order to end this silly discussion of work/not work for me?

**How to reproduce this issue?** 
*Step 1*: First to turn of Compiz: go to System -> Preference -> Appearance, then go to Visual Effects tab and choose option "None", click Close. 
*Step 2*: Now open Mozilla Firefox and maximize it. Open a Nautilus window, like Places -> Home. It will open in front of Mozilla windows, ensure it is not maximized so you can see Mozilla window in the background. 
*Step 3*: Move Nautilus window left and right in front of Mozilla and you should see old traces of window while dragging. 

This lagging effect is clearly visible only in inside of Mozilla Firefox window and outside of the window there is no any lagging. 

Please have a look at [this clip]("http://www.youtube.com/watch?v=OHUslzXTzDQ") so you can see what I am talking about. Post your opinion/results.
I did exactly as you said and have no lag. Obviously there is a problem even though small because some people have it. But to make the statement that "don't buy Nvidia" is counterproductive. I guess there has to be a common thread among those who have the problem with Nvidia.

---

### Post by FuturePilot on 2008-10-13
> **BlueSkyNIS said:**
> I can see many answers regarding compiz. Compiz works great on Nv hardware, there is no question about it, but 2D performance is the issue here. The OP, as explained later, was referring to very bad performance of Nvidia chips in 2D mode with restricted drivers installed. Someone posted later in the thread that 8x00 series got the biggest performance hit and pointed to the Nv forum regarding the issue.

So can I propose test method in order to end this silly discussion of work/not work for me?

**How to reproduce this issue?** 
*Step 1*: First to turn of Compiz: go to System -> Preference -> Appearance, then go to Visual Effects tab and choose option "None", click Close. 
*Step 2*: Now open Mozilla Firefox and maximize it. Open a Nautilus window, like Places -> Home. It will open in front of Mozilla windows, ensure it is not maximized so you can see Mozilla window in the background. 
*Step 3*: Move Nautilus window left and right in front of Mozilla and you should see old traces of window while dragging. 

This lagging effect is clearly visible only in inside of Mozilla Firefox window and outside of the window there is no any lagging. 

Please have a look at [this clip]("http://www.youtube.com/watch?v=OHUslzXTzDQ") so you can see what I am talking about. Post your opinion/results.

What's the problem? This is basically normal for no compositing. Guess what, this happens in Windows too. Interestingly enough it seems to be worse when you do it over a Firefox window, which basically confirms my point that I may have made earlier in this thread that it's something quirky with the way Firefox/XUL works. Try it over a different application that is **not** Firefox/XUL.

---

### Post by GrantsV on 2008-11-02
I have tested a batch of brand new PC's with onboard NVidia NForce chipset and integrated video.  Performance is flawless.  The NVidia problem appears to be present in just a few card models of the particular range highlighted in the opening post here.  According to the forums at NVNEW's, work is being done to fix this problem but nothing has been achieved just yet.

So my title "Dont by NVidia" may have been premature for the most part and not applicable to new cards and chipsets - but I do resent spending over £100 just over one year ago for a card exhibiting the worst performance imaginable due to a NVidia Linux driver issues.

All the best,
GrantsV

---

### Post by emshains on 2008-11-03
Maybe you have compiz enabled ? 

And, heck, why should I want a video card that supports only 2D, while the only fully functional 3D video card vendor on linux is nVidia?

---

### Post by derekr44 on 2008-11-03
EVGA 7600GT here on Arch.  Everything runs wonderfully for me.

/shrug

---

### Post by eenofonn on 2008-11-03
got an EVGA 7800 GT and it works fine with my setup... 2d 3d everything works fine.... and windows who uses that anymore ;)

---

### Post by CJ Master on 2008-11-03
Hey, my friend has a Nvidea card, any work-arounds for it?

---

### Post by Vadi on 2008-11-03
Interesting argument there.

Unfortunately I don't care of my 2d FPS is 500 or 200. What matters is the 3d FPS :)

---

### Post by Newuser1111 on 2008-11-03
It also happens in Vista. But it's still mostly only visible with FireFox.

I don't remember it happening in Ubuntu but that could have been because I always had Compiz on.

---

### Post by Frak on 2008-11-03
Nvidia GeForce 5600 FX Quadro in my Mac Pro runs Compiz just fine.

---

### Post by Vitamin-Carrot on 2008-11-03
Nvidia 8800GTX and i have no issues

---

### Post by kk0sse54 on 2008-11-03
I prefer Nvidia especially in the realm of drivers for *BSD

---

### Post by SqdnGuns on 2008-11-26
> **GrantsV said:**
> I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.


I say B0LL0CKS..................

---

### Post by Yownanymous on 2008-11-26
NVidia plainly sucks. It doesn't work with many things tbh.

---

### Post by 73ckn797 on 2008-11-26
7900GS running great in Ubuntu and using 177 driver

---

### Post by Polygon on 2008-11-26
i have a 9800gtx and it works perfectly. 2d acceleration is fine

---

### Post by Luke has no name on 2008-11-26
I agree with the OP. I notice that I have better scrolling and window movement speed in Compiz than I do with 2D rendering, using the 8800M GTS.

I think I'll leave Compiz on after discovering this... I just have to turn it off every time I play Nexuiz.

---

### Post by PhoenixMaster00 on 2008-11-26
> **GrantsV said:**
> I have been knocking Ubuntu and big distro's for extremely slow screen response and lag compared to windows.  I know many, many people on forums are thinking the same thing - Linux has bad response compared to Win.

Then I bought a new laptop with Intel video, and despite being half the spec of my main Linux workstation PC, the laptops Gnome session runs as fast as Windows.  Then I purchased another PC with Ati video card, and that too was as fast as Windows e.g. instant response from moving windows and scrolling Nautilus/Browsers etc.  Only the first PC, with NVidia video card, has terrible response (although the infamous Placement=2 line gets me a touch closer to the speed I'd expect).

Then I stumbled upon the Nvnews forums and learnt that my 8600GT video card is effectively a three legged horse in Linux due some mysterious problem with the drivers/x-rendering.  ***Anything beyond 6 series Nvidia cards have worse Linux 2d performance than the cheapest Intel/ATI card.  Even top of the range 8800GT etc...***

I just kitted out a new business with 8 new machines and made sure none of the machines have NVidia video technology.

I am posting this message on Ubuntu forums to warn others.  NVidia absolutely must get this sorted but from what I can gather havent even made an official comment to acknowledge the problem.

See NVIDIA FORUMS AT:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

I have no involvement with Ati, Intel or Nvidia beyond wasting £100 buying a 8600GT recently believing it would be the best choice for Linux.

huh thats odd because i have an old computer running a nvidia fx5500 (about 4/5 years old now!) that can run Compiz and 3d fine? plus its backed up by 1 gb ram thats 4 years old and a 2.53 ghz intel celeron proccessor thats 6/7 years old so its not as if it even has decent backup... its running Intrepid Ibex btw

---

### Post by Luke has no name on 2008-11-26
> **PhoenixMaster00 said:**
> huh thats odd because i have an old computer running a nvidia fx5500 (about 4/5 years old now!) that can run Compiz and 3d fine? plus its backed up by 1 gb ram thats 4 years old and a 2.53 ghz intel celeron proccessor thats 6/7 years old so its not as if it even has decent backup... its running Intrepid Ibex btw

Compiz is 3D. He's saying it runs 2D poorly.

---

### Post by PhoenixMaster00 on 2008-11-26
> **Luke has no name said:**
> Compiz is 3D. He's saying it runs 2D poorly.

sorry i meant Compiz and 2d (when Compiz isnt on)

---

### Post by dariusdwtt on 2008-11-30
8600gt - no problems here...

---

### Post by piousp on 2008-12-09
GTX260 here. Runs perfectly

---

### Post by MikeTheC on 2008-12-09
@O.P.:

Don't know what you're talking about. On my PC I've used both the on-board nForce 6100 with 128MB of shared system RAM, and now a XFX 9600GSO with 768MB of RAM, and I've never had any 2D performance issues on either.

The only issue I had with the 6100 is that running Compiz while trying to play video, but I wasn't upset because I knew what it was that I had bought.

Be careful in posting threads with such flame-bait titles in the future, and instead consider taking a more questioning, "Is my experience typical?"-type approach to titling as well as writing the post.

---

### Post by Delever on 2008-12-09
Had ubuntu on

GeForce MX 440
GeForce 9600 GT

It's not open source, but I can't complain, it runs well. So...

---

### Post by Therion on 2008-12-09
My nVidia 8800GTS has run everything I've thrown at it, under both Gutsy and Hardy, like the proverbial greased pig.

I hear the latest drivers (well, from the Intrepid repo anyway) seriously ratchet up the performance as well.  I'll be trying that later this week.

Ahhh.... Here's the thread I was thinking of:  [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180)

---

### Post by Insane_Homer on 2008-12-09
> **Therion said:**
> My nVidia 8800GTS has run everything I've thrown at it, under both Gutsy and Hardy, like the proverbial greased pig.

I hear the latest drivers (well, from the Intrepid repo anyway) seriously ratchet up the performance as well.  I'll be trying that later this week.

Ahhh.... Here's the thread I was thinking of:  [http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+driver+180)

Exactly what I was going to say.

I have an 8600GT and never really had any problems, I've just installed the 180.06 Beta drivers (Instructions [here]("http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+180.06+beta&page=4"))

and there certainly seems to be a performance improvement to go with them.

Having been both an NVidia and ATI user over the years, I can categorically say that NVidia have by far been the better cards and had the better drivers/support.

---

### Post by racoq on 2008-12-09
The name of this thread is stupid, and all the discussion is pointless. Configured the right way a nvidia graphics card can be as fast as an ATI equivalent.

---

### Post by mips on 2008-12-10
Wonders why this thread is still even open...:confused:

---

### Post by WaeV on 2008-12-10
I actually had a lot more trouble with ATI than my new nVidia card.  In fact, that was why I switched over.

Of course, I had all this trouble back when everyone was still using Beryl. :razz:

---

### Post by Perfect Storm on 2008-12-10
Thread closed. If anyone need to say something that havn't been said and want to say it PM a mod to request for opening the thread again.


Note that the problems regarding 2D with some Nvidia cards have been solved with the latest version 180.xx driver.
You can find more about it in [nVidia 180.06 Rocks!](http://ubuntuforums.org/showthread.php?t=990978) thread.


regards
A.I. Dude
Ubuntu Forum Staff

---

