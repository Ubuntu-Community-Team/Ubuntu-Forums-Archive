---
title: "&quot;RAM is there to be used&quot; . .  how do you feel about this statement?"
date: 2010-06-11
forum: The Cafe
---

### Post by Macfunky on 2010-06-11
I completely understand where this statement is coming from and i agree if you have large amounts of RAM that a programme that is a bit of a hog isn't going to make much of a difference. How do you feel about this statement? 

For me I have always stayed below what would at any current time be considered the average amount of RAM and have found i can still do plenty. I do find that some programmes to work fully need more RAM but generally speaking i find lower RAM (from what is considered average at any given time) works perfectly for most tasks. Unless you need resource intensive programmes i don't think a huge amount of RAM is needed. Anyone have any other views on this?

EDIT - I understand that if you have loads of RAM that this is not a problem but my point is if you have less RAM should programmes be so intensive. Should programmes be heavyweight just because computers can have so much RAM? Should they aim to have lower resources or should they be more intensive just because higher RAM allows it?

My reason for asking this question is because i heard recently that as computers processing power/RAM increases so too does the programmes demands that run on our computers, so much so that an old word processor on an old computer runs no quicker than a new word processor on a new computer/operating system. Any thoughts?

---

### Post by KingYaba on 2010-06-11
I couldn't care less as long as I'm not paging to disk.

---

### Post by Cam42 on 2010-06-11
If you have the RAM, then use it. The statement is perfectly true. Would you buy an air conditioning unit for your home and never turn it on, or only when it gets over 100 degrees?
Then why have 4GB of RAM and be worried when 45% is used?

---

### Post by alphaniner on 2010-06-11
I agree with the statement, unless it is used as an excuse for poor programming...

---

### Post by lostinxlation on 2010-06-11
Beyond the point that you can put all the processes running concurrently on memory, the memory size becomes financial matter rather than performance matter.

---

### Post by gnomeuser on 2010-06-11
I have a total of 4GB of memory (1GB taken by the graphic chip). Leaving all that nice storage idle is so.. wasteful.

Wasting memory is silly but leaving memory empty when disk IO is so slow is plain silly.

---

### Post by BoneKracker on 2010-06-11
It's there to be used, but by things that are value-added to me.

Also sloppy memory handling is a sign of poorly-designed, poorly-tested, poorly audited code, which has other consequences.

Furthermore, software these days should be striving to be deployable to portable and embedded devices, which typically have much less RAM than desktops.

If you have excess RAM, don't waste it on silly bells and whistles that are meaningless to you, put it to use by intelligently moving certain on-disk operations into RAM (e.g. using tmpfs for small parts of the filesystem that get thrashed a lot and cause I/O wait).

---

### Post by squilookle on 2010-06-11
I like having plenty free, just in case I start doing something else that needs it. 

If my OS and web browser are using more than 40-50%, I start looking for lighter software and, if that doent do everything I need it to, then I start looking to upgrade.

---

### Post by Legendary_Bibo on 2010-06-11
The way I look at it, as long as my OS does what I want without complaining then by all means it can use whatever resources it wants. I have 4gb of ram, and if it wants to use it to make itself faster or something then I say let it do what it wants.

---

### Post by cariboo on 2010-06-11
I'm in the process of ripping my dvd collection using Handbrake, even with both cores running at 98% and using 1.4Gb of 2 Gb ram the system still runs fairly well.

---

### Post by Letrazzrot on 2010-06-11
I've heard this saying used in the programming world, usually to deter needless and premature optimization when developing software.  Ideally, a developer will have a pretty good idea of what kind of hardware he/she wants to deploy on, and optimizes if necessary to reach that goal.  Optimization usually ends up being a balance between speed and memory usage.  Sometimes more drastic changes need to be made, such as cutting features.

So, to answer the OP, I suppose I agree with the statement, as long as the software in question seems to be targeted for the hardware I have. Eliminating memory management bugs is far more important, for security and stability reasons.

---

### Post by Mr. Picklesworth on 2010-06-11
I think people need to stop rating applications as if RAM and CPU usage trump all other factors. Some applications use memory really well, and they may use *a lot of it* to be more responsive; to squeeze the most out of the CPU.

