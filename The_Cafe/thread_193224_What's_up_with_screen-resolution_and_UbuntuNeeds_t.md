---
title: "What's up with screen-resolution and Ubuntu?Needs to be fixed before ubuntu rules all"
date: 2006-06-09
forum: The Cafe
---

### Post by Osamabingandhi on 2006-06-09
I've tried some more distros than ubuntu and what they have in common is screen-resolution trouble. The first thing an linux user need to fix is the screen resolution. That's where the trouble begins. I really believe a lot of people throw linux in the trashcan because of this! To write comands in the terminal will scare anyone especially when you are not sure what to write and what to do when you finally figure out how to do it. You have search the forums like a maniac and then trial and error.:confused:  I broke my ubuntu by doing this! To make a new installation was not very funny.:cry: 

How do you know what to write in safe mode to fix the xorg.conf? Ahhh i feel this frustration hanging over me and how easy it would have been for me to give up. When a total beginner is thrown into system modification on this level it's bad.

What i have understood is that linux systems only support up to 1024x768 resolutions. In this day of age most people have 1280x1024 on their monitors. And almost everyone needs to change the system settings! I can't believe that this isn't fixed yet. It seems like i should not be a impossible thing to correct.

After that what is really missing in ubuntu is an official cd with the codecs nvidia drivers, flash, java, more games, newer alsa sound drivers etc...and other things that for most people is a must have. I know work is being done here and automatix and easyubuntu is striving for this. When i go home to my father's computer with just a modem i will forget about ubuntu. To sit a couple of hours downloading is too much trouble. This gives me one good alternativ, vector linux. But ubuntu is better in other ways, but the fact is that a lot of people don't have broadbands yet and then you gives them big trouble. An mix of easy ubuntu and automatix in a 700meg super-cd would be perfect!!! This would beat windows on the fingers big time:KS 

Don't get me wrong here i really like ubuntu a lot! Linux will rule the world, and ubuntu has come such a long way. Things i talk about is minor but extremly important. For me almost everything else worked out of the box for exept these monitor issues and some sound problems. It will be very little windows for me after this...Linux is da shit!:D

---

### Post by aysiu on 2006-06-09
SuSE has a graphical tool for configuring X.

---

### Post by matthew on 2006-06-09
I'm going to move this from testimonials to the cafe.

---

### Post by aysiu on 2006-06-09
[QUOTE=matthew]I'm going to move this from testimonials to the cafe.[/QUOTE] Thanks, matthew.

---

### Post by _simon_ on 2006-06-09
I installed a fresh copy of Dapper the other day and it detected the correct 1280 x 1024!

---

### Post by basketcase on 2006-06-09
[QUOTE=Osamabingandhi]What i have understood is that linux systems only support up to 1024x768 resolutions. In this day of age most people have 1280x1024 on their monitors. And almost everyone needs to change the system settings! I can't believe that this isn't fixed yet. It seems like i should not be a impossible thing to correct.[/QUOTE]


My Ubuntu Installation out of the box is running at 1900x1200 on my notebook and has no issues running at 1600x1200 on my deskstop.

---

### Post by Ubunted on 2006-06-09
Dapper stuck to 1024x768 on my 17" LCD until I installed fglrx, then it went straight to 1280x1024.

---

### Post by benplaut on 2006-06-09
i've never had any problems with it...

---

### Post by WildTangent on 2006-06-09
Hmm... maximum 1024x786 huh? That's why I can run mine at 1920x1440 :-P In all seriousness...this issue is hit or miss. In order to use higher res's, one must know the horizontal and vertical refresh rates for their monitor if it's a CRT (this doesn't apply to LCDs, they're almost always autodetected correctly.). Sometimes, you get lucky and get the full res capable right away, sometimes you need to do some research and then edit your xorg.conf.

-Wild

---

### Post by briancurtin on 2006-06-09
[QUOTE=benplaut]i've never had any problems with it...[/QUOTE]
[COLOR="White"].[/COLOR]

---

### Post by zenwhen on 2006-06-09
Ubuntu DOES need a graphical X config tool. This config tool should even support changing setting that are specific to fglrx and the Nvidia drivers. The command line should not have to be touched to set this up. 

When I was starting out, having to edit xorg.conf frustrated me enough to give up twice before I finally got Slackware working how I wanted it in a dual head configuration.

---

### Post by Osamabingandhi on 2006-06-10
That is my point...But i guess it isn't true that everybody has this problem. Thought it was just me:???:

---

### Post by stairwayoflight on 2006-06-10
hi,

i think ubuntu rules, and i don't mind changing xorg.conf because my crappy 15"crt-bubble-screen probably gives the system no clues what it needs. but i'm curious where all these weird resolutions come from in my xorg.conf:

```

Section "Screen"
	[...]
	SubSection "Display"
		Depth		1
		Modes		"1272x1272" "960x768" "960x720" "800x600" "720x400" "640x480" "256x160" "152x810" "96x808"
	EndSubSection

```

i take out the ones i don't want (almost all of them) and put in the standard 1280x1024, 1024x768, etc.

i just thought it was strange for all these res.'s to be in there.. i thought those were supposed to be the ones my gfx card could do (s3 prosavage8 integrated) so once my moniter values were correct gnome would let me switch to all resolutions listed in xorg.conf--or is that wrong??

anyways i am otherwise happy.. gnome kicks the crap out of anything i have ever run including gentoo-compiled (not that that turns an athlon-xp into 'deep blue' or anything ;-) and gets me from login to a working desktop in ~2 secs.

