---
title: "Have you ever recompiled a kernel?"
date: 2007-12-17
forum: The Cafe
---

### Post by aysiu on 2007-12-17
Sometimes I read anti-Linux people complaining about how Linux isn't "user-friendly" and stating that average users don't want to have to recompile their kernels, etc.

I'm just curious as to how many people have actually recompiled their kernels. I know I haven't, but maybe I'm in the minority.

---

### Post by mellowd on 2007-12-17
I have, but not with Ubuntu yet. In the past very often especially with old redhat distro's

---

### Post by rune0077 on 2007-12-17
Never. Wouldn't know how to if I needed it. Good thing I never did :)

---

### Post by engla on 2007-12-17
Yes. I voted for "basic functionality" even though it was neither for _basic_ functionality nor for performance, just for adventure and learning, and for some added features. For example I wanted inotify (the early ubuntu releases didn't have that in the kernel, it wasn't mainline I think).

---

### Post by ironfistchamp on 2007-12-17
Yes I tried it once. Computer completely died!

Had to reinstall again. Fun fun!

---

### Post by conehead77 on 2007-12-17
I did it once to see how hard it really is. To compile a kernel just for fun isnt that difficult, but im too busy atm to really learn how to optimize my kernel.

edit: Just saw the post above and thought i should add that i followed a very good step by step introduction (dont know where i found it though).

---

### Post by Tristam Green on 2007-12-17
I never have, but I've been interested in learning it for a little while.  I'm not sure what one could do with it, but it'd be neat to learn.

---

### Post by neowolf on 2007-12-17
Yes, with Debian and Gentoo; but never on Ubuntu.

Recompiling the kernel is pretty pointless unless you have a particular patch you *really* need, or you just like watching compiler output :p

---

### Post by fatality_uk on 2007-12-17
Whats a KERNEL? :D

---

### Post by klange on 2007-12-17
Yup, compiled a slightly older kernel to get my SD card reader working back before .22-13. Since then, though, I haven't needed to.

---

### Post by -grubby on 2007-12-17
nope. Never needed to

---

### Post by qazwsx on 2007-12-17
No. I have compiled DVB device drivers but no need for actual kernel compiling.

---

### Post by tech9 on 2007-12-17
> **neowolf said:**
> Recompiling the kernel is pretty pointless unless you have a particular patch you *really* need, or you just like watching compiler output :p

+1

---

### Post by mutation on 2007-12-17
never recompiled under ubuntu but use to all the time under redhat and debian way back when to get freeswam working.

---

### Post by aaaantoine on 2007-12-17
I compiled a kernel once, but it was a purely experimental procedure.  It didn't go so well.  I've never *needed* to compile a kernel, though sometimes I've wondered whether doing so would improve system performance at all.  I think in the end, though, it would cause more harm than good.

---

### Post by bobbocanfly on 2007-12-17
I have never finished compiling a kernel. I have started and got very bored about half way through but thats about it really. I would really like to get into it to see if i can speed this Dual Core up a bit and just for learning about Linux.

[QUOTE="neowolf"]or you just like watching compiler output[/QUOTE]

You have know idea how long i can sit and watch a compiler. Also i can sit and watch BitTorrents download (in uTorrent only though, it has soo much rubbish you can read). Thats why i disable my bootsplash too. I like to watch all the text and stuff to see whats actually happening.

---

### Post by aaaantoine on 2007-12-17
Perhaps instead of "Other: Please explain" you should have had an option for "Yes: for other reasons (please explain)", since that would eliminate some obscurity in the poll responses.

---

### Post by aysiu on 2007-12-17
> **aaaantoine said:**
> Perhaps instead of "Other: Please explain" you should have had an option for "Yes: for other reasons (please explain)", since that would eliminate some obscurity in the poll responses.
Yeah, I'm realizing that now...

---

### Post by juxtaposed on 2007-12-17
I've never had to even consider it and I never plan on ever doing it.

---

