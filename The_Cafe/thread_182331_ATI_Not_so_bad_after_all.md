---
title: "ATI: Not so bad after all?"
date: 2006-05-25
forum: The Cafe
---

### Post by jdong on 2006-05-25
As some of you know, I've recently purchased a laptop that contained an ATI video card (Mobility Radeon X1400). I knew what I could've been getting myself into, but the deal ($1100 for a Core Duo and 1GB RAM) was just too good to resist. Plus, my other option for nearly the same price was an Intel GMA950, and I decided that I'd try my luck with ATI.

To make a long story  short, I've had a **VERY** smooth ride with fglrx... in some ways smoother than NVidia drivers. ATI was certainly terrible at supporting Linux a year or two ago, but I would go as far as saying that they've made a complete turnaround and are doing a great job at supporting Linux.


First of all, their installer... **I love it!** It's GUI, so friendly for the 'average user'. It is also capable of generating distro-specific packages (such as debs for Ubuntu or RPMs for SUSE, and so on) for 20+ distro flavors, and they definitely work. The Ubuntu deb generator makes debs that integrate tightly with Ubuntu and safely upgrade the pre-shipped fglrx implementation easily (there's an ATI howto on the wiki that explains this process in a bit more detail. It requires an additional module-assistant command to build the module and install it)

Secondly, ATI's been keeping up recently with nice monthly updates that are speedy at resolving problems. 8.24, which had problems with hanging if you switch from X to console to X too quickly, was followed this month by 8.25 which resolved all these problems. Last release didn't support TV-Out on my chipset yet, while this release added it.

