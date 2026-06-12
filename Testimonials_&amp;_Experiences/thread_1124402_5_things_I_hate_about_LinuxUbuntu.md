---
title: "5 things I hate about Linux/Ubuntu"
date: 2009-04-13
forum: Testimonials &amp; Experiences
---

### Post by memories on 2009-04-13
These are in descending order (1st is most annoying)

1) Firefox is slow on Linux. Optimized build, optimized settings, out of the box, etc.. all twice as slow as Windows or OS X (on the same specs)

Speaking of Firefox. It crashes often. It just closes without any notice or warning, and I lose what I was working on. this has been happening more often lately. The only change I recently made was to significantly increase memory usage in Firefox to help increase speed (and I turned off swap). 


2) Sound quality is inferior compared to Windows. I have not been able to get sound on Linux to be superior to the default Windows settings with official drivers and foobar2000 (player). This is probably fixable with some hacks though. 


3) Flash doesn't work. It really has never worked 100% in Linux. Sometimes the flash window will turn gray or disappear, which means npviewer or something crashed. The new npviewer restarts itself if you re-open the window. This is great because I no longer have to restart Firefox (which I cannot do). But is it really a fix? 

Sound goes out of sync sometimes. I'm not talking slightly, but the video will play fine with no sound, and then 30 seconds into it you'll begin hearing the first 1 second of audio keep repeating like a broken record. This only began in Ibex w/ flash 10.x - The only fix is to re-open the flash site (works sometimes) or to restart FF


4) GUI response is slow compared to Windows. The OS itself is quite fast, but in terms of GUI response, at least in Gnome and KDE, it feels sluggish. It's not "snappy." this is probably fixed with hacks. Maybe optimizing the kernel for the desktop and desktop apps instead of server and BG apps? 


5) There are small quirks. This is more related to certain apps, distros, window managers and a combination of these, but for example.. right now, I'm listening to music using "Listen." If I hold my mouse button on the desktop and select all my desktop icons, the music skips/pauses for a split second. It also skips or pauses if I quickly change from desktop to desktop - as if it's so CPU intensive that the OS must halt everything else. 

I'm not picky about this. It never really happens often, but Linux does have these tiny trivial quirks that cause a nuisance. Not that other OSes don't have them. Windows has countless ones, and so does OS X. Linux has the last in my experience, but they exist. 


I'm sure there are fixes or workarounds for 99% of my problems on Linux but there are some problems that I would have a hard time putting into words and searching for. Some other problems I just have not had any success fixing. The speed/memory leak issues in Firefox have persisted since the first Firefox build years ago. I don't blame Linux for this of course, but a memory leak being a "feature" is unacceptable. Just sayin' 

I love Linux. The only reason I'd use Windows right now is because there's no way to get Google Adwords Editor to work on Linux without using VirtualBox, and for some games I wanna play like .. once a month. As for OS X, it's really good but there are small things I hate. Like not being able to resize a window from any edge of the screen. You need to use the bottom right corner (... ?) though I would love to run OS X as my production box if I could afford a decent mac. 

