---
title: "Severe Disappointment"
date: 2011-03-26
forum: Testimonials &amp; Experiences
---

### Post by Thugdog Nasty on 2011-03-26
In 1997, I installed Linux  on my desktop computer and was an instant huge fan.  I used it exclusively for the next seven years, and then I went to OS X.

Over the last few years, however, I have heard great things about Ubuntu.

“It’s a replacement for Windows”, “it just works”, etc, etc, etc.

Well, I bought the hype.

This week, after a malware issue, I convinced a family member to let me scrub Windows from her machine and install Ubuntu.  It seemed like a no-brainer.  After all, her computer was so common that it was ridiculous.

Core 2 Duo, 4GB RAM, 1TB Hard Drive, Intel X3100 graphics (perhaps the most common budget graphics chip made over the last 5 years).

Everything about this machine is ordinary.

The monitor is a three year old 21” Samsung Syncmaster with a native resolution of 1600x1200.

Again, boring boring boring.

And so, I downloaded 64-bit Ubuntu, went through the install, and everything seemed to go fine.

When we booted the desktop, however, we noticed that the screen resolution was 1024x768.

Yuck.

It looks truly awful.

And so, for the last two days, I have been searching for a fix.  I’ve thrown every xorg.conf file I can find at the issue, but to no avail.  It either doesn’t work, or it locks up the reboot causing a hard reset.

At this point, she wants Windows back.  “Windows has it’s problems but at least it lets me clearly see what I am doing”, she said.

And she’s right.

Sure, someone who has kept up with the technicalities of Linux could probably solve the issue, but is not the point of Ubuntu to not have to research for hours just to get a screen resolution to work?

So, I sit here embarrassed.

Embarrassed that I so strongly recommended Ubuntu.  Embarrassed that I told her it would “just work” (since the hardware specs were deemed okay).  I’m sure she will be quite wary of my recommendations in the future.

Also, however, I am embarrassed for Ubuntu.  Embarrassed that it fails such a ridiculously common desktop hardware install, and embarrassed that I have not been able to find a fix in support.

I have before me what is arguably the most common, plain, conservative, most uninspired desktop computer ever made, and Ubuntu cannot convince the graphics card to paint the screen at native resolution.

It’s just embarrassing all around.

You have to get these common desktop installs right.  You simply have to.   Failure is not an option.

At least it’s not an option if you expect to gain any ground among average computer users.

In any event, I’ve got a couple more hours to figure it out, and then it’s back to Windows.

I tried to put another user in your camp, Ubuntu.  

I tried.

---

### Post by Bucky Ball on 2011-03-26
What release did you install? 10.04 LTS (long term support) is the most stable and the one to go for for your situation.

Have you looked in System>Administration>Additional Drivers? Anything there? I am presuming you have the machine online and have installed all the updates since you installed. If not, System>Administration>Update Manager.

Please remember: Canonical and Ubuntu are not responsible for and have no say in how hardware manufacturers go about licensing firmware and drivers. That is up to the manufacturers. They can release open-source drivers, Linux drivers, or make it difficult meaning endless workarounds and headaches for users. As many graphics and wireless softwares are licensed and generally not 100% open-source, many of these drivers and firmwares ***can not*** be included in the install ISO by law. You need to download personally and agree to various conditions of use set out by the manufacturer before they can be installed. By law. This has nothing to do with Ubuntu, Canonical, developers, users ... that is just the way it is. ;)

A lot of things will work 'out of the box', but you need to be online generally to get drivers and firmware, then know where to look for them.

---

### Post by uRock on 2011-03-26
Can you tell us what you have and haven't tried to do to fix it?

Have you went in the menus to System> Preferences> Monitors and made any adjustments to at least get the proper screen ratio?

> (perhaps the most common budget graphics chip made over the last 5 years)I think nVidia has that bragging right.

---

### Post by Thugdog Nasty on 2011-03-26
It is version 10.10.  I downloaded the latest Ubuntu version directly form their download section.

I have installed the additional drivers, and I have done absolutely everything with the GUI admin and settings tools. (note: 1600x1200 is not available in the GUI admin screens)

I have also scoured the Internet for a xorg.conf files from people that might possibly have similar configs to this one.

The machine is online and otherwise functions.

---

