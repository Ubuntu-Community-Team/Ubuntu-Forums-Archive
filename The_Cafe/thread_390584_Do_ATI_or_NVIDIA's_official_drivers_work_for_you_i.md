---
title: "Do ATI or NVIDIA's official drivers work for you in Ubuntu 6.10(Edgy)"
date: 2007-03-22
forum: The Cafe
---

### Post by TLE on 2007-03-22
[SIZE="2"]Do ATI or NVIDIA's official drivers work for you in Ubuntu 6.10(Edgy)[/SIZE]

[SIZE="2"]Hey everybody.
*Utilizing the 3D acceleration* on those fancy graphics cards people have seems to be one of the things that give 
people a *lot of trouble*, and therefore is also enveloped in a lot of rumors about what works and what don't. The *purpose of this poll is* to try to shed some light on this through *statistics*.


In order to make this as *fair and useable a result* as possible, please try to conform to the following guidelines

[LIST=1]
[*]Vote only if your situation accurately fits one of the options.

[*]**( * NOTE from poll options * )** When you evaluate how fast the acceleration work please remember, that if you are running games designed for Windows through Wine or Cedega, you are in fact running a "translation" layer in between the game and your system, that is bound to use some resources and therefore you cannot necessarily expect the same speed as you get with the same system and the same game in Windows. Furthermore, if the 3D acceleration is very slow, giving real low (depending on your hardware of course) frame rates in `glxgears -printfps`, then your 3D rendering is probably not hardware accelerated at all and you should choose the "...DO NOT..." option instead of the "...DO give me 3D acceleration. It is slower..." option.

[*]If you reply "...DO NOT..." please be as sure as you can that it is not the application you use (Wine/Cedega or various games) but in fact the graphics drivers that are to blame. This can be investigated by gathering info on whether that particular application works for other people and if you did what you could to set it up right.

[*]The poll options do not include any info on how easy or difficult it was to make it work. This is on purpose, as it would make it far to complicated to include all the different permutations of that also. To sum up, easy of installation might be the subject of another poll but not this one.
[/LIST]

