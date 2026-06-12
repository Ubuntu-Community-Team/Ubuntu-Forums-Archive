---
title: "Here are 3 hours with Ubuntu 11.04"
date: 2011-05-22
forum: Testimonials &amp; Experiences
---

### Post by TheDesertDragon on 2011-05-22
I turn the computer on.
There are 3 broken shortcuts on my Unity launcher.
I remove them and insert working ones.

There's a kernel update (OH PLEASE FOR GODS SAKE STOP PUSHING THEM SO OFTEN). Restarting - graphics driver dies. Safe mode, graphics driver dies again. I use the tty's to add the x-swat ppa, which solves it.

Compiz now runs like crap. The windows are glitching around and hardly work at all. The dash seldomly responds at all, and when it does, it's nearly unusable. I turn off V-sync. Compiz crashes. I can't start it again because the Alt+F2 button depends on, guess what? Compiz. Reboot.

Unity crashes within the first 30 seconds. I go into the terminal and start installing KDE in desperate frustration. DPKG crashes, apt-get crashes with it. The tty stops responding.
There are now broken packages with broken dependencies in my system. The system doesn't work. GNOME can no longer start.

Reboot, the system doesn't respond.
Failsafe with X, the system doesn't respond.
Failsafe without X, trying to fix the packages - DPKG crashes again and pulls the entire terminal with it. Again.

I switch to tty2 and back up my files, then reboot.
I type:
sudo rm -rf / --force (whatever the last bit it asked me was)
I laugh.
sudo init 0: Command not found.

*shrug*
*laugh some more*

I hold down the power button.

During all of this, the wireless drivers were also non-functioning, and it wasn't something I could really live with - but I held my priorities. But even doing regular things I kept encountering system-halting - or even system-breaking - failures. How about this one?
"A core system component has crashed. Would you like to send a report?"
"Yes"
"This isn't a core Ubuntu package."
Well I was running Unity. What the **** do you think it was? Ugh! :(

I know I seem like a massive troll, but I'm really not. Ubuntu 11.04 has been this bad for me, and I cannot emphasize enough how upset I am about it. Ubuntu 10.04 was arguably the best Linux distibution of all time. Ubuntu 10.10 was also right up there with the best. Absolutely wonderful releases. 8.04 was great, too. I was a fan for 6 years. I was recommending it to family and friends, and several of them jumped on the wagon. Many of them are using it today (but, of course, they didn't upgrade)

This one is just worthless. I guess you get what you pay for after all. And here I was thinking that Canonical had a real chance against the behemoth at Redmond.

I am sorely disappointed.

I needed to get that off my chest.

---

### Post by kaldor on 2011-05-22
I don't disagree. People usually complain about Unity in this version, but it seems like 11.04 has had more stability issues (particularly graphics drivers) than before. I've been here since 7.10 and this is the only release I've felt unsure of. It's also the first release where I've told people "grab the previous release instead" when they mention trying it out.

Unity will definitely be better by 11.10 though. But, due to some really strange design decisions, I sometimes wonder how much attention was paid to things. Why is the notification simply just a tiny, cyan triangle in the top left? I can barely see it and I never notice it. Stuff like that.

Edit: The "Get what you pay for" thing isn't really a factor. Not Free Software's fault that Canonical didn't test stuff enough during development before unleashing it to the world. 

If you want a very stable Desktop OS, I recommend Scientific Linux 6.0. It's based on Red Hat Enterprise Linux 6, and will be supported for longer than Ubuntu LTS. Also has Flash and Wireless drivers out of the box, too.

---

### Post by silex89 on 2011-05-22
> **kaldor said:**
> I've been here since 7.10 and this is the only release I've felt unsure of.


Me too!! and I've been trying Ubuntu since Breezy!......


This version really has a ton of issues, but I have put my loyalty in this OS, so if things don't get better for the time Oneiric is released I'll run to Arch, Sabayon or some other stable distro.



Best Luck

---

### Post by TheDesertDragon on 2011-05-22
> **kaldor said:**
> Edit: The "Get what you pay for" thing isn't really a factor. Not Free Software's fault that Canonical didn't test stuff enough during development before unleashing it to the world. 

If you want a very stable Desktop OS, I recommend Scientific Linux 6.0. It's based on Red Hat Enterprise Linux 6, and will be supported for longer than Ubuntu LTS. Also has Flash and Wireless drivers out of the box, too.