Being that browsing the web and using web apps is 90% of what I do on the PC, the fact that Firefox/Flash are broken is a major blow to my productivity. I have a shortcut set for killing windows (xkill) which I need to use on Firefox numerous times a day to keep it usable. (I don't shutdown/restart and I always have a lot of tabs open)

My specs aren't that great but my comparisons are relative to Windows/OS X running on the same hardware so it doesn't matter. 

Intel Q6600 quad-core, 8 GB of RAM, GeForce 8600 PCI-E, Gigabyte EP-45 mobo

---

### Post by anjilslaire on 2009-04-13
> **memories said:**
> 
My specs aren't that great but my comparisons are relative to Windows/OS X running on the same hardware so it doesn't matter. 

Intel Q6600 quad-core, 8 GB of RAM, GeForce 8600 PCI-E, Gigabyte EP-45 mobo

I think your perspective may be a bit skewed. 
Are you running x64 or x86 Ubuntu, by the way?

---

### Post by Slim Odds on 2009-04-13
There must be something specific wrong with your machine.

I'm running Intrepid Ibex 64 bit and I don't have any of those problems. Sound is flawless, no tweaking involved. Pulseaudio shares the soundcard with everything (including programs running with WINE and VirtualBox). Flash works fine (64 bit alpha from Adobe). GUI is quite responsive.

What install are you actually using?

---

### Post by sdennie on 2009-04-13
Moved to Testimonials and Experiences as no specific questions were asked.

---

### Post by Topsiho on 2009-04-13
I can not say much to this, but why did you turn off swap?
Further down you write that you always have a lot of tabs open in FF, and that after turning off the swap FF crashes quite often.

one plus one equals two, I guess :)

I am not telling you that my FF never quits, it does (and so is my weakest app on board), but this happens not really quite often.

One quirk removed :)

Topsiho

---

### Post by memories on 2009-04-13
running x64. I think a lot of the problems and quirks are due to Compiz. 

I turned off swap because I never exceed 8 gigs of RAM. I feel that having the hard disk work too much will kill its life span. Also, firefox really sped up after I increased memory and turned off swap. 

I used to fix some memory problems by doing "swapoff -a" and then "swapon -a" to clear the swap.

I'm using ALSA (had problems with pulse and skype). It might be my machine, but I've googled these problems and they seem common. I'm thinking about just doing a full re-install of 9.x when it's out. ext4 is tempting (running ext3, some partitions are reiser).

---

### Post by wolfen69 on 2009-04-13
i am also running 64bit and experience none of the issues you do. flash, firefox, sound and everything else runs perfect.
> **memories said:**
> It might be my machine, but I've googled these problems and they seem common.
even if you found  a thousand other people with problems similar to yours, it's still a drop in the bucket compared to the millions of people that use it without issue. i agree that your hardware is probably the culprit.
i have done over 40 installs of ubuntu on various hardware without issue.

have you done a memtest or other hardware diagnostics?

---

### Post by davec64 on 2009-04-13
With Firefox, you have disabled IPV6 have you?

Type:
```
about:config
```

in the address bar and search for:

> network.dns.disableIPv6

Ensure it's value is set to "false"

---

### Post by memories on 2009-04-13
Yes, ipv6 is disabled. Firefox downloads webpages fast, but it's slow at rendering pages, JS etc. There's a pause between switching tabs. 

I did run memtest and so on. I doubt it's the hardware because every other OS runs fine. But I did NOT format when I updated my motherboard, so that might be the problem (but why would it be?). My installation of Ubuntu is bloated.. its been years since I formatted. But I don't think it was any faster when I first installed it, compared to osx/windows I mean. 

A few of the problems are likely to be fixed when I do a re-installation, but Firefox has been slow on Linux forever. On all my hardware, and all my distros. Mozilla itself was slow but I figured it was just bloated (it was). 

By "slow" I don't mean slow for regular use. I just mean slow-er than it is on Windows or os x. It might just be that Windows' GUI is snappier than Gnome and apps "appear" faster. Regardless, if I use Windows for 30 mins and go back to Linux, I notice major sluggishness.

edit: windows is 32bit

---

### Post by Maheriano on 2009-04-13
I've got:
- 32 bit 8.1 on an old Dell D600 laptop
- 64 bit 8.1 on my semi-recent single core but pretty fast desktop
- 64 bit 9.04 on my 2 day old Dell Studio 15 warrior of a laptop

All with zero of the problems you've specified. I even have my desktop set up as my media machine with 5.1 Dolby Digital and DTS via fiber optical SPDIF out. The sound is incredible.

---

### Post by roshanjose on 2009-04-13
i agree to the points mentioned...but then i dont hate Linux looking at the positive issues like security

