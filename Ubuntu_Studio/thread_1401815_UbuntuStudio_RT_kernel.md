---
title: "UbuntuStudio RT kernel"
date: 2010-02-08
forum: Ubuntu Studio
---

### Post by marin123 on 2010-02-08
i was wondering how to get my ubuntu karmic on realtime kernel (the kernel that is used by ubuntu studio)...

where can i download it? 
any way to get it in update manager or will i have to compile it by myself?

---

### Post by jocampo on 2010-02-08
> **marin123 said:**
> i was wondering how to get my ubuntu karmic on realtime kernel (the kernel that is used by ubuntu studio)...

where can i download it? 
any way to get it in update manager or will i have to compile it by myself?

Please take a look here: [https://help.ubuntu.com/community/UbuntuStudioPreparation]("https://help.ubuntu.com/community/UbuntuStudioPreparation")

but I do not recommend it. I think is better install Ubuntu Studio as dual boot or on a complete different PC. I am running my Ubuntu Studio as dual boot with Jaunty and have no issues.

A PC with a powerful CPU and lot of RAM helps a lot, by the way, so you can get the full advantage of the RT kernel.

---

### Post by marin123 on 2010-02-08
why dont you reccomend it? did you have bad experiences or you heard so? i want to run lmms (or fruity loops) without having to bother with pulseaudio and latencies...
i have core duo @1.73 GHz and 2 GB of ram memory with ati mobility radeon x1350 (128 MB), do you think thats powerful enough to run an RT kernel? And my sound card is intel ICH8 family? Is that ok?

---

### Post by viktormas on 2010-02-08
"..why dont you reccomend it? ..."
There are so many reasons why people actually create and bother at all with 'audio tuned' Distros, that books are written about it. 

Low audio latency, RT and all that are really complex issues and unless you know what you are doing you shouldn't even think of starting that way. What Jocampo suggests is true: either dual-boot or another computer are the best solutions. 

If you still want to get on with your idea, best is to install the whole Ubuntu Studio desktop, that is pre-tuned for audio using the following command:
sudo apt-get install ubuntustudio-desktop

That way, when you start your computer, you will have the option to choose between the RT or 'normal' kernel. 

I hope this helps.

---

### Post by marin123 on 2010-02-08
i wanted to just try out ubuntu studio without having to install it on a partition... i will try with idea of installing ubuntu desktop and choose on boot, just to see how it will cope with my computer...
if i like ubuntu studio i can do a fresh install, but do you recommend using it as a regular desktop for internet and 'usual stuff'?

---

### Post by AutoStatic on 2010-02-08
> **marin123 said:**
> i was wondering how to get my ubuntu karmic on realtime kernel (the kernel that is used by ubuntu studio)...

where can i download it? 
any way to get it in update manager or will i have to compile it by myself?Hello marin123, just open Synaptic, search for 'linux-rt', install it, reboot and select the 2.6.31-9-rt kernel.

---

### Post by AutoStatic on 2010-02-08
> **jocampo said:**
> but I do not recommend it. I think is better install Ubuntu Studio as dual boot or on a complete different PC. I am running my Ubuntu Studio as dual boot with Jaunty and have no issues.I do recommend it, of course you can install Ubuntu Studio on a different partition but personally I think this is a waste of time and a risk because repartioning could mess up your system also if you don't know what you're doing.

> **jocampo said:**
> A PC with a powerful CPU and lot of RAM helps a lot, by the way, so you can get the full advantage of the RT kernel.I use the RT kernel on a 1.2 Ghz netbook and run Hydrogen, LinuxSampler and other CPU hungry stuff on it with the onboard soundcard and it runs fine with a <10ms latency. It's the RT kernel that allows me to get the most out of my netbook, not the other way around.

---

### Post by AutoStatic on 2010-02-08
> **viktormas said:**
> "..why dont you reccomend it? ..."
There are so many reasons why people actually create and bother at all with 'audio tuned' Distros, that books are written about it. 

Low audio latency, RT and all that are really complex issues and unless you know what you are doing you shouldn't even think of starting that way. What Jocampo suggests is true: either dual-boot or another computer are the best solutions.With Ubuntu it's pretty straightforward I think. It's well documented and in this forum we're glad to help if you're running into trouble anyway.

---

### Post by marin123 on 2010-02-08
thanks to all of you guys, i did like autostatic said, installed just the kernel (thats what i wanted to do from the beginning) and now i'll see how it works...

one more question: if rt kernel gets most out of the system, why isnt it used in 'ordinary' distros like ubuntu, kubuntu etc
what are the downsides?

---

### Post by raboofje on 2010-02-08
> **marin123 said:**
> if rt kernel gets most out of the system, why isnt it used in 'ordinary' distros like ubuntu, kubuntu etc
what are the downsides?

2 reasons: First, there's some trade-off going on: some thoughput is sacrificed, overhead is introduced to achieve lower latencies. 

Secondly, the realtime changes were, certainly at first, a pretty racidal change in the way the Linux kernel works. Those needed to be tested, and prove themselves in practice without jeopardizing the stability of the 'normal' linux kernel. Over time, slowly and steadily more code originally vetted in the RT patchset made its way into the mainline kernel. Still, some improvements are being worked on and tested to get them into good enough shape to be included in the mainline kernel - if you want to take advantage of them now, you can by using the RT-patched kernel.

---

### Post by jocampo on 2010-02-08
> **AutoStatic said:**
> I do recommend it, of course you can install Ubuntu Studio on a different partition but personally I think this is a waste of time and a risk because repartioning could mess up your system also if you don't know what you're doing.

I use the RT kernel on a 1.2 Ghz netbook and run Hydrogen, LinuxSampler and other CPU hungry stuff on it with the onboard soundcard and it runs fine with a <10ms latency. It's the RT kernel that allows me to get the most out of my netbook, not the other way around.

I respect your opinion a lot! like other folks here who know you already ;-)  but to me, makes no sense install Ubuntu Studio on top of a regular Ubuntu Setup giving the case you can get the full/regular Studio version with all whistles and stuff  doing dual boot. If you are brave enough to upgrade your kernel to an RT version, why not setup a dual boot instead?

