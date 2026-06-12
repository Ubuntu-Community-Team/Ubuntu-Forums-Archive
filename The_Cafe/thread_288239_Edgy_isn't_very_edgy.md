---
title: "Edgy isn't very edgy?"
date: 2006-10-29
forum: The Cafe
---

### Post by prizrak on 2006-10-29
After using Edgy for couple of days I must say that it's awesome. It's noticeably quicker than Dapper and the interface colors seem to have changed to a slightly lighter shade making the interface look a little cleaner. 

However, XGL/Compiz are still not installed by default and there is no "XGL" button/session to use it. Network-Manager is also nowhere to be found, which is something that did get on my nerves when I was trying to connect to a WPA network. This an actual functionality issue :( Tablet is also not activated out of the box and no improved Bluetooth (Gnome's BT software sux). Haven't tested the new on screen keyboard and handwriting recognition yet but so far while I do like the new version it doesn't seem very edgy :( 

Just to reiterate I really do like it just wish it would be more of a geek toy :)

---

### Post by .t. on 2006-10-29
Under the hood, mate. Surely that makes it *more* of a "geek toy"?

Anyway, remember there was only a 4 mount dev period for this release?

AIGLX is installed by default. To install Beryl, just add the beryl-project repo and hit install beryl.

---

### Post by Reshin on 2006-10-29
> **prizrak said:**
> After using Edgy for couple of days I must say that it's awesome. It's noticeably quicker than Dapper and the interface colors seem to have changed to a slightly lighter shade making the interface look a little cleaner. 

However, XGL/Compiz are still not installed by default and there is no "XGL" button/session to use it. Network-Manager is also nowhere to be found, which is something that did get on my nerves when I was trying to connect to a WPA network. This an actual functionality issue :( Tablet is also not activated out of the box and no improved Bluetooth (Gnome's BT software sux). Haven't tested the new on screen keyboard and handwriting recognition yet but so far while I do like the new version it doesn't seem very edgy :( 

Just to reiterate I really do like it just wish it would be more of a geek toy :)

Edgy as in "on the edge". Cutting edge. The latest. Unstable. Badly tested. ETC.

---

### Post by prizrak on 2006-10-29
> **Reshin said:**
> Edgy as in "on the edge". Cutting edge. The latest. Unstable. Badly tested. ETC.
But it isn't badly tested or unstable :(

---

### Post by prizrak on 2006-10-29
> **.t. said:**
> Under the hood, mate. Surely that makes it *more* of a "geek toy"?

Anyway, remember there was only a 4 mount dev period for this release?

AIGLX is installed by default. To install Beryl, just add the beryl-project repo and hit install beryl.

Ok lazy geek toy :) I do really wonder why network manager isn't on by default it seems very stable and useful.

---

### Post by Shay Stephens on 2006-10-29
edgy is finally working for me after a few days of install gymnastics.  I really like it and won't go back to dapper.  But it doesn't feel edgy to me either.  More like "extra eft" or "exceptional eft", but it's too safe to be seen as edgy.  That will probably be in fiesty ;-)

---

### Post by mrgnash on 2006-10-29
It's just Edgy enough in my opinion ;)

---

### Post by chickengirl on 2006-10-29
The only part that's edgy about it is the upgrade (yikes!).

---

### Post by Polygon on 2006-10-29
i agree with that chicken girl...

and i did notice some de-improvements, at least on the live cd, the network manager does no longer auto detect and provice a list of wireless EESID's to choose from

and update is terrible.. i upgraded from dapper and i got "fsck died with error 8" and some x server errors... not sure what happened yet as i switched back to dapper.

but once you actually get into the OS it seems very stable :D

---

### Post by mrgnash on 2006-10-29
I didn't even bother with the upgrade. I've learnt from previous experience that it's usually not worth the trouble; and so far everything works fine on my clean install... well, with the exception of XV on AIGLX/Beryl, but that's a problem with ATI's fglrx driver, not Ubuntu.

---

### Post by kuja on 2006-10-30
> Edgy isn't very edgy
Any edgier and I don't think we would have had something usable on the release date. With this many problems being spouted out, it seems that it was quite edgy enough, no? Seems it needs a lot of work in the "clean upgrade path" category.

---

### Post by darrenrxm on 2006-10-30
I did a clean install of edgy. And I must say it's fantastic. I was using breezy before this. And compared to breezy it a huge step forward.

---

### Post by eriqk on 2006-10-30
Well, it's the first time in ages I had to do a dpkg-reconfigure xserver-xorg to get out of 640x480 (clean install), so that must count for something.
Unlike the last time, it worked seamlessly, though, so on my laptop it's slightly less edgy than Breezy was.

Groet, Erik

---

### Post by stimpack on 2006-10-30
Out of the box:

No parallelized booting
No SELinux or AppArmor
No XGL
No WPA, so still my laptop is Windows... (I need internet to download something that lets me connect to the internet, wtf?)

As much of a fan of Ubuntu that I am, without the above improvments there seems little reason to risk stability by upgrading Dapper at this point (for me).

---

### Post by Sushi on 2006-10-30
> **stimpack said:**
> No parallelized booting

Does any distro have this? Nope. ubuntu at least has groudwork ready for this (Upstart)

> No XGL

So what? Edgy has AIGLX, which does the same thing. And AIGLX is part of Xorg, instead of being a whole different X-server (like XGL is). So why should it have XGL? Of the two, AIGLX is the elegant and sensible solution.

---

### Post by prizrak on 2006-10-30
> So what? Edgy has AIGLX, which does the same thing. And AIGLX is part of Xorg, instead of being a whole different X-server (like XGL is). So why should it have XGL? Of the two, AIGLX is the elegant and sensible solution.
It also has SELinux out of the box but there are no policies, so it's useless. Much like AIGLX that is in there but has nothing at all that uses it. Also AIGLX is a part of the current X server as you said and the X server is the worst part of Linux by far. 

It doesn't even matter what is a better solution what matters is that Edgy was supposed to be a "cool" release with the latest and greatest and not necessarily the safest or sanest stuff in it. Yet we still see no out of the box Compiz/Beryl eyecandy, doesn't even have to be the default session it could have been installed under a different X session choosable at startup. I still see no network-manager out of the box, which means no WPA out of the box (at least easily). Wacom tablet still requires tweaking instead of being enabled when it was detected, Bluetooth in Gnome is still horrible and is actually missing a program that Dapper had (not that either seem to be able to pick up my BT adapter).

Basically Edgy is a good release but it is nothing like the toy it was announced to be.

---

### Post by Sushi on 2006-10-30
> **prizrak said:**
> It also has SELinux out of the box but there are no policies, so it's useless. Much like AIGLX that is in there but has nothing at all that uses it.

Um, Compiz?

> Also AIGLX is a part of the current X server as you said and the X server is the worst part of Linux by far.

I think that X is pretty darn nifty, and I find no fatal flaws in current X-server. true, things were pretty stagnant with Xfree, but with Xorg, things have been moving very fast.

So what is your suggestion? Scrap the X-server and do something else instead? AKA "reinvent the wheel"? Why not simply improve the system we already have, especially since it does work for most users as we speak?

> It doesn't even matter what is a better solution what matters is that Edgy was supposed to be a "cool" release with the latest and greatest and not necessarily the safest or sanest stuff in it. Yet we still see no out of the box Compiz/Beryl eyecandy

Could it be because it still causes problems for some users? Even though Edgy is meant to be "cutting edge", it's not meant to be un-usable. If you want nifty 3D-animations you can enable the feature yourself.

---

### Post by prizrak on 2006-10-30
> Um, Compiz?
Not installed by default. If I'm gonna install things I can just as easily pull AIGLX and XGL down. 
> I think that X is pretty darn nifty, and I find no fatal flaws in current X-server. true, things were pretty stagnant with Xfree, but with Xorg, things have been moving very fast.

So what is your suggestion? Scrap the X-server and do something else instead? AKA "reinvent the wheel"? Why not simply improve the system we already have, especially since it does work for most users as we speak?
Because there is a lot of backward compatibility in place for one. For two an X server is great in an environment where you need to open a remote GUI to a machine on a local machine it's a waste or resources and an extra security hole. While Xorg is moving along quite nicely it is still by far the least advanced and the most problematic part of Linux. Try setting up dual head without a nifty front end like FC/RH and SuSE give you. 
> Could it be because it still causes problems for some users? Even though Edgy is meant to be "cutting edge", it's not meant to be un-usable. If you want nifty 3D-animations you can enable the feature yourself.
Moot point, the upgrade procedure gives alot of people headaches yet it's there. I understand that there is no way XGL can be enabled by default as it requires proprietary drivers for nVidia and ATI cards before it can work. However shipping Edgy with a Compiz/Beryl session as one of the choices when you start Ubuntu should have been quite possible.

---

### Post by daynah on 2006-10-30
I'm confused as to why you want it to be "edgy" or "unstable."

One of the reasons I like my Ubuntu more than Windows is because (ha) Ubuntu "just works." With all this talk of scary edginess, I'm a bit scared to go on to Edgy. I'll skip it (yay LTS) and wait till Fiesty.

If it IS not as edgy as many want it to be, maybe it's because of people like me. In the end, Ubuntu is famous for being that one disto that your average Joe like me can use and doesn't often sacrifice it's user friendliness for the power user playground. :) I think Ubuntu has kept (and still does, I'm just paranoid) a good balance and I'm thankful!