That comment wasn't really meant to be taken much seriously either way. Of course I realize that a ton of effort has gone into Ubuntu 11.04 and that I got loads more than what I paid for - but considering I'm a student that actually does get Windows for free (not Windows tax - it's actually free) it takes a little bit more than a political argument to make me use Linux. For many, many years Ubuntu was that argument. I feel a bit stripped now! :(

I've considered running Mint instead. Well actually I'm willing to try just about anything as long as it's Debian based, preferrably Ubuntu-based, and has taken special care to remove the new version of Compiz and Unity along with it.

I really don't think it's Unity that's a piece of crap. I think it's Compiz. Compiz went through a very big change - it went from 0.8 to 0.9 and was rewritten into a modular format using C++ instead of C, and it has suffered absolutely grotesquely on the performance for it. I recall trying to update Compiz via a PPA on 10.10 and my system came to a grinding halt back then as well.

I dunno about the DPKG error though. That was utterly pathetic, though I'd prefer to stay in the Debian world. It's what I know and love, and I know how to use Debian packages and ppa's. The last time I tried RPM (openSUSE) I hated it because it did essentially the same but it was more complicated and there were 1/5th as many packages. Sure, there's Alien, but compared to auto-updating installers? Heh, I'll take Debian, tyvm. :p

---

### Post by mastablasta on 2011-05-23
> **TheDesertDragon said:**
> I really don't think it's Unity that's a piece of crap. I think it's Compiz. Compiz went through a very big change - it went from 0.8 to 0.9 and was rewritten into a modular format using C++ instead of C, and it has suffered absolutely grotesquely on the performance for it. I recall trying to update Compiz via a PPA on 10.10 and my system came to a grinding halt back then as well.

 
if you think COmpiz is the problem then KDE should get a try. 
 
> 
I dunno about the DPKG error though. That was utterly pathetic, though I'd prefer to stay in the Debian world. It's what I know and love, and I know how to use Debian packages and ppa's. The last time I tried RPM (openSUSE) I hated it because it did essentially the same but it was more complicated and there were 1/5th as many packages. Sure, there's Alien, but compared to auto-updating installers? Heh, I'll take Debian, tyvm. :p
 
Why was openSUSE more complicated? i thought everything is done through Yast or yeast or whatever it's called... 
 
how about FreeBSD? THey seem to have some nice distros there... One even sort of works like windows. but i only read about them. i think i might give one or two a spin. cause i am curious...

---

### Post by rjbl on 2011-05-23
So stick to the LTS release. If you are in GNU/Linux to test development releases of the various of the distros then Enjoy!

Meanwhile Ubuntu 11.04 is not, repeat not, a 'chance against the behemoth at Redmond'. 10.04LTS knocks Vista and Windows 7 into a cocked hat. You wanna hear about my Windows 7 experiences?

rjbl

---

### Post by coffeecat on 2011-05-23
> **TheDesertDragon said:**
> There's a kernel update (OH PLEASE FOR GODS SAKE STOP PUSHING THEM SO OFTEN). Restarting - graphics driver dies. Safe mode, graphics driver dies again. I use the tty's to add the x-swat ppa, which solves it.

No. There has been no kernel update in Natty since it was released. The current kernel is 2.6.38-8. The only way you could have got a kernel update was by enabling a ppa before you enabled the x-swat ppa or, more likely, enabling the proposed repository. If you've enabled the proposed repository, you would have got the 2.6.38-9 kernel. And if you have enabled the proposed repository, you need to read this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)

In particular:

> Enabling the proposed updates repository can break your system. It is not recommended for inexperienced users.The proposed 2.6.38-9 kernel has been reported to cause problems and we are unlikely to see it in a routine update. If you did enable the proposed repository, then most of your problems are probably down to a kernel that you should not have been running on a routine system. So - did you enable the proposed repository?

---

### Post by mastablasta on 2011-05-23
> **rjbl said:**
> So stick to the LTS release. If you are in GNU/Linux to test development releases of the various of the distros then Enjoy!
 
 
well LTS - what can i say. on one computer it's running really well the other one - sound wasn't working. after i solved it the updates broke it over and over again. and even when i did solve the sound the sytsem felt it was necessary to change my settings occasionally. i also crashed for no good reason occasionally. 
 
so i "upgraded" to Kubutnu 10.10 and then added the latest KDE PPA. now it works as it should -very stable, very fast even with very usefull effects turned on. though i still can't play audio CD in GUI. i don't plan to upgrade it yet eventhough on every start up an annoying info pops up suggesting me i should click th eupgrade button. very windows like i must say. it seems they also copied the annoying things (like those "updates are ready click here to update" bubbles).
 
also certian GTK applications don't work for some strange reason. no error messages nothing just dont' work. others (GIMP etc...) though work fine.

---

### Post by el_koraco on 2011-05-23
> **TheDesertDragon said:**
> Sure, there's Alien, but compared to auto-updating installers? Heh, I'll take Debian, tyvm. :p

Install Debian Stable. It has fairly newer packages than Lucid, and there's no Plymouth :D

---

### Post by armandh on 2011-05-23
I like Ubuntu, but I am in NO rush to upgrade
this change seems about as catastrophic as the [8.10?] compiz.
for the mission critical computers it is LTS
[like my wife's laptop for her e-mail and shopping]
and not day one, more like when the old support expires.

do you know firemen some times refer to first responding police as the blue canaries? 
my thanks to all the brave early adopters and their poisonous OSs.

---

### Post by 3rdalbum on 2011-05-23
> **coffeecat said:**
> 
The proposed 2.6.38-9 kernel has been reported to cause problems and we are unlikely to see it in a routine update. If you did enable the proposed repository, then most of your problems are probably down to a kernel that you should not have been running on a routine system. So - did you enable the proposed repository?

I did. My computer doesn't even power on now. It seemed to be having problems before so I don't know if the kernel update caused it 

Maybe next time you should help by testing Ubuntu before the release and reporting bugs?

---

### Post by SeijiSensei on 2011-05-23
> **mastablasta said:**
> if you think COmpiz is the problem then KDE should get a try.

I've had to turn off desktop effects on my older Dell laptop when I upgraded my 10.10 installation to KDE 4.6 and later to 11.04.  I have no performance issues on a 4GB quad-core desktop with an NVIDIA 9500GT, but on a 2GB Core2 with Intel 945GM graphics, KDE 4.6 ground to halt.  Once I turned off desktop effects, which don't matter to me at all, performance has been just fine.

---

### Post by mastablasta on 2011-05-23
I am using ATI opensource and they also lagged, so i had to turn off the effects when i installed it but lately they fixed some issues and now it works well.
 
yeah effects are not that important. but some are nice to have like the mouseover preview on the taskbar and when you are alt tabbing through open windows. wobbly windows and such are useless.
 
did you upgrade with 4.6 turned on or you had to turn off the PPA first?

---

### Post by TheDesertDragon on 2011-05-23
> **mastablasta said:**
> if you think COmpiz is the problem then KDE should get a try.
Nahhh, KDE is a problem, too. It just causes a different set of problems. I'm not gonna get too much into that here, but basically their compositing is slow, too. Not quite that slow, but still slow. You can turn off compositing and it runs okay, but meh.

Someone in this thread described KDE compositing as running poorly on a Dual Core CPU, 2GB RAM and Intel graphics cards machine. You know, when you can't even run the desktop on such a machine - something is wrong. My mom runs Windows 7 (and she hates it lol. Think I could convert if I wanted to at this point), and her PC is a singlre core multithreaded 2.4GHz, she has 1GB of RAM and her graphics card is a Radeon 4400Pro. (Not the new HD series - this graphics card is more than 10 years old!)
You know what? It runs smooth. And so did Compiz 0.8 I recall. Isn't that insane?

Another problem with KDE is that it's so similar to Windows but has far fewer programs and actually has so few widgets for it's panels you may as well be using Windows.
The third problem is that PackageKit and Ubuntu Software Center ALWAYS crash when you close them when running Kubuntu with KDE 4.6. Don't ask me why. It was fine in 4.5.

> **mastablasta said:**
> Why was openSUSE more complicated? i thought everything is done through Yast or yeast or whatever it's called... 
 
how about FreeBSD? THey seem to have some nice distros there... One even sort of works like windows. but i only read about them. i think i might give one or two a spin. cause i am curious...

YaST (Yet Another Setup Tool) is a massive application with very poor organization that lacks a lot of important packages. You cannot add repositories to it, and so you're often ending up downloading RPM packages left right and centre, which may or may not be compatible with your system because the vast majority are actually for Fedora/RedHat, and they want dependencies. YaST is unable to find those dependencies because it cannot interface with the package properly, and now you're dependency-hunting.

FreeBSD is indeed something I've looked at recently but I have no idea what to expect, really... :S
If I was to go this way I'd propably rather run Darwin. (The kernel of OSX without actually running OSX. It's free software incase you didn't know)

> So stick to the LTS release. If you are in GNU/Linux to test development releases of the various of the distros then Enjoy!

Meanwhile Ubuntu 11.04 is not, repeat not, a 'chance against the behemoth at Redmond'. 10.04LTS knocks Vista and Windows 7 into a cocked hat. You wanna hear about my Windows 7 experiences?

rjbl 
Here's the problem:
Most software developers only package software for the newest release. For example, Eclipse-cdt is a software that's really easy to install on Ubuntu 10.10, but on Ubuntu 10.04 it's a nightmarishly outdated piece of crap that hardly works at all.

This is because 10.10 and 11.04 are called releases, not beta tests. Now I realize that that is actually grossly misleading, apparently. 
When you make a release, you make sure it's a solid improvement on the last and that it works on every system the last one worked on. Unrealistic with a 6 month release schedule? Well, what can I say... who would've thought it.

I don't particularly like Windows at all, but it's mostly a usability issue for me. In Windows I feel that I'm being forced an extremely annoying UI down my throat and, in fact, it isn't even properly themeable. Then there's the political argument of free software - I like the idea of being able to use my PC without paying royalties to Microsoft if I ever become big and make a lot of money and Microsoft sees itself sour.
And lastly the Linux kernel is just FAST. That doesn't really help a lot though when the software that's layered on top of it is so slow it offsets all that massive performance gain. Shame, really.

> and not day one, more like when the old support expires.
It's now almost a month since this upgrade was released. I don't day-1-upgrade either but this time... well it didn't really have an effect. It still feels like day 1.

> No. There has been no kernel update in Natty since it was released. The current kernel is 2.6.38-8. The only way you could have got a kernel update was by enabling a ppa before you enabled the x-swat ppa or, more likely, enabling the proposed repository. If you've enabled the proposed repository, you would have got the 2.6.38-9 kernel. And if you have enabled the proposed repository, you need to read this:

[https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)
I enabled x-swat because it happened in the first place, so it can't be x-swat.
In that case I shall not rule that out, although I really can't think of what repository might've done this.

Although I do consider it a problem that we can add repositories that overwrite important system files automatically and break our system. That's very, very silly. :/

---

### Post by ivanovnegro on 2011-05-23
> **SeijiSensei said:**
> I've had to turn off desktop effects on my older Dell laptop when I upgraded my 10.10 installation to KDE 4.6 and later to 11.04.  I have no performance issues on a 4GB quad-core desktop with an NVIDIA 9500GT, but on a 2GB Core2 with Intel 945GM graphics, KDE 4.6 ground to halt.  Once I turned off desktop effects, which don't matter to me at all, performance has been just fine.

My Intel integrated works perfectly with Kubuntu 11.04 with enabled effects on a Dual Core but I know some older Intel cards are not working properly, I even dont remember which Intel chip I have, have to look again. :)
Also, the default effects are relativeley slow, in the settings for them enable fast or faster, it works like a charm.
And for me, Kubuntu runs faster as Ubuntu 11.04 and KWin is far more responsive as Compiz and that even more responsive as Compiz enabled on the Maverick release, I would say I had some luck that it works so perfect.
But in the end I settled on Xubuntu, more lightweight, dont need effects at all and runs even better as Kubuntu.
The 11.04 release for me is in this class:

- Xubuntu (amazing)
- Lubuntu (very good)
- Kubuntu (also very good but lacks in some areas, but for me KDE specific)
- Ubuntu (not usable for me)

---

### Post by BigSilly on 2011-05-23
> **TheDesertDragon said:**
> 
YaST (Yet Another Setup Tool) is a massive application with very poor organization that lacks a lot of important packages. You cannot add repositories to it, and so you're often ending up downloading RPM packages left right and centre, which may or may not be compatible with your system because the vast majority are actually for Fedora/RedHat, and they want dependencies. YaST is unable to find those dependencies because it cannot interface with the package properly, and now you're dependency-hunting.

I switched to Opensuse 11.4 with Gnome 3 after problems with Natty, and I've had no massive problems at all with the package manager. It's even easier to add community repositories with YasT than it is with Ubuntu imho. Certainly I've not had to 'dependency hunting' or adding Fedora RPM's. The only extra RPM's I've added are games I've bought (World of Goo, And Yet It Moves, etc).

I'm also running PCLinuxOS with KDE4.6.3 on a dual core AMD machine and it runs like an absolute dream, easily outwitting my Windows 7 install. I don't know where this idea comes from that it struggles on lower specs, because I also put it on my dad's single core Sempron and it's just as fast as Gnome is on it.

---

### Post by SeijiSensei on 2011-05-23
> **mastablasta said:**
> did you upgrade with 4.6 turned on or you had to turn off the PPA first?

I added [ppa:kubuntu-ppa/backports]("https://launchpad.net/~kubuntu-ppa/+archive/backports") to 10.10 when I upgraded to 4.6.2.  When I upgraded to 11.04, it rewrote my /etc/apt/sources.list to point to the Natty repositories.  I don't think it carried over any other PPAs I use; I recall adding them manually to sources.list afterwards.

> **BigSilly said:**
> I switched to Opensuse 11.4 with Gnome 3 after problems with Natty, and I've had no massive problems at all with the package manager. It's even easier to add community repositories with YasT than it is with Ubuntu imho.

How does SuSE handle non-free items like libdvdcss2?  I had to add Dag's rpmforge repositories to get those items when I was running Fedora.

---

### Post by BigSilly on 2011-05-23
> **SeijiSensei said:**
> 
How does SuSE handle non-free items like libdvdcss2?  I had to add Dag's rpmforge repositories to get those items when I was running Fedora.

You just go into the repository settings in YasT, click add repository, and then tick the community repository box. It then shows you a list of available repos, and there's a libdvdcss repo there to handle that. I also added things like Packman and non-free software from the list. There's quite a few, and enabling them is just a few clicks. Like I say it's not hard, and probably a bit easier than adding Medibuntu each release.

---

### Post by ivanovnegro on 2011-05-23
> **BigSilly said:**
> I switched to Opensuse 11.4 with Gnome 3 after problems with Natty, and I've had no massive problems at all with the package manager. It's even easier to add community repositories with YasT than it is with Ubuntu imho. Certainly I've not had to 'dependency hunting' or adding Fedora RPM's. The only extra RPM's I've added are games I've bought (World of Goo, And Yet It Moves, etc).

I'm also running PCLinuxOS with KDE4.6.3 on a dual core AMD machine and it runs like an absolute dream, easily outwitting my Windows 7 install. I don't know where this idea comes from that it struggles on lower specs, because I also put it on my dad's single core Sempron and it's just as fast as Gnome is on it.

I think OpenSuse is really underrated in the Ubuntu community, 11.4 is really good IMHO, there are some glitches but for me less as in Unity.
PCLinuxOS is also an impressive thing and yes its fast as hell, I dont know what they did to their KDE edition, but on the downside its somehow cluttered with GTK apps and things I dont think go well with KDE, of course just asthetically.

---

### Post by el_koraco on 2011-05-23
> **BigSilly said:**
> You just go into the repository settings in YasT, click add repository, and then tick the community repository box. It then shows you a list of available repos, and there's a libdvdcss repo there to handle that. I also added things like Packman and non-free software from the list. There's quite a few, and enabling them is just a few clicks. Like I say it's not hard, and probably a bit easier than adding Medibuntu each release.

That's just the beginning of it. You can add repos for Nvidia and ATI, so whenever a new version of your GPU is released, you can run it. Old and new packages are even colored differently. Yast is like a mission control center, it might not be as straightforward as USC, but once you learn to use it, you don't need anything else. 

That's not saying that its CLI equivalent is any worse. In the unlikely event that something is not functioning with Yast, you use zypper (for instance, upgrading to Tumbleweeds is done via zypper). Both are extensions of an extremely powerful library, and much more modern than the apt and dpkg tools. Plus, the documentation rocks.

---

### Post by mastablasta on 2011-05-24
KDE i am running is doing fine with effects on with 1Gb ram, celeron 3300 and old Radeon 9600XT. and ram is DDR :-)
 
