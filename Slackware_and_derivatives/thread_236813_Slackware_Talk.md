---
title: "Slackware Talk"
date: 2006-08-15
forum: Slackware and derivatives
---

### Post by halfvolle melk on 2006-08-15
[http://distrowatch.com/?newsid=03629#0](http://distrowatch.com/?newsid=03629#0)

I think I'll check out the world of Slackware when it's finished.

---

### Post by SoundMachine on 2006-08-29
> **halfvolle melk said:**
> [http://distrowatch.com/?newsid=03629#0](http://distrowatch.com/?newsid=03629#0)

I think I'll check out the world of Slackware when it's finished.

If you have any questions feel free to PM me, things that are different is basically the install and package tools, it also uses the BSD style init, it's a lot easier once you learned it but you do have to learn how it works.

In Slackware, you edit config files when you want to change anything.

Some people say that Gentoo is a great way to learn Linux but i don't see why it would be, watching stuff compile doesn't teach you anything, Slackware will teach you everything you ever wanted to know about setting up a system, it's like Linux from scratch without the compiling.

Well, if you are not satisfied with the standard choice that is, but then again, who ever is?

One thing you will notice is that it is stable as a rock, even the /current is more stable than any distro's /release that i know of.

When it comes to packages, there are the ones you need to get going, but if you are going ot be using it as a home desktop with all that it entails you will either have to compile it yourself or use [www.linuxpackages.net](www.linuxpackages.net) which is fairly stable but as with all third party repos, don't upgrade important packs from them unless you really, really need to.

---

### Post by halfvolle melk on 2006-09-16
SoundMachine, sorry to post back so late, I had other stuff going on and forgot to check back. Thanks for your reply!

I'll be sure to contact you if I encounter any problems :) From what I gather SlackWare means getting down and dirty, no problem with a challenge :)

I'll let you know, thanks again!

edit: I'll get into the substance of your post.

I have no clue what BSD is about. From what I've heard it's mainly GNU rewritten so it can be covered under BSD licence.

> Some people say that Gentoo is a great way to learn Linux but i don't see why it would be, watching stuff compile doesn't teach you anything
funrolloops.something mocks this also and made me giggle, though I'm sure it's a decent distro (that I'll never try).

> Linux from scratch
Tried that a few times, awesome boot times!

> without the compiling
Excellent :biggrin: 

And: compiling myself probably, can work most things out.

Thanks again adn be sure to get a PM :D

---

### Post by haxer on 2006-09-20
I also have to try out Slackish

---

### Post by sl_4ck on 2006-09-25
Slackware is great, but it is not user friendly like Ubuntu.  There is no automatic hardware configuration and device mounting unless you set that feature up yourself.  It doesn't automatically download dependencies when installing packagegs, that can be a good thing or a bad thing depending on how you run your system. Most configuration is done through a text editor, which I prefer.  Slackware is what one would call a true linux distribution, if you really want to learn linux, Slackware is the way to go. You can't beat its stability, security.  But for all the lazy folks, including myself, Ubuntu will do.

---

### Post by victorche on 2006-10-03
[http://www.slackware.com/announce/11.0.php](http://www.slackware.com/announce/11.0.php)

:mrgreen: :mrgreen: :mrgreen:

---

### Post by K.Mandla on 2006-10-04
Cool! I wonder how long before we see fresh editions of Zenwalk and  Slax. ...

---

### Post by arox on 2006-10-04
Zenwalk is independent from Slackware

Zen 3.2 will be released in november

---

### Post by victorche on 2006-10-04
Anyway I am still celebrating it ;)

Great news! I simply love it... Stable, powerfull... Just wonderful!

:KS :KS :KS

---

### Post by Reshin on 2006-10-04
BTW, why kernel 2.4 by default? :-k

---

### Post by xXx 0wn3d xXx on 2006-10-04
> **Reshin said:**
> BTW, why kernel 2.4 by default? :-k

It uses less memory and the 2.6 kernel series drops support for many old pieces of hardware.

---

### Post by victorche on 2006-10-04
> **Reshin said:**
> BTW, why kernel 2.4 by default? :-k

Actually it is not a big deal since you can boot with 2.6 during install. And you have 2.6.18 in /testing and 2.6.17.13 in /extra

So there are 3 kernels to choose from ;)

---

### Post by odinfromvalhalla on 2006-10-04
slack still has great speed and simplicity but i have dumped it since they no longer have gnome in the distro. i know dropline is an option or freerock but it would have been nice to have gnome there.

i was a little dissapointed on slack 10.2 since i have installed a server and in like 1 week the server was highjacked by some script kiddie due to an apache flaw :(. updated the packages and that server still runs now with no problem. i would love to see slack by default with a better package management. i understand from the changelog that there is some support in this last release for that. anyone has tryed it?

---

### Post by halfvolle melk on 2006-10-04
Do you need all 3 ISO's or can you just use the first and do the rest from the net?

---

### Post by Reshin on 2006-10-04
> **halfvolle melk said:**
> Do you need all 3 ISO's or can you just use the first and do the rest from the net?

No such luxury :/

---

### Post by halfvolle melk on 2006-10-04
Hmm, too bad. Oh well, I should get myself a DVD writer one of these days. Thanks for the info.

---

### Post by xXx 0wn3d xXx on 2006-10-04
Hello, I have found a dvd in which I can burn the Slackware Dvd. I think it is about 4.5 Gb. Could I burn this in Gnomebaker. Now onto the Slackware questions:

1. How difficult is Slackware to install on a scale of 1-5 ? 1 being easy 5 being insanely difficult.

2. How difficult is Slackware to use ? 1-5 ?

3. How difficult is Slackware to setup ? In terms of configuration. 1-5

4. How difficult is it to install packages in Slackware ? I heard there were seperate package managers like slap-get (sp?) to manager dependencies. 1-5

5. I heard Slackware uses Lilo, is grub an option ?

Thanks this is a dvd-r so I figured it would be sensible to ask some questions.

---

### Post by bonzodog on 2006-10-05
hi there;

1.Slackware is fairly easy to install, but has a lot more options than ubuntu. Like Ubuntu, it has an ncurses interface for the main installer, and you can choose different levels of install (I use Expert, which allows individual package choosing). It does not do ANY partitioning for you, and advises you to set up the partitions with cfdisk first. cfdisk is all CLI.

2. Slackware IS harder than Ubuntu, but not that difficult if you aren't afraid of the CLI. It will not hold your hand for you, and has almost no GUI config tools - it relies on you finding the config file responsible, and changing things manually. 

3. On the first boot, you are pushed to runlevel 3- the CLI. login as root, and create a user account with 
```
$useradd
```.

Stay logged in as root, and get X setup. At this point there is no xorg.conf file written. 
If you need the nvidia drivers, now would be the time to get them installed. 

It's advisable to have a seperate /home partiton, and normally, I always have a copy of the latest nvidia tarball in there. un-tar and run the driver installer. the latest nvidia drivers actually include a tool which will scan your hardware, and write out the xorg.conf file. 
If you don't have an Nvidia card, then you will need to run the xorg set up tool, called xorgconfig. This will ask a number of questions about your hardware - if unsure, opt for the vesa driver. 
next, test X with startx - if it runs, grand!!.

To get your system to boot to X, you need to alter the /etc/inittab file, and change the runlevel from 3 to 4 (slacks X runlevel). DO NOT TOUCH ANYTHING ELSE IN THIS FILE EXCEPT FOR THE RUNLEVEL LINE!!!!.

Reboot, and cross your fingers. if all went well, you should be presented with a GUI login screen.

4. There are varying ways of installing packages - this is where it gets slightly confusing, as it uses .tgz for it's binary packages. These packages are installed from the command line as root with either pkgtool, which is an ncurses tool which allows for package management, or you can use individual commands such as 'installpkg' or 'removepkg'. There is, however, no dependency checking with this tool.
BUT - there is a package repository, and a tool called slapt-get - this DOES check for dependencies, and now has a new, spiffy front end much like synaptic, called GSlapt. You will need to install this tool manually first - it's not OOB.

5. Yes, Slack uses Lilo - however, grub is an option, and slack will not automatically install lilo at install. if you want to keep grub, then simply tell slack not to install lilo, but this all presumes that grub is also booting another linux OS, as slack does not come with grub.

Hope this helped :D

---

### Post by victorche on 2006-10-05
> **halfvolle melk said:**
> Hmm, too bad. Oh well, I should get myself a DVD writer one of these days. Thanks for the info.

It is not so true... You can install Slackware with only one CD for sure. On the first CD you'll not find X and KDE which means you'll have a nice and simple server-like OS without X

But with terminal you just have to install slapt-get and that's it
Slapt-get is an APT-Like package management tool for Slackware...
So then you'll only need to configure your /etc/slapt-get/slapt-getrc file to choose your source

And then
slapt-get --install *whateveryoulike*

:)

---

### Post by victorche on 2006-10-05
> **bonzodog said:**
> hi there;

...
5. Yes, Slack uses Lilo - however, grub is an option, and slack will not automatically install lilo at install. if you want to keep grub, then simply tell slack not to install lilo, but this all presumes that grub is also booting another linux OS, as slack does not come with grub.

Hope this helped :D

Slackware has grub in /extra
You can simply install it will lilo and then replace lilo with grub
Not so hard job at all... ;)

---

### Post by tseliot on 2006-10-06
> **victorche said:**
> But with terminal you just have to install slapt-get and that's it
Slapt-get is an APT-Like package management tool for Slackware...
So then you'll only need to configure your /etc/slapt-get/slapt-getrc file to choose your source

And then
slapt-get --install *whateveryoulike*

:)
Does slapt-get handle dependencies?