Another application could use very little memory, very little CPU, but be horrendously slow because it was poorly designed. May even slow down your whole computer with that theoretically low CPU consumption, if it happens to be hitting the right things in a horrible enough fashion.

---

### Post by juancarlospaco on 2010-06-11
*dont worry theres a java app for using all these ram.*

---

### Post by BoneKracker on 2010-06-11
> **juancarlospaco said:**
> *dont worry theres a java app for usig all these ram.*

:lol: \o

---

### Post by BoneKracker on 2010-06-11
> **Mr. Picklesworth said:**
> I think people need to stop rating applications as if RAM and CPU usage trump all other factors. Some applications use memory really well, and they may use *a lot of it* to be more responsive; to squeeze the most out of the CPU.

Another application could use very little memory, very little CPU, but be horrendously slow because it was poorly designed.

Do you really think lots of people do that?  It seems to me like most people rate applications according to *bling*.  If it's *bling*, I want it.  If not, I don't.

Look at all the emphasis that has gone into *bling* in MacOS X, Vista/7, KDE, and Gnome.  To me it seems like most people are fixated on desktop gadgets, wobbly windows , transparency, drop shadows, and a bevy of dingleberrydaemons to tickle their fancy.

I've even noticed some supposed minimalists running conky setups that consume 20% of their cpu so they can have something impressive-looking on their desktop (which shouldn't be showing anyway because you're supposedly actually using your computer to do something). :p

---

### Post by t.rei on 2010-06-11
Honestly, I like software to be smooth and small and all. Because of those times when it needs to get it's data written into the ram. It's not about the amount of memory but about the amount of date that needs to get there and back out. 

But... looking at it...
gnome + compiz +couple of chatclient +several firefox +evolution and a movie ... and its at around 13% of those 4 Gig. I can live with that. :D

---

### Post by dtfinch on 2010-06-11
I'm all for fixing memory leaks and processes that waste seconds worth of cpu at a time doing nothing special. The main reason being that the bugs that make programs perform poorly on yesterdays computers almost always make them perform poorly on tomorrow's computers as well when dealing with an only slightly bigger load.

---

### Post by MattiJ on 2010-06-11
I have 8GB of memory but still it start to swap after some day's usage so I have to do "sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches" " or reboot to free it. This is using ftp sever and Transmission but still it should not overuse the memory....:guitar:

---

### Post by NightwishFan on 2010-06-11
I like my software to be conservative and functional, but not necessarily minimal. I really like the way correctly conforming Gnome applications are organized.

Having powerful hardware available is no excuse to be lax on quality of programming. I agree applications should squeeze as much ram as they can when free. I even run some self contained stuff straight from /dev/shm to reduce loading times on disk heavy i/o.

I rarely ever use most of my 3gb unless I am editing images or running virtual machines.

---

### Post by SunnyRabbiera on 2010-06-11
> **alphaniner said:**
> I agree with the statement, unless it is used as an excuse for poor programming...

Like Vista and Windows 7 hogging up one gig alone for fancy graphics

---

### Post by RiceMonster on 2010-06-11
I have 4 GB, and I don't really pay attention to how much is being used. Maybe if it was reaching maximum I would be worried, but it never even goes to half.

> **SunnyRabbiera said:**
> Like Vista and Windows 7 hogging up one gig alone for fancy graphics

*sigh*

---

### Post by Npl on 2010-06-11
> **SunnyRabbiera said:**
> Like Vista and Windows 7 hogging up one gig alone for fancy graphicsReally? Must be doing something wrong.. Win7 uses 560MB currently and thats with the browser grabbing 130MB of that.

Anyway, I dont have a problem with a program using up all ram, aslong it (and thus myself) is actually benefiting. Sadly this excuse of "using" much RAM is often stated when the program is just wasteful with resources... ie if you could do the same thing in a fraction of that (and likely faster) while actually having a potential use from the additional free RAM.

---

### Post by SunnyRabbiera on 2010-06-11
> **Npl said:**
> Really? Must be doing something wrong.. Win7 uses 560MB currently and thats with the browser grabbing 130MB of that.