i didn't really see lack of good software for KDE. in fact i see people recomending and using KDE software on gnome (e.g. k3b ). i never had Kpackagekit crash.
 
Yast is really a powerfull control center. it's like everything or most things collected in one place. i am sure that whoever knows how to use it is the king of his OS. besides ones you set it all up on start you probably won't touch it so much anyway. 
 
oh and XFCE (Xubuntu) improved quite a bit in terms of memory usage. and got faster. in Linux mint they got it almost as low as lxde now.

---

### Post by prodigy_ on 2011-05-24
No matter what fanboys say, Unity is horrible. (Well, probably not as horrible as KDE, but still.) It's ugly, slow and buggy as hell. Besides, the last thing Linux needed was another useless DE. And Unity consumed resources that could be spent on fixing bugs, optimizing the existing code or even - why not? - writing kernel patches.

It's bad not only because it's broken and unnecessary. Bugs happen and redundant options can't hurt anyone just because they exist. But the whole "revolution" part was a serious mistake. One would expect Ubuntu developers ought to know better after Plymouth disaster in 10.04. And Plymouth was a minor thing - disable and forget. Unity is different. I don't know who decided to make it the default DE all of a sudden... but the guy's just plain crazy and ignorant to boot. PC isn't about revolutions. In fact I can't recall **anything** that was successfully forced upon customers by **any** IT company. Even MS had to take a chill pill when Vista failed.