---

### Post by Sushi on 2006-10-30
> **prizrak said:**
> Not installed by default.

Install it then. Last time I checked, installation of new software is VERY easy on Ubuntu. And are you REALLY suggesting that Ubuntu should be using a piece of software that just reached 0.2 "milestone" as it's default windowmanager?!?!

> For two an X server is great in an environment where you need to open a remote GUI to a machine

X is very nifty for other things besides that.

> on a local machine it's a waste or resources

Is this the old (and refuted) "X is slow and bloated!"-argument? You are beating a dead horse here. I thought the complaining about X's "slowness" died 1-2 years ago?

> While Xorg is moving along quite nicely it is still by far the least advanced

How do you define how "advanced" things are? X has hardware-accelerated 3D-compositing that is right up there with Vista and OS X, and you are calling it "least advanced part of Linux"? Hell, X has features that put OS X and Vista to shame, so what is the problem here? In many ways X is the most advanced piece of GUI-technology, even when compared to Vista and OS X.

Hell, OS X's idea of doing remote sessions consists of sending screenshots across the network! Blech!

Want to know what I think are "the least advanced stuff in Linux"? 

- Office-suites. When will we get something that approaches Keynote or Pages on OS X? Propably never. OpenOffice is utter crap. And it keeps on staying crap, even thougn the version-number climbs higher.

