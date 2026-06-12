---
title: "Ubuntu boot time"
date: 2008-06-23
forum: The Cafe
---

### Post by Methuselah on 2008-06-23
On 1 GHz machine I had that dual booted with windows Xp, I noticed that ubuntu took slightly longer to boot than Xp.

However, there's more to it.
After logging in, my ubuntu desktop is fully ready to use in a matter of seconds. Usually, I had to wait another 1-2 minutes for my windows desktop to become usable after logging in. During this time if you try to launch any programs, the wait cursor comes up and nothing happens.

It seems to me that ubuntu initializes certain services at boot time that windows defers until you actually login. So while windows login prompt might come up faster, you still have a bit of a wait after logging in. 

Has anyone else that has had a dual setup noticed this?

---

### Post by edd07 on 2008-06-23
Yes, I too have noticed that. Personally, I like the Ubuntu approach better, because I find it very irritating to be able to see my desktop but not to use it. My XP installation is pretty recent (I endured Vista for a while), but after some time, I find the time you're waiting for stuff to load while the desktop is showing is virtually the same (or longer) that the boot process.

In Ubuntu, on the other hand, once the desktop is showing it's completely operational, and it doesn't seem to slow down after a long time since installation.

---

### Post by Mr. Picklesworth on 2008-06-23
It's my understanding that Windows is able to load way more than Ubuntu at boot time since the infrastructure is designed around a single desktop environment and UI toolkit. Vista, for example, can preload the desktop so that the start menu and desktop background is there as soon as you enter your password. However, the slowdown occurs thanks to horrible third party software in Windows, such as Apple's Quicktime updater, Adobe Updater, Adobe Reader Speedloader, and the various viruses and spyware. Those are often specific to a user account, so only happen upon logging in, and take forever.

In fairness, I suspect Ubuntu is technically a tad slower at starting up right now, but faster and more responsive most of the time since we don't have all that unregulated junk clogging up the works. That, and System -> Preferences -> Sessions is a really easy to follow dialog in contrast to msconfig.

---

### Post by AndyCee on 2008-06-23
Yeah, I've noticed the same thing.