I know that no matter what we'll say or do, Ubuntu is on its way to self-destruction. And it's something we can't change. We don't have a say in the matter.

That's why after all I choose Windows. A resource hog? One big security hole? Sysadmin's worst nightmare? True, all true. I hate Windows as much as everyone does. It's crap. But it's predictable crap. It allows me (out of the box!) to use more or less the same UI I used 16 years ago. Even during the Vista days I knew that MS will - sooner or later - deliver. Because for MS it's about money. In the long run they always release what market expects them to release and market wants predictable things that simply work.

---

### Post by Tamlynmac on 2011-05-24
> prodigy_

I'm not one to posture or debate in this section of the forums. Nor, will I question your opinions or choices. 

However, one should keep in mind that for Ubuntu to grow and compete (at  some level) with MS, they must try new and innovative ways to attract  Windows users (not saying that Unity is similar to Windows). There's a  limited number of Linux users and for Ubuntu to compete with other Linux  distros, doesn't improve the over all Linux market share.

Like you, I'm not pleased with the new release. Unlike you, I'm in no  hurry to make any decisions (10.04 supported until 2013) - least of all  returning to Windows. With all the available choices, why hurry. My  family & I are finding xfce a nice DE and for our purposes it seems to work.

To continue arguing over Unity is (as you suggest) foolish. The decision  has been made and unless something significant changes, it will remain.  If your comfortable in the Windows environment, I wish you the best. I  suspect some Ubuntu user who don't like the new release, would rather  investigate and test alternative Linux options than to return to  Windows.