my drivers are not found for my monitor..so improper screen resolution...

---

### Post by wolfen69 on 2009-04-13
if linux does not run well on your machine, then it *is* your hardware. i don't mean as in broken, but as in ultra proprietary. i just built 2 new machines and have had the best OS experience ever. faster than anything i've ever used.

if you are not willing to get a new pc or hardware, then you will not have a good experience. it's that simple.

---

### Post by stchman on 2009-04-13
1.  I find Firefox to be faster on Ubuntu than it is on Vista.  I run Ubuntu on 5 different machines and Firefox so rarely crashes it is hard to remember.  Firefox is snappier on XP a tad IMO.

2.  I cannot tell the difference in SQ from XP, Vista, Ubuntu on my SB cards.

3.  Since Flash 10 is out it works very well even in 64 bit.  Flash 9 was a touch buggy  but those days are over.

4.  Gnome runs fine to me.

5.  Every OS has it's quirks.

---

### Post by hufferd on 2009-04-13
> 1) Firefox is slow on Linux. Optimized build, optimized settings, out of the box, etc.. all twice as slow as Windows or OS X (on the same specs)

Speaking of Firefox. It crashes often. It just closes without any notice or warning, and I lose what I was working on. this has been happening more often lately. The only change I recently made was to significantly increase memory usage in Firefox to help increase speed (and I turned off swap).

Not an issue at all for me... Have not noticed firefox crashing or running slow..  So maybe its your setup?? I don't know

> 2) Sound quality is inferior compared to Windows. I have not been able to get sound on Linux to be superior to the default Windows settings with official drivers and foobar2000 (player). This is probably fixable with some hacks though.

I will admit sound is a bit touchy sometimes 

> 3) Flash doesn't work. It really has never worked 100% in Linux. Sometimes the flash window will turn gray or disappear, which means npviewer or something crashed. The new npviewer restarts itself if you re-open the window. This is great because I no longer have to restart Firefox (which I cannot do). But is it really a fix?


Have not had any issues with flash 

> 4) GUI response is slow compared to Windows. The OS itself is quite fast, but in terms of GUI response, at least in Gnome and KDE, it feels sluggish. It's not "snappy." this is probably fixed with hacks. Maybe optimizing the kernel for the desktop and desktop apps instead of server and BG apps?



Again not an issue on my machine.. 

> 5) There are small quirks. This is more related to certain apps, distros, window managers and a combination of these, but for example.. right now, I'm listening to music using "Listen." If I hold my mouse button on the desktop and select all my desktop icons, the music skips/pauses for a split second. It also skips or pauses if I quickly change from desktop to desktop - as if it's so CPU intensive that the OS must halt everything else.

You are right other os's have quirks as well. 

You compare linux to windows allot - you are forgetting two very important things. 1. Linux / ubuntu **IS NOT WINDOWS** & the one I like is (as far as I am concerned) 2. You get what you pay for did you pay anything for linux? I think its a damn good OS for being free to use.

---

### Post by hufferd on 2009-04-13
> **wolfen69 said:**
> if linux does not run well on your machine, then it *is* your hardware. i don't mean as in broken, but as in ultra proprietary. i just built 2 new machines and have had the best OS experience ever. faster than anything i've ever used.

if you are not willing to get a new pc or hardware, then you will not have a good experience. it's that simple.

Would agree with this - I built a new machine a year ago - when I first switched to ubuntu / linux....... But before I built my machine I knew that I was going to use ubuntu. So I did lots of reading and knew what hardware to buy with no issues.  If you are trying to use hardware that is known not to play nice with ubuntu then you are out of luck. IMO

---

### Post by Methuselah on 2009-04-13
If you're running 64 bit download the flash 10 beta for 64 bit linux. I've been using it and it works fine.
The behavior of the 32 bit version with the pluginwrapper can be hokey.

---