- Photomanagement. Where is Aperture-killer?

- Photoshop-killer? GIMP might offer similar features, but the UI is horrible. Hopefully Krita manages to utterly kill GIMP, the Linux-users deserve it.

- Games. In Widows, the state-of-the-art gaming would be something like Alan Wake. In Linux we are raving about TuxRacer.

And that's just tipping the iceberg. I REALLY don't think that X is our biggest problem. Hell, we should all get down on our knees and thank $DEITY for X!

> and the most problematic part of Linux.

Do you have ANY idea how complex something like drawing a GUI can be, especially if you have to rely on third-party binary-only driver to do it? Yes, I have heard of people having problems with X. And quite often those problems are related to the closed drivers the users are running.

Kernel has it easy: most of the drivers are open and they are part of the mainline kernel. Those nifty Ati/NVIDIA-drivers everyone wants to use? Closed, outside the Xorg-tree.

---

### Post by prizrak on 2006-10-30
> I'm confused as to why you want it to be "edgy" or "unstable."

One of the reasons I like my Ubuntu more than Windows is because (ha) Ubuntu "just works." With all this talk of scary edginess, I'm a bit scared to go on to Edgy. I'll skip it (yay LTS) and wait till Fiesty.

If it IS not as edgy as many want it to be, maybe it's because of people like me. In the end, Ubuntu is famous for being that one disto that your average Joe like me can use and doesn't often sacrifice it's user friendliness for the power user playground. I think Ubuntu has kept (and still does, I'm just paranoid) a good balance and I'm thankful!