### Post by 23meg on 2007-12-17
I used to, to add realtime capability for audio applications. I no longer need to, since there's now a -rt kernel in the repositories.

---

### Post by kevdog on 2007-12-17
If anyone is really interested in learning more about the linux kernel, compiling a linux kernel is a great introduction.  Its an easy process, however really hard to perfect and optimize because of the vast number of options available.  Master Kernel has a good thread that is useful to start out with.  I never noticed any speed or performance gain with my compiled kernels --> probably b/c I didnt optimize it correctly, and b/c many of the options are loaded and created as modules anyway.  

Anyway -- this is a good link for anyone interested in learning more about kernel compilation:

[http://ubuntuforums.org/showthread.php?t=311158&highlight=master_kernel](http://ubuntuforums.org/showthread.php?t=311158&highlight=master_kernel)

The only problem with the above thread is that its over 81 pages long.  Sorry.

---

### Post by DrOlaf on 2007-12-17
In Ubuntu? No, I've not needed to. 

I did have to recompile the kernel on a SparcStation once - that was nerve-wracking. 

And I did install Gentoo from sources once, and compiling the kernel is just part of that whole hazing process.

---

### Post by rune0077 on 2007-12-17
Now, if I *do* try to recompile a kernel, but somehow makes a complete mess of everything, does this mean that I'm totally screwed? Or, do I also get to keep the old, functioning kernel, and then choose at login which one to use? (that would probably be on bootup instead, though. Does both kernels show up in GRUB?)

---

### Post by PrimoTurbo on 2007-12-17
I've done it before on Ubuntu, but I somehow missed some settings and completely messed everything up.

---

### Post by mthakur2006 on 2007-12-17
i have but i have recently took to using kernelcheck (google the forums for it) with staggering results.
Does that count?

---

### Post by matthew on 2007-12-17
I've done it a few times, but not recently. I was experimenting to see if compiling options as modules vs functions within the kernel would make any speed differences. It didn't. I also did it to see how small I could make a kernel and still have it function, and for other totally useless, but fascinating (to me) reasons like that.

I've never had to compile one for functionality since I began using Ubuntu.

---

### Post by odiseo77 on 2007-12-17
I voted "Yes, for basic functionality". I haven't been forced to do it on Ubuntu (yet, and I think it won't be necessary at all), but had to do it once on Gentoo to get my wireless card working and once on Debian Lenny to get my graphic card working. (Don't remember having serious issues these times). I also remember having done it once in the past, when I used Fedora, but this was for experimental purposes and for improving the performance (I think the result was a disaster).

Greetings.

---

### Post by Lostincyberspace on 2007-12-17
I haven't yet but I probably will next week just for fun after I get any new hardware.

---

### Post by lizzard on 2007-12-17
When I was working with Gentoo I recompiled the kernel several times. It's just part of the installation procedure. In Ubuntu I can't see any necessity to do that.

---

### Post by kevdog on 2007-12-17
If you compile your own kernel -- you dont hose your current kernel.  It basically adds another kernel that you can boot to in the grub menu.  You can delete the compiled kernel if its not compiled optimally (as I did many times).

---

### Post by Sunflower1970 on 2007-12-17
Yes, I've done it. I was so proud of myself, too. I had to do it more than once since I screwed up the first few times, but the feeling of accomplishment is amazing when it's done :D 

I was also surprised at how easy it was to do, and I'm nowhere near being a Linux expert

---

### Post by smartboyathome on 2007-12-17
I never have had to on Ubuntu, but did try once when trying to install the Gobohide patch (it ended when I got bored of doing "yes" to every question because the kernel's source folder was named differently than the normal kernel folder). I am probably going to try again.

---

### Post by Happy_Man on 2007-12-17
Yes. Whenever I install for the first time, as soon as all my updates are in, I go and compile a new kernel. The first time I tried, it was just for experimental purposes,  but once I saw how much faster my computer became, it was instantly deemed a neccessity.

---

### Post by Nekiruhs on 2007-12-17
> **neowolf said:**
> [snip]or you just like watching compiler output :p[/snip]
Is it a bad thing that I like watching compiler output? Mmm,  GCC... :)

---

### Post by xeth_delta on 2007-12-17
I have recompiled the kernel quite a few times. While the time I was a RedHat 9 user, it used to come with a 2.4 kernel. I wanted to try the (then brand new) 2.6 kernel and the way to go was recompiling.
I learnt a lot in the process and was also able to avoid compiling modules I considered unnecessary, as they did not apply to my hardware.

Before Ubuntu, I used Gentoo Linux, I really liked and still like it a lot, it is fast and clean, optimized for the machine in question, but compiling everything from source used to take a long time, especially big packages.

One of the steps during installation was compiling the kernel, and also recompiling when an update was available.

I have also recently compiled a kernel configured for my Macbook, but had some problems with the behaviour of the trackpad and remote control.

Right now I am using the 2.6.22-14 Gutsy generic kernel on Feisty Fawn. When I'll more time I would like to compile another custom kernel, as they tend to be lighter and some times faster than generic ones. You also get to choose the optimization flags you are willing to use.

Xeth

---

### Post by x0as on 2007-12-17
I recompile the kernel almost every time a RC is released on my Debian box,  I normally try and keep everything as up to date as possible.   Ubuntu box is currently used for work so I stick to official ubuntu packages.

---

### Post by Sn3ipen on 2007-12-17
I have never needed to do so but after reading this i think i have to try it out just for fun:p

---

### Post by xeth_delta on 2007-12-17
> **Sn3ipen said:**
> I have never needed to do so but after reading this i think i have to try it out just for fun:p

It is actually very interesting, but remember to not remove your stable kernel from the system, in case not everything goes fine.

I'm sure there are several guides on the forum on how to recompile a kernel, look for them and good luck!

---

### Post by ~LoKe on 2007-12-17
Several times.

---

### Post by yabbadabbadont on 2007-12-17
I used Gentoo for many years.  Nuf said.  ;)