### Post by Slim Odds on 2009-04-13
> **Methuselah said:**
> If you're running 64 bit download the flash 10 beta for 64 bit linux. I've been using it and it works fine.

Well... it's actually an alpha. But it does work fine.

---

### Post by cariboo on 2009-04-13
I think the op should wait until next week when Jaunty is released, I think he'll be pleasantly surprised. The one thing that really sticks out for me, aside from the speed, is the sound. There has been a vast improvement in sound quality.

Jim

---

### Post by Chemical Imbalance on 2009-04-13
> **cariboo907 said:**
> I think the op should wait until next week when Jaunty is released, I think he'll be pleasantly surprised. The one thing that really sticks out for me, aside from the speed, is the sound. There has been a vast improvement in sound quality.

Jim

I concur with this, sound is crystal-clear now with the improved Pulseaudio in Jaunty.  Works beautifully, including multiple applications open with sound.

---

### Post by linux5uper on 2009-04-13
> **Chemical Imbalance said:**
> I concur with this, sound is crystal-clear now with the improved Pulseaudio in Jaunty.  Works beautifully, including multiple applications open with sound.

Yay for MULTIPLE applications open with sound ;)

---

### Post by Slim Odds on 2009-04-13
> **Chemical Imbalance said:**
> I concur with this, sound is crystal-clear now with the improved Pulseaudio in Jaunty.  Works beautifully, including multiple applications open with sound.

Glad to hear that, but as I mentioned, it works fine for me in 8.10.

PulseAudio shares the sound card (actually the audio controller on the motherboard) between everything. No tweaks, just works.

---

### Post by hockeyhead019 on 2009-04-13
never experienced any of these problems personally but i'm sure your a much heavier user than i am haha or at least that's what it sounds like so i mean my machine is a piece and i don't use the system like it sounds as you do so i guess i'm not much help haha :D

but in contrast with those 5 negatives think of the positives which the OS brings you as well

---

### Post by caravel on 2009-04-14
> **memories said:**
> But I did NOT format when I updated my motherboard, so that might be the problem (but why would it be?). My installation of Ubuntu is bloated.. its been years since I formatted. But I don't think it was any faster when I first installed it, compared to osx/windows I mean.

That might be the issue.  I did something similar last year and I'm sure that the OS was still loading the kernel modules for a lot of hardware that was no longer in use.  It was quite sluggish until I formatted and reinstalled.

---

### Post by Sprut1 on 2009-04-14
Your specs are a hundred times better than mine and still everything works fine and nothing seems "sluggish".

---

### Post by Saint Angeles on 2009-04-14
i have found that EVRYTHING works all the time using Jaunty. There is nothing this OS can't do and everybody should just use it.

HOLY CRAP... i can't even begin to describe how fast it is. everything worked immediatly after installing it (which only took about 30 minutes). my madwifi wireless driver and FGLRX ATI drivers (both of which are proprietary) worked perfectly with zero configuration needed. it was a lot easier than any windows install i've ever done... any OS install i've ever done.

i don't know how they did it, but if you do a clean install of jaunty, i bet all your problems will be over forever.

---

### Post by Methuselah on 2009-04-14
> **Gambitt said:**
> I can see that my CPU usage gets abnormally high whenever i usa a GUI component in Ubuntu as compared to Windows. for example during playing a movie the CPU usage touches 100% at full screen (1440x900) and around 40-50% at a small window.

It's possible that there's no hardware (ie video card) acceleration of video playback in Ubuntu, at least with your setup.
Honestly, the linux video card landscape is better than it was but still not perfect.
The manufacturer provided binary drivers for the 'big two' are often unstable and while the open source drivers generally won't crash your computer, they might not support all your card's features.
I have personally declared a moratorium on further video card purchases until I can choose stability *and* functionality.

---

### Post by longtom on 2009-04-15
> **memories said:**
> 