How does it work?

---

### Post by xXx 0wn3d xXx on 2006-10-06
> **tseliot said:**
> Does slapt-get handle dependencies?

How does it work?

Yes, I believe it handles dependencies. It works like apt-get for slackware and it has a new Synaptic-like interface.

---

### Post by tseliot on 2006-10-06
> **xXx 0wn3d xXx said:**
> Yes, I believe it handles dependencies. It works like apt-get for slackware and it has a new Synaptic-like interface.

I have heard that you have to handle dependencies manually in Slackware, that's why I'm asking.

BTW I have already tried slapt-get in Vector Linux but it was a version patched by Vector Linux's developers.

---

### Post by ruhar on 2006-10-06
> I have heard that you have to handle dependencies manually in Slackware, that's why I'm asking.
You are correct.  You have to handle dependencies on your own in slackware.  Slapt-get will not resolve dependencies. 
I've installed Slack 11.0 and I absolutely love it!!  Its very fast and contains very up to date packages and kernels (2.6.17 and 2.6.18 are both available.)

---

### Post by victorche on 2006-10-07
> **tseliot said:**
> I have heard that you have to handle dependencies manually in Slackware, that's why I'm asking.


It is true and not at the same time... Slapt-get itself can handle dependancies, but it depends on the packages themself... They have to be build with a small tool, called "requiredbuilder"