---

### Post by SunnyRabbiera on 2007-12-17
For me, not so far.
Only if i had built my own computer or something do i see a reason to recompile

---

### Post by yatt on 2007-12-17
I have, for Ubuntu too. I did back in the Dapper days because the Ubuntu kernel needed a boot param. Then in Edgy development, I got the SATA bug that caused the root fs to take about 4 minutes to mount. Then in the release form of Edgy, I needed a new boot param, so I compiled my own kernel again. Since Feisty, I have done a Gentoo install, where I needed to compile a kernel. Otherwise, I have used what is provided by Debian.

---

### Post by jrusso2 on 2007-12-17
The only time I compile my own is if there is some hardware I need to run that requires it.

The stock kernels work pretty well.

---

### Post by user1397 on 2007-12-17
Well, one time I followed one of those kernel recompile threads to supposedly boost my amd athlon xp's performance, by replacing the 386 kernel with the k7 one...but I didn't notice anything. That was a while ago, and I've never done it again, so I put 'no' in the poll.

---

### Post by mmb1 on 2007-12-17
I've never had to, but I may be looking into it to run some legacy hardware.

---

### Post by Anduu on 2007-12-17
I have tried a few...3 or 4 times...never successfully.I tried recompiling for performance but it seems I took too much out.

One day I'll get serious and take baby steps and hopefully get something going.

---

### Post by xeth_delta on 2007-12-17
> **ubuntuman001 said:**
> Well, one time I followed one of those kernel recompile threads to supposedly boost my amd athlon xp's performance, by replacing the 386 kernel with the k7 one...but I didn't notice anything. That was a while ago, and I've never done it again, so I put 'no' in the poll.

Did you also enabled optimization flags, -O2, -O3?

---

### Post by stmiller on 2007-12-18
Low-latency desktop and higher kernel timing are two settings that stock Ubuntu kernels do not use. These settings are particularly for desktop users for better performance so I'm not sure why the Ubuntu kernel team does not enable these.

