---
title: "How is 12.04 running on AMD's APUs"
date: 2012-03-21
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by pqwoerituytrueiwoq on 2012-03-21
namely the a6-3500 (desktop processor)
going to be building a system for my dad (probably Monday) I figure 12.04 would have the needed support
probably going to use lubuntu, xubuntu, or gnome-fall-back at least until mint 13 is ready
since I am going to need to get the layout something like XP (going to be hard enough forcing him to not use aol's browser) and unity lacks the ability to customize it's panels (yes i have never got ctrl/super/alt right click to do anything on them)
or would I be better off using 11.10/mint 12 with (or without) the xswat ppa?
I would use lucid but I think the software is a little old for the hardware
should I use fglrx or the open source driver for best 2d performance?

---

### Post by tista on 2012-03-21
> **pqwoerituytrueiwoq said:**
> namely the a6-3500
going to be building a system for my dad (probably Monday) I figure 12.04 would have the needed support
probably going to use lubuntu, xubuntu, or gnome-fall-back at least until mint 13 is ready
since I am going to need to get the layout something like XP (going to be hard enough forcing him to not use aol's browser) and unity lacks the ability to customize it's panels (yes i have never got ctrl/super/alt right click to do anything on them)
or would I be better off using 11.10/mint 12 with (or without) the xswat ppa?
I would use lucid but I think the software is a little old for the hardware
should I use fglrx or the open source driver for best 2d performance?

Well cinnamon would be the better choice for your dad? ;)
Yeah you're right. Unity-3D/2D didn't have any option to put own panel onto bottom of screen... but cinnamon could.

Or more seriously, gnome-fallback (classic) session have gnome-panel. Although it's not so perfect, but enough to use as daily home use...

Finally I could suggest radeon/Gallium3D driver to be fitted with Fusion/Vision platform well. ;)
If you only need 2D performance, you should stay with radeon/gallium instead of fglrx. In past, I've experienced some issues especially for gnome-shell family (to be honest, I hate fglrx). I heard now it could be fixed though... In fact I'm using Thinkpad X121e AMD Fusion/E-350 with Gallium, then it's really fantastic!! All you have to do is register the xedgers ppa or oibaf's ppa to get the latest codes of gallium... ;)

Cheers,
Tista

---

### Post by kaldor on 2012-03-21
I'd avoid APU's for a while. While some people seem to have some good results with them, I don't think they're trouble-free quite yet.

For minimal issues in building a Linux-ready PC for basic usage then it's a good idea to stick to pure Intel. If you need graphics that are a bit better than the integrated Intel graphics, get a low end Radeon card from the 5000 series (5450 maybe) and use the default Radeon driver. It seems like the open source support is pretty stable around that generation. The default drivers are plenty good for basic, non-gaming usage. 

For the DE, why not just use a stock Unity or Shell setup? Trying to turn a Linux desktop into something that *looks* like Windows will probably just annoy the new users because they can't understand why it doesn't *work* like Windows. Who knows.. maybe your dad could end up loving the Unity desktop :)

And most importantly, wait for 12.04 LTS to actually be released before you let an inexperienced user use it on their main PC- you don't want to put them off from using Ubuntu because of inevitable crashes and problems in the development versions.

---

### Post by Gregory Lee on 2012-03-22
I'm running the current version of 12.04 on an AMD APU: a8-3820, 4 core.  It crashes about once a day and I can't play any video files, but aside from that, it seems fine, to me.  I'm running an fglrx which I think is not the most current version, but it's good enough for Unity 3d and Gnome 3 (when it doesn't crash, of course).

---

### Post by pqwoerituytrueiwoq on 2012-03-22
> **tista said:**
> Well cinnamon would be the better choice for your dad? ;)
Yeah you're right. Unity-3D/2D didn't have any option to put own panel onto bottom of screen... but cinnamon could.

Or more seriously, gnome-fallback (classic) session have gnome-panel. Although it's not so perfect, but enough to use as daily home use...

Finally I could suggest radeon/Gallium3D driver to be fitted with Fusion/Vision platform well. ;)
If you only need 2D performance, you should stay with radeon/gallium instead of fglrx. In past, I've experienced some issues especially for gnome-shell family (to be honest, I hate fglrx). I heard now it could be fixed though... In fact I'm using Thinkpad X121e AMD Fusion/E-350 with Gallium, then it's really fantastic!! All you have to do is register the xedgers ppa or oibaf's ppa to get the latest codes of gallium... ;)