### Post by linuxuser12345 on 2011-03-26
There is a simple fix to this problem: Go to the top toolbar, click "System", go to "Administration", then go to "Additional Drivers".
Something that also might work is going to "System", "Preferences", then "Monitors" and directly changing the resolution.

If neither of these work, download Ubuntu 10.04.2 LTS "Lucid Lynx" and install it to a thumb drive. Install this and remove the 10.10 installation. This may fix the problem. You can then (if you want) try manually upgrading back to 10.10 through the Software Update process, and it will probably keep any drivers, configuration, etc. that it needs to keep.

---

### Post by linuxuser12345 on 2011-03-26
You can also try looking for the specific Intel program to manage the graphics chip, like AMD has the ATI Catalyst Control Center for it's AMD/ATI Radeon GPUs

---

### Post by Thugdog Nasty on 2011-03-26
> **linuxuser12345 said:**
> There is a simple fix to this problem: Go to the top toolbar, click "System", go to "Administration", then go to "Additional Drivers".
Something that also might work is going to "System", "Preferences", then "Monitors" and directly changing the resolution.

Tried both again.  No additional propriety drivers available, 

No option for the 1600x1200 in monitor screen, and no place to manually change the resolution.

> If neither of these work, download Ubuntu 10.04.2 LTS "Lucid Lynx" and install it to a thumb drive. Install this and remove the 10.10 installation. This may fix the problem. You can then (if you want) try manually upgrading back to 10.10 through the Software Update process, and it will probably keep any drivers, configuration, etc. that it needs to keep.

I don't have a thumb drive at my disposal at the moment, but thanks.

---

### Post by linuxuser12345 on 2011-03-26
You don't have any CD-Rs? You can probably find somebody with one they can give to you! lol

---