The stock Ubuntu kernels are set for the lowest kernel timing and non-low latency which makes sense for a server but not a desktop user.   :(

---

### Post by toupeiro on 2007-12-18
I've recompiled a kernel lots of times -- though not on my ubuntu desktop.

---

### Post by FuturePilot on 2007-12-18
Nope, never had to.

---

### Post by 23meg on 2007-12-18
Performance boosts with custom kernels are, most of the time, placebo effect.

* ducks *

---

### Post by toupeiro on 2007-12-18
haha yeah, I'd duck ;)

---

### Post by K.Mandla on 2007-12-18
> **aysiu said:**
> Sometimes I read anti-Linux people complaining about how Linux isn't "user-friendly" and stating that average users don't want to have to recompile their kernels, etc.

I'm just curious as to how many people have actually recompiled their kernels. I know I haven't, but maybe I'm in the minority.
I have, several times, but never because I had to. It was only ever as a learning experience, or to figure out how something worked. Or didn't work.

---

### Post by BuffaloX on 2007-12-18
I did, and it worked OK
The system worked 100%, but still tried to load modules or something that I had disabled. 
And I don't know enough about the startup sequence to prevent it.

---

### Post by plun on 2007-12-18
> **23meg said:**
> Performance boosts with custom kernels are, most of the time, placebo effect.

* ducks *

Well. "duck"...:)    

I find Ubuntus wiki good about this....

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

> **Reasons for NOT compiling a custom kernel**

    *      You merely need to compile a special driver. For this, you only need to install the linux-headers packages.
    *      You have no idea what you are doing, and if you break something, you'll need help fixing it. Depending on what you do wrong, you might end up having to reinstall your system from scratc[B]h.
    *      You got to this page by mistake, but checked it out because it looked interesting. Believe me, this isn't interesting at all :)[/B]


> **Reasons for compiling a custom kernel**

    *      You are a kernel developer.

    *      You need the kernel compiled in a special way, that the official kernel is not compiled in (for example, with some experimental feature enabled).

    *      You are attempting to debug a problem in the stock Ubuntu kernel for which you have filed or will file a bug report.

    *      You have hardware the stock Ubuntu kernel does not support.



The "special way" and hardware is important because of what happens upstream and what comes from Ubuntus kernel team.

Then you of course have the "nerd" factor running the latest kernel...:lolflag:

---

### Post by Megaton on 2007-12-18
I used to be a Gentoo user, so yes. But, I also do it regularly on my Ubuntu system. It isn't hard at all and usually has its benefits. I think the hardest part is your first time working through the .config file. When starting with a new custom source tree, (such as the Zen kernel I am now using) I spend a couple of hours just going through all of the config options. On a modern dual core system, it doesn't take very long to actually compile the kernel at all. I have significantly decreased boot times, increased speed and responsiveness, and added the features that I want by compiling my own kernel. I think that with linux, you just can't be afraid to break things. It is almost always savable in some way, even if the system won't boot. Just keep a stable kernel around just in case.

---

### Post by daou on 2007-12-18
Not for desktop Linux... I wouldn't try to replace my Ubuntu kernel with a custom one, unless I had no other choice.

But for embedded Linux, sure. Custom devices need custom solutions.

---

### Post by SOULRiDER on 2007-12-18
> **engla said:**
> Yes. I voted for "basic functionality" even though it was neither for _basic_ functionality nor for performance, just for adventure and learning, and for some added features. For example I wanted inotify (the early ubuntu releases didn't have that in the kernel, it wasn't mainline I think).

+1
I also compiled it because i decided to run Gentoo too, but i didnt really do any customization. Compiling a kernel and applying patches is something i REALLY want to learn.

---

### Post by argie on 2007-12-18
I have. Once. Back in breezy I thought I had to do that to enable Direct Rendering for my VIA Unichrome VT8378 onboard graphics. I didn't have to. I was running at too high a colour depth that's all. Naturally the recompiled kernel didn't help. All versions of Ubuntu since then haven't needed me to do anything of the sort.