I am one of those users and as an alternative DE, xfce is finding a home  in our home (5 systems). Going back to Windows is not an option for my  family and as long as Linux is around it never will be.

Good luck with your choice of OS and notice that I simply said Windows  is not an option for us. I didn't waste time complaining about or  demeaning it. Wonder why? I'd like to suggest that those users who  aren't happy with Unity, let it go and instead of wasting time  complaining - seek alternative choices. With every new release, a  percentage of users take exception in the T&E. Four months from now  this release will be history in the T&E.

Just my $0.02

---

### Post by compmodder26 on 2011-05-24
> **mastablasta said:**
> KDE i am running is doing fine with effects on with 1Gb ram, celeron 3300 and old Radeon 9600XT. and ram is DDR :-)
 
i didn't really see lack of good software for KDE. in fact i see people recomending and using KDE software on gnome (e.g. k3b ). i never had Kpackagekit crash.

I've got Kubuntu 11.04 on an Intel Core Duo with 1GB RAM and Intel 945 graphics.  Only issue I had was with Window Blur enabled.  If I disable that, KDE runs perfectly.

[QUOTE=TheDesertDragon]Another problem with KDE is that it's so similar to Windows but has far fewer programs and actually has so few widgets for it's panels you may as well be using Windows.
The third problem is that PackageKit and Ubuntu Software Center ALWAYS crash when you close them when running Kubuntu with KDE 4.6. Don't ask me why. It was fine in 4.5.[/QUOTE]

Are we talking about the same DE?  There are plenty of plasmoids available for the panels. Sure, vanilla KDE may look a bit like windows, but it's not hard at all to fix that through the many customizations you can do. And I've never had any stability issues with anything inside of KDE.

Guess I got lucky.

---

### Post by IWantFroyo on 2011-05-24
Natty is unusable for me. It doesn't like my wireless.

I have, however, been happy so far with Debian 6, Elementary OS, and I'm now burning a F15 disc (hope I like it).

---

### Post by ventrical on 2011-05-24
> **prodigy_ said:**
> No matter what fanboys say, Unity is horrible. (Well, probably not as horrible as KDE, but still.) It's ugly, slow and buggy as hell. Besides, the last thing Linux needed was another useless DE. And Unity consumed resources that could be spent on fixing bugs, optimizing the existing code or even - why not? - writing kernel patches.

It's bad not only because it's broken and unnecessary. Bugs happen and redundant options can't hurt anyone just because they exist. But the whole "revolution" part was a serious mistake. One would expect Ubuntu developers ought to know better after Plymouth disaster in 10.04. And Plymouth was a minor thing - disable and forget. Unity is different. I don't know who decided to make it the default DE all of a sudden... but the guy's just plain crazy and ignorant to boot. PC isn't about revolutions. In fact I can't recall **anything** that was successfully forced upon customers by **any** IT company. Even MS had to take a chill pill when Vista failed.

I know that no matter what we'll say or do, Ubuntu is on its way to self-destruction. And it's something we can't change. We don't have a say in the matter.

That's why after all I choose Windows. A resource hog? One big security hole? Sysadmin's worst nightmare? True, all true. I hate Windows as much as everyone does. It's crap. But it's predictable crap. It allows me (out of the box!) to use more or less the same UI I used 16 years ago. Even during the Vista days I knew that MS will - sooner or later - deliver. Because for MS it's about money. In the long run they always release what market expects them to release and market wants predictable things that simply work.

Well, then you have to ask the question then if you are playing the piano or the piano is playing you!? Thats what we get with predictable crap  - endentured servitude. Fair enough .. I was there ... once or perhaps twice.  Now - ! I have peeled that straight-jacket off.  even as frustrating as Natty and Unity are - if I consider all the time  I had to spend doing work-a-rounds for XP (and not get paid by Ms) then why can't I spend that time customizing and learning a new install?

 I'm not rocking the penguin or sounding the Ubuntu drums... I think that  at certain times , when we are dealing with new computer concepts, we have to take a step back and do a good and earnest study.

 But in all honesty I have to say also that I too have become addicted and adjusted to that predictable crap. sort of like a bug-out kit when the -stuff hits the fan - so to speak- thaty I got windows in my other back-pocket.

---