i have a logitech desktop express i picked up from computer warehouse outlet, works perfectly (uses the ps2 style ports). it was only $10 plus batteries! all the xtra-functionality keys work (volume+/-/mute, email, home page) except for the "back <-" and "calc" keys :-( i wish i knew how to set that up..

oh yeah, running 6.06 lts, linux-386 2.6.15.22, on amd athlon-xp 2400+ system. it is more than fast enough with only 768mb of ddr ram. my god i am glad i moved from gentoo.. talk about a high-maintenance relationship! but i suppose if i needed to configure a system for a more important purpose, like servers in high-risk environments with selinux, acl's and rbac and all that crap, i'd check it out again.

---

### Post by Stormy Eyes on 2006-06-10
[QUOTE=Osamabingandhi]What i have understood is that linux systems only support up to 1024x768 resolutions. In this day of age most people have 1280x1024 on their monitors. And almost everyone needs to change the system settings! I can't believe that this isn't fixed yet. It seems like i should not be a impossible thing to correct.[/QUOTE]

WTF? I've got a 21 inch Samsung SyncMaster display on my Ubuntu box, and the last time I reinstalled, the installer set the resolution to 1600x1200, just like it's supposed to. If you're using a CRT display, however, perhaps X is underestimating the display's capability in order to avoid burning out the tube by accident.

---

### Post by Jason_25 on 2006-06-10
19/20 times ubuntu will make an intelligent decision regarding the screen resolution.  That's why there is no need for a graphical x config utility.  We already have one in the gnome screen resolution switcher, if that's your thing.  If you have an old CRT or graphics card which sends the wrong display information to x, then you probably know how to fix that yourself.

---

### Post by bruce89 on 2006-06-10
[QUOTE=Stormy Eyes]WTF? I've got a 21 inch Samsung SyncMaster display on my Ubuntu box, and the last time I reinstalled, the installer set the resolution to 1600x1200, just like it's supposed to. If you're using a CRT display, however, perhaps X is underestimating the display's capability in order to avoid burning out the tube by accident.[/QUOTE]
I have a Samsung SyncMaster 730BF (17 inch), and it defaults to 1024x768, where it should be 1280x1024.

---

### Post by sophtpaw on 2006-06-10
Dapper has really sucked when it comes to screen configuration.

I've installed Dapper twice as ubuntu and once as kubuntu and each time the screen resolution comes up at 1600x1200, which means i can hardly see anything on the monitor. 

that is fine, but when i go to System/Preferences/ScreenResolution and change it *whatever* the changes don't hold!

Now why have the screenresolution option if it doesn't work?

I end up having to dpkg reconfigure-xserver (or whatever) now, as a newbie and Linux delinquent that is not something i like messing with.

I just felt like saying this, because there are alot of you who gonna say how it 'just works' and 'you don't have a problem' 

Good for you! but that doesn't mean there ain't none

Sorry, i do love Ubuntu otherwise:D

---

### Post by Jason_25 on 2006-06-10
Isn't that more of a problem with your monitor?  If the edid says it supports 1600x1200 but is not clear at that resolution then I would say so.

---

### Post by Osamabingandhi on 2006-06-22
Ubuntu desperatly need a screen-configuration tool. 

*If you have two monitors and want to use both of them in twinview. *

*If you want to change your monitor refresh rates (i have tried to make my lcd 17 inch VP171s Viewsonic have the right refresh rates with no luck...)Best way for this would be to use the windows driver for my monitor so i know that all is right.

*change resolutions

To go into a textfile to change settings is not a good idea for beginners or if you want to make it fast. Big chance you break the system...and to know how to get the right information to make the right changes and even how to start making the changes.](*,) 

Twinview doesn't work by default and more and more people are using this especially when htpc and lcd tv's are more and more popular.

---

### Post by joe_lace on 2006-06-22
A couple of days ago I installed ubuntu, my first time ever using a Linux distro. I had resolution problems but it took me a total of 30 min. to find and implement a solution so I'm not too worried about it.

---

### Post by darkalemonkey on 2006-06-23
I am a complete newbie and am having problems with the screen resolution issues and not sure how to fix.  I've gotten close to ](*,)  and quittin'.   

I can tell that my new install of edubuntu is working and even getting on line, but I can't fully read the monitor (everything is uber-stretched).    I'll keep pluggin and trying till I figure it out.  Probably need specific video drivers for my ATI card, but its flippin impossible for me to install those without being able to see my desktop! 

I doubt that most folks like me trying to wake up from the windoze would have enough patience.  If umbuntu is to be used by a wider market, I agree that this issue should be addressed.

In my case, I am lucky enough to already have friends who are willing to help me trouble shoot.

cheers

---

### Post by jonrkc on 2006-07-08
> **WildTangent said:**
> In order to use higher res's, one must know the horizontal and vertical refresh rates for their monitor if it's a CRT (this doesn't apply to LCDs, they're almost always autodetected correctly.). Sometimes, you get lucky and get the full res capable right away, sometimes you need to do some research and then edit your xorg.conf.

-Wild
"Almost" is the keyword here.  My LCD monitor's refresh rate wasn't detected correctly; luckily I know enough from three years' use of Linux distros that I was able to fix the problem, but I pity the unfamiliar user's predicament when something like that happens.

It's not the fault of Ubuntu, however; it just seems to me that xorg has not come fully up-to-date.  Or is it a kernel issue?  Anyway, it can be very discouraging for someone with no prior troubleshooting experience and no knowledge of how to change this or that essential file, such as xorg.conf.

There used to be a good configuration tool available; I think it was called xorgconfig.  I noted in a Google search that many people are puzzled by its disappearance from various distros.

---