This way the package itself contains a file where all the dependancies are listed.

For example - [http://slacky.it/](http://slacky.it/) - a great Italian site for Slackware packages... All the packages there are using this tool. So if you put their repository... Slapt-get will manage the dependancies ;)

I've read a review of the new Slack these days... It finishes this way:
> What are my impressions of the latest release of Slackware? I'm impressed!

Not only does Slackware 11 keep true to it's roots, but I was able to achieve all my objectives for this installation with minimal effort.

What a truly outstanding system. I tip my hat to Pat and everyone on the Slackware team.

Not a single issue came up, and everything was just the way I remembered it.

There's an old saying: "Slackware - The best 1995 has to offer." And I could not disagree more, but there's one thing Slack did back in '95 that it does now in its modern form...being completely rock solid.

So... happy Slacking to all :D

---

### Post by mahy on 2006-10-14
Hi everybody,

do you know about the condition of Xfce in the newest Slack? Last time i tried it (10.2), there wasn't even a battery indicator and i had to download one in source from Xfce website...

Second, does it recognize ipw2200 wifi adapter by default, or i'll have to search the web for drivers and firmware?

TIA

---

### Post by taurus on 2006-10-14
If you want to run XFce4 with Slack, why not try VectorLinux!!!  It's Slack based but uses XFce4 as it window manager...  It also runs great on a older and slower machines.

[http://www.vectorlinux.com/](http://www.vectorlinux.com/)

---

### Post by bonzodog on 2006-10-15
There is also Zenwalk Linux, which is much more advanced, and has the latest version of Xfce4 with all the plugins.

It also has xorg 6.9, and kernel 2.6.17.

---

### Post by mahy on 2006-10-17
> **bonzodog said:**
> There is also Zenwalk Linux, which is much more advanced, and has the latest version of Xfce4 with all the plugins.

It also has xorg 6.9, and kernel 2.6.17.

Alrite, i installed Zenwalk and it works perfectly, even though i had to compile my own kernel to use wifi card ;)

The one thing that bugs me are THE FONTS. How do i make them look nicer? In Ubuntu, they are already worse than in windows, but they're much worse in Slack and Zenwalk :(

Thanks for any ideas

---

### Post by bonzodog on 2006-10-17
In the xfce user interface settings, make sure that hinting is on full and anti-aliasing is also on, and sub-pixel hinting. That should clean the fonts up quite a bit, but I admit, they aren't perfect. 
This is not Zenwalks fault however - the reason windows fonts look so good is because they use a proprietry algorithm to draw the characters. Linux does not have this feature, thus just renders and hints the characters as much as possible. 
You could try installing the mscorefonts, though i'm not sure where or how you do this.

---

### Post by tseliot on 2006-10-17
> **mahy said:**
> Alrite, i installed Zenwalk and it works perfectly, even though i had to compile my own kernel to use wifi card ;)