If you are serious about Music, Video, etc, better to install Ubuntu Studio from scratch. It will be a clean, nice installation which was originally designed and packaged that way for media users.

Now, the RT kernel will give you low latency but you will not get the same results if you use a crappy machine. Yeah, the kernel is RT but will run on top of hardware, no?

EDIT: forgot to mention ... the wifi driver issues ... not all wifi drivers work well on Studio and I can tell that by own experience. Mine works better on Karmic but on previous version I was not able to use my laptop wireless.

---

### Post by jocampo on 2010-02-08
> **marin123 said:**
> but do you recommend using it as a regular desktop for internet and 'usual stuff'?

No!

Ubuntu Studio is for high intense use of media, like video and music editing. The RT allow you low latency between your software and hardware, which is desire when you are recording music, for example, or using DJ consoles.

Because Ubuntu Studio is kind of specialized Ubuntu Distro, it is not recommended or oriented for just browsing internet. You will not give the RT kernel the proper usage. In other words, you will not browse internet faster because you're using Ubuntu Studio.

I would stay on regular Ubuntu Karmic or Jaunty if you just browse internet or use your PC for create documents. But, feel free to try if you want, america is a free country :-)

---

### Post by jocampo on 2010-02-08
--sorry, duplicate post, pls delete---

---

### Post by AutoStatic on 2010-02-09
> **jocampo said:**
> I respect your opinion a lot! like other folks here who know you already ;-)  but to me, makes no sense install Ubuntu Studio on top of a regular Ubuntu SetupI'm with you on that. I only use plain Ubuntu myself and install the stuff I need on top of it.

> **jocampo said:**
> ...giving the case you can get the full/regular Studio version with all whistles and stuff  doing dual boot. If you are brave enough to upgrade your kernel to an RT version, why not setup a dual boot instead?Because installing the RT kernel just takes a few clicks and installing a complete OS takes at least half an hour?

> **jocampo said:**
> If you are serious about Music, Video, etc, better to install Ubuntu Studio from scratch. It will be a clean, nice installation which was originally designed and packaged that way for media users.I tried it two times. And two times I lost a lot of time cleaning up my system because I don't do video and I don't use the majority of the music applications. So for me personally it's faster to install a plain Ubuntu and then install the things I need on top of it.