I voted enhanced functionality since that was the whole point of that one time I recompiled it the main objective was to get those Con Kolivas' patches in. I think I did something wrong (forgot to compile with a high optimisation or whatever) and I always felt like the resulting kernel was slower :)

I haven't compiled a kernel since.

---

### Post by LeAstrale on 2007-12-18
> **SOULRiDER said:**
> +1
I also compiled it because i decided to run Gentoo too, but i didnt really do any customization. Compiling a kernel and applying patches is something i REALLY want to learn.


any special reason why you really want to learn it?

Personally id like to get my new Apple aluminium Keyboard working (wired model) and to get it working it seems i have to apply a kernel patch :S

thats as far as my research goes.

---

### Post by starfry on 2007-12-18
I've built my entire Linux server from source - everything from the kernel up.

I use Ubuntu on my desktop machine but my server contains just what I want - I built it so I know exactly how it all works. A great learning experience :)

Building the kernel is very easy. Do not be scared of it. You can always add multiple boot entries to Grub so you can boot your original kernel if your new one doesn't work.

---

### Post by PartisanEntity on 2007-12-18
I have not needed to recompile a kernel, but I would like to do it. Just to see if it makes any difference and to learn something new.

---

### Post by xyz on 2007-12-18
I did several months ago following the excellent guide on ubuntuforums.
It was very interesting but no difference really.

---

### Post by Skorzen on 2007-12-18
No, I haven't. I let that things for programmers.

---

### Post by isecore on 2007-12-18
I've recompiled a kernel several times. Not with Ubuntu yet though, since as far as I can tell the default kernel is perfectly acceptable to me.

But yes, I've recompiled kernels several times, especially in the old days before modules caught on.

---

### Post by eth on 2007-12-18
Yes, I have. Mainly for performance enhancements, as everything usually worked for me. 

Anyway, that's a pointless point for Linux haters (well, they ARE actually pointless...who needs them?) since you can have a pefectly working user-friendly opensourced machine under your butt without even knowing what a kernel is?
The fact is that in this OS at leat you CAN have a clue about how does it works. 
Actually you can learn how it works.
And how it works anything inside.
And you sould have the right to know...you own it.
Everyone does.

---

### Post by void_false on 2007-12-18
Yep. Many times. But that was on Gentoo system. But I wont do it on ubuntu because i'm afraid it wont work and will be broken after that  ;)

---

### Post by igknighted on 2007-12-18
I've done it plenty of times to (a) learn how to do it, and (b) try to get some performance gains.   While not earth-shattering, the performance boost was noticable.  I have not yet had to do it because of a hardware issue, but am about to try it with my laptop as it seems to be having some issues that may be kernel related.

---

### Post by Prospero2006 on 2007-12-18
I recompiled when I was a slackware user in the early 2000's. 
I used the directions in O'Reilly's Running Linux.

Brew a cup of coffee, wait 20 minutes....

---

### Post by jayson.rowe on 2007-12-18
Back in my Slackware days it was a common occurance (As I wanted a 2.6 kernel, and Slackware finally moved to 2.6 long after I stopped using that distro)...

In Ubuntu, the defaults work well enough for me, so I haven't bothered.

---

### Post by jpittack on 2007-12-18
I am 64 bit and will try the new 2.6.24 kernel for tickless.  See if the change in battery life is worth it.  I might go ahead and stop using ati drivers and compiz at the same time.  I think I might try out the zen patch, to see the difference it will make.

I just don't feel like waiting for hardy.  I'm just a kid in a (free) computer store.

---

### Post by bruce89 on 2007-12-18
> **jpittack said:**
> I am 64 bit and will try the new 2.6.24 kernel for tickless.  

I was under the impression that tickless was in [2.6.21]("http://kerneltrap.org/node/8103"). (for i386, 2.6.23 for AMD64)

---

### Post by timpino on 2007-12-18
done it with slackware and redhat in my beginning days on linux, nowadays i just don't bother

---

### Post by hessiess on 2007-12-18
no- have never needed to

---