Anyway, I dont have a problem with a program using up all ram, aslong it (and thus myself) is actually benefiting. Sadly this excuse of "using" much RAM is often stated when the program is just wasteful with resources... ie if you could do the same thing in a fraction of that (and likely faster) while actually having a potential use from the additional free RAM.

With a more recent graphics card win7/vista is alright but with an older one I have seen them eat up ram

---

### Post by doas777 on 2010-06-11
my win7 box at work is always out of it's 4gb ram, but thats cause i have a VM of ubuntu, 2-3 visual studio instances, SQL management studio, and outlook open at all times, plus whatever small stuff. it doesn't slow down too much, but a little. 

my ubuntu boxes with 4gb never seem to use more than 2.5gb, no matter what i throw at them.

---

### Post by NightwishFan on 2010-06-11
I remember Vista started with Aero on my PC with an Integrated Nvidia 6150SE. It took nearly 15 minutes to get to the desktop on first boot. I suppose it does not implement its own form of "libxdamage" as it took nearly 80% cpu even when idle.

---

### Post by ubunterooster on 2010-06-11
I like to think it is being used for *something*...

---

### Post by BoneKracker on 2010-06-11
Most people's RAM is being used for Global Warming and that's about it.

---

### Post by NightwishFan on 2010-06-11
Go my ram, and allocate your epicness towards processing the final calculation I need to dominate the world..

The theory of more RAM used is better makes sense to me. Keep stuff you just used for faster access, perhaps preload for better start up times.

---

### Post by ubunterooster on 2010-06-11
> **BoneKracker said:**
> Most people's RAM is being used for Global Warming and that's about it.
LOL, my RAM (1444mhz capable) is running at 400mhz and my 3.9ghz CPU at 0.8Ghz.  Total usage of PC: 38 Watts

---

### Post by Frogs Hair on 2010-06-11
I have 2gb and 512mb on my graphics card but I would like more to try other distros with. Ubuntu is using only 4gb of 500gb of hdd space so I have the room.

---

### Post by Cam42 on 2010-06-11
Why would you downclock that bad?

---

### Post by ubunterooster on 2010-06-11
> **Cam42 said:**
> Why would you downclock that bad?
Power. I have a second profile so I can reboot into superfast mode should I need to; but I use it for web surfing, file sharing and music, little else. At full bore it can use over 200 watts!

---

### Post by Merk42 on 2010-06-11
> **squilookle said:**
> I like having plenty free, just in case I start doing something else that needs it. 

If my OS and web browser are using more than 40-50%, I start looking for lighter software and, if that doent do everything I need it to, then I start looking to upgrade.

Then what is taking up the other 60-50%?

---

### Post by phrostbyte on 2010-06-11
I don't like the statement because it's usually used as an excuse for crappy software design.

---

### Post by magmon on 2010-06-11
I have never been much of a multitasker, so I'd say my ram usage falls well below the average geek. I figure as long as I can't see performance decay, it can do whatever it wants lol. I certainly have no yearning to utilize all of my ram.

---

### Post by 98cwitr on 2010-06-11
1.3 of 2.0 used...so sue me.

---

### Post by wkhasintha on 2010-06-11
> **alphaniner said:**
> I agree with the statement, unless it is used as an excuse for poor programming...

Agreed!

---

### Post by gnomeuser on 2010-06-12
> **ubunterooster said:**
> Power. I have a second profile so I can reboot into superfast mode should I need to; but I use it for web surfing, file sharing and music, little else. At full bore it can use over 200 watts!

Have you considered something like the Acer Aspire Revo R3610. It would do the same as your downclocked profile (except at probably half the wattage). I use one as my primary machine and it is a glorious desktop machine for the price, performance is good as well (the hardware itself is capable of running Left 4 Dead at an acceptable framerate so it does carry a punch). Also given the ION chip you have VDPAU support for those high def videos.

---

### Post by ubunterooster on 2010-06-12
> **gnomeuser said:**
> Have you considered something like the Acer Aspire Revo R3610. It would do the same as your downclocked profile (except at probably half the wattage). I use one as my primary machine and it is a glorious desktop machine for the price, performance is good as well (the hardware itself is capable of running Left 4 Dead at an acceptable framerate so it does carry a punch). Also given the ION chip you have VDPAU support for those high def videos.
I'm a desktop user because of the ability to upgrade quickly if I want. Still, I have been keeping an eye open for a nice netbook so thanks.