I don't want it to be unstable but I do want it to be Edgy.
The original plan for Edgy (as outlined by Mark) was that it would be an intermediate release that will not be all that stable but will basically be like a stable beta and introduce some of the new stuff that will make it into later versions once it reaches stability. This was done due to Dapper's LTS status and to let the devs work on pet projects basically. There was talk of Beryl/Compiz/XGL/AIGLX all enabled out of the box. It doesn't even have Network-Manager installed by default. This gave me a nice little issue of not being able to connect to the internet until I got home and used a hardwired connection to pull it out of the repos. 
> Install it then. Last time I checked, installation of new software is VERY easy on Ubuntu. And are you REALLY suggesting that Ubuntu should be using a piece of software that just reached 0.2 "milestone" as it's default windowmanager?!?!
Please try your hardest to read what I type. You said that AIGLX is installed by default so the eye-candy is there. Nothing in the default install uses it so there is no point. Yes I can install Compiz and I did (well actually I installed Beryl from their repos) but if I'm going to install Compiz/Beryl I can install XGL and AIGLX, hell I can do that on Dapper (which I have before). I also said that it doesn't have to be the default, if you look at the Beryl Wiki the Ubuntu how-to for XGL/Beryl on Edgy starts off with making a separate session for it. Ship Edgy with two sessions, the default being Metacity + Gnome and the "Eyecandy" one using AIGLX and Beryl/Compiz. 

If you go into the "if it's not there install it" argument then there really is no point to Ubuntu or any other distribution. All the software is available and can be installed by those with knowledge. The point of Edgy was just that, to be edgy to include some not-so-stable-but-fun software that might not be good enough on a "production" desktop but is just fine for a home user who wants to play around with it. 
> Is this the old (and refuted) "X is slow and bloated!"-argument? You are beating a dead horse here. I thought the complaining about X's "slowness" died 1-2 years ago?
X is by no means slow, it's just crappy. I use an Intel card in this thing (open source drivers) and it has crashed more than once before on trying to play a video and by crash I mean it would go into an infinite restart loop at which point I couldn't kill X or even go into CLI console via ctrl+alt+F1 and had to forcibly turn off the system. 
> Hell, OS X's idea of doing remote sessions consists of sending screenshots across the network! Blech!

I did address that, like I said above X is great for remote access, not so much for local. It's not about the speed or the 3D acceleration, it's about the fact that it is overly complex for a local GUI. It is also an added security risk as it is network aware. (got friends in the security biz)

> Do you have ANY idea how complex something like drawing a GUI can be, especially if you have to rely on third-party binary-only driver to do it? Yes, I have heard of people having problems with X. And quite often those problems are related to the closed drivers the users are running.

I have X issues with open source drivers, and forget dual head regardless of what driver is being used. Also it seems like both OS X and Windows manage to work with binary drivers just fine.

---

### Post by Sushi on 2006-10-30
> **prizrak said:**
> I don't want it to be unstable but I do want it to be Edgy.

What is "edgy"? New and cool stuff? New stuff is often unstable.

> Please try your hardest to read what I type. You said that AIGLX is installed by default so the eye-candy is there. Nothing in the default install uses it so there is no point.

AIGLX is there to give you the tools you need to get gorgerous desktop. It's too bad that the other stuff needed for it is not quite there yet. But you do have the option of installing and using it, with minimim of fuzz.

> If you go into the "if it's not there install it" argument then there really is no point to Ubuntu or any other distribution. All the software is available and can be installed by those with knowledge.

Not all have the knowledge.

> The point of Edgy was just that, to be edgy to include some not-so-stable-but-fun software that might not be good enough on a "production" desktop but is just fine for a home user who wants to play around with it.

And it is there, you just need to install it separately. What is the problem here? Is the core of your issue the fact that Beryl/Compiz does not shp with the OS, but that you need to spend aybe 5 minutes of your time to install it?

> X is by no means slow

You did say that it's a "waste of resources".

> it's just crappy. I use an Intel card in this thing (open source drivers) and it has crashed more than once before on trying to play a video and by crash I mean it would go into an infinite restart loop at which point I couldn't kill X or even go into CLI console via ctrl+alt+F1 and had to forcibly turn off the system.

Tough luck, I find the open-source drivers to be very stable indeed.

> I did address that, like I said above X is great for remote access, not so much for local.

Why? And besides: why should we give up remote access? So we could reach the level of OS X "elegance" where we send screenshots across the network? Why should we give it up? Remote access does not mean that local access is slow. We can have it both ways. And we do.

> It's not about the speed or the 3D acceleration, it's about the fact that it is overly complex for a local GUI.

Do you REALLY think that Aero, Aqua, Quartz 2D Extreme etc. are one bit simpler?

> It is also an added security risk as it is network aware. (got friends in the security biz)

It's not like X just sits there waiting for random connections from the network. OMG, Firefox is network-aware as well! Kernel has some network-stuff as well, is it a security-risk as well?

> Also it seems like both OS X and Windows manage to work with binary drivers just fine.