This poll is for Ubuntu 6.10(Edgy) only. The reason for doing it now (right before Ubuntu 6.10(Edgy)'s successor is released) is that now everybody has had a chance to try and make it work, and in fact, if you have been working on it since the release of Ubuntu 6.10(Edgy) and it still doesn't work, then it probably won't at all ;)

I will make more of these polls in the future, regularly right before every release to track the development of this issue. If sufficiently many people vote in order for it to be a sound statistical base (maybe ~100), I'll forward the result to NVIDIA and ATI for them to use as they see fit.

**[SIZE="4"]Please also make a post[/SIZE]** describing you experience with these official drivers and what card you have.

Let's keep those votes coming
Regards TLE[/SIZE]

[SIZE="1"]PS: Regarding the formulation of the options. There are, off course, a lot of ways to define the categories for this poll. I have done everything that I can, to ensure that these categories are as clear and unambiguous as possible. I have additionally discussed the formulation with several other people (Thank you AskHL, Genrij, tseliot) before posting to try and ensure this. Therefore, if you have questions about the boundaries in the definitions, please post in this thread, but if you think they are inconsistent, please PM me instead since formulation-discussions, whether the critique is valid or not, tend to kill polls very quickly.

PPS: There are a lot of subjects related to this one that often initiate discussion: "How Wine works, what Wine is and is not", "ideological discussions about Wine vs. Cedega". Please make those discussion elsewhere and keep the posts here related to the subject.[/SIZE]

---

### Post by Spr0k3t on 2007-03-22
**Hardware:**
Motherboard: Foxconn C51XEM2AA-8EKRS2H
Video: Foxconn FV-N79GM2D2-HPOC (7950GT)
Processor: AMD FX64 X2 3800
Memory: 2GB
Displays: 2x Sceptre Naga 20w wide

**System:**
Ubuntu 6.10 (Edgy Eft) x86_64

**Personal Feedback:**
Both monitors are connected to the graphics card.  As a novice in Linux, it was not a simple task to locate and configure the twinview options.  I knew it was possible and used the guide written by PriceChild to get it working.  Later I changed over to the Envy script after the kernel updated to rev 11.  I still know how to recompile the kernel module by hand but it wasn't easy on a first time out without a second computer to get to the internet.  Once I finished the install of the official drivers from nVidia, everything was absolutely smooth.  3D applications ran like glass... no flickering, full double-wide screen 3D effects were stunning.  If the problems with the kernel modules needing to be recompiled into the kernel can be overcome, the method of installing the drivers into the system will be perfect.

---

### Post by SishGupta on 2007-03-22
Hardware:
Motherboard: ASROCK 775 Dual VSTA
Video: XFX NVidia 6200 256mb DDR2
Processor: Core 2 Duo @ 1.83Ghz (E6300)
Memory: 768MB DDR PC2100 (LOL, SO OLD)
Displays: 19 inch NEC LCD

System:
Ubuntu 6.10/7.04

Personal Feedback:
I use NVidia's official drivers with the Official installer. No problems whatsoever.
Accel is  fast. I get 100+ fps in steam and that is through the compatibility layer. Also my quake3 fps is up to par with windows. I also use beryl and it is smooth as butter.
When i want to watch movies on my tv i use xinerama. The way I enable my TV sucks though, I swap my hand made xorg.conf out with another xorg.conf set up for the TV and Monitor and then I restart GDM. That works well enough.

---

### Post by TLE on 2007-03-22
I've got an ATI X800XL and it have never really worked allright. I have 3D-acc but in certain games it is flawed and in others it simply doesn't work

---

### Post by AskHL on 2007-04-09
My ATI Radeon Mobility 9700 works MUCH better than last time, so thanks to the developers for that. However there are still graphical errors in some cases that are quite bad visually so it's still "not working" for me. It's a bit difficult to see the extent of the problems - some programs are unaffected.

---

### Post by jimrz on 2007-04-09
Perhaps you should have allowed mulitple answers. Many of us have more than one machine with different cards.

My laptop's ATI Radeon 9600 mobility 128Mb card is not supported by the official ATI driver, so that is how I answered the poll. However, the "ati" driver in the kernel does give me some 3d accel, not as fast as in win but sufficient to what I use the box for. 

Additionally, have 2 desktops with Nvidia that do get nice performance from the official drivers.  + a way older laptop that is hopeless for 3d no matter what is installed, but I like it so I still keep it going, and it is running edgy very nicely.

---

### Post by Polygon on 2007-04-10
i voted flawless ati support. the drivers work, dont crash xorg and ive played unreal tournament 2004 demo flawlessly (and faster + better then in windows!)

i have an ati radeon 9800 128mb

---

### Post by igknighted on 2007-04-10
Voted ATI works perfectly on my x800GTO.  Also have an Nvidia card where the drivers work fine but are slightly more finicky.  I think the ATI drivers have two advantages over nvidia: 1)ATI drivers have a gui install, no need to drop to runlevel 3; and 2) if you change kernel, X wont crash out like nvidia does.  That said, the nvidia drivers support composite so they can run things like beryl and Xfce's neat compositing tricks natively.  So both have their pluses and minuses.

Overall, they are still both binary blobs, and every effort should be made to force both companies to open their drivers.  Even if they work, a binary blob is a binary blob, and this is not an acceptable solution in the long run.

---

### Post by samjh on 2007-04-10
nVidia 7600GT

Yes, the official drivers give me fast and flawless 3D acceleration.  No problems so far, at all.

It was also easy to configure, I just get the package from synaptic, and change the display driver to "nvidia" in conf.

---

### Post by beefcurry on 2007-04-10
nVidia 6600GT

Never had much of a problem with the drivers (except problems when upgrading X and the Kernel)

---

### Post by sunexplodes on 2007-04-10
Yeah. Been using the official nVidia drivers with my FX5500, and i've never hard a problem of any kind. I don't do much gaming, but what I have done has been quite enjoyable.

---

### Post by jiminycricket on 2007-04-10
They work, but I hate  Nvidia's drivers.  They have horrible bugs with Compiz and Beryl, so that you have to change the "rendering path" to the slow "copy" instead of pixmap from texture.  They have weird glitches with beryl.  Twinview is a very stupid multi-monitor program (gnome-panel goes across the two screens, maximize opens the window in both monitors, windows  and dialogs pop up in the middle of the two screens so the're half in one and half in the other), which you might expect from a video driver trying to manage monitors for some reason..  The free X.org drivers for ATI and Intel worked out of the box on all my computers, where Nvidia is a hassle.  And not to mention that they violate the copyrights of the kernel developers, but I don't want to get into that here...