### Post by coolglobal on 2011-05-24
> **Tamlynmac said:**
>  
However, one should keep in mind that for Ubuntu to grow and compete (at  some level) with MS, they must try new and innovative ways to attract  Windows users (not saying that Unity is similar to Windows). There's a  limited number of Linux users and for Ubuntu to compete with other Linux  distros, doesn't improve the over all Linux market share.


Global Statistics April 2011 (sample survey 47,019 websites)

Operating Systems
1 	Windows XP 	38.14%
2 	Windows 7 	29.46%
3 	Windows Vista 	12.16%
4 	Mac OS X 	8.97%
5 	iPhone OSX 	2.57%
6 	Linux           1.41%
7 	Android 	0.85%
8 	BlackBerry 	0.48%
9 	Windows 2000 	0.15%
10 	Windows 2003 	0.15%

A good way to improve the Linux statistic? A simple DE that just works?

_Web Servers 2009-2010_

Sample 1
Windows 33.7%
Linux 63.7%
Other __%

Sample 2
Windows 20.36%
Linux 74.29%
Other __%

Linux owns the World Wide Web. It's also a serious threat to the desktop market, through share and share alike.
China, the world's most populated country and emerging superpower: [http://www.pcworld.com/article/214206/china_os_makers_partner_on_new_operating_system_brand.html](http://www.pcworld.com/article/214206/china_os_makers_partner_on_new_operating_system_brand.html)
China is a major manufacturer of computer hardware. It's political system tends towards conformity.

Richard Stallman, the guy who lit the fire (For those new to Linux): [http://en.wikipedia.org/wiki/Richard_Stallman](http://en.wikipedia.org/wiki/Richard_Stallman)
All Mark Shuttleworth needs to do now is be the producer of a Hollywood movie about Richard Stallman and create more "buzz". Anyone watch The Social Network about Facebook? There's a million times more drama in the evolution of GNU+Linux, it would have to be a trilogy. Phone freaking, to satellite rediversions, oh that's right, an awesome operating system. Wired geeks hacking late into the night, freedom. Many people around the world would be amazed at this global subculture.
:popcorn:

---

### Post by Tamlynmac on 2011-05-25
> coolglobal
6 	Linux           1.41%
It's also a serious threat to the desktop market, through share and share alike.

I agree that Linux owns the Web. However, I don't agree, that at present  it's a serious contender for the desktop market (1.41%). However, the  future could find Linux in a more competitive position.

Dumbing down the DE to a more simplistic, basic and functional format  may improve the dynamics. But right now that's only speculative. The  real opportunity IMHO exists in factors related to the world economy. I  honestly believe as more consumers have reduced resources (inflation,  lower disposal income, etc.), Linux & FOSS will offer extremely  appealing free products.

I think we  both agree that the future of Linux has potential. Though, we may  disagree on product evolution with respect to said potential.

* I will not debate in this section of the forums and will unsubscribe to this thread. Just to much of a temptation. ;)

---

### Post by mastablasta on 2011-05-25
> **coolglobal said:**
> Richard Stallman, the guy who lit the fire (For those new to Linux): [http://en.wikipedia.org/wiki/Richard_Stallman](http://en.wikipedia.org/wiki/Richard_Stallman)
All Mark Shuttleworth needs to do now is be the producer of a Hollywood movie about Richard Stallman and create more "buzz". Anyone watch The Social Network about Facebook? There's a million times more drama in the evolution of GNU+Linux, it would have to be a trilogy. Phone freaking, to satellite rediversions, oh that's right, an awesome operating system. Wired geeks hacking late into the night, freedom. Many people around the world would be amazed at this global subculture.

well all that coolness and it doesn't make the GUI play AudioCD or the sound work perfectly and in HD. and i am a user not programmer so i don't indent to fix these mistakes/bugs.
 
you knwo what they started puttind Adroid on netbooks here. well actually they all seem to have dual boot - AndroidOS and Windows7 starter. yes, Ubuntu (Canonical) is really playing this marketing game badly. Why is Android (linux based but with modified kernel) there and people accepted it as an OS while Ubuntu and others failed? perhaps because it actually works with no major glitches? perhaps because it's hardware is controled?
 
wish they had this dual boot config. i bet more users would give linux a try, but i also think when the upgrade pops up and they do it they might be disspointed as not everything might work in the next release. while it will work in the next release of AndroidOS or Iphone OS or whatever. developers make sure of that.

---

### Post by coolglobal on 2011-05-25
My quote there was a bit tongue in cheek. :)

I agree with the sentiment. On the most straightforward level, all Unity has to do is install flawlessly on any personal computer. Be easy to understand and adapt to. The user has to be able to theme it, to become attached to it and to make it their own. It has to work as expected. I'm really curious to see what the next release will be like.

---

### Post by Ni-el on 2011-05-26
This got my dander up so I have to say something, at least.
The only reason to use Windows at all is because so many other machines are using it. If it never existed, it would never be needed. I do have a copy on Virtualbox but I never even turn it on except to check website compatibility in Internet Explorer (again, just because so many other people are using it).
The problems with Linux are mostly because of the proprietary hardware/software manufacturers that play the hide and seek game to tip the competitive advantage to their favour (ie. Beating the competition). None of those companies will succeed in being anything other than the money pits that they are today because they are so wrapped up in dominating the rest of the world. Co-operation, not competition, is what succeeds.

---

### Post by Ni-el on 2011-05-26
Oh, by the  way of this conversation, I did try Fedora15 with Gnome3 and it's good. I also tried KDE in Fedora and Kubuntu.
All of these are good and all of them "work" in their own respect. That is to say NONE OF THEM ARE CRAP. 
I like Unity, even though it takes a little searching without much guidance to find the scroll bars and menu items (enabling menu items in the Main Menu dialogue makes them appear in the sidebar menu). I have an issue with my screen resolution that I haven't figured out yet, but I had the same problem with Fedora as I do with Ubuntu (I suppose it will turn out to be a problem with the Intel drivers). But all in all it seems like quite an over-reaction to get all emotional and start hurling insults because you may have to make a few personal adjustments of your own. Try an attitude adjustment.