Apple supports three pieces of hardware: Radeon, GeForce and Intel GMA950, and they control the hardware it runs on AND the OS. X works with A LOT more hardware than that. And wanna bet that Apple can go through the drivers with fine tooth-comb? X-developers can't do that.

And all the vendors spend LOTS of time and money to develop drivers for Windows. Their efforts in Liux receive a fraction of those resources. And if you think that Windows "works just fine with binary drivers", then I'm forced to tell you that you are mistaken. Drivers are the #1 reason for crashes and instabilities in Windows.

---

### Post by prizrak on 2006-10-30
> AIGLX is there to give you the tools you need to get gorgerous desktop. It's too bad that the other stuff needed for it is not quite there yet. But you do have the option of installing and using it, with minimim of fuzz.
> And it is there, you just need to install it separately. What is the problem here? Is the core of your issue the fact that Beryl/Compiz does not shp with the OS, but that you need to spend aybe 5 minutes of your time to install it?

Quite a bit less but if I am going to install Beryl I can just as well install AIGLX. Hell I can install it on Dapper, what is the point of Edgy then? Also you are concentrating on just the eyecandy, how about useable things like network-manager not being there? At least the on screen kbd finally got better, still no handwriting recognition tho.
> Tough luck, I find the open-source drivers to be very stable indeed.

They are obviously not.

---

### Post by prizrak on 2006-10-30
(sorry submitted by accident so it's broken up)
> Why? And besides: why should we give up remote access? So we could reach the level of OS X "elegance" where we send screenshots across the network? Why should we give it up? Remote access does not mean that local access is slow. We can have it both ways. And we do.
> Do you REALLY think that Aero, Aqua, Quartz 2D Extreme etc. are one bit simpler?
I know that for a fact, Aero and Aqua both do the same thing that AIGLX does but don't have the massive server infrastructure that X does. You don't have to give up remote access, but how often do you remote into your laptop? If we are talking about J6P they have no need for remote access, removing it could simplify the GUI system quite a bit and make it more stable if not faster. I never said X should be completely cut out, it has some great uses but there are also reason for why it is not necessary on an average desktop.
> It's not like X just sits there waiting for random connections from the network. OMG, Firefox is network-aware as well! Kernel has some network-stuff as well, is it a security-risk as well?
Search the security announcements forum for how many of kernel and Firefox bugs can be used to gain control of your system. Why introduce another venue of attack when it is not necessary? 
> Apple supports three pieces of hardware: Radeon, GeForce and Intel GMA950, and they control the hardware it runs on AND the OS. X works with A LOT more hardware than that. And wanna bet that Apple can go through the drivers with fine tooth-comb? X-developers can't do that.
Yes I will give you OS X it is quite limited in hardware support. 
> And all the vendors spend LOTS of time and money to develop drivers for Windows. Their efforts in Liux receive a fraction of those resources. And if you think that Windows "works just fine with binary drivers", then I'm forced to tell you that you are mistaken. Drivers are the #1 reason for crashes and instabilities in Windows.
#1 reason for crashes and instabilities of most modern OS's is hardware drivers that are run in kernel space. Open source drivers screw up as well as binary ones do. The only time my XP system on my new laptop died was when I overheated my video card. Ironically Linux worked just as well with the binary nVidia drivers on that same laptop, even XGL could not bring it down to the point where X wouldn't work.

---

### Post by darkhatter on 2006-10-30
????AIGLX is built into xorg, thats why its in the new release, there is a lot more reasons why people shouldn't have personal computers, look at all the problems it creates.

---

### Post by prizrak on 2006-10-30
> **darkhatter said:**
> ????AIGLX is built into xorg, thats why its in the new release, there is a lot more reasons why people shouldn't have personal computers, look at all the problems it creates.

So true. It seems like Edgy becomes VERY Edgy right after it is restarted ;) Strangely enough it's the same symptom on two different computers.

---

### Post by prizrak on 2006-10-30
Seems like Network-Manager was the culprit (the only thing common to both systems) that might explain why it's not shipped by default ;) Did work fine on Dapper though. 

Sushi,
Just crashed twice because of the video driver ;)

I also just discovered the autoremove command in apt-get about damn time :)

---

### Post by DJ Wings on 2006-10-30
> Edgy isn't very edgy?
It's really edgy! It's cutting-edge, and because of that, a lot of people are bleeding. So are their computers.

---