---

### Post by K.Mandla on 2010-06-12
I agree wholeheartedly. That's why I make a point of using all of the available 10Mb out of 16Mb physical in my Musca system running Crux on a Pentium. 

[http://kmandla.wordpress.com/2009/09/08/a-thousand-words-10mb/](http://kmandla.wordpress.com/2009/09/08/a-thousand-words-10mb/)

Just to elaborate. ...

[http://kmandla.wordpress.com/2009/09/02/unsolved-mysteries-x-in-1mb/](http://kmandla.wordpress.com/2009/09/02/unsolved-mysteries-x-in-1mb/)
[http://kmandla.wordpress.com/2009/02/15/how-can-it-all-fit/](http://kmandla.wordpress.com/2009/02/15/how-can-it-all-fit/)

If there's a need for me to use more than 64Mb in a computer, I haven't found it yet.

---

### Post by gnomeuser on 2010-06-12
> **ubunterooster said:**
> I'm a desktop user because of the ability to upgrade quickly if I want. Still, I have been keeping an eye open for a nice netbook so thanks.

Actually the Revo is a nettop. It's pretty much a standard, abide small, desktop machine. The R3610 model comes with 4GB of memory and an SMT capable  dualcore ATOM at 1.6GHz.

---

### Post by YuiDaoren on 2010-06-12
I prefer the statement **"Ram is there to be used *efficiently*."**

It gets to the point a bit better.

---

### Post by Paqman on 2010-06-12
> **KingYaba said:**
> I couldn't care less as long as I'm not paging to disk.

+1

Once you get up to 2GB or more, it's pretty hard to run out of RAM. I've got 4GB and big VMs are about the only thing i've got on my machine that stands a chance of using it up. Normal apps don't even come close.

---

### Post by red_Marvin on 2010-06-12
I prefer to reverse the argument; "If you don't really need it, why would you get it?"

---

### Post by DoktorSeven on 2010-06-12
Your HD space is there to be used, why isn't it full?

Your house space is there to be used, why isn't it packed full of stuff?

Even if RAM can more easily deallocate memory than you can get rid of things on your HD or in your house, it's still silly that you would fill it up uselessly just because you might need something.  

I'd rather have free RAM than the computer putting something there that it thinks I might use in the future, especially like the whole Superfetch thing in Windows (which I disable).  In fact, my system runs *better* with it disabled.

---

### Post by cartman640 on 2010-06-12
> **DoktorSeven said:**
> I'd rather have free RAM than the computer putting something there that it thinks I might use in the future, especially like the whole Superfetch thing in Windows (which I disable).  In fact, my system runs *better* with it disabled.

I'm sorry, what? That is ridiculous... So you'd rather wait for your HDD to thrash about looking for an application to launch than having it sitting in RAM already? You do know that prefetching has virtually no negative effect on a system, it uses otherwise empty memory and if that memory is needed it's just a memory free away (which happens in less time than it takes a signal to get from one end of a SATA cable to the other). As for performance, with prefetching enabled in Windows, all of my common applications open instantly, all of Office opens in less than 2 seconds, same story in Ubuntu, Firefox opens faster than the little animation of the launcher, as does nearly every other application.

I keep as much memory used as possible, there's usually <50Mb unused out of the 8Gb in my machine, and it's insanely fast as a result. I never have to wait for anything, it's great. RAM is very much there to be used.

---

### Post by BoneKracker on 2010-06-12
> **ubunterooster said:**
> LOL, my RAM (1444mhz capable) is running at 400mhz and my 3.9ghz CPU at 0.8Ghz.  Total usage of PC: 38 Watts

38 Watts x 3 Billion CPUs --> 388,984,146,200 BTU of heat

At any given time, what are those CPUs accomplishing, on average?

This:


[IMG]http://homemadearcade.com/images/Screen%20Saver%20Pack%202/SwirlsScreenShot.gif[/IMG]

---

### Post by cap10Ibraim on 2010-06-12
> **Npl said:**
> Really? Must be doing something wrong.. Win7 uses 560MB currently and thats with the browser grabbing 130MB of that.

32 bit or 64bit windows 7 ?

---

