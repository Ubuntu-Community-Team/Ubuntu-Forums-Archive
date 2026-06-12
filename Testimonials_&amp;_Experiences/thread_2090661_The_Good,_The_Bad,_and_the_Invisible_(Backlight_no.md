---
title: "The Good, The Bad, and the Invisible (Backlight not on!?)"
date: 2012-12-03
forum: Testimonials &amp; Experiences
---

### Post by Nightcreeper on 2012-12-03
I have been pushed towards linux by a long time friend (more like a brother from another mother) and have had a pleasant experience save for a couple of laptop installs and some older system installs.

1) Backlight not working on HP Laptops and some other laptops. Why is it so hard to incorporate the "acpi_osi=Linux"or the "acpi_backlight=vendor" into an oem check to make it work ootb? Just curious. Searching for the fix is after KNOWING what it is but not remembering exactly how to do it is at times futile unless you word it "just right".

2) Why is there no way to via GUI add 32-bit support to a 64-bit Version? If there is please explain how.

3) Eyecandy. If you have got the hardware, why not use it? It has made 4 people that I have shown want linux, but, I am using Linux Mint 13 to show them with the wobbly windows and screen fire writing, and I had to search for over an hour for a decent how-to on how to get the compiz effects going. Why not make it easy? And can you do that type of stuff with Unity?

I really like playing and using linux, and at one point found it replacing Windows 7 Ultimate x64, until it was time to unwind with Diablo 3. Wine, ok, I am a noob. It isn't that easy. But, Ubuntu has shown me some AWESOME apps like audacity, and Mixxx, Gimp, and a bunch more I can't think of right now.

Final Thoughts:
I believe that with a little more polishing and some tweaking, maybe making certain settings easier to find and 32-bit support easier to install, that with the "blingy" stuff for free, and a polished experience, we should see Linux competing with Windows on a more equal level. I am behind the Free Software scene, as, a man with 4 kids under my roof, upgrading windows and computers every three years gets expensive, and linux lets me let the kids online on a system that is capable and not likely to get a virus every time they turn around. All in all, good job to everyone at ubuntu and its forks. Thanks for the product you have given your time, sweat, and maybe blood (Got a temper and a sharp keyboard? lol). I appreciate it and truly thank you for the hard work for not only Ubuntu, but the forks I use as well (Linux Mint, Lubuntu, Edubuntu, Ubuntu Studio, and Uberstudent). Thanks again.

---

### Post by mastablasta on 2012-12-03
> **Nightcreeper said:**
>  
1) Backlight not working on HP Laptops and some other laptops. Why is it so hard to incorporate the "acpi_osi=Linux"or the "acpi_backlight=vendor" into an oem check to make it work ootb? Just curious. Searching for the fix is after KNOWING what it is but not remembering exactly how to do it is at times futile unless you word it "just right".

Don't know that. but best option in my opinion would be if the hardware maker would provide laptos with this OS or at least an OEM version of the OS for their hardware.
 
> 
2) Why is there no way to via GUI add 32-bit support to a 64-bit Version? If there is please explain how.

I think if you need 32bit programme the package dependency should be satisfied automaticly. otherwise check synaptic. you can manually select to install 32 bit packages there for your software that you want to run on 64bit.
 
> 
3) Eyecandy. If you have got the hardware, why not use it? It has made 4 people that I have shown want linux, but, I am using Linux Mint 13 to show them with the wobbly windows and screen fire writing, and I had to search for over an hour for a decent how-to on how to get the compiz effects going. Why not make it easy? And can you do that type of stuff with Unity?

 
the point/philosophy  of Gnome is to offer reduced number of GUI settigns as to not overwhelm the unexperienced user. the idea is that everyhitng is already set for the user. however at the same time system is still open for changes/tweaking etc. most stuff can be add on or tweaked but it's not always out in the open. with unity you need compiz config and can do some stuff in fact unity can't be there without compiz.
 
if you prefer something like that then you should actually try the KDE. which has the philosophy that every option should be  shown out there in GUI. so going into settings and desktop effects you will see all the things you like out of the box. 
 
> 
I really like playing and using linux, and at one point found it replacing Windows 7 Ultimate x64, until it was time to unwind with Diablo 3. Wine, ok, I am a noob. It isn't that easy. But, Ubuntu has shown me some AWESOME apps like audacity, and Mixxx, Gimp, and a bunch more I can't think of right now.

 
wine has a nice GUI called Play on linux or Commercial version  - Crossover. most programmes don't work with wine. or their performance is subpar. it is amazing that some do. since it's like reverse engineered windows :-)
 