Cheers,
Tista
i just installed mint 12+cinnamon on a spare hdd i have in my case (rig specs in sig)
to me it seems a lot better than anything else i have tried
though i still like my custom compiz settings on my trusty lucid install (explode effects,magic lamp,expo settings,etc)
cinnamon needs 3d right? will i need to use flglrx in that case (i do prefer the open source drivers since they get the little things right) which ppa will i need?
why does that name (cinnamon) just have to remind me of that apple jacks commercial...:lolflag:

---

### Post by xajeiw9I on 2012-03-22
I've tested Ubuntu 11.04, 11.10 and 12.04 beta on a E-350 netbook. I tried a lot of other distros too. Some of them didn't boot because of older kernels, or bugs with the open source driver.

In my opinion, 11.10 was barely usable, the performance left much to be desired, specially because Unity was horrible. 

The current 12.04 incarnation was the first time I actually wondered if Ubuntu is running faster on it than Windows.

Video drivers are still not good enough, no video acceleration, and I couldn't try a non-buggy FGLRX yet. Maybe they will add a fixed version of it in the repositories after 12.04 goes final, and it can be used for 720p video playback, what would make me happy.

Maybe Fedora 17 will work ok with it too, since it has a newer GNOME Shell. Fedora 16 was kind of slow and buggy too.

Ubuntu 12.04 is shaping up to be a remarkable desktop experience. I understand people that want old GNOME back, but I just want a new shiny toy, and Fallback Mode allows plenty of configuration, there is no need for Cinnamon, in my opinion Mint is a horrible mess. I tried Mint 12 and it had stupid bugs like OSD icons in wrong resolution.

If you want a cleaner Ubuntu experience, don't install Mint, install Trisquel.

---

### Post by ranch hand on 2012-03-22
I really think you need to get hold of a Live CD with Xfce4.8 on it and try it.

12.04-testing uses it and I think 11.10 uses it.  Debian testing uses it (Ubuntu LTS releases are based on Debian testing).  There is a Xfce version of LMDE that uses it.

This is a long way in advance of 4.6.  The panel(s) are much more customizable than the Gnome Panels ever were.

Xubuntu 12.04 is going to be somewhat more stable than Ubuntu in that Xfce4.8 is not new,  4.10 is on the way (should be out by now but held up a couple times).  When they change to 4.10 they will be using Gtk3 as is Gnome now.  Xfce4.8 is still using Gtk2.

If you have not used Xfce be sure to check /usr/share/xfce4/doc/C, and /usr/share/doc/xfce4-panel in particular but all the documentation is excellent.  

file:///usr/share/doc/xfce4-utils/html/C/xfce-user-guide.html
Is a great link to a lot of info.

Before rolling your eyes at the "antiquated" Thunar (you may not but I did) check this site;
file:///usr/share/doc/xfce4-utils/html/C/xfce-user-guide.html

I think for what you are doing you really owe it to your self  to check it out.  I think you can get the look and feel you want.

I configured mine for giggles to look like Unity.  Unfortunately it worked better than Unity.

I initially set it up like my Gnome Panels had been.  Then I learned to use these correctly and only use one instead of two to do the same jobs plus a couple extra.

I think XP should be pretty simple.

---

### Post by tista on 2012-03-22
> **pqwoerituytrueiwoq said:**
> i just installed mint 12+cinnamon on a spare hdd i have in my case (rig specs in sig)
to me it seems a lot better than anything else i have tried
though i still like my custom compiz settings on my trusty lucid install (explode effects,magic lamp,expo settings,etc)
cinnamon needs 3d right? will i need to use flglrx in that case (i do prefer the open source drivers since they get the little things right) which ppa will i need?
why does that name (cinnamon) just have to remind me of that apple jacks commercial...:lolflag:

hahaha! ;) yeah the name of "cinnamon" sounds pretty cute...

Unfortunately I didn't use Mint, and forgot to mention, because 12.04 would be released with the latest gnome-shell codes, So you might fial to kick cinnamon on 12.04 official release (it depends on cinnamon devs whether they could build cinnamon against latest upstream in time or not).