### Post by igknighted on 2007-12-18
> **jpittack said:**
> I am 64 bit and will try the new 2.6.24 kernel for tickless.  See if the change in battery life is worth it.  I might go ahead and stop using ati drivers and compiz at the same time.  I think I might try out the zen patch, to see the difference it will make.

I just don't feel like waiting for hardy.  I'm just a kid in a (free) computer store.

You can add the Hardy repo's, update the kernel to the latest hardy version (it should have 2.6.24 shortly after it comes out), and update all the modules packages that go with it, then remove the hardy repo's and run the new kernel on your Gutsy system without missing a beat.  This cuts out a lot of the instability of apps changing too.  Someone wrote a script to do this automatically for fiesty->gutsy, perhaps a similar one will pop up for gutsy->hardy?

---

### Post by Erunno on 2007-12-18
Compiling your own kernel is a requirement for using Gentoo so I did it every time a new version was released in the Portage tree. Getting a basic kernel to run is actually pretty straight forwarded as long as you know what hardware you have and which options *not* to deselect. It's quite daunting though when you go the first time through all the options and have to read the help file for explanations. This can take quite a few hours depending on how thorough you are. With some knowledge about computers and operating systems you should also have a gut feeling which options are dangerous to turn off (for instance, turning off the generic ATA driver *might* cause problems with accessing hard drivers later on). Otherwise from what I remember I needed less 20 percent of the offered options to ge the kernel running on my notebook. As long as you install your custom kernel alongside a fully functioning one you can always experiment if the kernel can be stripped down further as you can always boot back into the system and recompile with new options when you broke something.

Since the performance gains are mostly theoritical in nature and from my experience not noticable and distriubtions spend quite some time for testing and maintaining a specific kernel version I tend to use the stock kernel which comes with the distribution of my choice.

EDIT:

Not sure which poll option I should choose to be honest. When still using Gentoo I did for basic functionality as well as for *cough* ricing. Ah well, since basic functionality is a subset of performance gains I'll take the first one.

---

### Post by regomodo on 2007-12-18
yes for speed, twice. 1 on ubuntu one on debian. after installing they'd kernel panic on me

---

### Post by user1397 on 2007-12-18
> **xeth_delta said:**
> Did you also enabled optimization flags, -O2, -O3?Well if I did or didn't at the time, I wouldn't know...it's been over a year since I tried it.

---

### Post by Erunno on 2007-12-18
> **bruce89 said:**
> I was under the impression that tickless was in [2.6.21]("http://kerneltrap.org/node/8103"). (for i386, 2.6.23 for AMD64)

He's probably thinking about the new Completely Fair Scheduler (CFS).

---

### Post by InfinityCircuit on 2007-12-18
> **igknighted said:**
> You can add the Hardy repo's, update the kernel to the latest hardy version (it should have 2.6.24 shortly after it comes out), and update all the modules packages that go with it, then remove the hardy repo's and run the new kernel on your Gutsy system without missing a beat.  This cuts out a lot of the instability of apps changing too.  Someone wrote a script to do this automatically for fiesty->gutsy, perhaps a similar one will pop up for gutsy->hardy?

For some odd reason the Hardy kernels do not have dynticks enabled.  I have absolutely no idea why.

---

### Post by bruce89 on 2007-12-18
> **Erunno said:**
> He's probably thinking about the new Completely Fair Scheduler (CFS).

Excuse the pun, but that's fair enough.

---

### Post by erginemr on 2008-04-05
For those who feel young at heart and would like to try compiling the kernel, the following howto on Kernel Compilation in Ubuntu would be a nice start:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by jomiolto on 2008-04-05
Of course I have, plenty of times. I ran Gentoo on my desktop for almost two years and still run it on my server :p

---

### Post by Dekkon on 2008-04-05
Ubuntu, no. Fedora, yes, my ATI drivers required me to recompile my kernal. The most annoying thing in the world but I guess it was worth it.

---

### Post by Iandefor on 2008-04-05
I have, for the hell of it.

---