The one thing that bugs me are THE FONTS. How do i make them look nicer? In Ubuntu, they are already worse than in windows, but they're much worse in Slack and Zenwalk :(

Thanks for any ideas

Try installing Dejavu fonts

---

### Post by mahy on 2006-10-17
Thank y'all, i found some howtos, and now the fonts are on par with those in ubuntu.

---

### Post by tigerpants on 2006-10-18
Slackware 11 is da bomb. Just booted into it for the first time, having played with 10.2 a while back, and the speed of it is so impressive. Yeah, it needs a little tweaking around with, but that's half the fun. Shame it doesnt come with Gnome, but I'll be sticking dropline on it soon anyway. 

Get a spare hard drive, and dive in. It's worth it :D

---

### Post by ruhar on 2006-10-19
Yeah, I put on the release candidate of dropline Gnome 2.16 last night and it is very nice!!  Dropline produces a really polished gnome and includes some Gtk must haves (e.g. liferea, inkscape, Abiword, BlueFish, etc...)

---

### Post by whiterabbit on 2006-10-25
Downloading the DVD iso as I type this.  Looking forward to trying it out.

---

### Post by factotum218 on 2006-10-26
Slackware had always been my #1 choice in Linux up until about a year ago when i decided a package manager and a big repository of packages helped a lot on the Desktop system. As a server I will always go the Slackware or OpenBSD route. But for a large robust and extensive Desktop system i would rather go the Debian or *buntu route on newer systems.

---

### Post by towsonu2003 on 2006-10-26
slackware, the one that made me go for linux :) and the first linux distro I have ever used.

---

### Post by halfvolle melk on 2006-10-31
> **factotum218 said:**
> Slackware had always been my #1 choice in Linux up until about a year ago when i decided a package manager and a big repository of packages helped a lot on the Desktop system. As a server I will always go the Slackware or OpenBSD route. But for a large robust and extensive Desktop system i would rather go the Debian or *buntu route on newer systems.
I think I'm sort of seeing your point atm :) But still it's nice to play around with and learn how it works.

---

### Post by towsonu2003 on 2006-10-31
anyone interested in a 90 minute interview with Slackware devel?

[http://www.desktoplinux.com/news/NS8907215984.html](http://www.desktoplinux.com/news/NS8907215984.html)

:)

---

### Post by Ben Sprinkle on 2006-11-21
Hello all, I know this is sposed to be in the 'Other OS Talk', but just a quick question.
After burning all 4 iso's, I saw a screenshot of an option to choose which desktop enviornment to install. Is this true?

