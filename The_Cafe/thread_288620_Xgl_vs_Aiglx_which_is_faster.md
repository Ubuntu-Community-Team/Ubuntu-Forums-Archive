---
title: "Xgl vs Aiglx: which is faster?"
date: 2006-10-30
forum: The Cafe
---

### Post by elettronicha on 2006-10-30
In your opinion or feelings, which is faster or flowing between Xgl and Aiglx (both with Beryl or with Compiz)?
Please report your video card, too.

---

### Post by firetux on 2006-10-30
Aiglx generally is faster. The overall design is better too, and it is included in xorg 7.1.

---

### Post by mushroom on 2006-10-30
If you're using NVidia, stick with XGL. The beta drivers are ridiculously slow.

---

### Post by woedend on 2006-10-30
uh...what exactly do you base this statement on?  Beta drivers are not slow here...
and don't stick with XGL in any case, it was meant as a temporary hack of sorts(which  ifeel bad for saying, as it did A LOT for graphics)

---

### Post by elettronicha on 2006-10-30
As far as I know, technically:

1.
-Xgl is a **Xorg fork**, which replaces the whole X server
-Aiglx is a **Xorg extension** and can be (un)loaded as your wishes

2.
-Xgl is supported by **Novell**
-Aiglx is supported by **everyone**

3.
-Xgl delegates some functions to **Mesa libraries** and doesn't require drivers (often proprietary) supporting specific extensions
-Aiglx delegates everything to **drivers**, so driver and video card role are central matters

4.
-Xgl runs **upon a runnign X server**, so two graphical servers are running in the same moment
-Aiglx is a **simple extension** and doesn't weigh down X

---

### Post by blitzer on 2006-10-30
Hello,

Can't seem to get beryl running at the moment (it was sporadic in Dapper)causing 100% cpu usage when launched from sessions on startup.  I have to shut down the process then nav to the folder and launch it to no avail.  I have noticed that emerald didn't download or install.  I used this How to: [URL="http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/AiGLX"]Install/Ubuntu/Edgy/AiGLX
[/URL]

I will try and use the repos to download and install unless someone has a better way :-k

---

### Post by chaosgeisterchen on 2006-10-30
> **mushroom said:**
> If you're using NVidia, stick with XGL. The beta drivers are ridiculously slow.

The run very fast with most of the people.

---

### Post by oblivion on 2006-10-30
I'm on a nvidia FX 5900 card using beryl, and Xgl was running so much faster and smoother on my pc. Aiglx is so _very_ badly sluggish at times that i don't think it's usable at all on my system.

---

### Post by maniacmusician on 2006-10-30
that's because drivers for linux are crap. With XGL, the XGL part is doing much of the stuff that the graphics driver is supposed to be doing. AIGLX assumes that drivers actually work and relies on them to do things properly.

---

### Post by spockrock on 2006-10-30
I use beryl, with the beta nvidia drivers.  Runs perfectly smooth except for the occasional black window, on two computers, on both the low end system I get better performance on the new system umm, I cant really tell the difference, but I get better memory usage and better cpu usage.

System 1:
P4 1.4 w/ 256 MB of rdram 
Edgy, Xubuntu
Nvidia FX 5600
1600x1200

sufficed to say Beryl and the nvidia driver runs better on dapper xubuntu with xgl and compiz-quinn.

System 2:
AMD X2 3800+ @2.6GHZ
2GB of DDR520
Edgy, Ubuntu
7800 GT
3200x1200 AA:0x AF: 1x

Noticeably the system compared to xgl and the beta nvidia driver, is as follows, uses 200MB less of ram.  Video playback, with XGL my system played video back perfectly but at 60% on overall usage, with the beta driver around 10%, with perfect video playback.

Granted these were hardly scientific, but if anyone wants I am willing to run xgl or no xgl and give you hard benchmarks, frame rates, memory usage, video playback if you like.

-edit- I have never run aiglx I am comparing my experience with xgl and nvidia beta drivers.

---

### Post by darkhatter on 2006-10-30
just get a nvidia card and don't use Xgl or aiglx :D

---

### Post by spockrock on 2006-10-30
> **darkhatter said:**
> just get a nvidia card and don't use Xgl or aiglx :D

QFT

---

### Post by greggh on 2006-10-30
> **darkhatter said:**
> just get a nvidia card and don't use Xgl or aiglx :D

Huh?

---

### Post by darkhatter on 2006-10-30
if you have a Nvidia card you can run beryl with out using Xgl or Aiglx. That has nothing to do with the thread, but I love looking at my avatar so I like to post random jazz :-D

---

### Post by woedend on 2006-10-30
er...with the nvidia drivers, you are still using AIGLX.
it was merged into xorg 7.1.

---

### Post by darkhatter on 2006-10-30
I thought it didn't....guess I'm wrong

---

### Post by spockrock on 2006-10-30
yes it was merged into xorg 7.1 however I believe, in your xorg.conf you have to enable aiglx.  The nvidia driver adds GLX_EXT_texture_from_pixmap, which allows beryl or compiz to run without aiglx or xgl.

plx correct me if I am wrong.

---

### Post by Cynical on 2006-10-30
No, aiglx is enabled by default and what nvidia added was required for any compositing manager to work with aiglx, since it depends on driver support. An easy way to remember is just to think of what aiglx stands for, Accelerated Indirect GLX. 

And I wouldn't call XGL a hack, usually that implies that it was simple or dirty. Though it is just temporary. From the wikipedia article,

[quote=Wikipedia]Xegl