And now I'm using these ppa for radeon/gallium:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")
[https://launchpad.net/~oibaf/+archive/graphics-drivers]("https://launchpad.net/~oibaf/+archive/graphics-drivers")

For me, 1st is Oibaf's one. ;) He is really rock since he lives in phoronix forum for supporting lots of people those who loves bleeding edge mesa experiences...

Cheers,
Tista

---

### Post by cariboo on 2012-03-22
My Dad has an Acer laptop with an E350 apu, I tried Precise alpha 1 on a USB thumb drive, everything work without any additional configuration. I only played with it for an hour or so, so I can't comment on battery usage.

---

### Post by cryptotheslow on 2012-03-22
I have to agree with ranch hand. Graphics drivers aside. If you want to move a user from XP to 12.04 *buntu look at Xubuntu as the least shocking change followed by Lubuntu.

However, if you can bear the more extended change shock phase, for a user who just uses a few applications regularly Unity really works - pin the regular apps to the launcher, resize the launcher to 32px to make it less Fisher Price big button and I think it's a winner. Particularly on a wide screen format.

I surprise myself saying that as I absolutely loathed Unity initially, but having messed with 12.04 as a main OS for a couple of months on a widescreen laptop that's used for a limited number of applications rather than for real work - it's an environment that is rather nice to be in. I'm not so sure it will be so great on my real "work" PCs, but I'll approach that with a more open mind than I would have done a while back.

---

### Post by 3rdalbum on 2012-03-22
I'd echo the sentiments of an earlier poster: Allow the person to try Unity. If it looks and feels different to Windows, they won't expect it to behave like Windows or (probably) run Windows programs.

It may be more confusing for the person to see something that looks like Windows, but otherwise is nothing like Windows.

Unity is a great desktop shell, but if you really can't get to grips with it then you don't have to go installing a different distro. Gnome Fallback is available in the repositories. With Gnome Fallback you can alt-right-click on the panels to change them - you can't with Unity because it's not based on Gnome Panel.

---

### Post by pqwoerituytrueiwoq on 2012-03-22
we are talking about someone who uses AOL's browser,Firefox, and some free ware video player i installed to play wmv files he gets in emails
not like i am going to install a xp theme he would sit there just trying to install aol all day long :lolflag:
by similar layout i mean start button,app icons,window list, try icons

by needs are different i want compiz and panels i can customize to something like [this](http://i.imgur.com/sPOpB.png) and i like my app menu like is now

---

### Post by jerrylamos on 2012-03-22
Well, one way is to show your Dad smart phones and Nooks and iPad tablets and say that's the way the users are going, then show him Unity-2D is in that direction.  

By the way, my son-in-law has a very nice IBM Thinkpad T60 which had been running XP slower and slower and s-l-o-w-e-r to the point of uselessness until he had a co-worker install Xubuntu.  Picked up its skirts and flew!

My opinion, with Unity-3D your Dad will immediately think he's lost his glasses everything is so foggy and blurry.

Me, I'm testing whatever Ubuntu throws over the fence with a rock tied to it whether I like it or not.  Example ubiquity is a ripe field for bugs and I sure don't like running it - all set up to try lubuntu on a newer notebook to see what kernel it will install.

Have fun, 

Jerry

p.s.  My wife uses XP for web site support with proprietary software not available on linux - she has a MUCH easier time with the Xubuntu laptop than with my daughter's Apple.

---

### Post by suprman2020 on 2012-03-22
I'm using a Dell Vostro which has an a8-3500m. Using the Radeon 12.2 drivers and Gnome Shell, it has been a pretty good experience. I rarely see (hard) crashes. Videos work fine. Everything seems to be functioning smoothly. Make sure you use the latest drivers from AMD's site.

---

### Post by EgoGratis on 2012-03-22
1.) I think your dad will like Unity very much.
2.) If anything, then low quality video driver will make him sad and because of that if you don't get 100% confirmation that specific model of AMD APU has rock solid driver for Ubuntu 12.04 or you can't test it by yourself in the shop or with help of a friend that has the hardware you are interested in then buy Intel.

---

### Post by wnelson on 2012-03-22
I have a Lenovo B575 and with 12.04, kernel 3.3 and radeon video driver everything works great. I get about 5 1/4 hours out of the battery. The most important thing is to remove the battery when using AC. The battery will last longer.

Walt

---

### Post by pqwoerituytrueiwoq on 2012-03-22
> **wnelson said:**
> I have a Lenovo B575 and with 12.04, kernel 3.3 and radeon video driver everything works great. I get about 5 1/4 hours out of the battery. The most important thing is to remove the battery when using AC. The battery will last longer.

Walt
i found that out the hard way a couple years ago battey was at 50% inside of a week of gettting it

---

### Post by pqwoerituytrueiwoq on 2012-03-22
> **jerrylamos said:**
> Well, one way is to show your Dad smart phones and Nooks and iPad tablets and say that's the way the users are going, then show him Unity-2D is in that direction.  

By the way, my son-in-law has a very nice IBM Thinkpad T60 which had been running XP slower and slower and s-l-o-w-e-r to the point of uselessness until he had a co-worker install Xubuntu.  Picked up its skirts and flew!

My opinion, with Unity-3D your Dad will immediately think he's lost his glasses everything is so foggy and blurry.

Me, I'm testing whatever Ubuntu throws over the fence with a rock tied to it whether I like it or not.  Example ubiquity is a ripe field for bugs and I sure don't like running it - all set up to try lubuntu on a newer notebook to see what kernel it will install.