---

### Post by taurus on 2006-11-21
I am going to move this over to Other OS Talk--Slackware.  And to answer your question, Slackware doesn't have that option.  It will install KDE so if you want to use Gnome, then you need to install the Freerock version and if you want to use XFce4, then you can try either Zenwalk or VectorLinux.  

Maybe you mean the Fedora Core screen!

---

### Post by Ben Sprinkle on 2006-11-22
Freerock? Is this just slack with gnome? That's what I need.
Link please?

---

### Post by zgornel on 2006-11-22
[http://gsb.freerock.org/download/](http://gsb.freerock.org/download/) ;)

---

### Post by haxer on 2006-11-23
Hello ive downloaded the slackware dvd "the whole dvd with all discs" and burned it .. rebooted my computer installation came up i installed it then rebooted the computer then ive got this message "grub error 17" why did this happen? What did i do wrong? :-k

---

### Post by mysticrider92 on 2006-11-23
I think that grub error 17 means that the grub entry for slackware has the wrong part of the hard drive for the kernel. 

How is your hard drive partitioned? And can you post the Slackware entry in /boot/grub/menu.lst?

---

### Post by haxer on 2006-11-23
I had some trouble with my ubuntu system so i wanted to install slackware on my hdd and i formated the 2 and then when i wanted to use lilo "slackwares boot system name i think" the grub error 17 came so i installed ubuntu again :)

---

### Post by angryfirelord on 2006-11-24
(3 months ago) Coming from a apt-get/yum world, I decided to try Slackware for the first time. I was impressed by its responsiveness, the ability to set up madwifi easily, and a easy to use install. However, what made me get rid of it is its lack of a package management system.

Today my computer only has Ubuntu on it, but I'm wondering if there is an effective package manager out there for Slackware? I've heard of slapt-get which is good at installing packages, but bad at dependencies. 

The reason why I'm curious is to get a little more manual control over linux. Gentoo takes too long for me so Slackware seems like a good choice. 

Also, how would I keep GRUB instead of LILO? I assume that I just don't install a bootloader in Slack and just run a grub-install in Ubuntu.

Thanks for any info.

---

### Post by deepwave on 2006-11-24
I am not familiar with Slackware itself.  But you should have a choice between installing GRUB or LILO, from the Slackware installer.

Not sure how Slackware is supposed to give more manual control over Linux.  Every distro uses similiar configuration files, so you can manual tweak stuff in any Linux distro.  The only issue is that some of the automatic or graphical tools might throw fits over your changes.  Ubuntu is fairly nice with that.

A warning though: with any distro too much manual tweaking can lead to breakage.  One of the reasons I migrated from Gentoo, was the constant need for configuration, and I broke things more often then fixed them.

---

### Post by 23meg on 2006-11-24
Check out slapt-get.

---

### Post by bonzodog on 2006-11-26
Slapt-get is as close as you get for dependency handling;

If you examine how a package is built, closely, you will see that the dependency handling comes down to the inclusion of a script at the build stage - this is called a SlackBuild.sh script in this case. Traditionally, Slackware has always had binary packages in the form of .tgz's, and all of slacks younger derivatives do as well.

However, it was not a standard to include this script until recently, as slapt-get is still not part of a standard install, and a lot of us slackers still like to build software manually ourselves. 

I now use Zenwalk Linux, which _does_ handle dependencies as all of it's packages have to have a ZenBuild script included, and it comes with a good package manager called netpkg, which sorts all of this out for you.

---

### Post by RandomJoe on 2006-12-03
Slackware _does_ give you a choice of window managers.  But Gnome is not one of the choices.  You can have KDE, or one of a number of the lighter-weight environments.