---

### Post by wolfen69 on 2011-05-27
> **Ni-el said:**
> Oh, by the  way of this conversation, I did try Fedora15 with Gnome3 and it's good. I also tried KDE in Fedora and Kubuntu.
All of these are good and all of them "work" in their own respect. That is to say NONE OF THEM ARE CRAP. 
I like Unity, even though it takes a little searching without much guidance to find the scroll bars and menu items (enabling menu items in the Main Menu dialogue makes them appear in the sidebar menu). I have an issue with my screen resolution that I haven't figured out yet, but I had the same problem with Fedora as I do with Ubuntu (I suppose it will turn out to be a problem with the Intel drivers). But all in all it seems like quite an over-reaction to get all emotional and start hurling insults because you may have to make a few personal adjustments of your own. Try an attitude adjustment.

Wow. I rarely look at the comments that are "left at the door". Nice post.

---

### Post by prodigy_ on 2011-05-28
> **Tamlynmac said:**
> However, one should keep in mind that for Ubuntu to grow and compete (at  some level) with MS, they must try new and innovative ways to attract  Windows users (not saying that Unity is similar to Windows).

If we're talking about home desktop, it's really hard to compete with Windows 7 there. At work I'd prefer Ubuntu LTS (if only there was a decent Skype client for Linux). But company-wide migration to another OS requires patience and some long-term investments. Actually, the latter is not such a big problem, but patience and willingness to learn are always in short supply.

In any case it's not about DE. If Canonical wants to compete with MS they should contribute to Wine. [Modern](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23504) [games](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23521), [Skype](http://appdb.winehq.org/objectManager.php?sClass=version&iId=23488), [.NET](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10166) [framework](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886), [business-class](http://appdb.winehq.org/objectManager.php?sClass=version&iId=20263) [software](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21144)... fixing anything that has garbage-rated Wine support (135 pages in AppDB, take your pick) would be infinitely more useful than wasting time on Plymouth and Unity.

---

### Post by ivanovnegro on 2011-05-28
Yes, I see the problem with Ubuntu and maybe also with other Linux projects and of course with the Gnome Shell that the focus is too much on the interface and the looks of an OS but what I need are applications, the OS is for me to load a graphical environment to be able to use my preferred apps and not a UI in first place.
In the end you could use Open Source on any platform, you dont need Ubuntu for this.
But of course I want to use Linux on my machine because its free of licenses and I love Linux.
The only thing I see what Canonical is doing, is changing the UI, some default apps, all of them I maybe neither use but the world want to use programs that serve for their work regardless eye candy.
I doubt we will see more Ubuntu users coming from Windows just because of Unity.

---

### Post by rg4w on 2011-05-28
> **ivanovnegro said:**
> Yes, I see the problem with Ubuntu and maybe also with other Linux projects and of course with the Gnome Shell that the focus is too much on the interface and the looks of an OS but what I need are applications, the OS is for me to load a graphical environment to be able to use my preferred apps and not a UI in first place.
In the end you could use Open Source on any platform, you dont need Ubuntu for this.
But of course I want to use Linux on my machine because its free of licenses and I love Linux.
The only thing I see what Canonical is doing, is changing the UI, some default apps, all of them I maybe neither use but the world want to use programs that serve for their work regardless eye candy.
I doubt we will see more Ubuntu users coming from Windows just because of Unity.
I think you've hit on an important point:  the biggest growth for Linux won't come because of changes to its UI, but more because of growth in the number of apps available for it, and the growth of drivers that make it possible to run on more machines.

We can make fun of Steve Ballmer all we want, but his "Developers! Developers! Developers!" chant is even more relevant for Ubuntu than it is for Windows.

