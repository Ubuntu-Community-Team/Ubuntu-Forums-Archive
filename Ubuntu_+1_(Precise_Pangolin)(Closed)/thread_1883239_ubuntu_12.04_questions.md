---
title: "ubuntu 12.04 questions"
date: 2011-11-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by linuxusersince2008 on 2011-11-18
hello i'm a little upset of what i been hearing about ubuntu 12.04 not supporting 32bit
i have a dual pentium 3 1ghz i'm building, i really don't want to upgrade my hardware
but i don't want leave ubuntu. i'm also planning to install ubuntu on a pentium 2 350mhz
just for fun in the future what can be done?:(

---

### Post by coffeecat on 2011-11-18
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

Where did you hear that 12.04 will not support 32bit? I'm confident that is not right.

I'm sure people will be able to help you in this forum.

---

### Post by dcstar on 2011-11-18
> **linuxusersince2008 said:**
> hello i'm a little upset of what i been hearing about ubuntu 12.04 not supporting 32bit
i have a dual pentium 3 1ghz i'm building, i really don't want to upgrade my hardware
but i don't want leave ubuntu. i'm also planning to install ubuntu on a pentium 2 350mhz
just for fun in the future what can be done?:(

No one forces you to install the latest versions, there will be plenty of Ubuntu 32-bit releases still under support for a number of years past 2012.

---

### Post by Paddy Landau on 2011-11-18
At the moment, the [download page]("http://www.ubuntu.com/download/ubuntu/download") offers by default the recommended 32-bit, but also offers 64-bit.

Starting with 12.04, this will be swapped. The download page will offer by default the recommended 64-bit, but will also offer 32-bit.

---

### Post by dniMretsaM on 2011-11-18
Is he getting it from this maybe?
> 
[LIST]
[*]Investigate dropping i386 non-pae flavor
[*]Investigate dropping 32bit non-smp powerpc flavor
[/LIST]
[Source.]("http://fridge.ubuntu.com/2011/11/17/12-04-ubuntu-developer-summit-proceedings/")

---

### Post by buzzmandt on 2011-11-18
> The i386 non-PAE kernel provided support for antique CPUs, including Intel CPUs prior to Pentium II, 400Mhz Pentium M, Geode LX, and VIA C3.

> However, if people want this non-PAE i386 flavor to be kept in the kernel, Tim Gardner is willing to sponsor the first non-PAE kernel upload to the Universe repository of Ubuntu 12.04 LTS.

source: [http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml](http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml)


So yes it seems your 
> i'm also planning to install ubuntu on a pentium 2 350mhz
just for fun in the future what can be done?
isn't gonna happen (or at least possibly since it does specify '*investigate*'.)


But your
> i have a dual pentium 3 1ghz i'm building
will be fine since this is a PAE supported cpu.

---

### Post by effenberg0x0 on 2011-11-18
Just to clarify things a little in case someone reaches this thread: The translation of the above news is that nothing relevant will change.

**PAE** (Physical Address Extension): Allow you to use more than 4GB of RAM in Ubuntu 32-Bits. Non-PAE Kernel can only use about 3GB, no matter how much you buy and install in your PC. So enabling PAE support is good if you want to upgrade your PC. In this mention, they're talking about dropping kernel which doesn't have PAE enabled (thus probably keeping only versions that support it). If your PC BIOS does not support PAE (Memory Hole Remapping, among other names are used in BIOS), nothing will change for you. If you PC BIOS does support PAE, you'll be able to use more than 4GB of RAM. If you want to use more than 4GB of RAM but your BIOS don't support PAE, all you have to do is install the 64-bit version of Ubuntu. See more at [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

**EDIT:** It looks like PAE was introduced in 1995 in the Pentium Pro. The Pentium Pro 200MHz (1995) supports PAE, and so does all following CPUs Intel/AMD. It may or may not be usable to you depending on your BIOS support. But it will work if your PC is superior to a Pentium Pro. Unless you want to run Ubuntu on a 16+ years machine, it won't be a problem. 
 
**SMP** (Symmetric Multiprocessing): Technology to allow the use or more than one CPU. In today's common multi-core CPUs, SMP is used as it treats each core as a CPU. In this mention, they're talking about dropping kernel that doesn't support it. Unless you have an old powerpc-based computer, that doesn't support SMP, it won't affect you at all. If you had a powerpc you would know it. If your MAC was manufactured after 2006, it is intel-based (x86 architecture, not powerpc). See more at [http://en.wikipedia.org/wiki/Symmetric_multiprocessing](http://en.wikipedia.org/wiki/Symmetric_multiprocessing)

---

### Post by linuxusersince2008 on 2011-11-19
thanks for the reply, i got this info from softpedia here the link.[http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml](http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml)

and my motherboard is a asus cuv4x-d dual pentium 3 it can support upto 4gb of ram
but it's not 64 bit compatible that i know of.

---

### Post by Paddy Landau on 2011-11-19
> **linuxusersince2008 said:**
> thanks for the reply, i got this info from softpedia here the link.[http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml](http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml)

and my motherboard is a asus cuv4x-d dual pentium 3 it can support upto 4gb of ram
but it's not 64 bit compatible that i know of.
It's nothing to do with 64-bit. It's to do with non-PAE. 32-bit with PAE will still be supported.

As effenberg0x0 said, if your computer is younger than about 16 years old, you don't need to worry. How old is your computer?

---

### Post by effenberg0x0 on 2011-11-19
> **linuxusersince2008 said:**
> thanks for the reply, i got this info from softpedia here the link.[http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml](http://news.softpedia.com/news/i386-non-PAE-Kernel-To-Be-Removed-from-Ubuntu-12-04-234434.shtml)

and my motherboard is a asus cuv4x-d dual pentium 3 it can support upto 4gb of ram
but it's not 64 bit compatible that i know of.

> **Paddy Landau said:**
> It's nothing to do with 64-bit. It's to do with non-PAE. 32-bit with PAE will still be supported.

As effenberg0x0 said, if your computer is younger than about 16 years old, you don't need to worry. How old is your computer?

The motherboard can probably support 4GB of RAM, many do. In the sense that if you add 4GB of RAM it will boot and work. My old motherboard supported up to 8GB, but it would boot normally with 16GB. This is not unusual.

However,  do you see 4GB (run the command free -g) in the OS without running either a pae-enabled kernel or a 64-bit kernel? I seriously doubt it.

The purpose of the discussion 32-bit vs. 64-bit, pae-enabled vs. non-pae kernel, bios, motherboard, etc is this:

Each bit is the minimum unit representing data in any PC. It can only have two states: 0 or 1. It's like electricity: Either there's voltage or not. Or a lamp. It can be on or off.
A 32-bit processor can handle 32 of these small units of basic information.

b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|b|
There are 32 "spaces" above. Each can hold 1 bit (be 0 or 1). Alternating each "space" between 0 and 1, how many different numbers (integers) can be represented?

2^32= 4,294,967,296

So, the main point is that I need to be able to use these numbers, from 0 to 4,294,967,296) to access memory addresses. 

The symbol K normally represents 1.000 (1Kg = 1.000g). But because people have 10 fingers, some programmer decided, long ago in the beginnings of computer science, that 1K would represent 1,024 bits (2^10). Actually, there are infinite theories about this, blaming IBM, etc. Basically it was faster to work with powers of two (bit shifting) than floating point.

1K = 1.024 * (10^3) = 2^10 = 1,024
1M = 1.049 * (10^6) &#8776; 2^20 = 1,048,576  
1G = 1.074 * (10^9) &#8776; 2^30 = 1,073,741,824

So, using our first large number (2^32), I can access up to 4GB
(4,294,967,296 / 1,073,741,824 = 4)

PAE  is a mechanism that works around this limitation and, even though the CPU is 32-bit, makes it possible for it to access memory addresses over 4GB. It's a workaround.

In order to use PAE, we need:
- Operating System Support
- BIOS / Chipset support (AKA Motherboard support)
- CPU Support

So, most modern CPUs (post 1995) support PAE. Most OSs support PAE (even though some patch or kernel update might be needed) and modern motherboards may or may not support PAE. What Ubuntu is doing is dropping kernel in which PAE is **NOT enabled****. **If your PC doesn't support PAE, things will be the same. If your PC supports PAE, you can use more than 4GB of RAM and will benefit from it **on 32-bit, avoiding a migration to Ubuntu 64-bit**.

[B][http://en.wikipedia.org/wiki/3_GB_barrier](http://en.wikipedia.org/wiki/3_GB_barrier)
[http://dlsvr01.asus.com/pub/ASUS/mb/4GB_Rev1.pdf](http://dlsvr01.asus.com/pub/ASUS/mb/4GB_Rev1.pdf)

 [/B]

---

### Post by effenberg0x0 on 2011-11-19
Just a comment: I find it incredible that now the FUD will be about pae-enabled vs non-pae. 
Either a large portion of the Ubuntu community is really challenged or, more likely, this type of terrorism is orchestrated and promoted be interested parties.

---

### Post by VeeDubb on 2011-11-19
> **effenberg0x0 said:**
> Just a comment: I find it incredible that now the FUD will be about pae-enabled vs non-pae. 
Either a large portion of the Ubuntu community is really challenged or, more likely, this type of terrorism is orchestrated and promoted be interested parties.


Never underestimate the power of FUD.  

Just keep reminding folks that this is less important than having your apendix removed.  If your computer is new enough (less than 16 years old) to run a current Ubuntu desktop, the loss of non-PAE and/or non-SMP will have no effect on you at all.

---

### Post by effenberg0x0 on 2011-11-19
I was just watching a number of people chat on IRC. A dude said he had a "Very reliable source from inside Canonical" tell him that, after PP is released, all development for the next release will focus on moving back from Unity, Compiz, etc and pursue the design of a new interface that would be strongly similar to Gnome 2. As I joined the conversation and asked who the source was, he immediately signed of, of course. 

I can't understand what people gain from spreading such stupid things. Now the whole pae stuff is being reproduced all over the ubuntu hax0r blogs as the new cataclysm. It's getting on my nerves.

---

### Post by ranch hand on 2011-11-19
> **effenberg0x0 said:**
> I was just watching a number of people chat on IRC. A dude said he had a "Very reliable source from inside Canonical" tell him that, after PP is released, all development for the next release will focus on moving back from Unity, Compiz, etc and pursue the design of a new interface that would be strongly similar to Gnome 2. As I joined the conversation and asked who the source was, he immediately signed of, of course. 

I can't understand what people gain from spreading such stupid things. Now the whole pae stuff is being reproduced all over the ubuntu hax0r blogs as the new cataclysm. It's getting on my nerves.
Best thing to do is not read blogs.  Most of them are just parroting things from other misinformed blogs.

While I will admit that there are good ones out there it seems that no one reads them.

This is understandable.  They are written by people that are not trained to write so they are not as "smooth".  They are written by folks that have some technical knowledge so they confuse people that don't.  They are not exciting and splashy.  They are not, generally looking for big numbers of hits so they don't have to resort to tabloid tactics.

These things do get on your nerves but they also generally just fade out as the cataclysm fails to appear.

Of coarse then there needs to be a new thing to attract the "moths" back to the flame.

Best to just ignore them.

---

### Post by jerrylamos on 2011-11-20
> **ranch hand said:**
> 

Of coarse then there needs to be a new thing to attract the "moths" back to the flame.

Best to just ignore them.

Hmmm.  Reading things like Distrowatch and Planet Ubuntu looks like Unity Centric Ubuntu is losing ground.  Anyone have any way to get any real data?
I don't think so....

Qualification - I'm not a tablet & game fan like XXX% of the people I see.  As soon as I want to do something the tablet doesn't cut it.  Now I don't mind a Unity ubuntu for tablets for those customers - just not me.  This netbook is in the same size & price range and has a thousand percent more function and flexibility.

And yes I test Unity (and lubuntu lxdm) because I try whatever ubuntu management throws over the wall.

Jerry

---

### Post by effenberg0x0 on 2011-11-20
Unity grows on you. I find myself looking for the launcher and the dash on other OSs now. Much like any thing we use, once we customize it, mess with it to make it your way and use it 1000 or more hours, you begin to get the most out of it. 

EDIT: There was a poll on MNG Ubuntu, with 10.000 users or more, see if you can find it, asking what DE people were using. It was 43% Unity, 35% gnome-shell, a lot of 5% for the rest last time I saw it (one month ago, more or less). Of course, it's not a reliable methodology or sample, but it's something. Distrowatch is a joke.

---

### Post by Paddy Landau on 2011-11-20
> **effenberg0x0 said:**
> ... once we ... use it 1000 or more hours
Honestly, I really think 1,000 is a massive exaggeration. A single day is more than enough to get to grips with Unity; it is so easy and quick.

For the power users, I found [Jorge's Stompbox]("http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity") of help.

---

### Post by paul_in_london on 2011-11-20
> **effenberg0x0 said:**
> Unity grows on you. I find myself looking for the launcher and the dash on other OSs now. Much like any thing we use, once we customize it, mess with it to make it your way and use it 1000 or more hours, you begin to get the most out of it. 

EDIT: There was a poll on MNG Ubuntu, with 10.000 users or more, see if you can find it, asking what DE people were using. It was 43% Unity, 35% gnome-shell, a lot of 5% for the rest last time I saw it (one month ago, more or less). Of course, it's not a reliable methodology or sample, but it's something. Distrowatch is a joke.

This one?

[http://www.omgubuntu.co.uk/2011/11/which-desktop-environment-do-you-use-in-ubuntu-11-10-poll/](http://www.omgubuntu.co.uk/2011/11/which-desktop-environment-do-you-use-in-ubuntu-11-10-poll/)

I'm in the GNOME Shell camp.

---

### Post by effenberg0x0 on 2011-11-20
> **Paddy Landau said:**
> Honestly, I really think 1,000 is a massive exaggeration. A single day is more than enough to get to grips with Unity; it is so easy and quick.

For the power users, I found [Jorge's Stompbox]("http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity") of help.

At first I hated it, badly. Couldn't use the PC LOL... It really took me a while. I do an average of 16 hours/day on the PC.... took me about two months to really customize it the best way, find my apps and files easily, get things to become automatic, change it a little, etc. 

But others may adapt faster for sure. There are certain things in the design of it, like using the dash, the lenses, installing useful lenses and getting used to them instead of running the mouse top-right to the indicators, etc that required me some time.

But eventually, after that, I began to appreciate and understand the design concept and how it actually increases productivity. I think specially when you look at the code in a little more detail, you start to see what they want to achieve, how the thing will be in the future, etc, and it all makes more sense.

Although, as I use to say, it's just a damn launcher and a different menu in a Compiz plugin, it definitely it is somewhat of a change in paradigm (specially the dash, of course. The launcher is just a launcher). I think I'm becoming more mature as a user, in a way that I find that it is OK to have a nice looking desktop and waste a couple of CPU cycles with that and a little bling... The days of stripped DEs are kindda over for me :)

---

### Post by effenberg0x0 on 2011-11-20
> **paul_in_london said:**
> This one?

[http://www.omgubuntu.co.uk/2011/11/which-desktop-environment-do-you-use-in-ubuntu-11-10-poll/](http://www.omgubuntu.co.uk/2011/11/which-desktop-environment-do-you-use-in-ubuntu-11-10-poll/)

I'm in the GNOME Shell camp.

Yes, that's it. 15K votes now...it's basically gnome-shell and Unity running it. I don't think it looks bad at all. Both DEs have its weak and strong points, both are provided in the distro to be used. But Unity-FUD spreaders try to promote a much different scenario, like Unity was doing well worse. :) Then again, no poll is reliable. 

Actually, I find it more relevant to see XFCE topping KDE and gnome-fallback.

---

### Post by tlcstat on 2011-11-20
Greetings, I don't know what this has to do with PAE but I've been a Unity fan since day one. Dash works so well that I don't keep most of my apps on the side launcher. Finding docs are a breeze. Now there are more than enough tweaks to satisfy most users. It can only get better. I don't miss a desktop full of icons that are covered by windows. Who needs the clutter? 
tlcstat

---

### Post by effenberg0x0 on 2011-11-20
> **tlcstat said:**
> Greetings, I don't know what this has to do with PAE but I've been a Unity fan since day one. Dash works so well that I don't keep most of my apps on the side launcher. Finding docs are a breeze. Now there are more than enough tweaks to satisfy most users. It can only get better. I don't miss a desktop full of icons that are covered by windows. Who needs the clutter?  
tlcstat

Exactly... I found out I was addicted to having 100's of icons, obsessively arranged on my desktop in an specific order, always unaccessible behind the windows (I used to switch desktops to launch stuff). I was recreating this thing at every distro, every new release, year after year, etc. When it all got out of the away I kindda panicked a little. But changing the way I work had a positive effect... However, to a guy that does things sort of mechanically like me, it does take a while to adapt and then to finally understand and benefit from it. 

It's like when people were "betrayed by Microsoft" in the move from Windows 3.11 to Windows 95. I had friends moving to OS/2 Warp, etc. "How come this thing has no real DOS?" and "Who wants a OS that boots into the GUI directly?" were some of the common things people said back then. A year later people were adapted, using multitasking, the menu, the taskbar, multiple console windows in screen, developing for it in better IDEs, playing games without the need to boot the PC to a different set of config.sys and autoexec.bat for every game, etc, as if they always had that. Every change in paradigm, big or small, moves people in different levels. In our case here it is just a small change in the GUI, but for some it's a great impact.

---

### Post by tlcstat on 2011-11-20
Greetings,
> It's like when people were "betrayed by Microsoft" in the move from Windows 3.11 to Windows 95

Back in the early nineties when I was getting my electronics degree I actually told my electronics class "The day will never come when Windows will replace DOS". At that time I didn't know anything about linux. After all! Without all of the autoexec.bat and config.sys tweaks where's all the fun? But that didn't quickly disappear with Windows.
tlcstat

---

### Post by Paddy Landau on 2011-11-20
> **tlcstat said:**
> ... I actually told my electronics class "The day will never come when Windows will replace DOS".
So funny!

Think of all the other weird predictions that have been made. It's amusing to look at some of the predictions that were made in the 1960's regarding the turn of the century.

As Niels Bohr said, "Prediction is very difficult, especially about the future."

---

### Post by coffeecat on 2011-11-20
Ahem. *cough* *cough*.

This thread seems to have wandered up several side alleys. Let's get back on topic - 32-bit support in 12.04. :wink:

---

### Post by effenberg0x0 on 2011-11-20
> **coffeecat said:**
> Ahem. *cough* *cough*.

This thread seems to have wandered up several side alleys. Let's get back on topic - 32-bit support in 12.04. :wink:

Sorry :) I gotta hang out more at the Community Cafe.. I'm a talker.

---

### Post by Paddy Landau on 2011-11-20
> **coffeecat said:**
> Ahem. *cough* *cough*.

This thread seems to have wandered up several side alleys. Let's get back on topic - 32-bit support in 12.04. :wink:
It has been answered. 12.04 **will** support PAE-enabled 32-bit, but not non-PAE.

---

### Post by ventrical on 2011-11-20
> **coffeecat said:**
> Ahem. *cough* *cough*.

This thread seems to have wandered up several side alleys. Let's get back on topic - 32-bit support in 12.04. :wink:


 I have had some 500MHz machines work quite well and I am about to check to see if I can do an install of Precise on a 750MHz (32bit) machine. It has a 4MB SiS PCI graphics card  :) (please don't laugh out loud).

haehaeaeh

---

### Post by linuxusersince2008 on 2011-11-20
is it me or every new version of ubuntu is getting slower? it feels like i'm running windows vista? ubuntu 7
and 8 series used to be quick 9 was o.k but 10 series was getting very slow, or is it just me? ubuntu software center takes ages to start btw.:(

---

### Post by effenberg0x0 on 2011-11-20
> **linuxusersince2008 said:**
> is it me or every new version of ubuntu is getting slower? it feels like i'm running windows vista? ubuntu 7
and 8 series used to be quick 9 was o.k but 10 series was getting very slow, or is it just me? ubuntu software center takes ages to start btw.:(

I don't use my laptop much anymore. It's a Dual Core 1.6GHz, the slowest machine I have. But, last time I updated it, it was blazing fast for booting, shutting down, browsing, etc, standard apps. Now, Ubuntu Software Center can't really be a parameter for speed. Not only it is new software, it is known for being slow. I don't use this software. Fast software, like Chrome, seems to continues to be fast for me. Everyone I know that is using Ubuntu sees no difference in speed, as they were already using compiz previously.

However, wanting to run a hw accelerated opengl desktop on an old machine, that doesn't have a good GPU, or on a machine wlow on RAM, slow HDD, etc, will obviously produce bad results. If you feel like you are on Vista-speed, that might be the case. Ubuntu has never felt as slow as Vista for me.

Most of the time I'm on a PC that doesn't really count for measuring if the OS is heavy or not. It is running a custom low-latency kernel,  compiled from source with optimizations for the CPU, on Phenom II X6 3.3GHz with 6 cores overclocked to  3.9GHz, 16GB of ram, also overclocked Nvidia GTS450 1GB 128-bit vga  card, 2 x SATA3 SSD, etc. Even running Ubuntu, Eclipse, 3 simultaneous vmware VMs,  etc, the thing is absurdly fast. It's not the average hardware, it can't count on measuring current version speed.

---

### Post by ventrical on 2011-11-20
> **linuxusersince2008 said:**
> is it me or every new version of ubuntu is getting slower? it feels like i'm running windows vista? ubuntu 7
and 8 series used to be quick 9 was o.k but 10 series was getting very slow, or is it just me? ubuntu software center takes ages to start btw.:(

   The software center does take it's time for sure.  I decided to try out this old 32bit MoBo  (circa 1999) with Award BIOS/750MHz processor w 600MB SDRAM. I tried to install  11.10 so that I could upgrade to 12.04. No luck as the CD does not have boot options :) PLOP will also not work on this old girl. However .. I was able to stick a HDD in there with a previous install  of Kbuntu and I was able to fire it up in safe mode !!!

*note* Now this may sound off topic .. but just give me a minute here.  I'm not done experimenting yet. I just wanted to share an observation as to how  K10.10 had this neat video fall back safe mode and then it brought to mind to question why they don''t simply do this with GNOME classic for Precise! I mean it defies logic why the Precise kernel cannot present  a safemode option rather than a fall-back option. It seems that Precise/Oneiric kernel has the cart before the horse because video modes are called before LightDM is splashed hence it appears that 'X" can't be forced then into  a lower res standard display at that point. !

---

### Post by linuxusersince2008 on 2011-11-20
my video card is onboard sis . cpu is a pentium 4 1.7ghz with 512mb of ram i can't afford something that high
end. and beside i really don't like new tech well nothing newer then a pentium 4 or pentium dual core.

---

### Post by ventrical on 2011-11-20
> **linuxusersince2008 said:**
> my video card is onboard sis . cpu is a pentium 4 1.7ghz with 512mb of ram i can't afford something that high
end. and beside i really don't like new tech well nothing newer then a pentium 4 or pentium dual core.


  I have a Dell Inspiron 1.6GHz laptop with 1GB ddr running Edubuntu 12.04  It works just beautiful  but the only problem is the 4200rpm hdd. It runs a bit slow.  The 7200 ide's or SATAs are a lot quicker. I use all my faster drives on stable systems (with the exception of isolated drives with Precise) on faster machines. No offence but sounds like you need another ddr stick - however, I had an Intell MoBO with 2.66 GHz with 512 working just great with Precise.

---

### Post by Paddy Landau on 2011-11-21
> **linuxusersince2008 said:**
> is it me or every new version of ubuntu is getting slower?
That will happen. Even Linux has to move with the times ;), which means that it has to take advantage of newer graphics cards, newer desktop paradigms, bigger programs.

That's why we also have distros for older machines, [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") being a great example.

> **linuxusersince2008 said:**
> ubuntu software center takes ages to start
Canonical knows about this problem and has been working hard to speed its start-up time. If you are interested, see *"In The Press"* in the [latest newsletter (#241)]("https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue241"), where there are three separate references to the Ubuntu Software Centre performance enhancements.

---

### Post by jerrylamos on 2011-11-21
> **linuxusersince2008 said:**
> my video card is onboard sis . cpu is a pentium 4 1.7ghz with 512mb of ram i can't afford something that high
end. and beside i really don't like new tech well nothing newer then a pentium 4 or pentium dual core.

My 1.5 GHz Pentium Thinkpad 750 MB running Oneiric Ocelot Unity-2D O.K.  Lubuntu Oneiric Ocelot seems a bit faster response.
'
I have an older 1.0 GHz Celeron 512 mb running Oneiric Ocelot Unity-2D O.K., except internet videos rather jerky.  A bit jerky on Lubuntu Oneiric Ocelot as well.

This is a Acer Aspire one $250 netbook 1 GB 1.66 GHz, Oneiric-3D will run but I use -2D because I don't like fuzzy edges and foggy windows that Compiz loves.  Anyway, internet videos just fine.  I have seen this netbook on sale a bit lower than $250 from Walmart.

I don't consider $250 "high end".  It'll run anything I've seen from Ubuntu just fine.  And yes, if the 1024 x 600 screen is a bit small, it will run a 1280 x 1024 external monitor just fine.  And if the keys are small for your fingers it will run an external full size keyboard just fine.  At that point it's like a little tower with an external keyboard and external monitor.

Right now I'm running Precise Pangolin on the netbook from a usb hard drive. 2.5" hard drive I had laying around in a $20 case.  I can't tell the difference in speed between the USB hard drive and the native 250 GB hard drive.  

I'm running "unstable" Pangolin from the USB in hopes of not screwing up the native hard drive which is triple booted with Oneiric, Meerkat, and Windoze....7.

Jerry

---

### Post by linuxusersince2008 on 2011-11-21
hey i'm working on my own version of opensuse, with susestudio can anyone help me getting the older
version of gnome desktop environment? like 2.0.2?:D

---

### Post by thatguruguy on 2011-11-21
> **linuxusersince2008 said:**
> hey i'm working on my own version of opensuse, with susestudio can anyone help me getting the older
version of gnome desktop environment? like 2.0.2?:D

Absolutely.  You may want to check [here]("http://forums.opensuse.org/"). I'm sure they'd be glad to help.

---

### Post by linuxusersince2008 on 2011-11-21
thanks :)

---

### Post by linuxusersince2008 on 2011-11-21
btw is there anyway to install an older version of gnome into ubuntu 11.10?:D

---

### Post by Paddy Landau on 2011-11-21
> **linuxusersince2008 said:**
> ... install an older version of gnome into ubuntu 11.10?
I would not recommend it. It will break all sorts of dependencies.

If you don't like Unity, rather go for a different distribution. [Xubuntu]("http://www.xubuntu.org/") (uses XFCE); [Lubuntu]("https://wiki.ubuntu.com/Lubuntu") (uses LXDE, suitable for low-spec computers); [Mint]("http://www.linuxmint.com/") (a derivative of Ubuntu); [Fedora]("http://fedoraproject.org/"); [OpenSUSE]("http://www.opensuse.org/"); and others.

---

### Post by cariboo on 2011-11-21
> **linuxusersince2008 said:**
> btw is there anyway to install an older version of gnome into ubuntu 11.10?:D

11.10 is based on GTK3, you'd have to recompile most of the distribution to use GTK2. There is some backward compatibility built in, but you'd be better off going with an older version that uses GTK2.

On your system, the biggest drawback is the video card, it may be worth your while to give the [SIS]("http://www.sis.com/default.aspx?region=en-global&m=72") devs a poke, as they said they were going to create a new driver, as far back as Lucid.

---

### Post by linuxusersince2008 on 2011-11-23
i know i should post a new thread but does anyone know how i can modify ubuntu 8.04? like upgrade firefox,
ubuntu software center and the kernel with out upgrading the reversion? oh this setup won't be my main
for long i'm building a new one. it's a dual pentium 3 computer motherboard is a asus cuv4x-d if you want to look it up :)i want to upgrade these components in the iso then install.

---