Dropline Gnome is the way to get Gnome installed on top of a standard Slack install.  [http://www.droplinegnome.org/](http://www.droplinegnome.org/)

---

### Post by Wim Sturkenboom on 2006-12-08
I'm not convinced of dropline. Installed it and it works, but resulted in lots of errors (or warnings) when shutting down the PC.

It seems to have modified configs that it's not supposed to modify. I have heard this problem more often.

---

### Post by darkenedday on 2007-04-07
I just installed Slackware 11.0 today, it's pretty nice, fast, and seems rock solid, I like it alot however I have one HUGE complaint so far 

the repos for slapt-get seem INCREDIBLY slow, I mean download speeds of like 8kb/s does anyone know any faster repos I may be able to use?

I'd like to make it awhile before I have to move on to the last linux titan I have yet to conquer: Debian (I figured since I've tried so many derivatives how different can that be? and haven't tried it yet, but I figure I might as well give it a shot if this doesn't work out)

please please PLEASE let me know if there are any decently fast slapt-get repos out there

EDIT:
also I have another question, anyone know where I can get a good bootsplash screen? kinda plain white on black with the full name logo or such? And can that someone give me some help on how to install such a thing (kind've noobish I know but I've never had to do it before)

---

### Post by StarsAndBars14 on 2007-04-08
I tried slapt-get for a while and didn't like it.

If you can't uninstall it without breaking your system, don't install it.

---

### Post by saulgoode on 2007-04-08
To my knowledge, Slackware does not provide for a "bootsplash" support. Slackware uses a "pristine" kernel directly from the linuxkernel.org and bootsplash support is only available if you apply a patch to the linux source before compiling. At least that was the situation last time I checked.

---

### Post by bonzodog on 2007-04-09
Yes, thats correct.

Slackware prides itself on being 'vanilla', which means as few patches as possible, and all software built just as it comes down from sourceforge or where-ever.

Zenwalk is basically Slackware, but on the bleeding edge, with a patched kernel to allow for a bootsplash, but thats the only patch there is.

---

### Post by bodhi.zazen on 2007-06-16
Slackware Linux 12.0 RC1 was announced :)

---

### Post by marsmissionaries on 2007-06-16
I can't wait till 12.0 final is released, i will install it in a heartbeat.

---

### Post by Elvish Legion on 2008-01-16
I'm thinking about trying out slack, are these [http://www.slackwarehelp.org/](http://www.slackwarehelp.org/), the 'offical' forums?

Also, I was reading that the package manager doesn't handle depencies...there was something for this but I forget what it was called, is this needed?

Any advice for someone new to slack?

---

### Post by towsonu2003 on 2008-01-16
> **Elvish Legion said:**
> I'm thinking about trying out slack, are these [http://www.slackwarehelp.org/](http://www.slackwarehelp.org/), the 'offical' forums?

Also, I was reading that the package manager doesn't handle depencies...there was something for this but I forget what it was called, is this needed?

Any advice for someone new to slack?

I am not uptodate about Slackware, but this might be a better choice: [http://www.linuxquestions.org/questions/slackware-14/](http://www.linuxquestions.org/questions/slackware-14/)

as per the package handling, I googled for <slackware package handling> and found these two: 
[http://freshmeat.net/projects/slaptget/](http://freshmeat.net/projects/slaptget/) (slapt-get)
[http://www.newmobilecomputing.com/story/3974](http://www.newmobilecomputing.com/story/3974) (a slackware package management guide)

also, googling for <slackware package howto>, I found
[http://www.linuxpackages.net/howto.php?page=package&title=Package+Howto](http://www.linuxpackages.net/howto.php?page=package&title=Package+Howto) (which is not quite what you are loking for, but linuxpackages.net is kind of a community-driven repository for Slackware packages)

hope this helps.

---

### Post by Whiffle on 2008-01-16
> **Elvish Legion said:**
> I'm thinking about trying out slack, are these [http://www.slackwarehelp.org/](http://www.slackwarehelp.org/), the 'offical' forums?

Also, I was reading that the package manager doesn't handle depencies...there was something for this but I forget what it was called, is this needed?

Any advice for someone new to slack?


I don't think there is actually an officially sanctioned forum for slack, but theres many many users out there and I'm usually able to find what I need just by googling.  

Out of the box, it doesn't handle dependencies.  Slapt-get is a pretty good package management frontend for it though, that technically does handle dependencies, but not all slackware packages have dependency information in them, so it doesn't always take care of it for you.  Dependency resolution isn't always needed, but it sure is convenient.

---