This process of making PPAs and waiting in queue for them to get packaged is among the things that desperately need improvement, for all the reasons Matthew Paul Thomas described in his UDS session:
[http://www.youtube.com/watch?v=GT5fUcMUfYg](http://www.youtube.com/watch?v=GT5fUcMUfYg)

Ironically, Unity makes it harder for developers to deploy to Ubuntu, not easier.  With novel UI conventions like a global menu bar (even though I like it) and departure from some of the desktop file conventions, Unity requires extra work for an app developer to design for, and potentially contributes to the further fragmentation of the Linux platform in which we can't just run any Linux app and expect a great experience but must instead hope it's been designed for the particular distro we happen to be running at the moment.

That said, with Unity Canonical had little choice:  Gnome 2 was slated for EOL, and Gnome 3 would not be completed within Ubuntu 11.04 timeline.  Something had to be built, and warts and all Unity offers great promise as a solution going forward.

Still, it would be encouraging to see a greater focus on providing tools and systems that support more rapid deployment of apps for Ubuntu.

And equally important would be greater support for driver development.  When I look at beautiful machines like the Dell Duo I think, "Man, that's a perfect fit for Ubuntu!".  But more than 40 pages later, the thread here on that model has failed to come up with a recipe for fully using that great machine with Ubuntu. It doesn't matter how nice an OS might look if it can't be run.

---

### Post by prodigy_ on 2011-05-28
> **rg4w said:**
> Gnome 2 was slated for EOL, and Gnome 3 would not be completed within Ubuntu 11.04 timeline.
That's what happens when people bring corporate culture to OSS. Deadline is everything, common sense is nothing. Like I said before: at least companies like MS do it for money. But when OSS non-profit developers start acting like jerks, that's just sad.

---

### Post by wolfen69 on 2011-05-28
If people would stop upgrading and do clean installs, there would be a lot less problems.

---

### Post by madmax75 on 2011-05-28
> **wolfen69 said:**
> If people would stop upgrading and do clean installs, there would be a lot less problems.

Apparently it doesn't matter if you do either an upgrade or a clean install with the Unity version of Ubuntu - you *will* get bugs. Lots and lots of bugs and general breakage, mayhem and havoc. If you believe the experiences people are reporting on this forum.

---

### Post by madmax75 on 2011-05-28
> **prodigy_ said:**
> that's what happens when people bring corporate culture to oss. Deadline is everything, common sense is nothing.

+1

---

### Post by wolfen69 on 2011-05-28
> **madmax75 said:**
> Apparently it doesn't matter if you do either an upgrade or a clean install with the Unity version of Ubuntu - you *will* get bugs. Lots and lots of bugs and general breakage, mayhem and havoc. If you believe the experiences people are reporting on this forum.

Most of the problems I've seen are upgrade related. I've also done 2 installs with unity with no issues. Then again, the linux gods like me.

---

### Post by coolglobal on 2011-05-28
> **rg4w said:**
> 
still, it would be encouraging to see a greater focus on providing tools and systems that support more rapid deployment of apps for ubuntu.

And equally important would be greater support for driver development.  

+1

---

### Post by Tamlynmac on 2011-05-29
> wolfen69
Most of the problems I've seen are upgrade related. I've also done 2  installs with unity with no issues. Then again, **the linux gods like me**. 	

:lolflag: Glad someone does.:lolflag:

Once again - words of wisdom.
I must agree. Historically, most problems I've experienced with  upgrading were directly related to the install. Especially, when trying  to perform an online upgrade. Now, I always to do a clean install.

Just my $0.02

---

### Post by slooksterpsv on 2011-05-29
To the OP, that was an interesting read. It seems like about the lower-avg feel of Unity, but as Poster #2 stated, it'll get better in 11.10 (just be glad this isn't a LTS haha).

With all the issues you stated you were having, I just hope it's not bad RAM or a bad HDD. I doubt it is, but still just worry due to the content of the post.

---

### Post by Markmental on 2011-05-29
> **TheDesertDragon said:**
> I turn the computer on.
There are 3 broken shortcuts on my Unity launcher.
I remove them and insert working ones.

There's a kernel update (OH PLEASE FOR GODS SAKE STOP PUSHING THEM SO OFTEN). Restarting - graphics driver dies. Safe mode, graphics driver dies again. I use the tty's to add the x-swat ppa, which solves it.

Compiz now runs like crap. The windows are glitching around and hardly work at all. The dash seldomly responds at all, and when it does, it's nearly unusable. I turn off V-sync. Compiz crashes. I can't start it again because the Alt+F2 button depends on, guess what? Compiz. Reboot.

Unity crashes within the first 30 seconds. I go into the terminal and start installing KDE in desperate frustration. DPKG crashes, apt-get crashes with it. The tty stops responding.
There are now broken packages with broken dependencies in my system. The system doesn't work. GNOME can no longer start.

Reboot, the system doesn't respond.
Failsafe with X, the system doesn't respond.
Failsafe without X, trying to fix the packages - DPKG crashes again and pulls the entire terminal with it. Again.

I switch to tty2 and back up my files, then reboot.
I type:
sudo rm -rf / --force (whatever the last bit it asked me was)
I laugh.
sudo init 0: Command not found.

*shrug*
*laugh some more*

I hold down the power button.

During all of this, the wireless drivers were also non-functioning, and it wasn't something I could really live with - but I held my priorities. But even doing regular things I kept encountering system-halting - or even system-breaking - failures. How about this one?
"A core system component has crashed. Would you like to send a report?"
"Yes"
"This isn't a core Ubuntu package."
Well I was running Unity. What the **** do you think it was? Ugh! :(

I know I seem like a massive troll, but I'm really not. Ubuntu 11.04 has been this bad for me, and I cannot emphasize enough how upset I am about it. Ubuntu 10.04 was arguably the best Linux distibution of all time. Ubuntu 10.10 was also right up there with the best. Absolutely wonderful releases. 8.04 was great, too. I was a fan for 6 years. I was recommending it to family and friends, and several of them jumped on the wagon. Many of them are using it today (but, of course, they didn't upgrade)

This one is just worthless. I guess you get what you pay for after all. And here I was thinking that Canonical had a real chance against the behemoth at Redmond.

I am sorely disappointed.

I needed to get that off my chest.
In my opinion unity SUCKS, i like gnome more that's why im sticking with 10.04 LTS

---

### Post by jchw on 2011-05-29
I tried at various times to upgrade, install and reinstall 11.4 and ended up every time with the black screen problem and after wiping out my hard drive I have gone back to 10.10. I will not be moving to 11.4 and unless Ubuntu goes back to Gnome I will eventually and with much regret move to a different distro. Today I tried Mint 11 and that also had the black screen problem no doubt passed on from Ubuntu 11.4.

I cannot understand why Canonical should waste so much time and money on this release when fundamental issues still remain such as support for drivers for wifi, scanners, music etc. Until the system can be used out of the box by the average person in the street it will never be a viable alternative to Windows. Unity just gives more ammunition to the Windows supporters to say that Linux is unstable and unsuitable for the average user.

From what I have seen on uTube about Unity I think it is suitable for tablets for school children and teenagers but is not a substitute for the Gnome desktop which is better for more serious business users.

If they want to move Ubuntu into the tablet market why not have two distinct versions, one for touchscreens and the other for laptops and PC users?

---

### Post by coolglobal on 2011-05-29
Ubuntu hasn't dropped Gnome. Gnome 3 will be back soon enough alongside Unity.

---