again like before with backlight it would be great if software makers released linux ports of their games that way there would be no (or at least far less) wine issues. Valve started porting some stuff. let's see if others follow.

---

### Post by 3rdalbum on 2012-12-03
> **Nightcreeper said:**
> 
1) Backlight not working on HP Laptops and some other laptops. Why is it so hard to incorporate the "acpi_osi=Linux"or the "acpi_backlight=vendor" into an oem check to make it work ootb?

A couple of possibilities:

1. Not all HP laptops are affected, and adding those lines will cause bad things to happen on laptops that are not affected. I'd be willing to bet that very few laptops have the problem.

2. The affected laptops are newer than the kernel.

3. The Linux developers haven't seen your computer so don't know about the problem.

 Just curious. Searching for the fix is after KNOWING what it is but not remembering exactly how to do it is at times futile unless you word it "just right".

> 2) Why is there no way to via GUI add 32-bit support to a 64-bit Version? If there is please explain how.

What exactly do you mean by "32-bit support"?

> 3) Eyecandy. If you have got the hardware, why not use it? It has made 4 people that I have shown want linux, but, I am using Linux Mint 13 to show them with the wobbly windows and screen fire writing, and I had to search for over an hour for a decent how-to on how to get the compiz effects going. Why not make it easy? And can you do that type of stuff with Unity?


Compiz is in a bad state at the moment. There's not much development compared to its heyday. Even in its heyday, the really far-out effects were unsupported! There have been efforts to try and make the effects easier and safer to configure, but this always comes at the expense of true customisation power; and so people preferred to use Compizconfig Settings Manager so they could tweak everything by the millisecond.

Unity can support many of these effects, but some will conflict. Conflicts make Bad Stuff Happen; and since Compiz is not well maintained these days, if you venture outside of what is explicitly supported in Unity you may break your desktop.

---

### Post by Nightcreeper on 2012-12-03
The fix and wording. I have googled it and found the walkthrough on a site, after knowing the fix, and knowing what was on the title, I still have a hard time relocating that fix. The issue isn't as uncommon as one would think, and it seems to be a problem on the 2-year old hp touchsmart laptop that is being used. Was a problem on mine and my friends hp laptops before that. I think 10.04 was the last one to not have the issue. Has been reported on the bug forums/sites, as I have read about it there, and on this site, as well as a few others, but still not fixed. If it was working on 10.04, and not on 12.04 or 12.10, how can the kernel outdate the issue? I don't know if it is Grub related or what, but, something about setting the brightness during boot messes it up.

32-Bit full support: 
"sudo apt-get install ia32-libs"

Problems about it located here:
[http://askubuntu.com/questions/216845/manually-installing-ia32-libs-multiarch-on-ubuntu-12-10-64bit](http://askubuntu.com/questions/216845/manually-installing-ia32-libs-multiarch-on-ubuntu-12-10-64bit)

Also, Mastablasta, we have very few companies that are building anything that is Linux tailored, but, we are getting more PC suited. What you say about companies doing for linux is like a seatbelt company asking chevrolet to design their cars for the seat belt compatibility. It just isn't a manufacturers issue about linux compatibility or support, it is more the OEM parts makers' issue, as if they provide Linux drivers for the manufacturers, then, the manufacturers would surely tout that the PC supports linux, though, linux itself would probably be unsupported. Software I don't see as being that hard to compile on two different platforms. I think we would even agree that giving us a source code and/or script for a software to compile ourselves as a linux community could be done, probably even allow volunteers to compile it for them for free using their equipment so they know their code is safe. Either way, more support would be nice, but, don't expect it. If we do our best to use and praise it and not act like the Windows Community OWES us to make Linux PCs and Games, we will get further. Ubuntu is a better OS than windows, aside from application/game/driver support, which is what most people want out of their pc. We are getting there, but, patience is a must, and so is the right attitude.

Just so you know, I want Ubuntu to be an Equal to windows on user base as much as you, but, we can't go pointing fingers and expect people to accept it, especially the ones we point fingers at. Sorry if I offended you, my soapbox time is over.

---

### Post by mastablasta on 2012-12-03
> **Nightcreeper said:**
>  If it was working on 10.04, and not on 12.04 or 12.10, how can the kernel outdate the issue? 
 
that's the part i also don't like. when they break it and then they leave it open/hanging.

---