> **jocampo said:**
> Now, the RT kernel will give you low latency but you will not get the same results if you use a crappy machine. Yeah, the kernel is RT but will run on top of hardware, no?The more CPU and memory, the more you can get out of your machine of course. But like I said, the RT kernel helps me to get the most out of my machine, especially because it allows me to prioritise processes ([rtirq]("http://ubuntuforums.org/showthread.php?t=1328175")).

> **jocampo said:**
> EDIT: forgot to mention ... the wifi driver issues ... not all wifi drivers work well on Studio and I can tell that by own experience. Mine works better on Karmic but on previous version I was not able to use my laptop wireless.I use scripts to disable all services that might cause any unwanted overhead when making music. That includes things like ethernet, wireless and bluetooth. Besides, internet is a major distraction ;)

---

### Post by marin123 on 2010-02-09
> **jocampo said:**
> I respect your opinion a lot! like other folks here who know you already ;-)  but to me, makes no sense install Ubuntu Studio on top of a regular Ubuntu Setup giving the case you can get the full/regular Studio version with all whistles and stuff  doing dual boot. If you are brave enough to upgrade your kernel to an RT version, why not setup a dual boot instead?

If you are serious about Music, Video, etc, better to install Ubuntu Studio from scratch. It will be a clean, nice installation which was originally designed and packaged that way for media users.

Now, the RT kernel will give you low latency but you will not get the same results if you use a crappy machine. Yeah, the kernel is RT but will run on top of hardware, no?

EDIT: forgot to mention ... the wifi driver issues ... not all wifi drivers work well on Studio and I can tell that by own experience. Mine works better on Karmic but on previous version I was not able to use my laptop wireless.

i just want to use lmms without having issues like low latency, cracking sound etc, and i was hoping rt kernel would do the trick.. i just want to use LMMS, and i tried with rt kernel, and its better, but has some bugs (everything works fine and then i still get input from midi keyboard, but no sound), dont know is it kernel or program...
i thought about using ubuntu studio as my only linux distro, i would use it for music production and maybe just a little video and photo editing, but still want to use computer for browsing the web, chatting on im, burning cds, listening to mp3 etc... i guess i can do all this on ubuntu studio.. maybe i'll do a fresh install of ubuntu studio 10.04 (i just got this one the way i want it :) )...

---

### Post by markbuntu on 2010-02-12
I usually install ubuntu and then get the rt kernel and the ubuntustudio-audio packages. I started doing it this way because I had a lot of problems with getting the rt kernel to work on my machines with interpid and jaunty If you install just ubuntustudio you get no generic kernel to fall back to if the rt kernel does not work so it ended up being a huge waste of time downloading the dvd and then trying to install it.

btw, karmic is the first ubuntu distro since hardy that has an rt kernel that works for me.

Some of the rt patches will be in the .33 kernel but the various distribution kernel packagers usually mess with the scheduling and other stuff and that tends to make the rt patches in the kernel work at less than optimum. There is more to rt than just a few patches and optimized rt kernels will be a necessity for a good while going forward. 

There are a lot of services that could be eliminated and modules stripped out if one wanted a small fast kernel optimized for audio production only. The rt packagers will not go that far, but you can. Kernel building can be fun and interesting if you have the inclination and a lot of spare processing power.

---

### Post by AutoStatic on 2010-02-13
> **marin123 said:**
> i just want to use lmms without having issues like low latency, cracking sound etc, and i was hoping rt kernel would do the trick.. i just want to use LMMS, and i tried with rt kernel, and its better, but has some bugs (everything works fine and then i still get input from midi keyboard, but no sound), dont know is it kernel or program...It's probably the program. LMMS is under heavy development and has its whims. Are you using it with JACK or with plain ALSA?

---

### Post by marin123 on 2010-02-13
> **AutoStatic said:**
> It's probably the program. LMMS is under heavy development and has its whims. Are you using it with JACK or with plain ALSA?

i'm using it with alsa and rt kernel... dont know why, but now it all works fine.. i'm able tu run z3ta (vst instrument)... and now i have small problems with nexus, but i hope i'll get it to work properly...

---