1) Firefox is slow on Linux. Optimized build, optimized settings, out of the box, etc.. all twice as slow as Windows or OS X (on the same specs)

Speaking of Firefox. It crashes often. It just closes without any notice or warning, and I lose what I was working on. this has been happening more often lately. The only change I recently made was to significantly increase memory usage in Firefox to help increase speed (and I turned off swap). 


2) Sound quality is inferior compared to Windows. I have not been able to get sound on Linux to be superior to the default Windows settings with official drivers and foobar2000 (player). This is probably fixable with some hacks though. 


3) Flash doesn't work. It really has never worked 100% in Linux. Sometimes the flash window will turn gray or disappear, which means npviewer or something crashed. The new npviewer restarts itself if you re-open the window. This is great because I no longer have to restart Firefox (which I cannot do). But is it really a fix? 

Sound goes out of sync sometimes. I'm not talking slightly, but the video will play fine with no sound, and then 30 seconds into it you'll begin hearing the first 1 second of audio keep repeating like a broken record. This only began in Ibex w/ flash 10.x - The only fix is to re-open the flash site (works sometimes) or to restart FF


4) GUI response is slow compared to Windows. The OS itself is quite fast, but in terms of GUI response, at least in Gnome and KDE, it feels sluggish. It's not "snappy." this is probably fixed with hacks. Maybe optimizing the kernel for the desktop and desktop apps instead of server and BG apps? 




I have similar problems and hope for the new release.  Don't be discouraged by answers like "just buy new hardware" (some of us don't have moneytrees...) or "I never had a problem."

Some of us, and maybe more, than anticipated, have similar problems.  Since such people get brushed of easily as if it is all your fault.  It isn't, I, for once, can relate.  

But I try to get along on my own as much as I can.  If people can't help you because you can't afford new hardware, well, than that's just it, I guess.

Having said that, with specific questions I do get loads of friendly help in the beginners section in most cases.  Thank you to all for that!

---

### Post by digitalmonk on 2009-04-16
I too use the 64 bit version, i donot experience these issues. contrary my of working on ubuntu is better than that of working on windows xp.

---

### Post by rmayer32 on 2009-04-16
I would do a fresh install once 9.04 is released. That is bound to at least improve some if not all of those issues.

---

### Post by Arup on 2009-04-16
Really surprising, everyone who has tested Ubuntu against their existing Vista or XP installations have had exactly the opposite of what you have written here. Ubuntu is far faster in general terms, my perspective is with x64, from encoding, decoding, compiling, watching movies all are far quicker in Ubuntu. Also net is way faster for the same connection in Ubuntu over any Windows distro, pages open faster and downloads are quicker. You mentioned sound, Foobar with the ks plugin gives you low latency direct sound output, something ALSA and now PULSE already implements in Linux. Sound in Ubuntu is way deeper and superior to Windows even though my sound card drivers are always updated to latest. Whats interesting to see here is that my two Yamaha sound cards, one the high end DSXG-1000 and the other, a XG Waveforce both work fantastic in Ubuntu with sound quality which blows away most sound cards in the market including those from M- Audio. In Windowsx64, these cards are no longer supported.

---

### Post by MartyBuntu on 2009-04-16
I can reboot Ubuntu 8.10 3 times and get to a usable desktop before I can do it once with XP on my wife's dual boot computer.

---

### Post by yaztromo on 2009-04-16
> **memories said:**
> 
By "slow" I don't mean slow for regular use. I just mean slow-er than it is on Windows or os x. It might just be that Windows' GUI is snappier than Gnome and apps "appear" faster. Regardless, if I use Windows for 30 mins and go back to Linux, I notice major sluggishness.

edit: windows is 32bit

This is down to a mixture of Xorg and GTK issues which make the GUI feel slower on Linux than on Windows. Your experience with clunky GUIness's is perfectly valid and true (have you tried Thunderbird in linux - its very slow), but you will not find much agreement on the ubuntuforums where you have such a biased and zealous userbase.