Third, ATI drivers have quite a number of nifty features. For me, frequency scaling on the GPU is very important -- sometimes adding an extra hour of battery life (if I'm doing very light work). ATI's PowerPlay works fine under Linux, while NVidia has yet to support PowerMizer under Linux. Also, the aticonfig tool is _great_ for helping me generate and customize xorg.conf files (i.e. one-command dual head setup) not to mention the ability to apply some settings on the fly. (i.e. dynamically enable/disable TV-Out and VGA out, swap primary/secondary devices, etc)


Perhaps it's time to drop the overall stereotype that ATI sucks under Linux? What do you guys think?

---

### Post by khightower on 2006-05-25
Thanks for the review. I think I will no longer be afriad to try or recommend a laptop using that GPU. I will look more into ATI and Linux.

---

### Post by Jason_25 on 2006-05-25
So what games have you played with it?  Many graphical artifacts?  This is a big problem with the ubuntu-shipped driver.

Does wine/cedega work well?  Last time I tried on ATI no games worked.

Is XGL perfectly fast?  It is on nvidia.  On the ATI cards I've tried it's slow and crashes alot.

Have you used s-video?  With it, and the ubuntu-supplied driver I get a distorted screen on virtual terminals and bootup and shutdown.

Also, I have yet to hear from anyone with ATI that has a working HDTV setup.  Everyday, I use one of my PCs connected with DVI to my HDTV on 480p and 720p.

---

### Post by jdong on 2006-05-25
[QUOTE=Jason_25]So what games have you played with it?  Many graphical artifacts?  This is a big problem with the ubuntu-shipped driver.
[/quote]
I basically only play UT2004, and I haven't had any artifacts or problems running at native 1280x800 with all details on high.

> 
Does wine/cedega work well?  Last time I tried on ATI no games worked.

I've played Starcraft under Wine, and it does fine...

> 
Is XGL perfectly fast?  It is on nvidia.  On the ATI cards I've tried it's slow and crashes alot.

Good question, I haven't tried that yet. When I get some free time to fool around, I'll play with Xgl. Xgl is not too important to me, and a lot of the features it relies upon are still experimental in nature, so I'm not surprised if any driver's support for it is spotty.

> 
Have you used s-video?  With it, and the ubuntu-supplied driver I get a distorted screen on virtual terminals and bootup and shutdown.
Another good question. I've only messed with S-Video inside X, and it does fine. I've seen cases where if I boot up with a VGA cable attached, the BIOS will connect the primary display to the VGA port instead of the panel, and there'd be no console at the panel.... I'm still messing with BIOS settings regarding that, but that's not a fglrx problem as much as it's a BIOS and/or kernel problem.

---

### Post by Jason_25 on 2006-05-25
I wonder if something that uses direct3d/opengl will work with cedega/wine on ati though.  Starcraft uses directdraw I think.  It can even be played in an emulator.

XGL/compiz support for Nvidia may be less than perfect but to me, it's hard to tell.

My parents have a HTPC that I built for them with a fanless 9600.  S-video is the only thing hooked up.  So you can see how important it is to have it working on all the screens. I've been running dapper on it anyway, but maybe I will try the newest driver with it soon.

---

### Post by halfvolle melk on 2006-05-25
Installation is a great. However, from what I gather, it's either composit or DRI. Not sure what that means but you either get direct rendering or get to play with Compiz or I'm wrong.

---

### Post by jdong on 2006-05-25
[QUOTE=halfvolle melk]Installation is a great. However, from what I gather, it's either composit or DRI. Not sure what that means but you either get direct rendering or get to play with Compiz or I'm wrong.[/QUOTE]
Last time I messed with compiz/Xgl on my NVidia card, I also was unable to get opengl apps _inside_ an Xgl session to be accelerated well.... glxgears sucked, and games (even simple ones) were unplayable, and I was forced to do those things on a separate terminal.

---

### Post by towsonu2003 on 2006-05-25
sorry, I wouldn't really post, but my disgust with ati is just too strong. they cannot code, and when they do, they are unwilling to code...

I mean, I'm using some **3-4** years-old ati mobility radeon 9000 (128MB Video RAM) on my laptop, and their crappy drivers tells me (in Xorg.0.log) "yo, your shit is not supported by the driver your MANUFACTURER wrote for you!". So I go complain to their site, and they say "shut up and **** off, we pity you the linux user"... Never using those terms of course... :rolleyes: 

They are not able to do stuff adequately, they are not willing to admit that, they are not friendly at all, and I will never ever buy crap from them until I get some sense of capability out of what they're doing... It's a pity HP (my laptop is an HP Pavilion ZV5120us) likes ATI instead of NVIDIA... 

The result of my unresearched laptop buy: having ~150 fps with fglrx, ~500 fps with open source ati/radeon drivers. My Dapper? Slow like a 1968 VW Beetle...

---

### Post by jdong on 2006-05-25
Interesting... so perhaps their support is somewhat spotty... I'm fairly content with the performance of my X1400... especially for a laptop. I also find that at some desktop drawing tasks (such as flipping tabs in FF that contain flash and other multimedia content), this ATI feels a bit more responsive than my nvidia, though that could just be the Core Duo processor owning my Athlon64....

---

### Post by towsonu2003 on 2006-05-25
[QUOTE=jdong]I also find that at some desktop drawing tasks (such as flipping tabs in FF that contain flash and other multimedia content), this ATI feels a bit more responsive than my nvidia, though that could just be the Core Duo processor owning my Athlon64....[/QUOTE]
if you're using the right kernel than it's (almost) definitely the dual core making up for ATI... On my one-cpu'ed & ati'ed laptop, even Swiftfox is using 60-80% CPU on average when browsing... But I'm not very objective of course. 

Anyway, you're either very lucky and the driver properly supports your video card, or you are an excellent researcher (and found an ATI that has good driver support)... or start worshipping your dual core ;)

---

### Post by jdong on 2006-05-25
Well, browsing is definitely CPU-limited, and for one reason or another it always seems like Intel chips have an edge in stuff like Firefox rendering (don't shoot -- I'm an AMD fan too.... I own two Athlon64 boxes), but yeah, Firefox is heavy on CPU and Swiftfox is no magic fix-all. But GPU limited 2D tasks, like swapping between two desktops, flipping between two tabs, etc, seem to redraw faster with my ATI card.... Of course, this is also a pretty crude statement.


I definitely researched chipsets and everything with my purchase, even bugging #ubuntu-devel for fglrx and ipw3945 inclusions before making my purchase decision. So perhaps I did get lucky...

Either way, my bottom line is that I am definitely rethinking what I say about ATI from here on, and will definitely be a bit more open-minded, trying to find both sides of the ATI story...

---