Have fun, 

Jerry

p.s.  My wife uses XP for web site support with proprietary software not available on linux - she has a MUCH easier time with the Xubuntu laptop than with my daughter's Apple.
only apple product i have is a ipos shuffled 2ed gen i have no cell phone
his old computer is a 3ghz Pentium 4 with1gb or ddr2 ram which runs xubuntu 10.04 like a dream with better screen resolution
getting suck nice results from such a weak integrated gpu makes me wish Intel would make actual video cards they don't have to be gaming class (like teh 70 USD and below price range)
"Xubuntu laptop than with my daughter's Apple" bet it is the keyboard

---

### Post by kelpdip on 2012-03-22
E350 thinkpad, running kubuntu.
Suspend is broken (in gnome3 too), and hardware overlay is broken due to the fglrx version. The amd 12.2 drivers fixed the hw acceleration problem, but i'm not going to try to fix it until beta2. All the thinkpad quirks seem to work well, preconfigured in kde. Wireless with all forms of encryption and cisco vpn actually are more reliable than on windows7.

---

### Post by wnelson on 2012-03-23
I ran into all type of problems with fglrx 12.2 I back out and reinstall xorg-ati/radeon.

Walt

---

### Post by kelpdip on 2012-03-23
The open source drivers haven't made much progress in power management. There is a noticeable heat and battery life difference in all versions, unfortunately.

---

### Post by tista on 2012-03-23
> **kelpdip said:**
> The open source drivers haven't made much progress in power management. There is a noticeable heat and battery life difference in all versions, unfortunately.

@kelpdip.

No.. No...
Our important thing is "How could we provide the **stable graphic drivers** to everyone now and the future", right?

Because graphic drivers are the key for every desktop experiences as highest priority... And more seriously, these must work "out of the box" without any visual glitches, compositor corruptions, ugly flickering and "sudden death". as fglrx, I know it has really fantastic GL performance on phoronix testing tools, but is it really needed such perf on generic desktops?

And fglrx would not be suitable for "Wayland". damned... on the other hand, Gallium on PALM (running on our X121e or so) could improve wayland compositor pretty well. So fglrx could survive this "wayland war"? Today at least I don't think so...

Exactly the battery drain seems bad on radeon/gallium, but I could say "It's even better than that un-handled drivers make some ugly visual issues". ;)

---

### Post by wnelson on 2012-03-23
Look at the various option with the radeon driver for power management. 

man radeon 

option "clockgating" "on"
option "dynamicPM" "on"

and other options possibly help.

Walt

---

### Post by pqwoerituytrueiwoq on 2012-03-27
got it setup the open source driver cant seems to figure out that there is only 1 monitor (using a55 chip set)plugged in and lacks 3d (slow fiber lamp screenaver )  and fglrx has tearing and stability issues (yes tear-free is enabled)
i have it running cinnamon 
i hope fglrx gets fixed by the time precise is released

---

### Post by kelpdip on 2012-03-27
Fglrx in 12.04 was recently updated to use 12.3(?) drivers. This fixed almost everything for me.

---

### Post by ruinairas on 2012-04-02
How is 12.04 running on AMD's APUs you say? Well, first off it's a gamble. Sometimes with a fresh install it works correctly, other times after installing the catalyst driver the system fails and I can't get back into the system without having to jump to fallback graphics mode. That aside if you do get drivers installed and everything set up don't expect 3D applications to work properly. Especially using Wine. In my case every game I know is supported on Wine crashes. Even an old game that I've used on wine on Nvidia's and Intel's chipsets; Scarface. Once again, you might get lucky and it works then you turn off your computer and as soon as you restart it it may stop working...at least that is the headache I've been having. Sadly I've been getting better performance for gaming on a Intel chipset lol.

---

### Post by pqwoerituytrueiwoq on 2012-04-02
> **ruinairas said:**
> How is 12.04 running on AMD's APUs you say? Well, first off it's a gamble. Sometimes with a fresh install it works correctly, other times after installing the catalyst driver the system fails and I can't get back into the system without having to jump to fallback graphics mode. That aside if you do get drivers installed and everything set up don't expect 3D applications to work properly. Especially using Wine. In my case every game I know is supported on Wine crashes. Even an old game that I've used on wine on Nvidia's and Intel's chipsets; Scarface. Once again, you might get lucky and it works then you turn off your computer and as soon as you restart it it may stop working...at least that is the headache I've been having. Sadly I've been getting better performance for gaming on a Intel chipset lol.
i have seen Intel chips run better on Linux that windows if only that was true for my nvidia gpu...

---