### Post by Bucky Ball on 2011-03-26
I would also try 10.04. You can run it off the disk to see if you get any joy (no need for thumb drive) or just install it over the current install and see how you go (manual partitioning and you can use the partitions you have created, install the OS to the / partitions, don't format /home if you have one and /swap).

One other thing; 10.10 uses grub2. It is very different from grub legacy so any advice you get for that is not going to be much help to you (although you might get some ideas).

---

### Post by hakermania on 2011-03-26
All you can install from USB :P

---

### Post by Thugdog Nasty on 2011-03-26
> **linuxuser12345 said:**
> You don't have any CD-Rs? You can probably find somebody with one they can give to you! lol

Yeah, not for nothing, but if the fix is to re-install the OS, an old version of the OS at that, then I think Windows might be the right way to go.

I mean, imagine if the fix to a Vista driver was re-installing XP from scratch and performing a software update from there.

Jesus, fellas.

---

### Post by Bucky Ball on 2011-03-26
> **hakermania said:**
> All you can install from USB :P

OP has indicated they don't have one. Please read all posts. ;)

---

### Post by Thugdog Nasty on 2011-03-26
Just for the sake of asking, does anyone have this card with a working xorg.conf file?

---

### Post by bkratz on 2011-03-26
> **Thugdog Nasty said:**
> Just for the sake of asking, does anyone have this card with a working xorg.conf file?



You might try PMing this poster, he seems to have had the same problems. Perhaps he/she has a solution.

[http://ubuntuforums.org/showthread.php?t=1068673](http://ubuntuforums.org/showthread.php?t=1068673)

---

### Post by Dutch70 on 2011-03-26
Welcome to the forums 

10.04 is not necessarily an old version as compared to XP. It's an LTS (Long Term Support) version, which means it has support for 3 years as opposed to 10.10 being 18 months. If you're installing on someone else's computer for them. The best thing to do would be install an LTS version.

If you think of 10.04 as an old OS compared to XP, then in about 1 month, when 11.04 comes out, you'll be thinking of 10.10 the same way.

> I mean, imagine if the fix to a Vista driver was re-installing XP from scratch and performing a software update from there.

Jesus, fellas.

If you only knew how ridiculous that statement really was, you wouldn't have said it. 10.04 & 10.10 are almost the same thing, except for the length of support & possibly that 10.04 is more stable.

Edit: Have you checked this thread? 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=269052[/COLOR]]("http://ubuntuforums.org/showthread.php?t=269052")

---

### Post by Learning Linux 2011 on 2011-03-26
I have an Intel 3500 graphics chip and I can tell you that it works at 1280x1024 at least.
I am using a Dell 17" LCD, and its maximum resolution is 1280x1024 so I can't go any higher anyway.

I might guess that the 64-bit OS might be the problem.

If I were you, I would download the 32-bit version, burn it to disc and boot using the live cd option.  See if that fixes it.

If she only has 4GB of RAM, she doesn't need the 64-bit anyway.

---

### Post by tredegar on 2011-03-26
X is getting quite smart nowadays, and tries to calculate for itself the settings we used to have to put into **xorg.conf**

But it needs to find out about your hardware before it can do this, and I think this is where the problem lies: Some monitors do not report their EDID information correctly, and so their capabilities are not fully appreciated or used.

Please take a look at **/var/log/Xorg.0.log** and see if you can work out what isn't working. My guess is the monitor's EDID isn't being read correctly. This may be the monitor's fault, or the connector's fault.

How is your monitor connected (standard VGA connector, or something else)?

---

### Post by heyho on 2011-03-26
Not sure that using somebody else's .conf file is ideal, unless they have the exact same hardware, including monitor.

I would also vote for a clean install of 10.04(32bit).

Also, if you are connected via VGA, check that you are using a good quality, fully pinned cable.

---

### Post by uRock on 2011-03-26
> **heyho said:**
> I would also vote for a clean install of 10.04(32bit).
Why would you recommend someone use a 32bit OS on a modern 64bit system? That'd be pointless.

---

### Post by johntaylor1887 on 2011-03-26
> **Thugdog Nasty said:**
> 
You have to get these common desktop installs right.  You simply have to.   Failure is not an option.


You think this is a universal experience?

I once had a terrible experience with windows. I guess if windows wants to keep from losing all its users, they had better get these common desktop installs right.

---

### Post by Learning Linux 2011 on 2011-03-26
I'm not an expert, but if you look in /usr/share/doc/xserver-xorg-video-intel
there is a readme file in there that tells you what is supported and also directs you to [http://intellinuxgraphics.org](http://intellinuxgraphics.org)

That apparently is Intel's linux driver page.

[http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html)   tells you about what is supported.

---

### Post by Learning Linux 2011 on 2011-03-26
Also, make sure you have updated the entire system and kernel with the 
"System > Administration > Update Manager

---

### Post by Learning Linux 2011 on 2011-03-26
This might be blasphemous, but before giving up on Linux over something like screen resolution, try other distributions like Fedora.

---

### Post by stoneage on 2011-03-26
You could try working through this:-
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by Thugdog Nasty on 2011-03-26
> **johntaylor1887 said:**
> You think this is a universal experience?

I once had a terrible experience with windows. I guess if windows wants to keep from losing all its users, they had better get these common desktop installs right.

I tried the Live CD on 10.04, same deal.  

John, as I said, the card and monitor are EXTREMELY common.  Aside from video card and monitor, there's not much else that can be at fault.

As such, yes, this would be a universal experience across this combination of video chip and monitor and yes, Windows would lose a lot of installs if they didn't support it.

They do, though.

I loved Linux for a long time, and I'm sure I will again, but this is a show stopper.

Remember, "it just works" has got to become a semi-reality before mass adoption occurs.  Few people are going to try downgrading/reinstalling/and pulling up vi.

Imagine if she popped in the install CD herself.  Do you think she would still be a Linux user?

She would have abandoned it long ago, and you have no idea how many people have already done that.  There are no stats for it.  I'm starting to think that those numbers may be larger than you think, especially give the anemic hardware on this one.

I would understand if we had a $1,500 megadope FX BZ450000232 graphics card released in March of 2011, but this thing is so common that I would offer the opinion that getting this hardware right is a baseline.


I'm sorry, that's just how I feel about it.

I'm sure things will get better as development continues.

---

### Post by Thugdog Nasty on 2011-03-26
> **stoneage said:**
> You could try working through this:-
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Thanks, this looks promising.  Let me see if I can make something happen.

---

### Post by heyho on 2011-03-26
> **uRock said:**
> Why would you recommend someone use a 32bit OS on a modern 64bit system? That'd be pointless.

I'm not the first person in this thread to recommend it.

On the official download page, it is the recommended version.  The general consensus seems to be that it is also more stable, and that most programs are still built for 32bit systems.

Only trying to help.

---

### Post by ARMNHIE on 2011-03-26
You could update, reboot, check hardware drivers via System > Administration > Hardware Drivers. Or try going to System > Preferences > Monitors and seeing if that works. Or fire up a terminal and type lshw, find your graphics card (should be under a pci), and find the support online, if the basic update, reboot stuff doesn't work.

I would also like to add that I'm with the others. I would definitely install 10.04 LTS. I had 10.10 installed for a while. I liked it but I won't lie there were just a few bugs. 10.04, however, has worked fine with everything I want and need it to do. No complaints, other than I wish I could spend all day everyday on it. And I'm not just your basic internet surfer and solitaire player. I have it on my laptop, my desktop pc, installed it on a friend's laptop, and talked some of my family into using it. When my girlfriend and I got together she hated using my computers like anyone would who was uncomfortable with any other operating system other than ever using Windows. But within a few months she started begging me to install it on her laptop. I'm just lazy and haven't gotten to it, even though it's easy as cake.

I won't lie, and I think others would back me up on this, Linux isn't for everyone. Ubuntu Linux is just the closest you get to a Windows environment. Keyword - close. Not exact. The thing with Linux is that you make it what you want. Here's what happens with Windows: Let's say you have your beloved Windows on your laptop or desktop pc. And let's say you only use about 20% of what came with your Windows operating system. Even though you're only using that 20%, Windows will probably/probably (is) run(ning) the other 80% in the background logging, saving random files, importing internet junk, etc. Now, with Linux you build it to what you want to be. It will only go as big as you build it instead of coming preloaded with A LOT of stuff you probably won't use. So my point is, your software comes with the minimum basics. And you build it to what you want. It sounds intimidating, frustrating, annoying, etc. But it's not. It works for you instead of against you. It does what it's told instead of these other operating systems telling you what it will and won't do. Please don't be disappointed with Ubuntu. There is all kinds of support out there for whatever your problem is.



[http://www.mybuntu1.com](http://www.mybuntu1.com)

---

### Post by Dutch70 on 2011-03-26
You can rest assured that mass adoption is the last thing most of us want.

---

### Post by terry_gardener on 2011-03-26
hope you can get this sorted thugdog. 

you might think these are common hardware but i don't agree with the statement that it is linux and it should just work. 

it is impossible to have a OS that just works with every hardware configuration out there, even windows doesn't do it. 

i find it amazing that linux supports so much out of the box. 

i have installed ubuntu, other linux distros and windows on countless hardware configurations and sometimes it is not plain sailing even on windows when it comes to driver support. 

windows has the perception of hassle free installs because the PC comes with the OS already installed and ready, usually with alot of bloatware to go with it. 

i just don't agree or like the idea that people think you can pick you a cd with ubuntu or any other linux distro on it install it and it should work out of the box with all the hardware in there computer no matter what it is. 

just my .02 pence worth

---

### Post by Chronon on 2011-03-26
> **heyho said:**
> I'm not the first person in this thread to recommend it.

On the official download page, it is the recommended version.  The general consensus seems to be that it is also more stable, and that most programs are still built for 32bit systems.

Only trying to help.

Most programs are also built for 64-bit systems.  I don't think availability of binaries is a sensible reason to avoid 64-bit these days.

---

### Post by tgm4883 on 2011-03-26
> **heyho said:**
> I'm not the first person in this thread to recommend it.

On the official download page, it is the recommended version.  The general consensus seems to be that it is also more stable, and that most programs are still built for 32bit systems.

Only trying to help.

The general consensus (even if there is one) is built on old outdated information. 


To the OP, I have a 3150 in my netbook (HP Mini 210), and it worked out of the box with 10.04. The resolution is 1024x600.

---

### Post by Learning Linux 2011 on 2011-03-26
I think you are being overly dramatic about this.  You could easily solve this woman's problem by purchasing a cheap video card either through the internet or a local store.
I doubt the 3100 is the most common.  Linux supports practically every other Intel video chipset.

---

### Post by TroN-0074 on 2011-03-26
You can try the macbuntu theme when you install through the command line it downloads everything you need to have a crisp display.
Here is the link
[http://macbuntu.sourceforge.net/](http://macbuntu.sourceforge.net/)

---

### Post by Dlambert on 2011-03-26
Latest x-org Edgers drivers? Could be some setting in the bios?

---

### Post by jhargis1012 on 2011-03-26
Honestly, I sympathize with the topic creator. I love Linux, and I love Ubuntu, and I personally greatly enjoy getting to the bottom of some incompatibility and the satisfaction that follows figuring things out. Yet, I'm pursuing a degree in IT. My experience will be far from the average user's.

I've been having a slightly similar experience to that of the topic creator in trying to bring my brother into Ubuntu. He's not quite so tech minded, but the idea of Ubuntu and Linux appealed to him. Well, he's been having trouble with it too, and I've heard such things as "I want to go back to Windows... it just worked." You just feel bad when you hear these things and you don't know what to tell someone. You don't blame them for wanting to go back.

I think the Ubuntu community would do well to take what this guy is saying into consideration with more understanding, thinking what can be done to bring an approachable experience that the user is looking for. This seems more productive than being defensive about it.

Just my thoughts.

---

### Post by johntaylor1887 on 2011-03-26
> **Thugdog Nasty said:**
> 

Remember, "it just works" has got to become a semi-reality before mass adoption occurs.

Let me tell you a little story. I had 4 computers all brand new with no OS on them. They all had an Intel video card in them. Guess what? No matter what driver was tried, resolution in win7 could not get above 800x600. The video card had been out for at least a year or 2. I had to install windows xp on them because xp had all the correct resolutions.

What would somebody think if they were to purchase one of these machines and went out and bought win7, only to find out they could not get the correct resolution? You are kidding yourself if you think windows is some magical OS that always works perfectly.

Btw, I've installed ubuntu on probably over 25 different computers without 1 single problem. That's damn good if you ask me. I've had much bigger problems with windows than with linux.

If you're computer is not linux compatible, go buy one that is, or stay with windows. Simple. No need to bash linux because *your* computer is having problems.

I would like to go to the windows forums and complain every time I get frustrated with it, but I fear it would do no good, and only get people upset.

Finally, who says ubuntu/linux *needs* mass adoption? I think most people don't really care that it is only used by a small number of people, relatively speaking. My life goes on either way.

---

### Post by johntaylor1887 on 2011-03-26
> **jhargis1012 said:**
> thinking what can be done to bring an approachable experience that the user is looking for.

Instead of buying a pc with windows preinstalled, why not buy one with linux preinstalled. Makes sense, right?

---

### Post by I2k4 on 2011-03-26
Is 64-bit necessary?  I'm running Lubuntu 10.10 off Live USB in 32-bit on a SyncMaster at 2048 X 1152 no problems.  Have to say, I don't think 64-bit OS has reached that level of reliable "ordinariness" that buyers might think they get.  I'm sure 64-bit is someplace on the totem pole of Ubuntu development priorities, but wouldn't bet it's at the top.

---

### Post by fabricator4 on 2011-03-26
> **Thugdog Nasty said:**
> Thanks, this looks promising.  Let me see if I can make something happen.

If it's just screen resolution, It sounds like the monitor is not passing the EDID data along correctly.  Strangely enough, some monitors seems to have trouble.

I work through a KVM switch for two machines so I _do_ have a problem getting the EDID data passed through at boot time.  The solution that worked best for me (and has for about two or three years now) is to put the correct sync data in xorg.conf.  Not only does it just work, but it's by far the simplest method.  I tried defining all the modes etc but usually finished up with X not running at all.  This just works and all you need to know is the horizontal sync and Vertical refresh for your monitor.  Here's my entire xorg.conf:

```

Section "Monitor"
	Identifier	"Samsung 1100p"
	Horizsync 30-110
	Vertrefresh 50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Samsung 1100p"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

I'm actually not sure if anything other than the monitor section is necessary.  I got it working years ago and never changed it, except once I changed my monitor.

Chris.

---

### Post by johntaylor1887 on 2011-03-27
> **I2k4 said:**
> I'm sure 64-bit is someplace on the totem pole of Ubuntu development priorities, but wouldn't bet it's at the top.

64bit ubuntu works perfect *for me*. Have you tried it?

---

### Post by fabricator4 on 2011-03-27
> **Thugdog Nasty said:**
> Yeah, not for nothing, but if the fix is to re-install the OS, an old version of the OS at that, then I think Windows might be the right way to go.


It's not an "old" version, it's the current LTS (Long Term Support) release.  It's my everyday OS on three of my four main computers (see my sig).

Why do I use 10.04 instead of stampeding to use every new version that comes out?  Because it's the "boring" safe option that will almost always work.  The only time I _don't_ recommend the boring option is when there's required hardware support in a newer version that isn't in the LTS release.  Having said that: I've noticed that hardware support for some things that was better in 10.10 on my 900SD has now been ported back into 10.04, probably as part of the LTS philosophy.

Most people new to Ubuntu tend to grab the absolute latest version and skip over the LTS release.  This is a mistake.  A first time user just want the OS to work (be boring), they don't want the experience to be exciting (have the potential to require lots of work to get things running smoothly).

I really appreciate the 6 month release schedule that the Ubuntu developers stick to.  It's amazing was is achieved, and it makes the whole distribution a very "exciting" thing to be part of.  I like putting bleeding edge software on my computer and seeing with the current state of the distribution is, but pardon me if I also like to keep my boring old LTS releases for everyday use and if I recommend it to newcomers over any release that has just come out of a six month development cycle. ;-)

Chris.

---

### Post by I2k4 on 2011-03-27
> **johntaylor1887 said:**
> 64bit ubuntu works perfect *for me*. Have you tried it?

Nope, machines don't support 64-bit.  Doesn't matter, does it?  What matters is that the initial poster tried it, it didn't work on his monitor, and he's apparently trying all sorts of gobbledygook to try to make it work.

On my same Samsung monitor, 32-bit version, it was a simple one click setting in Preferences > Monitor Settings with no grief.  Only just thinking.  If you have a good suggestion about your experience with monitor resolution, please do share.

---

### Post by tgm4883 on 2011-03-27
> **I2k4 said:**
> Nope, machines don't support 64-bit.  Doesn't matter, does it?  What matters is that the initial poster tried it, it didn't work on his monitor, and he's apparently trying all sorts of gobbledygook to try to make it work.

On my same Samsung monitor, 32-bit version, it was a simple one click setting in Preferences > Monitor Settings with no grief.  Only just thinking.  If you have a good suggestion about your experience with monitor resolution, please do share.

I think the point is that you are jumping to a conclusion that 64-bit is the issue, with absolutely nothing to back up that claim.

---

### Post by rjbl on 2011-03-27
[QUOTE=Thugdog Nasty;10603626]

[I]Core 2 Duo, 4GB RAM, 1TB Hard Drive, Intel X3100 graphics (perhaps the most common budget graphics chip made over the last 5 years).

[/I]Funny you should say that. 

On Feb 14th 2011 I built a box with that spec to run MS FSX / MS FS2004. I tried installing Windows 7 Home Premium (32bit) and could only get 1024 x 768 output to an el cheapo Hanns-G Widescreen. So I fitted a cheap ATI 1Gb card and was able to get, with the latest driver found and installed, an unstable 1368 x 768 x 32 output whose sync failed consistently after 35 minutes flying in FSX. Did that P*ss me orf with Windows 7? Nah .... that moment came about a week later when I downloaded and installed Windows 7 SP1. It borked my box and made it unbootable. So I had to buy XP Home SP3 and rebuild around that OS.

My Linux Box? The cheapest available foxconn, single core AMD 3800+ CPU, 4Gig, on board Nvidia graphics and audio. Ubuntu 10.04 LTS (32bit). The fastest, cleanest, install and configuration I have ever, repeat ever, seen (I've been in PC's since 1985). The box does all my stuff except Microsoft Flight Simulator and has worked flawlessly for 12 months. Ain't complaining about Ubuntu. Windows 7? Well, Sh*t happens, with every MS OS since MS DOS 2. Twas ever thus.

rjbl

---

### Post by Timmer1240 on 2011-03-27
Im severly Satisfied with Linux Darnit!I wont lie though it did take me a good day to figure out how to get my printer to print with it but I knew that was part of the fun!Once you get it all set up and sometimes it takes some work it really flies!

---

### Post by armandh on 2011-03-27
first of all try a different monitor

I have two that are defective in their PnP

thus the OS defaults and does NOT want to go to unsupported resolution.

the work around is a monitor that that does work and save the X config.
then try the one with a failure to communicate.  
just dont get stuck in an unsupported rez.

---

### Post by el_koraco on 2011-03-27
it all comes down to individual experience. since win 2000, which worked flawlessly on my first workstation, as opposed to the horrendus win 98, i've installed xp, vista, and win 7 about ten times (not counting the reinstalls every year or so), and 90 percent of the time i had the situation of not having three or four critical drivers, one of which was always the wireless one. without an ethernet cable, this can get really annoying. i guess it's my fault, for never having bought one. in fact, this is the reason i initially switched to ubuntu, which never presented me with these dilemmas. 

it's just hardware and software, things are bound to get ugly at some point in time, you shouldn't take it personally. it's not like ubuntu has anything against you and your wife.

---

### Post by malspa on 2011-03-27
Thugdog Nasty, good luck with whatever you decide to do. Lots of very happy Linux users out here, and lots of very happy Ubuntu users; too bad if you can't make it work for you. 

Reading your posts, I kept thinking back to something I read when I was first starting out with Linux, something about the necessity of creating the right environment for Linux to run in... That seemed like a good starting point, to me. 

The other thing I kept thinking about early on was that there are so many folks out there who are happily using Linux so I should be able to do it, too.

So, I don't know. Windows-free for some years now, here. Again, good luck.

---

### Post by Thugdog Nasty on 2011-03-27
Well, thanks for all of your help (for those that provided it).

I spent the past 8 waking hours playing with xrandr, cvt, addmode, etc.  

Oh, I also downgraded to 10.04.  It worked fine, albeit in the same lower resolution.

Honestly, I think the solution lied in a good working xorg.conf file or the right combo of xrandr and newmode, but I just couldn't get it exactly right.

Ubuntu repeatedly move this post and once it hit this particular forum, the usefulness of suggestions dropped off a cliff (thanks Ubuntu!).  I understand the original post was a bit of a mix, but you should make a decision and stick with it instead of kicking it all over the place.

You should never throw a support question to fanboys.  The hostility and silliness will repel all of those making a serious effort.  I promise.  

Once the "buy a new computer" comments started, I rolled my eyes, called it a day, and re-installed Windows on the machine.

It works great, but I have to keep an eye on malware, viruses, etc.  I would have personally preferred Linux, but her patience ran out and buying new hardware to make screen rez work was not on her acceptable lists of solutions.

I understand that every OS has it's problems, but usually with Windows, a solution can typically be found within a day that doesn't involve, you know, buying a new computer/monitor/video card.

It is what it is.

I think Ubuntu is a great OS for people with time and technical inclinations, but for the average consumer desktop, it's just not ready in my opinion.   One of the great things about the OS used to be being able to bring slightly older hardware back to life, but it didn't happen in this case.

Honestly, I am surprised.  Back in the late 90's - early 00's, I installed Linux on literally dozens of machine, and it was smoother than than it is now if you can believe it.  I even had a triple-headed linux workstation myself that only took about an hour to get right.

Please don't take this the wrong way, but back then there was also waaaaay more intellectual support.  I swear to god, if I had a problem, I threw it up on a Red Hat newsgroup and it was solved by the time I hit "enter".

Ironically, perhaps Ubuntu's general ease of use has attracted a slightly less cerebral crowd in the support forums which have, in my opinion, taken on Mac-forum-type insults and "it works for me therefore the don't insult my OS!" responses.  I found myself longing for the old days when the guys participating in the groups were some of the best and brightest on the Internet.  I envied the intelligence of those guys (who were far smarter than I) and really miss them.  They never told me to buy a new computer, and there wasn't a problem they couldn't help me overcome.  I guess they're getting paid for support now while the wannabes who found Linux three years ago try to take their place.

In any event, for those with good suggestions (and there were certainly some which I GREATLY appreciate), thank you very much for you time.

I'll revisit Ubuntu again in the future when I get a new machine for myself, and I have time to spend with VI and config files.

I would like to become proficient with Linux once again, but you have to pick your battles and this is not one I have the time to wage at current.

Thanks again.

---

### Post by Thugdog Nasty on 2011-03-27
> **johntaylor1887 said:**
> Instead of buying a pc with windows preinstalled, why not buy one with linux preinstalled. Makes sense, right?

Yeah, that makes perfect sense.  Thanks.

---

### Post by Thugdog Nasty on 2011-03-27
> **Learning Linux 2011 said:**
> I think you are being overly dramatic about this.  You could easily solve this woman's problem by purchasing a cheap video card either through the internet or a local store.
I doubt the 3100 is the most common.  Linux supports practically every other Intel video chipset.

The x3100 is (was?) incredibly common.  It was the default onboard Intel chip for 2-3 years, and it is on the list you printed.   It uses the 965.

---

### Post by Thugdog Nasty on 2011-03-27
> **johntaylor1887 said:**
> If you're computer is not linux compatible, go buy one that is, or stay with windows. Simple. No need to bash linux because *your* computer is having problems.

k

I'm on my way to buy one that is.  Sorry for bashing Linux.

---

### Post by johntaylor1887 on 2011-03-27
> **Thugdog Nasty said:**
> k

I'm on my way to buy one that is.  Sorry for bashing Linux.

That's the spirit! I hope you enjoy it.

---

### Post by Thugdog Nasty on 2011-03-27
> **Dutch70 said:**
> You can rest assured that mass adoption is the last thing most of us want.

Clearly.

---

### Post by tgm4883 on 2011-03-27
> **Dutch70 said:**
> You can rest assured that mass adoption is the last thing most of us want.

I think you are speaking for yourself. I think most people would was a higher adoption rate.

---

### Post by tgm4883 on 2011-03-27
To the OP, I wonder if it's the monitor giving incorrect EDID information. I've seen that happen with some monitors although usually it is with TV's giving the incorrect info.  

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

---

### Post by galacticaboy on 2011-03-27
I had this same problem when I tried Fedora, the resolution was all out of whack. I tried everything, changing the resolution did not work, updating my drivers did not work. I tried it all. I switched to Ubuntu and it was all fine. But it turns out, it was my old CRT monitor, it was the problem. Try another monitor. You can find cheap CRT monitors on craigslist or thrift stores. Or try a newer monitor. Just a thought!
David

PS- Please do not give up on Ubuntu, this is the best!

---

### Post by uRock on 2011-03-27
The OP is working on a family member's PC. I am sure the owner does not want to buy a new monitor to make the OS work.

---

### Post by tredegar on 2011-03-27
> **tgm4883 said:**
> To the OP, I wonder if it's the monitor giving incorrect EDID information. 
That's what I posted at [#17]("http://ubuntuforums.org/showpost.php?p=10603875&postcount=17"), with a couple of questions for clarification.

No response though :(

---

### Post by fabricator4 on 2011-03-27
> **Thugdog Nasty said:**
> 
Honestly, I think the solution lied in a good working xorg.conf file or the right combo of xrandr and newmode, but I just couldn't get it exactly right.

Did you try just setting the sync frequencies in xorg.conf?  I too tried all the other mode setting parameters and couldn't get anything to work.  Perhaps it just seemed too simple and easy a solution?  Some feedback on the method would be good if you did try it - I've never actually had anyone say they tried it and it didn't work.

> 
You should never throw a support question to fanboys.  The hostility and silliness will repel all of those making a serious effort.  I promise. 

True, but to be fair your original post started with a rant...  not the question.  Of course you're going to get mostly noise in return.  If you just stick to the question on hand you'll only get solutions in reply.  The rest of the post I'm replying to is similar opinion - there's actually a forum for rants in either direction, but I suspect that most of us don't bother to read them.


Chris

---

### Post by tgm4883 on 2011-03-27
> **tredegar said:**
> That's what I posted at [#17]("http://ubuntuforums.org/showpost.php?p=10603875&postcount=17"), with a couple of questions for clarification.

No response though :(

Heh, I've been following the thread since the beginning and surely read your post. I must have forgotten about it in all the threads I try to read. :)

---

### Post by galacticaboy on 2011-03-27
I understand that the case usually is that is "Just works" but sadly that is not the case in some hardware. Some of my drivers are not perfect, they use the crappy generic stuff, I cannot do hardware acceleration or things like that. Not everything "Just works", things take tweaking, don't judge a book by its cover!

---

### Post by kelvin spratt on 2011-03-27
> **Thugdog Nasty said:**
> Clearly.
Yes it was and it worked very well if I recall. But things have changed the later xserver does not use a xorg config file for resolution hence your problem it uses files in the folder xorg.conf.d and the 20. files uses EDID information the file needs to be blacklisted. so you can use the standard Xorg conf simple.

---

### Post by walt.smith1960 on 2011-03-27
> **rjbl said:**
> 
  Windows 7? Well, Sh*t happens, with every MS OS since MS DOS 2. Twas ever thus.

rjbl

But Windows **8** will be the greatest O.S. ever:lolflag:

---

### Post by overdrank on 2011-03-27
On that note. Thanks for sharing, thread closed.

---