Xegl is the future of Xgl and a long term goal of X server development. The Xegl server will share much of the drawing code with the Xglx server, except that the initialization of the OpenGL drawable and context management is handled by the Embedded GL specification, referred to as EGL API. The current implementation uses Mesa-solo to provide OpenGL rendering directly to the Linux framebuffer or DRI to the graphics hardware. As of August 2005 Xegl can only be run using Radeon R200 graphics hardware and development has currently been delayed. It is likely that it will remain so until the Xglx server has proven itself and the closed source drivers add support for the EGL API, in which case it should be a transparent replacement for the nested Xglx server.[/quote]

---

### Post by spockrock on 2006-10-31
ok I stand corrected....thanks.... well then I prefer aiglx less resource intensive, but wouldn't mind giving xegl a whirl when its ready.

---

### Post by chaosgeisterchen on 2006-10-31
Hmh.. will we ever see XOrg version 8 ?

Or will XEGL1.0 be released before that..

---

### Post by mushroom on 2006-10-31
On my GeForce FX 5550 (128MB) using the beta drivers, AIGLX wasn't necessarily slow as much as it was choppy. Using XGL without the beta drivers it's the same speed, but it runs much more smoothly. That was my experience, anyway.

---

### Post by elettronicha on 2006-10-31
I'm on an ATI mobility radeon 9700 using the open source 'radeon' driver and installed AIGLX + Beryl. 
I find the system is quite responsive in animations, and all that stuff provided by Beryl, when using both aiglx and beryl (though obviously system is much faster with common X server + common KDE window manager Kwin), but is a bit sluggish when for example I scroll web pages.
May I need to modify something more in xorg.conf?

Never used Xgl.

---

### Post by nbound on 2006-10-31
AIGLX runs awesomely on my nvidia 6600 DDR2 512MB :D

---

### Post by DJ Wings on 2006-10-31
Where can I download a copy of AIGLX? Where's the repository? I know Ubuntu's repositories have XGL, but I've decided to switch.

---

### Post by nbound on 2006-10-31
Its part of xorg 7.1 so if your running edgy (which you are) you already have it :D

---

### Post by elettronicha on 2006-10-31
Are Beryl and Compiz quite similar in perfomances?

---

### Post by woedend on 2006-10-31
compiz vanilla will appear much faster,initially at least, at least to me.  but thats because beryl is a juggernaut with everything enabled.

---

### Post by user1397 on 2006-10-31
On edgy, I installed XGL + Beryl using this guide: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

and I enabled my ati fglrx driver before that using this guide: [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by elettronicha on 2006-11-01
What card do you have? And are you satisfied of system performances with Beryl?

---

### Post by chaosgeisterchen on 2006-11-01
AIGLX runs quite smooth here but XGL ran much smoother before that.

---

### Post by user1397 on 2006-11-01
> **elettronicha said:**
> What card do you have? And are you satisfied of system performances with Beryl?if you mean me, i have an ati radeon x1600 pro 512 mb agp card.  beryl runs very smoothly here, and its fast, until i start going crazy with the water effects.

---

### Post by bruce89 on 2006-11-01
> Xgl vs Aiglx: which is faster?

The question shouldn't be which is faster, but which is better.

AIGLX wins, as it is in X.org now, and isn't a hack.  Also DRI works with AIGLX (in other words 3D apps will work at the same time as Beryl et al.)

---

### Post by chaosgeisterchen on 2006-11-01
AIGLX has proven superiority.

---

### Post by toallpointswest on 2006-11-02
Have to say that I'm impressed with AIGLX/Beryl. I'm running it on a Duron 1.3GHz, 1.5GB SDRAM, an ATI Radeon 64 VIVO (7200 series chipset), and the opensource Radeon driver and it's very smooth. From the menus wiggle/fading in and out, to the transparency, and even the desktop switching..smooth as silk. My only problem is that X freezes when I try to log out, but I havent' troubleshot that error yet.

---

### Post by xdevnull on 2006-11-04
I ran xgl/compiz on my averatec 1050 with a intel 855GM card when it first became available in Suse 10.1.  It was reasonably quick, but the install was messy and I had a lot of gnome/kde weirdness.  

I just installed Edgy, and am enjoying it and would like to give the latest stuff a whirl so my question is:

Should I use aiglx instead, since the intel drivers are probably well supported?  Will that likely be as fast/faster?

Also - should I use compiz or beryl?  I enjoyed compiz (except that you couldn't shade windows), but I don't know much about beryl.  Also, I don't want to run all the effects one might try on a desktop.  Wobbly windows are okay, but I'm more interested in the transparancy, cube and app switcher.

Thanks

---

### Post by steveneddy on 2006-11-04
I like XGL - no problems here.

nVidia GeForce 5200, beryl....I guess all this is in my sig.

-SE

**EDIT**
For those of you keeping score at home, this was my 100th post.

---

### Post by joshuapurcell on 2006-11-07
The only one I've tried is XGL, but it was when it first came out. I wonder how much of an affect (if any) the recent Novell/Microsoft agreements will have on people's decision between these two technologies.

I personally was leaning towards AIGLX anyway because of the integration with the already-existing X.org project, and now that this MS/Novell deal has been announced I'm leaning in that direction even more.

By the way, Beryl looks great... can't wait to try it out when I get my next computer.

---

### Post by songochain on 2007-01-06
> **elettronicha said:**
> I'm on an ATI mobility radeon 9700 using the open source 'radeon' driver and installed AIGLX + Beryl. 
I find the system is quite responsive in animations, and all that stuff provided by Beryl, when using both aiglx and beryl (though obviously system is much faster with common X server + common KDE window manager Kwin), but is a bit sluggish when for example I scroll web pages.
May I need to modify something more in xorg.conf?

Never used Xgl.

I cant use open source radeon driver because cpu fan is always 100% (in my laptop). How do u get work aiglx with your 9700??

---