I remember some time ago, I heard (so that's kind of the same as an official notice ;) )win2000 was accused of moving boot processes to after logon, giving the appearance of a faster startup.

Kind of not related, you can speed the Ubuntu boot time for future boots by adding "profile" to the end of the kernel line when grub boots up.

---

### Post by Methuselah on 2008-06-23
Edd07, I think I do prefer the ubuntu approach too.

Mr Picklesworth, you're probably right about all the third party software. But one can't help feeling that the OS should bring those up faster.

---

### Post by edd07 on 2008-06-23
> **Mr. Picklesworth said:**
> However, the slowdown occurs thanks to horrible third party software in Windows, such as Apple's Quicktime updater, Adobe Updater, Adobe Reader Speedloader, and the various viruses and spyware.
Not to mention the Anti-virus. If you've installed one of those monsters (my experience has been mostly with Norton) the start-up time starts getting ridiculous. It got me thinking, I'd rather have the virus...

---

### Post by SomeGuyDude on 2008-06-23
When I log in, Ubuntu sits at an orange screen for... somewhere around 20-30 seconds. It's quite aggravating.

---

### Post by gn2 on 2008-06-23
What I found when I dual-booted was that the more I used Ubuntu and the longer I went between booting Windows, the slower Windows became to load. 

It eventually got to a stage where Windows at boot would have to download and install huge anti-virus updates and Windows updates and might even need a re-boot to install them, taking anything up to ten minutes to get from power on to useable desktop.

Windows just had to go and I don't miss it at all.

---

### Post by Pasto on 2008-06-23
> **AndyCee said:**
> 
Kind of not related, you can speed the Ubuntu boot time for future boots by adding "profile" to the end of the kernel line when grub boots up.

Any idea where can I see more info about this?

---

### Post by FuturePilot on 2008-06-23
> **Pasto said:**
> Any idea where can I see more info about this?

This looks like it. :)
[http://ubuntuforums.org/showthread.php?t=254263]("http://ubuntuforums.org/showthread.php?t=254263")

---

### Post by ma_nkooo on 2008-06-23
For me it is faster than XP, don't know why!

---

### Post by Canis familiaris on 2008-06-23
I my PC Ubuntu boot is 1 min 20 sec. Windows boots in 55 sec to 1 min 5 sec. Yes Windows is faster in booting but this is a plain vanilla install of Windows which I use only for gaming. I'm sure bootup time for Windows will increase considerably if I install more apps.

---

### Post by K.Mandla on 2008-06-23
It might be important to make a distinction between desktops too. Gnome is hideously sluggish (unless you go way back to something like Debian Sarge), and other desktops will be faster. So a plain Ubuntu setup is terribly slow, while a sparser Ubuntu machine will be quite faster.

Different distros will definitely give different results though too. My 1Ghz machine boots to an Openbox setup in 14 seconds with Crux. Ubuntu is around 36-37 seconds to the same software. 

I have yet to see a Windows desktop, even a speed-tweaked one, that boots faster than a Linux machine that has been properly set up and arranged for performance.

---

### Post by sharkinfested on 2008-06-23
Just did a test run on each OS on my dual booted Acer laptop.
Ubuntu – 55 seconds
XP – 19 seconds. :o 
Have to say I’m really shocked.  I didn’t notice that XP was loading that fast – I wonder why…  Is it because I only have Photoshop loaded on that side?  Should the number of programs make a difference?  I wouldn’t think so.
Still, with both OSs loading in under a minute I have no complaints.

---

### Post by mips on 2008-06-23
> **Anurag_panda said:**
> Yes Windows is faster in booting but this is a plain vanilla install of Windows which I use only for gaming. I'm sure bootup time for Windows will increase considerably if I install more apps.

Have you ever used nLite? You should try it is you only use windows for gaming. I stripped about 340MB out of a XP install cd the other day and could probably take out more. What you are left with is just the basic os & minimal services running and none of the crap like ie, msn, briefcase, defrag etc, it is really lean.

---

### Post by andrewabc on 2008-06-23
> **sharkinfested said:**
> Just did a test run on each OS on my dual booted Acer laptop.
Ubuntu &#8211; 55 seconds
XP &#8211; 19 seconds. :o 
Have to say I&#8217;m really shocked.  I didn&#8217;t notice that XP was loading that fast &#8211; I wonder why&#8230;  Is it because I only have Photoshop loaded on that side?  Should the number of programs make a difference?  I wouldn&#8217;t think so.
Still, with both OSs loading in under a minute I have no complaints.

You can always speed ubuntu up.
I have a pentium 4 1.8 ghz 768 ram and have lots of stuff disabled on normal ubuntu install. It uses a lot less ram than my newer computer with default ubuntu installed.

Depending on what you need, go to
system->administration->services

I have disabled:
- bluetooth device management (I don´t have any bluetooth on either of my computers)
- braille display management (I don´t need braille)
- printer cupsys (disabled on old computer which has no printer hooked up)

system->preferences->session
- bluetooth disabled
- check for new hardware drivers disabled
- evolution disabled
- visual assistance disabled
- tracker disabled (for old computer which only firefox is used)

To get an accurate idea of how long it takes to boot into ubuntu, install bootchart.
Here is the bootchart thread: [Attach your boot-chart!](http://ubuntuforums.org/showthread.php?t=531453&highlight=bootchart)

If it is taking 55 seconds for ubuntu and 19 seconds for winxp then there is a chance that something in ubuntu is slowing down the startup time. Attaching bootchart would be helpful.

---

### Post by quanumphaze on 2008-06-23
A lot of Ubuntu's slow boot problems probably come from having to detect your hardware at start up or unnecessary start up processes or modules.

The advantage of this can be that it should survive being transplanted into a different computer with completely different hardware with, hopefully, no problems.

After GDM is up the majority if slowness is from Gnome and Compiz. Loading without Compiz is faster, though once loaded it's just as fast.

---

### Post by sharkinfested on 2008-06-23
> **andrewabc said:**
> You can always speed ubuntu up.
I have a pentium 4 1.8 ghz 768 ram and have lots of stuff disabled on normal ubuntu install. It uses a lot less ram than my newer computer with default ubuntu installed.

Depending on what you need, go to
system->administration->services

I have disabled:
- bluetooth device management (I don´t have any bluetooth on either of my computers)
- braille display management (I don´t need braille)
- printer cupsys (disabled on old computer which has no printer hooked up)

system->preferences->session
- bluetooth disabled
- check for new hardware drivers disabled
- evolution disabled
- visual assistance disabled
- tracker disabled (for old computer which only firefox is used)

To get an accurate idea of how long it takes to boot into ubuntu, install bootchart.
Here is the bootchart thread: [Attach your boot-chart!](http://ubuntuforums.org/showthread.php?t=531453&highlight=bootchart)

If it is taking 55 seconds for ubuntu and 19 seconds for winxp then there is a chance that something in ubuntu is slowing down the startup time. Attaching bootchart would be helpful.


Ha-ha – I really appreciate that you are trying to help me speed up my boot time but I think 55 seconds is a GREAT number!  Besides, I’m so new to Linux that I am scared to death (right now) to go changing things around – especially now that I’ve got everything working… er, almost everything (still no DVD playback).  The 19 second boot time with XP (just did it again –17 seconds!) anyway, it doesn’t matter either.  I only use Photoshop on that side anyway.
My “regular” laptop is a 17” Dell Vostro and it boots XP in about 45 seconds.  I think anything under a minute is pretty good.

---

### Post by fatality_uk on 2008-06-23
> **Methuselah said:**
> On 1 GHz machine I had that dual booted with windows Xp, I noticed that ubuntu took slightly longer to boot than Xp.

However, there's more to it.
After logging in, my ubuntu desktop is fully ready to use in a matter of seconds. Usually, I had to wait another 1-2 minutes for my windows desktop to become usable after logging in. During this time if you try to launch any programs, the wait cursor comes up and nothing happens.

It seems to me that ubuntu initializes certain services at boot time that windows defers until you actually login. So while windows login prompt might come up faster, you still have a bit of a wait after logging in. 

Has anyone else that has had a dual setup noticed this?

Define boot!!!

Haven't read the whole thread but I usually here this and ask for a direct comparison. My copy of Hardy boots on my HP 6910p very quickly and I can be working in my OS in under a minute.

There isn't a chance that XP or Vista could do that for me.

---

### Post by gn2 on 2008-06-23
> **sharkinfested said:**
> Just did a test run on each OS on my dual booted Acer laptop.
Ubuntu – 55 seconds
XP – 19 seconds. :o 
Have to say I’m really shocked.  I didn’t notice that XP was loading that fast – I wonder why…  Is it because I only have Photoshop loaded on that side?  Should the number of programs make a difference?  I wouldn’t think so.
Still, with both OSs loading in under a minute I have no complaints.

But is Xp booting to a usable desktop in that time?
Xp usually shows the desktop long before it has finished loading everything.
A better comparison of time is from pressing the power button to a Firefox home page.

---

### Post by Victormd on 2008-06-23
> Define boot!!!

Haven't read the whole thread but I usually here this and ask for a direct comparison. My copy of Hardy boots on my HP 6910p very quickly and I can be working in my OS in under a minute.

There isn't a chance that XP or Vista could do that for me.
I agree, I think it all depends on how you define your start and end boot times.

---

### Post by Canis familiaris on 2008-06-23
I define start and end points at power down to the point when entire desktop is loaded.

---

### Post by Victormd on 2008-06-23
In my case, timing from grub to time to open a FF window, and Hardy = 1'06" while Windows = 1'22"...

---

### Post by fatality_uk on 2008-06-23
> **Anurag_panda said:**
> I define start and end points at power down to the point when entire desktop is loaded.

Then id bet good money that Linux/Ubuntu would be a clear winner over XP each and every time. And I am not just talking about a dodgy two year old XP install with wonky drivers, I mean a clean XP install would, I suggest, be behind.

---

### Post by nick09 on 2008-06-23
The booting gets faster as the kernel updates so Ubuntu will load faster than windows.

---

### Post by Canis familiaris on 2008-06-23
> **fatality_uk said:**
> Then id bet good money that Linux/Ubuntu would be a clear winner over XP each and every time. And I am not just talking about a dodgy two year old XP install with wonky drivers, I mean a clean XP install would, I suggest, be behind.
Actually it is not. 
Ubuntu boots is 1 min 20 sec while Windows boots in 55sec to 1 min 5 sec(it varies in Windows). But I have to mention it a fresh Windows installation with no software except games. If I install Office and few other apps then Windows would be definitely slower. Even I do nothing, then after few months it will be slower and eventually CRASH.

---

### Post by sharkinfested on 2008-06-23
> **gn2 said:**
> But is Xp booting to a usable desktop in that time?
Xp usually shows the desktop long before it has finished loading everything.
A better comparison of time is from pressing the power button to a Firefox home page.

Yes, it is completely up and running in those 19 seconds.  I know it sounds crazy.
I am timing it from the page in which I choose which OS to run.  It takes ten seconds from when I hit the power button to get to that page, so from power button to up and running: 
XP &#8211; 29 seconds
Ubuntu &#8211; 1 minute, 5 seconds.
I have lots of those little games and inkspace loaded on the Ubuntu side and only Photoshop loaded on the XP side.  The laptop is an Acer 3003Lci, with a Mobile AMD Sempron processor 3000+ - edited to add that I have 2Gigs of ram too - if that matters.  
*Edited AGAIN to say I went a little dyslexic up there &#8211; I meant I have inkscape on the Ubuntu side

---

### Post by Mr. Picklesworth on 2008-06-23
We should incorporate Fedora's tiny X and have a little playable Pong game instead of the splash screen. Then nobody will have a problem with boot time again ;)

---

### Post by Frak on 2008-06-23
On a minimal Ubuntu installation, it boots in around 20 seconds on a 1.8Ghz machine.

Minimal Windows, around 22 seconds.

---

### Post by gn2 on 2008-06-23
> **sharkinfested said:**
> Yes, it {Xp} is completely up and running in those 19 seconds.  I know it sounds crazy.

Indeed it does sound crazy. 

In all the time I used Xp it never booted anywhere near that fast even on my E6300 Core 2 Duo desktop PC, which I reckon has significantly better performance than your Sempron laptop.

---

### Post by FuturePilot on 2008-06-23
> **sharkinfested said:**
> Yes, it is completely up and running in those 19 seconds.  I know it sounds crazy.
I am timing it from the page in which I choose which OS to run.  It takes ten seconds from when I hit the power button to get to that page, so from power button to up and running: 
XP – 29 seconds
Ubuntu – 1 minute, 5 seconds.
I have lots of those little games and inkspace loaded on the Ubuntu side and **only Photoshop loaded on the XP side.**  The laptop is an Acer 3003Lci, with a Mobile AMD Sempron processor 3000+ - edited to add that I have 2Gigs of ram too - if that matters.  
*Edited AGAIN to say I went a little dyslexic up there – I meant I have inkscape on the Ubuntu side

That's why. Try installing a bunch of stuff and watch how fast it slows down.

---

### Post by sharkinfested on 2008-06-23
> **FuturePilot said:**
> That's why. Try installing a bunch of stuff and watch how fast it slows down.

Oh wait – I just remembered something else too…
When I decided to dual boot a Linux OS I grabbed this Acer that no one in the family was using.  It only had a pitiful little 40GB hard drive so I bought a 160GB 7200 rpm model.
Oops – forgot about that, surly my fast boot times speak more about the speed of my hard drive than the OS.

---

### Post by mips on 2008-06-23
> **gn2 said:**
> Indeed it does sound crazy. 

In all the time I used Xp it never booted anywhere near that fast even on my E6300 Core 2 Duo desktop PC, which I reckon has significantly better performance than your Sempron laptop.

I installed XP Pro on my pc two days ago and I'm pretty sure it loads even faster than 19sec. I did cheat though as I stripped the entire install cd bare with nLite.

---

### Post by Victormd on 2008-06-23
> **Frak said:**
> On a minimal Ubuntu installation, it boots in around 20 seconds on a 1.8Ghz machine.

Minimal Windows, around 22 seconds.

What would you consider minimal? Do you know of any how-tos' explaining what can and can't be removed? I'm sure I don't need half of what ubuntu is loading (i.e., services) but am afraid of removing what I think is unecessary and later find out that it is necessary... or something like that...

---

### Post by andrewabc on 2008-06-23
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Frak on 2008-06-23
> **Victormd said:**
> What would you consider minimal? Do you know of any how-tos' explaining what can and can't be removed? I'm sure I don't need half of what ubuntu is loading (i.e., services) but am afraid of removing what I think is unecessary and later find out that it is necessary... or something like that...
I use BUM to stop starting system services, readahead since I have extra RAM, and I also use a minimal ubuntu-desktop manual installation from the terminal.

---

### Post by Victormd on 2008-06-24
Alright, I'm going to have to give it a shot. Even though I appreciate my ubuntu install if I could speed it up, that would be great. I have readahead but I don't know if I'll be able to speed it up because I have compiz and emerald running... and a few extra seconds during boot is a price I'm willing to pay to have them...

---