Anyway don't let X's clunkiness put you off, there are many other reasons to choose Linux over Windows :)

---

### Post by mdsmedia on 2009-04-17
> **yaztromo said:**
> This is down to a mixture of Xorg and GTK issues which make the GUI feel slower on Linux than on Windows. Your experience with clunky GUIness's is perfectly valid and true (have you tried Thunderbird in linux - its very slow), but you will not find much agreement on the ubuntuforums where you have such a biased and zealous userbase.

Anyway don't let X's clunkiness put you off, there are many other reasons to choose Linux over Windows :)
Considering the number of people who've agreed with the OP, I doubt you could call the forums, based on this thread, biased or zealous.

Some have provided valid possible reasons for the OPs problems. Someone called that "dismissing his problems" as hardware problems. 

Those reasons weren't from bias or zealotry. They were based on experience and cold hard logic.

Others have related their own experiences, with their own(and others') hardware. Some are in a similar boat, others have different (positive)experiences. 

Is it only biased and zealous if it doesn't agree with the one having problems, or is it biased and zealous when someone agrees with him?

---

### Post by wolfen69 on 2009-04-17
> **mdsmedia said:**
> Considering the number of people who've agreed with the OP, I doubt you could call the forums, based on this thread, biased or zealous.

Some have provided valid reasons for the OPs problems. Someone called that "dismissing his problems" as hardware problems. That's not from bias or zealotry. That's from experience and cold hard logic.

Others have related their own experiences, with their own(and others') hardware. Some are in a similar boat, others have different experiences. Is it only biased and zealous if it doesn't agree with the one having problems, or is it biased and zealous when someone agrees with him?

huh?

---

### Post by mdsmedia on 2009-04-17
> but you will not find much agreement on the ubuntuforums where you have such a biased and zealous userbase

I was responding to this.

How can anyone call these forums biased or zealous, based on this thread?

Others have related their experiences. Some have agreed with the OP, some have disagreed.

Those who have disagreed, including you, have disagreed based on their own experience or at least pointed them at possible reasons they are having problems.

Is that clearer, or do you still have problems with what I've said?

Edit: But I do see where I was unclear....I'll edit my previous post to make it clearer.

---

### Post by eye208 on 2009-04-17
> **linux5uper said:**
> Yay for MULTIPLE applications open with sound ;)
The fact that this is worth mentioning tells you a lot about the sorry state of Linux audio.

Soundcard sharing was introduced with ALSA many years ago. Now people are celebrating it as the latest innovation of PulseAudio. Better not tell a Windows or Mac user about it because it's too embarrassing.

About desktop snappiness: I recently switched to Debian 5.0, and it feels quite a bit faster than Ubuntu 8.04. It also starts up and shuts down faster. I don't know how it compares to 8.10 or 9.04 though.

---

### Post by yaztromo on 2009-04-17
> **mdsmedia said:**
> I was responding to this.

How can anyone call these forums biased or zealous, based on this thread?



But I wasn't basing it on solely this thread. None of my words should have given you that notion at all if you read them more carefully.

I see this type of thing happen all too often:

1. User posts thread critiscing Ubuntu, often with perfectly good reasons.
2. Majority of replies tell user it must be something wrong with him or his hardware, even when it obviously isn't.
3. OP goes away frustrated.

To draw an analogy, it's like posting a thread criticising fast cars on a sports car forum. Logic goes out the window and bias and zealotry come in.

Hope that has made my opinion a bit clearer.

---

### Post by ssdt on 2009-04-17
I hate when you can't use a lot of programs that you need. For example you can't make the TV sites up and they make the Wine harder. Some parts of Ubuntu should be much easier.

---

### Post by Slim Odds on 2009-04-17
> **ssdt said:**
> Some parts of Ubuntu should be much easier.

Feel free to fix it. And when you're done, make sure you give us the results.

---