Also they love to drop cards into the "legacy" bin, as they [did just recently to most current cards]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html").  So when the free [Nouveau drivers]("http://nouveau.freedesktop.org/")come along, I will say bye bye to Nvidia's proprietary crap.

I can't even get ATI's fglrx to work on my card, but the open source drivers worked perfectly and out of the box--it was so easy.

---

### Post by neighborlee on 2007-04-11
nVidia 6800XT

Yes, the official drivers give me fast and flawless 3D acceleration. No problems so far, at all hjere either.

It was also easy to configure, I just added driver from restricted menu and voila ,no tinkering needed...

so why is ubuntu sponsoring nouveau ? :)

cheers
nl

---

### Post by daynah on 2007-04-11
I was able to boot using ATI's official drivers, but my computer would freeze every 10 minutes or so, so I voted that they didn't work at all. If I had voted that "they don't give me 3D-acc. or the graphics is flawed," it would have given the drivers too much props. When I could use my computer, I had graphics full. But I couldn't use my computer that often.

I've switched to nvidia. I dunno what feisty set up for me, but it's workin' great, with Beryl. ~cheesy commericial smile~

---

### Post by mstlyevil on 2007-04-11
Nvidia drivers have worked on both my 6600GT and 7600GT flawlessly . I junked my Radeon card shortly after installing Linux because of it's poor performance with the fglrx drivers.

Playing Doom3 on Linux performed just as well as playing it on Windows at the same settings with Nvidia.

---

### Post by FuturePilot on 2007-04-11
The Nvidia drivers work great for my GeForce 2 Go. Though the card itself is not that great of a card, it pretty much chokes on Beryl. But the appearance  and performance is greatly improved by the drivers.

---

### Post by hardyn on 2007-04-11
This poll is quite desktop oriented... i have run both nvidia, and ati based notebooks, and i have had good 2d and 3d performance from both... BUT... neither driver will hibernate or suspend worth a damn.  neither driver will 'really' underclock.

from that experience, i would say that neither are good, but i am certainly glad to be off ATI, as the nvidia driver is much better.  I am grateful that both companies offer drivers period... i know it wouldn't hurt them any to not make them at all (and they know that, i think that accounts for alot of the substandard driver support)

ps. i have my xbox360/ati conspiracy theories as well... but that is another thread.

---

### Post by mstlyevil on 2007-04-11
The best overall graphics experience in Linux would using a Intel solution. As long as your 3d needs are not massive you can not go wrong with Intel.

---

### Post by yatt on 2007-04-11
I am stuck with the fglrx driver. It is very slow (on phoronix, they compared nvidia and ati cards that performed similarly on Windows and found the ati cards are half as fast on average). It is also missing support for various things. The Cataylist Control Center in the newest driver is nice, but the kernel module will not compile unless I use an official repo kernel, so I am still using an old version of the driver.

---

### Post by yatt on 2007-04-11
> **mstlyevil said:**
> The best overall graphics experience in Linux would using a Intel solution. As long as your 3d needs are not massive you can not go wrong with Intel.
I've read somewhere that they are planning to do discrete graphics. The cards would basically be any array of there onboard chips with their own RAM. I think they are expected late 2008.

---

### Post by mstlyevil on 2007-04-11
> **yatt said:**
> I've read somewhere that they are planning to do discrete graphics. The cards would basically be any array of there onboard chips with their own RAM. I think they are expected late 2008.

They have not made it official but Intel just hired a bunch of new engineers for their graphics division. Amd's merger with ATI and the CPU/GPU combo has forced their hand.

---

### Post by Extreme Coder on 2007-04-11
> **yatt said:**
> I am stuck with the fglrx driver. It is very slow (on phoronix, they compared nvidia and ati cards that performed similarly on Windows and found the ati cards are half as fast on average). It is also missing support for various things. The Cataylist Control Center in the newest driver is nice, but the kernel module will not compile unless I use an official repo kernel, so I am still using an old version of the driver.
Could you plz link to that article on phoronix? Thanks.

Back on topic, I've managed a few months ago to make fglrx work with my ATI RADEON 9200 SE on Edgy, and while there was a speed improvement on the open-source driver, it wasn't enough to convince me to use an old un-updated driver.

---

### Post by TLE on 2007-04-18
Thanks for your replies so far. Let's get a few more.

---

### Post by hasplu on 2007-04-18
GeForce Go 7400 with the original 2.6.17-10-generic works fine, after the upgrade to 2.6.17-11 can't start at all and the X crashes...both kernels look the same, but......:(

---

