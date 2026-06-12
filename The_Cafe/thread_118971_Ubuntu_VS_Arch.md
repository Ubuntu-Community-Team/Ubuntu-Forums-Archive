---
title: "Ubuntu VS Arch"
date: 2006-01-18
forum: The Cafe
---

### Post by Gandalf on 2006-01-18
Hello,

I just wanted to know everyone's opinion on Ubuntu and [Arch](http://www.archlinux.org), and before anyone ask Arch is not Newbie dedicated distro :)

Ok i will begin describing what ive experienced (me and another one, he knows himself :p )

I'm using ubuntu since Warty release and i like it a lot, it is user friendly, easy to install, easy to update/upgrade, nothing more to say, talking about ubuntu VS some others, they aren't even compared (hey! am talking about RPM based distro :D a.k.a FC/Mandriva)

But allow me now to compare 1 year Ubuntu VS 1 week [Arch](http://www.archlinux.org)
Ubuntu is user friendly or may i say Newbie dedicated distribution, it's a very cool envirement to learn linux, to work, to play games. Arch is a bit more experienced user distro, for example, When u boot boot with installation cd into  you will get into a console where u will launch installer manually, partiton manually with cfdisk, select packages, configure grub/rc.conf etc.. so the installer is not fancy, as well as installing xorg, u have to configure it urself (as usual having ubuntu's xorg.conf will save time on it :) ). For now u may think that Ubuntu is much more better than arch, but my answer is NO! why? well leave installation behind coz following an installer questions is like following a good [installation guide](http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html)

Now you are wondering why did i say No!, well because of the below reasons:
[list]
[*]Arch is 3 / 4 (maybe more) faster than Ubuntu, when i installed it, i couldn't beleive it, i felt i was using FreeBSD (yes i tried freeBSD its cool, but package system sucks)
[*]It has a very good package manager, similar to apt-get didn't find any difference till now except the easy way to create a binary package for it (look below) also it's easy to use ( pacman -Syu = apt-get update && apt-get upgrade )
[*]Packaging creation is very easy for example newton wasn't in the repo (it ain't in ubuntu as well), I wanted to install it, so i have created a binary package out of sources in a Very Easy way, I just get one file called PKGBUILD specially for it and running makepkg will create a package similar to .deb instaling it would be with pacman -A ( = dpkg -i )
[*]The most important point is that Arch is heavly up to date, let's see umm for example Thunderbird 1.5 was released Jan 12th 2006, it was in Arch official Repo Jan 13th 2006 ( [http://www.archlinux.org/packages.php?id=4237](http://www.archlinux.org/packages.php?id=4237) ) While ubuntu is not in that case (even dapper hasn't got TB 1.5 till now )
[*]Rebuilding packages is Very easy, it is called abs which is similar to portsnap in FreeBSD
[/list]
I guess above reasons are enough to show why i liked Arch more than ubuntu but remember Going with Arch means saying good bye to GUI apps, No update manager, no users management manager etc... (though everything can be installed from [AUR](http://aur.archlinux.org) 

Please note also that i posted this topic with no offence intended to anyone, I just want to know everyone's opinion, even if u can't try it i guess i've gave a good point of view between ubuntu/arch, if u want to give it a try follow [this](http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html) to get an up & running system and im sure that if u don't care about being forced to use Terminal, u will like it ;)

---

### Post by Perfect Storm on 2006-01-18
You forgot to mention that arch is i686 optimized ;)

Arch is a very cool distro and very fast. But as you said it's more for experience users who aren't afraid using commands.

---

### Post by kairu0 on 2006-01-18
After hearing positive comments about Arch, I downloaded it and gave it a try.

My trial stopped abruptly when the CD wouldn't boot on my PC with both "arch" and "arch-noscsi" parameters. Yes, the CD passed the MD5 checksum.

---

### Post by Gandalf on 2006-01-18
> **Artificial Intelligence]You forgot to mention that arch is i686 optimized  said:**
> 
Yea I forgot to mention that  :D

[QUOTE=kairu0]After hearing positive comments about Arch, I downloaded it and gave it a try.

My trial stopped abruptly when the CD wouldn't boot on my PC with both "arch" and "arch-noscsi" parameters. Yes, the CD passed the MD5 checksum.
hmm haven't u tried to ask their forum support, guys there are advanced and helpfull :)

---

### Post by BSDFreak on 2006-01-18
[quote=Gandalf]Arch is 3 / 4 (maybe more) faster than Ubuntu, when i installed it, i couldn't beleive it, i felt i was using FreeBSD (yes i tried freeBSD its cool, but package system sucks)[/QUOTE]

The ports system sucks or the pkg system sucks and why do you believe it sucks (it's generally thought of as the best system available bar none when it comes to availability and ease of use).

Regarding Arch, personally i thought that the lack of applications coupled with stability issues made it unusable, i returned to slackware after about a month of using it (and it's nowhere near FreeBSD 6/7 when it comes to speed).

---

### Post by Gandalf on 2006-01-18
> **BSDFreak]The ports system sucks or the pkg system sucks and why do you believe it sucks (it's generally thought of as the best system available bar none when it comes to availability and ease of use).
[/QUOTE]
Well Just a hint, [upgrade to GNOME 2.12](http://www.freebsd.org/gnome/docs/faq210.html#q2)  Took 13 hours on a fresh install (Tried it two times)  said:**
> 
Regarding Arch, personally i thought that the lack of applications coupled with stability issues made it unusable, i returned to slackware after about a month of using it (and it's nowhere near FreeBSD 6/7 when it comes to speed).
I did use FreeBSD6, I'm using Arch right now (replaced ubuntu) and I feel they are pretty much the same speed, maybe not as fast as FreeBSD is ( Unix in general is faster than Linux system) But beleive me it's pretty much the same!

---

### Post by DaMasta on 2006-01-18
Thanks for this post. I was planning on giving Arch a try and now I'm a little more prepared.

---

### Post by BSDFreak on 2006-01-18
> **Gandalf]Well Just a hint, [upgrade to GNOME 2.12]("http://www.freebsd.org/gnome/docs/faq210.html#q2")  Took 13 hours on a fresh install (Tried it two times)  said:**
> 

I assume you used the ports system to do that then. You can install via pkg instead, it's as fast as apt. It's still amazing though, i updated my entire machine from 5.3 to current via cvsup buildworld, buildkernel and then portupgrade -af, that rebuilds every installed package, including an upgrade of every KDE, XFCE, xorg and so on and it didn't take much more than 13 hours on an Athlon-XP 2300 with 1 gig of ram. Sounds like something went wrong for you.


[QUOTE]I did use FreeBSD6, I'm using Arch right now (replaced ubuntu) and I feel they are pretty much the same speed, maybe not as fast as FreeBSD is ( Unix in general is faster than Linux system) But beleive me it's pretty much the same!

Well then they must have done something with it because when i tried Arch (about six months ago) it was considerably slower than FreeBSD and not really much faster than Slackware (i ran them all on the same machine).

Did you use the stable branch? If not, a recompile is almost mandatory to get rid of all the debugging, it slows it down to a crawl.

Anyway, this is my opinion, that's all, i prefer BSD. :)

---

### Post by Buffalo Soldier on 2006-01-18
downloading arch iso now.

---

### Post by WildTangent on 2006-01-18
I was considering giving this a try last night after bored2k spoke so highly of it in #ubuntuforums on IRC, but now I REALLY want to try it out :) Perhaps if I have time on the weekend...

-Wild

---

### Post by Viro on 2006-01-18
[QUOTE=Artificial Intelligence]You forgot to mention that arch is i686 optimized ;)
[/QUOTE]

Does that give a noticeable performance improvement?

---

### Post by poofyhairguy on 2006-01-18
Thanks for the post. More experianced users (aka those who demands the newest apps faster than backports can or will provide) would be happy with Arch.

Personally I won't use it again until I hear it has more in its repos (last time I checked it was a mear fraction of Ubuntu) but I am happy for you to talk about it here.

Note for all concerned: No trolling in this thread. This is a nice thread. Lets not mess it up.

---

### Post by fuscia on 2006-01-18
[QUOTE=Gandalf]I did use FreeBSD6, I'm using Arch right now (replaced ubuntu) and I feel they are pretty much the same speed, maybe not as fast as FreeBSD is ( Unix in general is faster than Linux system) But beleive me it's pretty much the same![/QUOTE]

i've seen it mentioned, on numerous occassions, that freebsd is faster than linux. if that's true, why is that? (please insult my intelligence with the simplicity of your response. thanks.)

---

### Post by bored2k on 2006-01-19
What's funny about arch is the fact that although yes, you have to **not** be afraid of the command-line, after a few days have gone by and after I've reinstalled it several times (playing with it), I noticed that getting the system up and running the way I wanted it to was (In **my** opinion) arguably the same or faster than UBuntu. Why do you ask? Well, although the repositories are considerably smaller than Ubuntu's, the "meat" of them are a lot more focused on what the regular user/power-user/linux-juggler wants. I'm talking about having the *codecs* package (w32codecs on ubuntu), the audio codecs, Sun's java (j2re, j2sdk), flash (flashplugin), and a whole plethora of packages Ubuntu, due to its for the 100% free/libre human will never be able to have on its **default** repositories.

I still haven't said why I got my functional distro up and running faster than Ubuntu. Well, on Ubuntu, the regular install takes me about 40-60 minutes (specially slows down while copying a gazillion debs I'll mostly don't use). The UBuntu server install + gnome usually takes as much too. On arch, the base install takes about what, 3 minutes? 5? It takes a lot less than 5 minutes, but let's leave it at that. After that, configuring the network (via static IP or dhcpd) was so easy it was silly (took me a while to figure it out at first... probably due to me getting to use to GUIs). After the net's configured correctly and the KDE/Gnome packages are in place (I have my own local Arch repository, so no need to fetch them off the net), any of them install a _lot_ faster than what the regular sudo apt-get install kubuntu-desktop would take. On top of that, me being able to log in for the first time, make NO changes to the sources.lst file (ok ok, the pacman.conf file :-P) and do a nice and quick
```
pacman -S xorg gdm kde azureus codecs divx4linux gstreamer gst-plugins-mad gst-plugins-flac gst-plugins-mikmod libmikmod kmplayer mplayer-plugin x264 flash-plugin j2sdk bittorrent amarok-base-mysqlfree anjuta alsa-utils alsa-lib alsa-oss k3b amule
```(of course, nothing stops anyone from making a nice script for this, but its that easy), see how all that installs fast++ with no need to go nuts with getting certain files from not-so-trusted repositories is just great.  By the time It takes my fully working environment (that means full audio/video support, C/C++ IDE/compiler with all the shabang, X and a few more things), a regular Ubuntu install would still be finishing up with none of the above.

Oh and by the way, I haven't mentioned its speed, or I have? It's **ridiculous**. I won't go as much into details as Gandalf, but it's pretty fast. And for once, fluxbox didn't take a full moon flip to load. KDE? This is a KDE I can actually use. Doesn't go boom here, and its as fast and more snappier than  Gnome.

Even when I install find it challenging but easy (heh), you still learn a lot from it. It took my three days to figure out my DHCP was the source of my networking troubles, but even when It didn't work, I learned a lot from it.

Right now, I'd take it over Ubuntu. Not because its necessarily better (they're aimed at different crowds), but because you learn a lot more from it. The way I see it, it's the step Ubuntu users who **want** to keep learning their way into Linux and/or --force-focus on their CLi input need to take. For everyone who just wants their OS to work, please, do not even try it. It's on the arch About page:
>  Arch Linux is an i686-optimized linux distribution targeted at competent linux users (read: not afraid of the commandline)

I just noticed how I forgot to speak about how retardedly updated their packages were, but I also noticed that If I even try to write in full details on why I like arch, It'd take me a while.


All in all, should someone on the streets ask me about Linux and what distribution to try,  I'd still definitely say Ubuntu. Some would say the arch-type (non-GUI) is better for new users to learn things the Linux way, but from personal experience, teaching users how to use the CLi because Linux is retardly more hard is not a good method, specially when Automatix's around ;).

For everything else, there's Masterc... err, arch.

P.S. -  Gandalf, adding GDM to the daemons is not necessary. I don't have it and it works.

---

### Post by rpgcyco on 2006-01-19
I switched to Arch six months ago, and have not looked back. I love it's almost always up to date state. I've never had problems with instability when using the "stable" repos.

It's package system is as good, if not more simpler than Debian based systems (my opinion), but still powerful.

A lot of the speed difference I noticed between Arch and Ubuntu was mostly due to the large amount of services enabled by default on Ubuntu, though even basic things such as listing a directory in the GTK File chooser takes longer in Ubuntu than Arch.

I still like Ubuntu however, it's what restored my faith in Linux as a useable desktop system and enabled me to learn at a slower pace. I still recommend it for people new to Linux.

- Rpg Cyco

---

### Post by nocturn on 2006-01-19
[QUOTE=fuscia]i've seen it mentioned, on numerous occassions, that freebsd is faster than linux. if that's true, why is that? (please insult my intelligence with the simplicity of your response. thanks.)[/QUOTE]

FreeBSD is actually much older then Linux is, it is what is called genetic Unix (evolved from the original Unix source code) while Linux is a re-implementation of the POSIX standard.

Their kernels are hugely different which makes it difficult to compare them and they handle a lot of stuff in a different way.  It was largely accepted that FreeBSD outperformed Linux 2.4 by a large margin, But as I heard and experienced, there was a significant slowdown after the 4.x series while Linux improved in 2.6.

My experience from running both on the same (server) machine is that Linux 2.6 and FreeBSD 5 came out roughly equal, but FreeBSD remained more responsive under high loads.

Linux 2.6 with Reiserfs did outperform FreeBSD with UFS2 on IO operations though.

In the end, what frustrated me the most about FreeBSD was the lack of binary updates, even for a lot of security patches.

---

### Post by Gandalf on 2006-01-19
[QUOTE=BSDFreak]I assume you used the ports system to do that then. You can install via pkg instead, it's as fast as apt.[/QUOTE]
Well from what i can read on that page, they mentioned not to upgrade gnome with portage (if am not mistaken by the name :$) :)

Thank you bored2k for the more **enlighted** (? :D ) post about ubuntu and arch, and like everyone said too, Arch is not for new users, as all new users will tell us (why do i have to type "hibernate" and patch kernel and etc to get suspend2 on arch while i can hit hibernate on windows :) ) so Ubuntu Still and will always be a good place for new comers, for GUI lovers too (an advanced user doesn't mean he can't use ubuntu :D) I personaly even on ubuntu have never used Synaptic, I always prefered VI on GEDIT, so being with Arch was not much different on the Usage, though there was some things to do, am still strugling since 3 days to get Gensplash (kinda like usplash) and finally this morning i got suspend2 working.. but at least when i am not maintaining it and/or playing with kernels i really feel like i am on ubuntu, not much changes but all the time I **must** have Terminal open and ready for any command...

anyway as mentioned before and i'll mention it again please keep this topic clean **I** don't mean any offense to any ubuntu Lover/User we are just chatting here, everyone likes what he want to like (freedom no? :D) so let's just make it a comparison topic and not a **War** topic :p

---

### Post by BSDFreak on 2006-01-19
[quote=Gandalf]Well from what i can read on that page, they mentioned not to upgrade gnome with portage (if am not mistaken by the name :$) :)[/QUOTE]

Portage isn't in FreeBSD, it's Gentoo. The *ports* system is what you used if it compiled everything for you before installing it (which is what the ports system does, it works that way) the pkg system deals with binary packages and is what sysinstall uses. For example, portinstall KDE will take hours to complete because it's compiled before it's installed, this gives you the advantages of choosing how some things are compiled though, for some packages (like kmplayer) it's a better way to install since you can choose if it should be compiled with support for arts, xine and so on, if you use pkg_add instead then it fetches the binaries and executes the install script, it's as fast as apt-get install KDE would be. Hope that clears things up. :)

---

### Post by Gandalf on 2006-01-19
[QUOTE=BSDFreak]Portage isn't in FreeBSD, it's Gentoo. The *ports* system is what you used if it compiled everything for you before installing it (which is what the ports system does, it works that way) the pkg system deals with binary packages and is what sysinstall uses. For example, portinstall KDE will take hours to complete because it's compiled before it's installed, this gives you the advantages of choosing how some things are compiled though, for some packages (like kmplayer) it's a better way to install since you can choose if it should be compiled with support for arts, xine and so on, if you use pkg_add instead then it fetches the binaries and executes the install script, it's as fast as apt-get install KDE would be. Hope that clears things up. :)[/QUOTE]
Yeah exactly thanks for refreshing my memory up, from what i remember i used portsnap
```

portsnap fetch
portsnap update

``` again i hope i'm not mistaken about arguments it's been a while and i used it so little time
anyway i will quote what that page has
```

NOTE: Do not run portupgrade(1) to upgrade to GNOME 2.12!

The simple answer is this:

   1. CVSup your ports tree.
   2. Download the FreeBSD GNOME Project's upgrade script.
   3. Run the script as root. Read a good-sized book.

```
i didn't use CVSup i used portsnap, and followed the script :)

anyway let's keep this topic Arch/Ubuntu shall we? :)

---

### Post by foxy123 on 2006-01-26
I still have to make Arch workable on my desktop's test drive. It feels faster at the moment. However, I was thinking why is that. 

OK, packages are i686 optimised. Does it mean that all packages are compiled with this optimisation and how much it contributes to the speed. You can have i686 kernel in Ubuntu as well. 

Another thing is that Arch does not have a lot of services loaded by default, but I guess you can unload all those services in Ubuntu and make it slimmer. 

And finally that Arch does not have all those GUI config tools. Does it really speed it up? I do not see how, frankly speaking, but I am not a knowledgeable enough to judge it. I mean one can always use command line in Ubuntu to avoide GUI tools, but how the presence of those tool influences the speed of the system.

To sum up, after thinking about all that I've got two questions: what is the main reason of Arch being faster and is it possible to tweak Ubuntu to match it?

---

### Post by midwinter on 2006-01-26
If there was a viable 64 bit version I would be using it already... it sounds like the distro for me.  Hopefully one day.

---

### Post by Gandalf on 2006-01-26
I think Arch is faster than Ubuntu for two reasons
kernel has been built optimized, as well as many packages
Arch does not have anything loaded by default except (ATM in Testing) udev

---

### Post by Gandalf on 2006-01-26
[QUOTE=midwinter]If there was a viable 64 bit version I would be using it already... it sounds like the distro for me.  Hopefully one day.[/QUOTE]
Currently there isn't Arch64, check [Current state of Arch64 developement](http://wiki.archlinux.org//index.php/Current_state_of_Arch64_developement) and [Arch64](http://wiki.archlinux.org/index.php?title=Category:Arch64&action=edit)

---

### Post by foxy123 on 2006-01-26
[QUOTE=Gandalf]I think Arch is faster than Ubuntu for two reasons
kernel has been built optimized, as well as many packages
Arch does not have anything loaded by default except (ATM in Testing) udev[/QUOTE]
So does it mean that if I install i686 kernel in Ubuntu and unload unnecessary stuff, I will get close to Arch, holding back b only unoptimised other packages?

---

### Post by Gandalf on 2006-01-26
I think yes, but u have many things to unload maybe install server one, then compile the kernel after that install gdm, gnome and gamin that would make the system lightwight, if u seek more then go for fluxbox instead of gnome, but i have no idea how much it would be

---

### Post by BSDFreak on 2006-01-26
[quote=Gandalf]Yeah exactly thanks for refreshing my memory up, from what i remember i used portsnap
```

portsnap fetch
portsnap update

``` again i hope i'm not mistaken about arguments it's been a while and i used it so little time
anyway i will quote what that page has
```

NOTE: Do not run portupgrade(1) to upgrade to GNOME 2.12!

The simple answer is this:

   1. CVSup your ports tree.
   2. Download the FreeBSD GNOME Project's upgrade script.
   3. Run the script as root. Read a good-sized book.

``` i didn't use CVSup i used portsnap, and followed the script :)

anyway let's keep this topic Arch/Ubuntu shall we? :)[/quote]

The ports tree is a collection of make/config files, you will compile anything you install via ports. Whether you use cvsup with a file containing "ports-all" or you use portsnap fetch/extract/update doesn't really matter, you will still have downloaded only the config/makefiles for the ports tree.

The PKG version is compiled binaries, you can use pkg_add to add compiled binaries to your system, it's as fast as installing it via apt.

You can make it easy by using sysinstall and set your version to current, then go to packages and install it from there.

You were the one who brought FreeBSD into this and the discussion continues since you are not capable to comprehend the simple concepts of PKG and PORTS.

---

### Post by raublekick on 2006-01-26
I've been thinking about giving Arch a try, but the size of the repos kinda has me worried. I'll have to check it out more in depth, but that's really the only thing holding me back.

Ok, I don't really feel prepared for the "no-GUI" nature of it, but I'd like to learn. Maybe this would be a good project after this semester ends. Until then, I think I'll stick with Breezy/Dapper (when it's released).

---

### Post by midwinter on 2006-02-08
I got around to installing Arch yesterday.  I love it already, so damn fast.  Everything is slick and 5.10 seems clunky in comparison.  Dragging a terminal in gnome used to leave junk all over the screen for me in 5.10.. none of that here.  The install and getting everything going was simpler than I thought it would be, but I would definitely spend a month or two with Ubuntu before jumping in..  

I still have to play with Arch a bit more but I absolutely recommend it so far.

---

### Post by kabus on 2006-02-08
> I've been thinking about giving Arch a try, but the size of the repos kinda has me worried. 

While Arch can't compete with Debian I haven't found much software I need that isn't available from either the official repos or the AUR. 
Another thing is that Arch makes it very easy to create your own packages, at least compared to the nightmare of creating a proper deb.

---

### Post by foxy123 on 2006-02-08
Reading some reviews about Dapper I was thinking if 6.04 will be comparable to Arch in terms of speed. At least many mentioned that it is much faster than Breezy. However, what I like about Arch is that although its repos are smaller they are much up to date than Ubuntu. The only way to have updated packages on Ubuntu is to run development version all the time which is quite insecure. Unfortunately backports do not provide enough updates.

---

### Post by Gandalf on 2006-02-08
Also to note, [Gnome 2.13](http://bbs.archlinux.org/viewtopic.php?t=18561) which i have finally completed yesterday (building/compiling) is a little bit behind being stable, I still have a little problem about the Obligation to use gstreamer 0.10, but other than that Arch really rocks, I never was able on ubuntu to make my own things, on Arch i have my own repo, more than 50 packages are made, even with packages newer than any arch repo... so Really Pacman JUST ROCKS!!!

---

### Post by bored2k on 2006-02-08
[QUOTE=foxy123]Reading some reviews about Dapper I was thinking if 6.04 will be comparable to Arch in terms of speed. At least many mentioned that it is much faster than Breezy. However, what I like about Arch is that although its repos are smaller they are much up to date than Ubuntu. The only way to have updated packages on Ubuntu is to run development version all the time which is quite insecure. Unfortunately backports do not provide enough updates.[/QUOTE]
The repositories are actually smaller, but a lot more of the "good"/useful stuff is here. In ubuntu, never will you be able to boot your machina for the first time and be able to install totem-xine, codecs (_All kinds_), divx4linux, mplayer-plugin, flashplugin, j2re, j2sdk, azureus and many more applications that almost everyone uses that on Ubuntu, you'd have to manually edit your sources.list to include other ones that you might not be so sure about. On top of that, I must remember everyone that like Gandalf and everyone else said, building your own packages is a lot easier than trying to build a proper debian package by yourself. Again, I'm sure it doesn't have the gazillion files the ubuntu repositories have, but at least it has everything I need. And what it doesn't have, I can easily build my own packages.

---

### Post by bored2k on 2006-02-08
The repositories are actually smaller, but a lot more of the "good"/useful stuff is here. In ubuntu, never will you be able to boot your machina for the first time and be able to install totem-xine, codecs (_All kinds_), divx4linux, mplayer-plugin, flashplugin, j2re, j2sdk, azureus and many more applications that almost everyone uses that on Ubuntu, you'd have to manually edit your sources.list to include other ones that you might not be so sure about. On top of that, I must remember everyone that like Gandalf and everyone else said, building your own packages is a lot easier than trying to build a proper debian package by yourself. Again, I'm sure it doesn't have the gazillion files the ubuntu repositories have, but at least it has everything I need. And what it doesn't have, I can easily build my own packages.

---

### Post by wrtpeeps on 2006-02-08
i used arch for a while. It requires a lot more skill to install, as most of it is done through commands. Pacman is the package manager as far as i remember.

---

### Post by Gandalf on 2006-02-08
u remember correctly, and no it doesn't require more skills, it required to read more :)

---

### Post by Perfect Storm on 2006-02-08
Gandalf you have use my splash for arch ^^ : [http://www.gnome-look.org/content/show.php?content=28891](http://www.gnome-look.org/content/show.php?content=28891)

[IMG]http://www.gnome-look.org/content/pre1/28891-1.png[/IMG]

---

### Post by Gandalf on 2006-02-08
WOW that's a nice one Artificial, I'll add it
Thx :)

---

### Post by DaMasta on 2006-02-08
All my parts just came in for my laptop. I'll be installing Arch in the A.M......assuming all goes well with the laptop build. I'm pretty excited about giving this distro a try.

---

### Post by briancurtin on 2006-02-08
[QUOTE=raublekick]Maybe this would be a good project after this semester ends. Until then, I think I'll stick with Breezy/Dapper (when it's released).[/QUOTE]
same with me, i want to try it out but i dont have time to mess with this right now because of school. i might start reading about it in my free time so that if i do get a day off i can try and get it running at least

im very interested in arch though, sounds very fast and i have a very fast computer, and i like fast stuff.

---

### Post by briancurtin on 2006-02-08
[QUOTE=raublekick]Maybe this would be a good project after this semester ends. Until then, I think I'll stick with Breezy/Dapper (when it's released).[/QUOTE]
same with me, i want to try it out but i dont have time to mess with this right now because of school. i might start reading about it in my free time so that if i do get a day off i can try and get it running at least

im very interested in arch though. it sounds very fast and i have a very fast computer, and i like fast stuff.

---

### Post by bored2k on 2006-02-08
[QUOTE=briancurtin]same with me, i want to try it out but i dont have time to mess with this right now because of school. i might start reading about it in my free time so that if i do get a day off i can try and get it running at least

im very interested in arch though, sounds very fast and i have a very fast computer, and i like fast stuff.[/QUOTE]
The harder step is installing Arch for the **first** time. After that, it's as easy as any debian-based distribution. If you have a copy of ubuntu's xorg.conf in hand and you know how to enable your network, you're golden.

---

### Post by briancurtin on 2006-02-09
that doesnt sound too bad at all. ive never had to enable the network on my own, it has always just worked in ubuntu, suse, and FC4 for me. ill have to read up on that, but im looking forward to trying Arch out

---

### Post by bored2k on 2006-02-09
[QUOTE=briancurtin]that doesnt sound too bad at all. ive never had to enable the network on my own, it has always just worked in ubuntu, suse, and FC4 for me. ill have to read up on that, but im looking forward to trying Arch out[/QUOTE]
Well, I have a DSL router with a static IP (although I have configured it for dhcpcd) and all I did was modify a file called "/etc/rc.conf" to suit my needs (just change the default 192... IP and stuff to my own, as well as remove the "!" fromROUTES=(gateway) because I dont use dhcpcd ), insert my nameservers in /etc/resolv.conf (even ubuntu has this). After that, I ran dhcpcd -B and that's it.

As an example, here is the default /etc/rc.conf file :
[http://rafb.net/paste/results/2a64zx10.html](http://rafb.net/paste/results/2a64zx10.html)

---

### Post by briancurtin on 2006-02-09
awesome, thanks a lot man. im going to look into trying this soon, maybe over the weekend

---

### Post by geearf on 2006-02-09
Hello, 
just a little question, because Arch seems interesting to me now.
How does it compare to Gentoo, is it easier ? faster ?
I am looking at trying something else now, I've only used debian based distros at home, and I was looking at FreeBSD, but maybe I'll try another GNU/Linux distro instead.

Thanks,

---

### Post by newuser111 on 2006-02-09
arch linux may have some potential but it has to have the worst installer I have seen

installing anything but the base package causes depedency problems, and this is from the install cd!

---

### Post by Gandalf on 2006-02-09
[QUOTE=geearf]Hello, 
just a little question, because Arch seems interesting to me now.
How does it compare to Gentoo, is it easier ? faster ?
I am looking at trying something else now, I've only used debian based distros at home, and I was looking at FreeBSD, but maybe I'll try another GNU/Linux distro instead.

Thanks,[/QUOTE]
I have never used Gentoo because i am not willing to compile every package in the world in order to use it, so i cant say if it's faster or not, easier or not.
About Arch, as i said before in my eyes and IMHO, it is as faster as *BSD


[QUOTE=newuser111]arch linux may have some potential but it has to have the worst installer I have seen

installing anything but the base package causes depedency problems, and this is from the install cd![/QUOTE]
I TOTALLY,  ABSOLUTELY disagree with You!!!
Pacman is Much easier, better than apt-get, at least building a binary package is no easier, and Since one month i'm using it I haven't had one single dependecy problem, at contrary on Ubuntu i've had lot of dependecy problem specially when install a non supported package,I mean using checkinstall, Have u ever dreamed to release ur own package and let the package manager take care of all dependecies ??? how easy is to create a deb package taking care of all dependecies (conflicts, depends, makedepends, replace, provides) ??

anyway I said that IMHO, I adore pacman and I Congratulate Judd Vinet for the Marvelous package manager, for making my life easier, making my PC the way i like it, being on bleeding edge with every software I like without asking Backports geeks to do it for me :)

---

### Post by ow50 on 2006-02-09
I tried Arch this afternoon. The installation was fairly easy. I got net, sound, GNOME and all essential stuff working in no time. Thanks Gandalf for the installation guide.

I was impressed with pacman. It's very fast. I did not experience any dependency problems except for one xorg confilicts with ttf-bitstream-vera oddity. Building your own packages is indeed extremely easy. Package selection seemed adequate to me when including [AUR](http://aur.archlinux.org/).

The only major problem I had was with the fonts. I didn't get the fonts to look as good as in Ubuntu. Either the letter spacings were way off (using hinting) or alternatively the fonts were very blurry (hinting off). Bad fonts can be very annoying, something that'll prevent you from using an otherwise good distro.

Arch seemed faster than Ubuntu, but the difference was not that big. I guess the upside with Arch is also the downside. It's fast because there's nothing extra, but in turn you need to install and configure a lot of basic stuff (e.g. gamin and hal) on your own, that in Ubuntu are a part of the basic install. Overall, Arch seems a bit less polished, e.g. GNOME is missing most of the System -> Administration menu and by default it's not there at all.

One thing I always look at before trying a distro is documentation and community support available. Arch is well covered in this respect with the [official documentation](http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html), [wiki](http://wiki.archlinux.org/index.php/Main_Page) and [forums](http://bbs.archlinux.org/).

---

### Post by geearf on 2006-02-09
[QUOTE=Gandalf]I have never used Gentoo because i am not willing to compile every package in the world in order to use it, so i cant say if it's faster or not, easier or not.
About Arch, as i said before in my eyes and IMHO, it is as faster as *BSD

[/QUOTE]
I may then make a stage4 of my laptop, and install Arch in place of Kubuntu to try it, then put my stage4 if I don't like it.
I just hope I won't need one day to get something nice.

---

### Post by cdhotfire on 2006-02-09
Hmm, just installed it, took me a while to figure out why x wouldnt start up, seems it had wmaker to start as windows manager, I have no idea how that happened because I did not even install wmaker.  Anyways, this quite fast, scratch that, super fast.  Still getting used to pacman.  I did not even have to add any repos(not that I know how to), and everything that I need seems to be here, and I do mean everything, its like having automatix for ubuntu.  Only thing Im missing is a "dpkg-reconfigure" command, these dam fonts are gonna make my eyes pop out soon. :(

Anyways, this is a well built distro, maybe ill use for a while. :)

---

### Post by newuser111 on 2006-02-09
[QUOTE=Gandalf]I have never used Gentoo because i am not willing to compile every package in the world in order to use it, so i cant say if it's faster or not, easier or not.
About Arch, as i said before in my eyes and IMHO, it is as faster as *BSD



I TOTALLY,  ABSOLUTELY disagree with You!!!
Pacman is Much easier, better than apt-get, at least building a binary package is no easier, and Since one month i'm using it I haven't had one single dependecy problem, at contrary on Ubuntu i've had lot of dependecy problem specially when install a non supported package,I mean using checkinstall, Have u ever dreamed to release ur own package and let the package manager take care of all dependecies ??? how easy is to create a deb package taking care of all dependecies (conflicts, depends, makedepends, replace, provides) ??

anyway I said that IMHO, I adore pacman and I Congratulate Judd Vinet for the Marvelous package manager, for making my life easier, making my PC the way i like it, being on bleeding edge with every software I like without asking Backports geeks to do it for me :)[/QUOTE]

yes it sounds very cool, but i mean i couldnt get many packages to install from the actual install cd, maybe im doing something wrong, it gives dependency issues if you select all the package repos from the cd during the installer,  it says just install the base package but that doesnt even include xorg...

ill have to read the install guide, but it doesnt sound right

---

### Post by Gandalf on 2006-02-09
Yes i agree that Arch is very fast :)

@cdhotfire wmaker is the default WM if Xorg, u have to add "exec gnome-session" to ~/.xinitrc in order to start gnome with startx command, or otherwize follow my howto to have gdm on startup

for the fonts problem guys, open /etc/fonts/local.conf and replace any content with it (if there's any, i don't remember) with the below one
```

<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<!-- the cathectic LCD tweaks, from linuxquestions.org, 
http://www.linuxquestions.org/questions/showthread.php?postid=1361098#post1361098 
-->

<fontconfig>

<!-- Disable sub-pixel rendering. X detects it anyway, and if you set 
this as well, it just looks really horrible  -->
<match target="font" >
  <edit mode="assign" name="rgba" >
   <const>none</const>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hinting">
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle">
   <const>hintfull</const>
  </edit>
 </match>

<!-- The first part of the 'magic.' This makes the fonts start to look 
nice, but some of the shapes will be distorted, so hinting is needed 
still -->
 <match target="font" >
  <edit mode="assign" name="antialias">
   <bool>true</bool>
  </edit>
 </match>

<!-- Autohinter is not turned on automatically. Only disable this if you 
have recompiled Freetype with the bytecode interpreter, which is run 
automatically. Although to be honest, Freetype are right, there isn't 
much difference between the two. Note that OpenOffice is built against 
the bytecode interpreter, so even if you have compiled it and override 
it with the autohinter, OOo will still use the bytecode interpreter -->
 <match target="pattern" >
  <edit mode="assign" name="autohint">
   <bool>true</bool>
  </edit>
 </match>

<!-- Helvetica is a non true type font, and will look bad. This replaces 
it with whatever is the default sans-serif font -->
 <match target="pattern" name="family" >
  <test name="family" qual="any" >
   <string>Helvetica</string>
  </test>
  <edit mode="assign" name="family" >
   <string>sans-serif</string>
  </edit>
 </match>
 <dir>~/.fonts</dir>
</fontconfig>

```
logout/login and that should give u a quite cool fonts

---

### Post by bored2k on 2006-02-09
[QUOTE=newuser111]yes it sounds very cool, but i mean i couldnt get many packages to install from the actual install cd, maybe im doing something wrong, it gives dependency issues if you select all the package repos from the cd during the installer,  it says just install the base package but that doesnt even include xorg...

ill have to read the install guide, but it doesnt sound right[/QUOTE]
It is recommend for you to stick with the base install. Why? because as you explained correctly, the installer won't tell you what to and not to install (after all, its trying to make you chose). After the base installation, installing everything should be easier. You should have read the installation guide ;). [http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html](http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html)

Edit: Gandalf, log in :P

---

### Post by Sirin on 2006-02-09
[QUOTE=Gandalf]Well Just a hint, [upgrade to GNOME 2.12](http://www.freebsd.org/gnome/docs/faq210.html#q2)  Took 13 hours on a fresh install (Tried it two times) ;)
[/QUOTE]

What the hell? How does upgrading to 2.12 take 13 hours? :eek:

---

### Post by Gandalf on 2006-02-09
[QUOTE=newuser111]yes it sounds very cool, but i mean i couldnt get many packages to install from the actual install cd, maybe im doing something wrong, it gives dependency issues if you select all the package repos from the cd during the installer,  it says just install the base package but that doesnt even include xorg...

ill have to read the install guide, but it doesnt sound right[/QUOTE]
Yes i am actually aware of that issue, it seem they forgot a package to include in the CD or was expecting U to use FTP, anyway i have never used installation this way, i like to have Basic system and do installation with the lastest package snapshots, I even made on my server a local repo of all Arch repository and made my own installation script, so now I can reinstall in 10 mns top :)

---

### Post by Gandalf on 2006-02-09
[QUOTE=Sirin]What the hell? How does upgrading to 2.12 take 13 hours? :eek:[/QUOTE]
I wish i can answer you, i quit freebsd right after, but note that it was on a non updated fresh install so i guess not only gnome but wide upgrade

---

### Post by cdhotfire on 2006-02-09
Thanks for the font tip. :)

---

### Post by Gandalf on 2006-02-09
[QUOTE=cdhotfire]Thanks for the font tip. :)[/QUOTE]
np :)

---

### Post by foxy123 on 2006-02-10
[QUOTE=bored2k]<snap>...building your own packages is a lot easier than trying to build a proper debian package by yourself...[/QUOTE]
what do you mean? If I need to build a package on Ubuntu I basically run ./configure --options, make and checkinstall to have a deb. Whnat maybe easier? As I understand building packages in Arch involves creating some PKGBUILD file. I may be wrong though.

---

### Post by Gandalf on 2006-02-10
Yes I agree about checkinstall, but don't forget that it doesn't take care of any dependecies :) a PKGBUILD do :)
Plus checkinstall fail most of the time for me :roll: donno why...

---

### Post by bored2k on 2006-02-10
[QUOTE=foxy123]what do you mean? If I need to build a package on Ubuntu I basically run ./configure --options, make and checkinstall to have a deb. Whnat maybe easier? As I understand building packages in Arch involves creating some PKGBUILD file. I may be wrong though.[/QUOTE]
Like Gandalf said, checkinstall 1) Fails a **lot**, 2) Does not handle dependencies, thus being a very **bad** way to create a package. Anyone would tell you that. You can't even re-edit your compilation options with that.

---

### Post by briancurtin on 2006-02-10
im probably installing arch tonight, and im looking forward to it. i read the install documentation, gandalf's installer tutorial type page, and i think it should go smoothly.

---

### Post by alvinblank on 2006-02-10
All this juicy stuff said bout Arch, I'll give it a shot once the download finishes.

EDIT: From the first few thread, Arch doesn't install straight to a GUI does it?

---

### Post by bored2k on 2006-02-10
Nope.
[http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html](http://www.archlinux.org/docs/en/guide/install/arch-install-guide.html)
My favorite guide --> [http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html](http://wael.nasreddine.com/Articles/Articles/Install_Arch_Linux.html)

---

### Post by DaMasta on 2006-02-10
Installed Arch the other day on my P3 500mhz, 196mb laptop and it's exponentially faster than my P3 850mhz, 1gb desktop with Ubuntu (well app load times are faster). Gnome runs smooth as silk. Nautilus pops right up. Very happy.

---

### Post by mstlyevil on 2006-02-10
Very interesting and informative thread. I just do not have enough confidence in my knowledge or skills in Linux to give it a try yet but I will keep it in mind when I get one of those wild hairs up my arse to do something daring. In fact it was one of those wild hairs that got me to try Linux and Ubuntu in the first place. :mrgreen:

---

### Post by DaMasta on 2006-02-10
[QUOTE=mstlyevil]Very interesting and informative thread. I just do not have enough confidence in my knowledge or skills in Linux to give it a try yet but I will keep it in mind when I get one of those wild hairs up my arse to do something daring. In fact it was one of those wild hairs that got me to try Linux and Ubuntu in the first place. :mrgreen:[/QUOTE]
It really isn't very complicated. People made it sound like you need to be a 10 year vet to get it going. While I'm pretty experienced, I'm no expert. I had it installed and was up and running in less than 30 minutes. Configuring xorg was a breeze. Enabling sound was the most difficult part for me. But there is an excellent wiki for that.

---

### Post by cdhotfire on 2006-02-10
Yes, it is actually very simple, if you follow the guide.  For xorg youl'l be glad you have ubuntu, just copy over your xorg from ubuntu, and you'll be rocking.

---

### Post by briancurtin on 2006-02-10
yeah ive been logged into arch for about 20 minutes now and i love it. xorg.conf was the only thing that gave me a problem at first, but having a copy of the xorg.conf i had in ubuntu was a great help. so far it is incredibly fast, i love it. it wasnt as hard as it seemed, and i learned a bunch from it. i think im going to like this.

i just cant figure out how to install things from the AUR yet but ill figure it out. im trying to get gaim's extended preferences from there

---

### Post by bored2k on 2006-02-10
Create a directory where you will copy the .tar.gz package AND the PKGBUILD. After installing fakeroot (optional but good), type fakeroot makepkg and let it fly. That is it. If you filled all the dependencies, it should work. If not, solve them (dependencies are listed). Note: sometimes fakeroot might not work.

**Example:**
```
pacman -S glibc
```
```
mkdir gaimext && cd gaimext
```
```
wget http://dl.sourceforge.net/sourceforge/gaim-extprefs/gaim-extprefs-0.5.tar.gz http://aur.archlinux.org/packages/gaim-extprefs/gaim-extprefs/PKGBUILD
```
```
fakeroot makepkg
``` OR ```
#makepkg
```(# stands for root)
To install the package
```
pacman -A package.pkg.tar.gz
```
And that's about as hard as it gets.


Note: The Gaim 2beta2 AUR script rocks. [http://aur.archlinux.org/packages.php?do_Details=1&ID=3387&O=0&L=0&C=0&K=gaim&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=3387&O=0&L=0&C=0&K=gaim&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)

---

### Post by briancurtin on 2006-02-11
thanks a lot for that, but i came across this error. do you know anything for this? im registering and checking out the arch forums in a minute here

im sure where or what the pkg-config script is, or how to get it

```
checking for pkg-config... no
*** The pkg-config script could not be found. Make sure it is
*** in your path, or set the PKG_CONFIG environment variable
*** to the full path to pkg-config.
*** Or see http://www.freedesktop.org/software/pkgconfig to get pkg-config.
configure: error: Library requirements (gaim) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
make: *** No targets specified and no makefile found.  Stop.
==> ERROR: Build Failed.  Aborting...
```

---

### Post by bored2k on 2006-02-11
Install pkgconfig . That's a missing dependency. A lot of the PKGBUILD guys actually asume or forget about that one.
Reporting it as we speak.

---

### Post by bored2k on 2006-02-11
To those who just tried Arch, how do you like the "small" default repositories ;)? Don't they fulfill almost --if not-- everything you need?


Edit: Although Arch's Gnome is pretty fast, I've been lately trying other lighter distros. On arch is when I realized how fast Fluxbox/XFCE really were.

---

### Post by raublekick on 2006-02-11
Man, you guys are making my trigger finger itchy... bored2k, perhaps you can answer this: does their repository have Gnomad2? And if so do you know if it works? The Ubuntu one got borked by something or other and I haven't been able to fix it :(

---

### Post by bored2k on 2006-02-11
[http://aur.archlinux.org/packages.php?do_Details=1&ID=1689&O=0&L=0&C=0&K=gnomad&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd](http://aur.archlinux.org/packages.php?do_Details=1&ID=1689&O=0&L=0&C=0&K=gnomad&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd)

For further references:
Arch official repositories: [http://www.archlinux.org/packages.php](http://www.archlinux.org/packages.php)
AUR (Community-drive): [http://aur.archlinux.org/packages.php](http://aur.archlinux.org/packages.php)


Edit: I'll try building it now. Check back in like 5 ;).

---

### Post by briancurtin on 2006-02-11
[QUOTE=bored2k]Install pkgconfig . That's a missing dependency. A lot of the PKGBUILD guys actually asume or forget about that one.
Reporting it as we speak.[/QUOTE]
haha, i knew it would be something that easy. thanks a lot man.


[QUOTE=bored2k]To those who just tried Arch, how do you like the "small" default repositories ;)? Don't they fulfill almost --if not-- everything you need?[/QUOTE]
i havent been able to find a package that i need/use/want that **isnt** in there. everything i need/use/want is in the repos. pacman is great too. i really like this whole thing a lot, im glad i gave it a try. ill be staying here for a while

---

### Post by bored2k on 2006-02-11
[QUOTE=briancurtin]pacman is great too.[/QUOTE]
If you ever feel like pacman should be faster, try boosting it up with wget ;) 
[http://wiki.archlinux.org/index.php/Boost_Pacman](http://wiki.archlinux.org/index.php/Boost_Pacman) .
Note: I tried it once, but overall, I have no complaints on its default behaviour.

---

### Post by briancurtin on 2006-02-11
[QUOTE=raublekick]Man, you guys are making my trigger finger itchy[/QUOTE]
i got too itchy and had to try it, i love it.

one thing i have that i havent figured out yet (only looked for like 1 minute on this, have to get to it) is my resolution still isnt right. my xorg.conf has the correct one (1440x900) yet im getting something smaller. going to Desktop > Preferences > Screen Resolution shows 1152x768. its tolerable, but im kind of not sure why im not getting the 1440x900

---

### Post by alvinblank on 2006-02-11
I think I locked myself out, i tried su but can't get into root. I know the default password for root is blank, but I can't login using that now.

---

### Post by bored2k on 2006-02-11
[QUOTE=raublekick]Man, you guys are making my trigger finger itchy... bored2k, perhaps you can answer this: does their repository have Gnomad2? And if so do you know if it works? The Ubuntu one got borked by something or other and I haven't been able to fix it :([/QUOTE]
Here is my screenshot.

---

### Post by bored2k on 2006-02-11
[QUOTE=alvinblank]I think I locked myself out, i tried su but can't get into root. I know the default password for root is blank, but I can't login using that now.[/QUOTE]
Did you login with the user root ? Did you setup a passwd right after login in **after** your first reboot?

---

### Post by bored2k on 2006-02-11
[QUOTE=briancurtin]i got too itchy and had to try it, i love it.

one thing i have that i havent figured out yet (only looked for like 1 minute on this, have to get to it) is my resolution still isnt right. my xorg.conf has the correct one (1440x900) yet im getting something smaller. going to Desktop > Preferences > Screen Resolution shows 1152x768. its tolerable, but im kind of not sure why im not getting the 1440x900[/QUOTE]
You could cheat it by copying your Ubuntu's xorg.conf.
[http://wiki.archlinux.org/index.php/Install_and_configure_xorg](http://wiki.archlinux.org/index.php/Install_and_configure_xorg)

---

### Post by alvinblank on 2006-02-11
[QUOTE=bored2k]Did you login with the user root ? Did you setup a passwd right after login in **after** your first reboot?[/QUOTE]

No i didn't! I followed a guide, I'm not sure I see that steps in there. OH NO! Is there anyway to save my installation?

---

### Post by bored2k on 2006-02-11
[QUOTE=alvinblank]No i didn't! I followed a guide, I'm not sure I see that steps in there. OH NO! Is there anyway to save my installation?[/QUOTE]
Just where are you locked? On your first boot? If so, enter with the user root and no passwd. After logged in, **set up a password** for it. 

So, where are you?

---

### Post by alvinblank on 2006-02-11
[QUOTE=bored2k]Just where are you locked? On your first boot? If so, enter with the user root and no passwd. After logged in, **set up a password** for it. 

So, where are you?[/QUOTE]

I already finish the guide, right now typing this in Arch. But I can't pacman or su without that root password which I didn't set in the first place. I guess the installation is hosed.

EDIT: I boot into single mode to change root passwd. Saved!

---

### Post by briancurtin on 2006-02-11
[QUOTE=bored2k]You could cheat it by copying your Ubuntu's xorg.conf.
[http://wiki.archlinux.org/index.php/Install_and_configure_xorg](http://wiki.archlinux.org/index.php/Install_and_configure_xorg)[/QUOTE]
thats essentially what i did. i typed it all in by hand during the install, probably not the easiest way but it was done. i made sure everything is correct, and how i have it setup right now is how it was in ubuntu, except that this doesnt give me the full 1440x900

wow, ive done this before but not in a long time. right after i finished that last line i hit ESC then ":wq" -- i love vim

---

### Post by bored2k on 2006-02-11
@ alvinblank
Are you logged in as another user? You setup a user, rebooted without setting one for root? Bad. Very bad.

> Arch Linux is a general purpose linux distribution that can be molded to do just about anything. It is fast, lightweight, flexible, and most of the parts under the hood are quite simple to understand and tweak, which **can make it a good distro to "learn the ropes" on. We do not provide any configuration helper utilities (ie, you won't find linuxconf in here) so you will quickly become very proficient at configuring your system from the shell commandline. **
Lesson #1: Setup a root password as soon as possible.

---

### Post by bored2k on 2006-02-11
Glad you got that worked out alvin ;).

---

### Post by raublekick on 2006-02-11
Thanks bored2k, I guess I should have been more clear/asked if you had a Creative MP3 player, though. If you do, have you been able to transfer songs? That's the trouble that it's been giving me in Ubuntu. (The "no jukeboxes found" error is because it's not run with sudo or there are no devices connected).

Also, have any of you guys succefully dual booted? Seems kinda trivial, but I've messed it up before, and it's a huge pain in the butt to fix.

---

### Post by bored2k on 2006-02-11
[QUOTE=raublekick]Thanks bored2k, I guess I should have been more clear/asked if you had a Creative MP3 player, though. If you do, have you been able to transfer songs? That's the trouble that it's been giving me in Ubuntu. (The "no jukeboxes found" error is because it's not run with sudo or there are no devices connected).

Also, have any of you guys succefully dual booted? Seems kinda trivial, but I've messed it up before, and it's a huge pain in the butt to fix.[/QUOTE]
I don't have one, sorry :/. This _might_ help: [http://wiki.archlinux.org/index.php/Connect_your_MP3-Player_with_ArchLinux](http://wiki.archlinux.org/index.php/Connect_your_MP3-Player_with_ArchLinux)

Yes, I've been able to dual boot. That's something I need here. 
Note: If you don't know how  to add lines to grub's menu.lst, copy the one from Ubuntu so you can study it later.

---

### Post by DaMasta on 2006-02-11
Just built an opera preview 2 package. Woop woop!

---

### Post by raublekick on 2006-02-11
I'm posting this from Archie (the Live Arch). I dunno how similar Archie is to the actual Arch, but it seems pretty keen to me. Perhaps if there is nothing going on after work tomorrow, Arch will be on here. Unfortunately that means bye-bye Ubuntu. 

But that gives me a good course of action for a while. Arch, then FC5 if I feel so inclinded, then Dapper, then whatever I feel like!

---

### Post by bored2k on 2006-02-11
[QUOTE=raublekick]I'm posting this from Archie (the Live Arch). I dunno how similar Archie is to the actual Arch, but it seems pretty keen to me. Perhaps if there is nothing going on after work tomorrow, Arch will be on here. Unfortunately that means bye-bye Ubuntu. 

But that gives me a good course of action for a while. Arch, then FC5 if I feel so inclinded, then Dapper, then whatever I feel like![/QUOTE]
Bon voyage ;).

---

### Post by bored2k on 2006-02-11
I just thought I'd let the few of you who read this thread know that I've decided to stop "giving support" of Arch Linux here on our forums. Why? Because I don't want to be taken as an ungrateful "bastard" of Ubuntu. Thus, I'll stick to answering any question I can rather than helping people here :).

---

### Post by DaMasta on 2006-02-11
[QUOTE=bored2k]I just thought I'd let the few of you who read this thread know that I've decided to stop "giving support" of Arch Linux here on our forums. Why? Because I don't want to be taken as an ungrateful "bastard" of Ubuntu. Thus, I'll stick to answering any question I can rather than helping people here :).[/QUOTE]
You ungrateful bastard!;)

---

### Post by bored2k on 2006-02-11
/me hides in happy place :(

---

### Post by Gandalf on 2006-02-11
Morning Guys :D

@bored2k u don't need to type
```

fakeroot makepkg

```
makepkg uses fakeroot by default, you can verify this in /etc/makepkg.conf, so just installing fakeroot and 
```

makepkg

```
is enough

For guys who are copying ubuntu's xorg, there is a minor thing You must change, and it is not yet mentioned in my howto, Actually in Ubuntu i had the files section this way
```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

```
but i find out afterwards by carefully reading /var/log/Xorg.0.log

so i did change them to this:
```

Section "Files"
        FontPath        "/usr/X11R6/lib/X11/fonts/misc"
        FontPath        "/usr/X11R6/lib/X11/fonts/cyrillic"
        FontPath        "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/X11R6/lib/X11/fonts/Type1"
        FontPath        "/usr/X11R6/lib/X11/fonts/CID"
        FontPath        "/usr/X11R6/lib/X11/fonts/100dpi"
        FontPath        "/usr/X11R6/lib/X11/fonts/75dpi"
        FontPath        "/usr/X11R6/lib/X11/fonts/TTF"
        # paths to defoma fonts
#       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

```

And if it happend that you want to use Xorg 7, which is in Testing Repository and not recommanded, then it must be:
```

Section "Files"
        FontPath        "/usr/share/fonts/misc"
        FontPath        "/usr/share/fonts/cyrillic"
        FontPath        "/usr/share/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/Type1"
#       FontPath        "/usr/share/fonts/CID"
        FontPath        "/usr/share/fonts/100dpi"
        FontPath        "/usr/share/fonts/75dpi"
        FontPath        "/usr/share/fonts/TTF"
        # paths to defoma fonts
#       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
#       FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

```

---

### Post by cdhotfire on 2006-02-11
Ya come on guys, post your questions in the Arch forums, thats what their there for, this is turning into an Arch support thread. :|

---

### Post by Gandalf on 2006-02-11
We aren't supporting, we're discussing about how easy/hard things are :roll: ok there was a bit support :) lol

---

### Post by tseliot on 2006-02-11
[QUOTE=cdhotfire]Ya come on guys, post your questions in the Arch forums, thats what their there for, this is turning into an Arch support thread. :|[/QUOTE]
Actually I'm kind of interested in Ark

---

### Post by bored2k on 2006-02-11
[QUOTE=tseliot]Actually I'm kind of interested in Ark[/QUOTE]
Ark Linux != Arch Linux

Ark Linux = Ark Linux is a GNU/Linux distribution designed especially for desktop use, easy to use even for people without prior Linux (or computing) experience while still powerful enough for power users.

Arch Linux =  Arch Linux is an i686-optimized linux distribution targeted at competent linux users (read: not afraid of the commandline)

---

### Post by bored2k on 2006-02-11
[QUOTE=Gandalf]
@bored2k u don't need to type
```

fakeroot makepkg

```
makepkg uses fakeroot by default, you can verify this in /etc/makepkg.conf, so just installing fakeroot and 
```

makepkg

```
is enough[/QUOTE]I'm used to using for a few things fakeroot. Getting used to not using it and trying another distributions might be hurtful ;). Just an old-schoolish thought ;).

---

### Post by tseliot on 2006-02-11
[QUOTE=bored2k]Ark Linux != Arch Linux

Ark Linux = Ark Linux is a GNU/Linux distribution designed especially for desktop use, easy to use even for people without prior Linux (or computing) experience while still powerful enough for power users.[/QUOTE]
I'm downloading Arch via bittorrent.

[QUOTE=bored2k]Arch Linux =  Arch Linux is an i686-optimized linux distribution targeted at competent linux users (read: not afraid of the commandline)[/QUOTE]
I'm studying bash in my spare time and, if it weren't for compilation times, I would be using Gentoo (beside Ubuntu and Fedora) and FreeBSD (and yes I'm aware of the existence of binaries).

Thanks for the information

---

### Post by briancurtin on 2006-02-11
yeah im done asking Arch questions on here, just wanted to get those out of the way. im registered on the arch forum and have a thread going over there for my monitory problem. thanks for the start though bored.

---

### Post by johannes on 2006-02-11
I decided to give Arch a try, and so far it has been really neat exept for installing the ATI drivers. The graphical installer from ATI:s website does not work on the default kernel, and the information on the wiki is pretty strange. Some of it seems to be outdated, some of it assumes you have a "ck" patched kernel and the link to the driver package is broken. Installing the package from the community repository does not work for me...

Anyway, it's a nice distro. As others have said, it's really fast and has an effective package system.

---

### Post by raublekick on 2006-02-12
::shoots arrow::

::misses target::

The install went well, I followed the official guide with Gandalf's easier guide for how I should configure stuff. Everything was going well, got gnome/gdm/etc... installed through pacman. But then when I set up my user and followed the config stuff from Gandalf's guide, the network wasn't working anymore (displayed FAIL on boot) and when I tried to unmute the sound it told me there was no device configured for the mixer or something. 

It was 4AM when ran into these troubles and I needed sleep, then I had to come into work this morning (yay snow and being the only person within walking distance!). Anyways, not really looking for support here, just thought I'd update with how it went so far. It does seem faster, but not really that much faster (Epiphany takes awhile to come up, but Firefox is pretty zippy).

---

### Post by jejones3141 on 2006-02-14
[QUOTE=bored2k]To those who just tried Arch, how do you like the "small" default repositories ;)? Don't they fulfill almost --if not-- everything you need?[/QUOTE]

Well... I installed Arch on a computer this past weekend, and I'm disappointed with the absence of a bunch of packages that are there with Ubuntu if you pull in the {uni, multi}verse.  zapping, the only TV viewer I've seen for Linux that does closed captioning right, isn't present. noteedit isn't there. 

OTOH, the versions that are present in Ubuntu aren't up to date; the version of zapping that Ubuntu repositories have dies for no apparent reason, so what to do?

I got an ATI gfx card after having lots of trouble with nVidia on this computer (an ECS KT-600). Turns out that you have to use someone's hacked kernel under Arch (archck) to use fglrx. I did, but I still don't seem to have 3D acceleration for some reason... and there's a new release of the kernel out for Arch. Do I switch back from archck, or wait for its author to catch up?

That said... yes, Arch seems to be much faster than Breezy Badger. I'm ashamed to say this after having written a compiler back end for the x86, but I don't know enough to say whether it makes a serious difference that not just the kernel, but also the apps are compiled for i686. Ah, well. I'll be upgrading another computer to Dapper Drake, and if it feels respectively faster than Breezy Badger, I'll see about setting up the Arch computer to dual boot to either Dapper Drake or Arch, and then we can get a decent comparison.

---

### Post by Gandalf on 2006-02-14
Whatever is the package that is missing you can always request it to be at AUR or do it urself, there's currently 2295 packages in AUR (at the time where this post was posted :D ) so don't think anything would be forever missing, you love a soft, it ain't there, request it ...

about archck is great am using it but am not sure about ATI, ask on their forum plz this is not a support topic :)

EDIT: hold on I'm creating zapping for you, you'll get a PM with details in a few minutes...

---

### Post by Gandalf on 2006-02-15
Just for information, I made both zapping and noteedit
zapping -> [http://bbs.archlinux.org/viewtopic.php?t=18822](http://bbs.archlinux.org/viewtopic.php?t=18822)
noteedit -> [http://aur.archlinux.org/packages.php?do_Details=1&ID=3492](http://aur.archlinux.org/packages.php?do_Details=1&ID=3492)

Voilà :D

---

### Post by poofyhairguy on 2006-02-15
I want an OS to make a media box. It must be able to play DVDs, play Zsnes, and use the Nvidia driver. Can Arch do this all for me?

---

### Post by Gandalf on 2006-02-15
DVDs are no problem, i donno what are Zsnes
Nvidia drivers -> [http://www.archlinux.org/packages.php?s_repo=4&s_category=all&s_keyword=nvidia&s_lastupdate=&pp=50](http://www.archlinux.org/packages.php?s_repo=4&s_category=all&s_keyword=nvidia&s_lastupdate=&pp=50) but as i don't have Nvidia i donno if it is good or bad, u may want to check [http://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver](http://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver)

---

### Post by bored2k on 2006-02-15
[QUOTE=poofyhairguy]I want an OS to make a media box. It must be able to play DVDs, play Zsnes, and use the Nvidia driver. Can Arch do this all for me?[/QUOTE]
What's wrong with Ubuntu for that ?

[How to install **NVIDIA** driver?]("http://wiki.archlinux.org/index.php/How_to_install_NVIDIA_driver")

**Arch's main repositories:**
[LIST]
[*][zsnes]("http://www.archlinux.org/packages.php?id=394")
[*][libdvdcss]("http://www.archlinux.org/packages.php?id=472")
[*][nvidia-legacy]("http://www.archlinux.org/packages.php?id=6835")
[*][nvidia]("http://www.archlinux.org/packages.php?id=5419")
[*][nvclock]("http://www.archlinux.org/packages.php?id=741")
[*][nforce]("http://www.archlinux.org/packages.php?id=5430")
[/LIST]

**Arch's AUR:**
[LIST]
[*][gens-cvs (An emulator for multiple Sega videogamesystems such as the Genesis, Master System, Sega CD and 32X.)]("http://aur.archlinux.org/packages.php?do_Details=1&ID=691&O=0&L=0&C=0&K=genesis&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd")
[*][gxmame]("http://aur.archlinux.org/packages.php?do_Details=1&ID=1285&O=0&L=0&C=0&K=mame&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd")
[*][advanced-mame]("http://aur.archlinux.org/packages.php?do_Details=1&ID=3313&O=0&L=0&C=0&K=mame&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd") (MAME with advanced video support for use with TVs, Arcade Monitors, Fixed Frequencies Monitors)
[*][]("http://aur.archlinux.org/packages.php?do_Details=1&ID=1169&O=0&L=0&C=0&K=nintendo&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd")
[*][zsnes-wip (zsnes in wip [wth?])]("http://aur.archlinux.org/packages.php?do_Details=1&ID=2029&O=0&L=0&C=0&K=nintendo&SB=&SO=&PP=25&do_MyPackages=0&do_Orphans=0&SeB=nd")
[/LIST]

---

### Post by poofyhairguy on 2006-02-15
[QUOTE=bored2k]What's wrong with Ubuntu for that ?
[/QUOTE]

Nothing, but then I can't try new distros I cannot replace Ubuntu on my desktop, but I want to try Arch. Here is its chance.

Thanks for the info.

---

### Post by foxy123 on 2006-02-15
[QUOTE=bored2k]To those who just tried Arch, how do you like the "small" default repositories ;)? Don't they fulfill almost --if not-- everything you need?[/QUOTE]
it looks fine for me. At least I have not noticed any packages that are missing for me. WHat is good the most of the packages are newer versions that you have in stable Ubuntu release and the current release looks more stable than a development branch of Ubuntu.

Saying that and trying Dapper I personally do not see much of advantage of Arch. Dapper is faster than Breezy and feels better. Maybe not so fast as Arch, though I have not configured Arch to my liking yet. Package management is comparable and checkinstall works fine for me if I need to make a package for myself.

However, Arch has its own ascetic grace, which I guess appeals to many.

---

### Post by Robgould on 2006-02-15
I want to see if I understand this correctly.....
 
I just looked at the arch linux page and looked at the package list.  Gambas is not on there.  I like Gambas.
 
What I think I am hearing on here is that I can build this with arch somehow and then arch would keep it updated for me?

---

### Post by bored2k on 2006-02-15
[QUOTE=Robgould]I want to see if I understand this correctly.....
 
I just looked at the arch linux page and looked at the package list.  Gambas is not on there.  I like Gambas.
 
What I think I am hearing on here is that I can build this with arch somehow and then arch would keep it updated for me?[/QUOTE]
[Gambas]("http://aur.archlinux.org/packages.php")
> The ArchLinux User-community Repository (AUR) is a community driven repository for Arch users. This document shows the normal user how to access AUR and work with it.

---

### Post by Robgould on 2006-02-15
I did not know about AUR.  Thanks for the info.

---

### Post by geearf on 2006-04-16
I'm now also a dual user of dapper / arch (well I've just installed the latter). 
I'm joining the community of this thread :)

---

### Post by jakemikey on 2006-04-19
Well I seem to be in the minority here.  I got excited by all the "Arch orgasms" on this thread and decided to give it a shot and install it on my laptop.  I'm no expert, but I consider myself a fairly seasoned *NIX user (tried lots 'o Linux distros and even FreeBSD for a while).

As far as my experience, the hype around Arch is exaggerated, if not simply untrue.  I've tried it for a while and I've simply lost interest.  Here are a few observations:

-I'm not sure that a complete lack of ease-of-use features should be synonomous with a "performance" linux distro.  I mean, even gentoo has a GUI installer and makes configuration a pleasure rather than a chore.  I got things up and running, and it wasn't even really complicated, but more time consuming.

-I don't know how anyone could compare pacman to the beauty of apt.  Apt, in my experience, is light years ahead of pacman.  pacman had difficulties resolving both dependencies and conflicts, and I had to use a "force" option to install something as typical as gnome - only within a few minutes of a fresh install.  It just seemed really clunky.  Even FreeBSD's ports/pkg system was a breeze to use compared to pacman.

-speed: this was my big disappointment.  For reference, I'm using the latest Dapper (beta).  Boot time was about the same.  Starting gnome took noticably longer (in Arch vs Dapper).  Starting Firefox also took noticably longer.  The system became basically unusable during a large file copy, and during normal use, the mouse cursor would undergo pretty distracting "lagginess" when being dragged across the screen.  The only place where I noticed a "slight" improvement in performance over dapper was in the responsiveness after clicking a button in a window, and in window redraws - but this alone sure wasn't enough to convince me to stick with it.

I'm sure that I could've gotten Arch where I wanted with a lot more work, but it just didn't do a very good job of enticing me to do so.  I couldn't see the payoff coming.  I kept thinking, "why am I spending time on this again?  It's not any faster - even slower- than Dapper, and it's sure not any more convenient, and it's a lot less fun to use..."

Personally, if somebody were looking for this kind of "adventure" I would recommend FreeBSD or one of its variants.  It's more stable, smart, and convenient and it really gets you out of the Linux paradigm.  The drawbacks are a lack of support for proprietary things like drivers, etc. and also lack of support for Linux filesystems and vice versa - those can become a real pain.

This isn't a flame, just an experience from a not-so-satisfied customer.

---

### Post by endersshadow on 2006-04-19
Well, I'm dualbooting Breezy and Arch right now, and this post is coming from Arch.  A couple of things:

1. I don't find the package management better or worse in Arch.  I can do the same things with makepkg that I can with checkinstall.

2. Arch is a bit faster, and noticably so, but it's not flying off the handle and I don't know what to do with myself half the time.

3. I don't mind the text based editting of Arch...used to doing it a lot in Ubuntu...what I do mind is the significant lack of documentation...you definitely need to brute force your way through installation, but it's okay.

4. I'm happy with Arch but I don't think that it's the savior of all distributions...it's a nice distro that's fast, light, and impressively done.  I recommend it for anybody wanting to be a bit adventerous.

---

### Post by briancurtin on 2006-04-19
[QUOTE=jakemikey]-I'm not sure that a complete lack of ease-of-use features should be synonomous with a "performance" linux distro.  I mean, even gentoo has a GUI installer and makes configuration a pleasure rather than a chore.  I got things up and running, and it wasn't even really complicated, but more time consuming.[/QUOTE]some say a GUI would be nice, some dont want it. its really all preference, and most arch users/devs like it as CLI. there has been talk on the arch boards of adding a GUI installer because some people do want it, but i dont think that will show up in arch for a while

[QUOTE=jakemikey]
-I don't know how anyone could compare pacman to the beauty of apt.  Apt, in my experience, is light years ahead of pacman.  pacman had difficulties resolving both dependencies and conflicts, and I had to use a "force" option to install something as typical as gnome - only within a few minutes of a fresh install.  It just seemed really clunky.  Even FreeBSD's ports/pkg system was a breeze to use compared to pacman.[/QUOTE]
you did something wrong then as far as i know. ive never once had any problems with pacman at all including the 5-6 times i have installed arch from scratch and had to completely start from the ground up, along with every day use of it. however, i had the same exerience with apt for the most part too. im also not sure how you ran into problems installing gnome...

[QUOTE=jakemikey]-speed: this was my big disappointment.  For reference, I'm using the latest Dapper (beta).  Boot time was about the same.  Starting gnome took noticably longer (in Arch vs Dapper).  Starting Firefox also took noticably longer.  The system became basically unusable during a large file copy, and during normal use, the mouse cursor would undergo pretty distracting "lagginess" when being dragged across the screen.  The only place where I noticed a "slight" improvement in performance over dapper was in the responsiveness after clicking a button in a window, and in window redraws - but this alone sure wasn't enough to convince me to stick with it.[/QUOTE]
im very surprised that you were having these problems in arch. what are your system specs? what do you have in your mkinitrd.conf? if you didnt like it or didnt want to fix things up to make it a lot faster, then thats fine, i just find it odd that after tuning some things up that you would still be having these problems 

[QUOTE=jakemikey]I'm sure that I could've gotten Arch where I wanted with a lot more work, but it just didn't do a very good job of enticing me to do so.  I couldn't see the payoff coming.  I kept thinking, "why am I spending time on this again?  It's not any faster - even slower- than Dapper, and it's sure not any more convenient, and it's a lot less fun to use..."[/QUOTE]
thats the beauty of linux. if you cant get it to work how you want it, you can just jump back to something that you know works. it takes some time but not all that much if you know where to look, and you can have a solid and quick system. "fun to use" is completely subjective, and i wont go into what i have to say on the topic. convenience is also in the eyes of the user. some want GUIs to do it all, some want to have everything in front of them in a file

[QUOTE=jakemikey]Personally, if somebody were looking for this kind of "adventure" I would recommend FreeBSD or one of its variants.  It's more stable, smart, and convenient and it really gets you out of the Linux paradigm.  The drawbacks are a lack of support for proprietary things like drivers, etc. and also lack of support for Linux filesystems and vice versa - those can become a real pain.[/QUOTE]
are you saying FreeBSD is better because Arch is unstable, stupid, and inconvenient? it sure sounds like it, and those are completely subjective. it sounds like you put no effort into your arch install, so im not sure where you get off saying anything. i couldnt get my car to drive 200 MPH on the first day either, so i guess ill just get rid of it.

> This isn't a flame, just an experience from a not-so-satisfied customer.
thanks for the post.

---

### Post by jakemikey on 2006-04-19
[QUOTE=briancurtin]

are you saying FreeBSD is better because Arch is unstable, stupid, and inconvenient? it sure sounds like it, and those are completely subjective. it sounds like you put no effort into your arch install, so im not sure where you get off saying anything. i couldnt get my car to drive 200 MPH on the first day either, so i guess ill just get rid of it.

[/QUOTE]
 Yikes.  I didn't mean anything personal.  I wouldn't disagree with "unstable" and "inconvenient", but "stupid" is going a little far.  What I really was getting at with saying "smart" is that in my experience FreeBSD's pkg/ports system did a better job of installing packages without a hitch.  It's packaging system is "smart"-er than what I experienced with Arch.

And exactly how much effort am I expected to put into an install?  I find it ironic that we THIRST for better performance (the driving force behind so many of us trying Arch) - but here's the kicker - I would expect that we want better performance to save time and make use more enjoyable, yet we're willing to waste tons of time sifting through config files and hunting down pieces of documentation here and there, booting and rebooting, all for the sake of shaving off a few milliseconds of redraw time on our windows.  Don't get me wrong, I'm just as guilty as anyone on these grounds, but I still think it's funny.

In the big picture (don't flame me for this), one could argue that Arch really is a *lower*-performing distro since you spend so much more time getting things set up just right.  One could make the same argument against Gentoo (even more so).

Just trying to represent the other side of the story so that people reading this thread can get a realistic idea of what to expect.

---

### Post by briancurtin on 2006-04-19
if you think arch and gentoo are lower performing distros, you are insane. your problems seem to be isolated to whatever hardware you installed it on. i installed it on my laptop and it flew, then i tweaked one file where i changed like 6 lines and it flew even more.

---

### Post by jakemikey on 2006-04-19
[QUOTE=briancurtin]if you think arch and gentoo are lower performing distros, you are insane. [/QUOTE]

I wasn't measuring performance in benchmarks or app load times, I was strictly interpreting it from a standpoint of productivity.  I would be very very impressed if you could make a convincing argument that :

```
(seconds saved in launching app or booting) - (hours/days spent configuring & tweaking) = increased net productivity
```

From this standpoint, Arch and Gentoo have a long way to go.  That's all I'm exploring here.  Is meaningful performance measured in (milli)seconds and benchmarks, or what it takes to set up and maintain and use properly?  Different strokes for different folks.

Personally I would like to see Ubuntu develop a side-project focused on performance, much like SUSE has SUPER.  Combine the convenience of Ubuntu with the performance of Gentoo, ck kernel patches, etc.  I've tried apt-build, but it has problems and seems underdeveloped.  I'd like to see that pursued a little more.

As an aside, maybe it was some sort of hardware issue that led to Arch's poor performance.  That's not really the point for me though - I have a newer Compaq Presario laptop with a 1.8 GHz Sempron, 512 MB RAM, integrated wireless, yada yada yada.  Pretty vanilla hardware and none of the other Linux distros I tried on it had hardware issues.

---

### Post by Gandalf on 2006-04-19
> **jakemikey]Well I seem to be in the minority here.  I got excited by all the "Arch orgasms" on this thread and decided to give it a shot and install it on my laptop.  I'm no expert, but I consider myself a fairly seasoned *NIX user (tried lots 'o Linux distros and even FreeBSD for a while).

As far as my experience, the hype around Arch is exaggerated, if not simply untrue.  I've tried it for a while and I've simply lost interest.  Here are a few observations:

-I'm not sure that a complete lack of ease-of-use features should be synonomous with a "performance" linux distro.  I mean, even gentoo has a GUI installer and makes configuration a pleasure rather than a chore.  I got things up and running, and it wasn't even really complicated, but more time consuming.
[/quote] I'm not sure what do you actually mean by user-friendly, do you refer to click-change-click thing like in Ubuntu or simplicity of doing things??, anyway Now under dapper for example i want you to create for me a small bash script to print Hello World on startup, how much would it take ?? man, CLI rules .. anyway IMHO
A lot like urself prefer GUI, GUIs are cool but not for everything, i love use GUI to change background, to change internet connection using network manager, but not to edit fstab or inittab or install/remove any program, that's a CLI job, it's both better and faster than any GUI exist or not even made yet, beleive me  said:**
> 
-I don't know how anyone could compare pacman to the beauty of apt.  Apt, in my experience, is light years ahead of pacman.  pacman had difficulties resolving both dependencies and conflicts, and I had to use a "force" option to install something as typical as gnome - only within a few minutes of a fresh install.  It just seemed really clunky.  Even FreeBSD's ports/pkg system was a breeze to use compared to pacman.
 LOL !
No Comments =D> 
> **jakemikey]
-speed: this was my big disappointment.  For reference, I'm using the latest Dapper (beta).  Boot time was about the same.  Starting gnome took noticably longer (in Arch vs Dapper).  Starting Firefox also took noticably longer.  The system became basically unusable during a large file copy, and during normal use, the mouse cursor would undergo pretty distracting "lagginess" when being dragged across the screen.  The only place where I noticed a "slight" improvement in performance over dapper was in the responsiveness after clicking a button in a window, and in window redraws - but this alone sure wasn't enough to convince me to stick with it.
[/quote] that may be true, may be not, but when i refered to speed, it was because of two things that no one can deny existance:
1- Arch is i686 optimized, all Programs are compiled with -march=i686 so it makes it run a bit more nicely on i686 machines
2- Ubuntu compared to Arch is (sorry KDE users) like KDE, it is so bloated with so so many useless things, what do i need for HP imaging things installed for example it takes time on startup, memory and HDD Space
[QUOTE=jakemikey]
I'm sure that I could've gotten Arch where I wanted with a lot more work, but it just didn't do a very good job of enticing me to do so.  I couldn't see the payoff coming.  I kept thinking, "why am I spending time on this again?  It's not any faster - even slower- than Dapper, and it's sure not any more convenient, and it's a lot less fun to use..."

Personally, if somebody were looking for this kind of "adventure" I would recommend FreeBSD or one of its variants.  It's more stable, smart, and convenient and it really gets you out of the Linux paradigm.  The drawbacks are a lack of support for proprietary things like drivers, etc. and also lack of support for Linux filesystems and vice versa - those can become a real pain.

This isn't a flame, just an experience from a not-so-satisfied customer.[/QUOTE]
I also recommand FreeBSD as for it's speed, unbeatable security, but don't forget the lack if softwares for it, so yea u'd be a bit limited unfortunately


[QUOTE=endersshadow]Well, I'm dualbooting Breezy and Arch right now, and this post is coming from Arch.  A couple of things:

1. I don't find the package management better or worse in Arch.  I can do the same things with makepkg that I can with checkinstall.
[/quote] Man, I like this joke, it's a joke isn't it ??
[QUOTE=endersshadow]
2. Arch is a bit faster, and noticably so, but it's not flying off the handle and I don't know what to do with myself half the time.

3. I don't mind the text based editting of Arch...used to doing it a lot in Ubuntu...what I do mind is the significant lack of documentation...you definitely need to brute force your way through installation, but it's okay.
[/quote] Well that's why we are users and wiki is open for everyone, u see a lack? fill it  said:**
> 
4. I'm happy with Arch but I don't think that it's the savior of all distributions...it's a nice distro that's fast, light, and impressively done.  I recommend it for anybody wanting to be a bit adventerous.

---

### Post by woedend on 2006-04-19
heres my short take on arch.  I like arch, I really do.  But it just seems like it takes a lot of work to do things that debian/apt make simple.  And while archers love their rc.conf, I find that having separate smaller confs is easier to manage(just me).  Arch boots much faster, but I honestly do not one bit see a speed increase.  Now keep in mind, I don't do long laborious compile or encoding jobs, or any real valid benchmarking, I only judge by desktop responsiveness.  What I've done is set Arch up with all the goodies(nvidia, xgl, compiz, firestarter) and stripped ubuntu way down(19 services removed, updatenotifier, evolution, braille crap, etc), and then added the same aforementioned goodies.  Just testing responsiveness that is, I set the clock to seconds to see how long many programs took to open and I found - well, they are identical, if not some things faster in ubuntu.  Openoffice writer took exactly 10 seconds on each.  Firefox took 2-3 seconds on each.  Thunderbird 2-3 seconds.  Gedit takes 2 seconds.  All on first runs.  Naturally from then on out it was quicker, Firefox and Thunderbird both take exactly 1 full second to open under both.  
What I didn't like in some cases it's unnecessarily cumbersome.  The setup really is cumbersome initially, and I'll never figure out why their automatic xorg.conf generator uses nv, or in the example vga, when neither comes with. I never could figure out exactly how to automount my cd's as a user, even in the optical group, but it worked in root.  Apparently it's a udev rule problem(guessing, obviously permission related).  And I could not find a way to see what packages pacman had installed.  Consider this example.  If you install the nvidia driver, then uncomment testing, then go to remove nvidia, it will not remove it.  At least for me it wouldn't.  Basically it didn't appear to have any kind of multiple version system or tracking.
Overall though, the community is great, tons of wiki information, it's just in the end I ask myself - What can Arch do that debian/ubuntu cannot?  And then what can Ubuntu do that Arch cannot?   I found many more objects in the latter, and none to my knowledge in the former.

---

### Post by endersshadow on 2006-04-19
[quote="gandalf"]Man, I like this joke, it's a joke isn't it ??[/quote]

No, not really.  Though, admittedly, I haven't used pacman any more than just your basic installation (pacman -Sy package and pacman -Syu), so I haven't used it to nearly the extent that I've used apt.  Like I said, my perceptions are just first impressions.  I don't have any more than a week or so of experience with Arch, so my impressions are too in depth.  Just an Ubuntu user turning to Arch and saying what he thought of it :)

---

### Post by ShanghaiTeej on 2006-04-19
Can you easily implement XGL/Compiz on an arch installation?

---

### Post by woedend on 2006-04-20
yes.  a guy named shadowhand manages a repo with xgl-cvs, compiz-cvs, compiz-quinn-cvs, and gaim-cvs binaries.  Search bbs.archlinux.org for "xgl gdm", you will find a post that has a link to the gentoo howto, with 1 modification that must be made.

---

### Post by DaMasta on 2006-04-20
Arch is my favorite distro. And pacman is, by far, superior to apt. It's hard for me to admit since debian was my first love, but it's true. Unlike what someone said above, it resolves dependencies flawlessly, outside of the occasional already exists message, and a simple force option clears that. My kde runs without a hitch on a p3 500mhz, 196mb ram laptop. No lag, and that's with quanta, amarok, konqueror and kopete all running.

---

### Post by Kindred on 2006-04-20
I've been running Arch for a couple of months, it's pretty much perfect for me. 

Simple, fast, knowledgeable community, very up to date, reliable, simple init system, great docs (imo), vanilla software, blah blah.  It's great.

---

### Post by kabus on 2006-04-20
[QUOTE=woedend]And I could not find a way to see what packages pacman had installed. [/QUOTE]

pacman -Q to list all installed packages

---

### Post by egon spengler on 2006-04-20
[QUOTE=woedend]Arch boots much faster, but I honestly do not one bit see a speed increase. [/QUOTE]

I had the same experience, I can't help but wonder if some people just convince themselves it feels quicker.

---

### Post by otake-tux on 2006-04-20
can anyone describe in detail their experience with arch on a laptop?

power managment is a very important feature to have if using a laptop and I'm wondering does arch deal with laptops.

if its easy to set up and supports suspend, smart battery detection and cpu frequency scaling, I will install arch tonight!

---

### Post by foxy123 on 2006-04-20
I was preety enthusiastic about Arch in the beginning. I've got it on my second drive on desktop and was thinking to dual-boot with Ubuntu on my laptop. However after a while I got sort of disappointed with it, especially after I failed to update from Xorg 6.8 to Xorg 7.0. I made a couple attempt to fix it but got tired and install Dapper and have been happy since.

Arch is a nice distro, no question about it. But it depends on one's aspirations whether it is worth all this hasse to switch from another distro. Personally I decided that I do not have much time to do it, so I gave up.

---

### Post by DaMasta on 2006-04-20
[QUOTE=otake-tux]can anyone describe in detail their experience with arch on a laptop?

power managment is a very important feature to have if using a laptop and I'm wondering does arch deal with laptops.

if its easy to set up and supports suspend, smart battery detection and cpu frequency scaling, I will install arch tonight![/QUOTE]
I installed arch on my laptop. Unfortunately it's very old so there is no frequency scaling. Also, I don't have a battery so I can't help you on the other two. However, there is [this thread](http://bbs.archlinux.org/viewtopic.php?t=4690).

---

### Post by briancurtin on 2006-04-20
i have arch running on my laptop right now, but i use it as a desktop basically and i dont know anything about this suspend, battery, or scaling stuff. i imagine that it does have those things, but i would say to ask on the forums in the newbie forum if it supports those things before installing.

---

### Post by kabus on 2006-04-21
[QUOTE=otake-tux]
if its easy to set up and supports suspend, smart battery detection and cpu frequency scaling, I will install arch tonight![/QUOTE]

I don't use Arch on a laptop, but I use suspend to disk iand it was pretty easy to set up. 
Cpu scaling is just a matter of installing the right daemon and adding it to rc.conf.
Some more info @ ArchWiki :

[http://wiki.archlinux.org/index.php/Category:Laptop](http://wiki.archlinux.org/index.php/Category:Laptop)
[http://wiki.archlinux.org/index.php/SpeedStep](http://wiki.archlinux.org/index.php/SpeedStep)

---

### Post by pelle.k on 2006-04-23
The fastest (simple config) way to get frequency scaling on my pentuim m.

pacman -S cpufrequtils
add speedstep_centrino, cpufreq_ondemand ( > #modules section in rc.conf)
add cpufreq-set -g ondemand ( > rc.local)

Just enables a very simple speedstep between 800-1800 mhz. (on my cpu that is)
Use cpufreq-info to see status.
This is not a substitute for a power manager though.

---

### Post by Skarjoko on 2006-04-23
Just want to reiterate that this is definitely not for noobs. I can't even get my X to run properly with blackbox...

But once I get a DE running i'll let you guys know how much faster it is...

---

### Post by hizaguchi on 2006-04-23
I've been running Arch for a few weeks now and I'm starting to get a little frustrated with a few things.  Most of my problem is that I'm very new to Linux and I'm learning via crash course, so they're not really Arch's fault.  But these nagging issues, like sound sometimes (seemingly randomly) not working (even after killall xmms, killall amarok, etc to make sure nothing is using ALSA) just didn't happen in Ubuntu.

I'm up in the air about it still though.  I still prefer apt to pacman (a few packages don't install for me in pacman), but I LOVE the build system that makes compiling nearly anything braindead easy.  I hate how confusing some problems can be (like ALSA for me), but "pacman -S kmplayer flashplugin j2re codecs" kinda makes up for it.  And it's also pretty hard to complain about Gnome running on half the ram that Ubuntu requires, or the fact that alot of programs make it into the official repositories only days after they're released.

I guess it all comes down to how much you want to tinker with your system.  Arch is definately faster, but it forces you to handle alot of stuff manually to get it working right, and its repositories are smaller but have more usefull packages.  While Ubuntu is a little slower but takes care of some of the less obvious configuration settings for you and lets you tinker at your leisure.

If I had the ram, I'd take Ubuntu hands down.

---

### Post by otake-tux on 2006-04-23
I'm installing arch on friday.  I will post the results.

---

### Post by Rikostan on 2006-04-23
I'll give it a try.. I have been trying out every distro I can find lately, even though I am more than happy with Ubuntu..

I find the tag line "(read: not afraid of the commandline)" from their site pretty humorous though. As if using the commandline is only for the brave.
"Don't mess with him, he can type!"

---

### Post by briancurtin on 2006-04-23
[QUOTE=hizaguchi]I hate how confusing some problems can be (like ALSA for me)[/QUOTE]
have you checked out the arch wiki? there is a bunch of stuff on there about ALSA and it helped me out the first time i used arch. if you cant get it there, try the newbie forums on the arch board. the developers, TUs, and all regular users frequent that area and you should get some good help from there.

---

### Post by geearf on 2006-04-24
I had some problem with ALSA too, but not too hard.
I went to the french chat did not have much help there, but the 'normal' one some people helped me resolved my problems pretty quickly :)

---

### Post by kabus on 2006-04-24
[QUOTE=Rikostan]
I find the tag line "(read: not afraid of the commandline)" from their site pretty humorous though. As if using the commandline is only for the brave.
"Don't mess with him, he can type!"[/QUOTE]

Well, a cursory glance through this forum will show you that lots of people are deathly afraid of 'typing', so it's only fair to warn them instead of throwing them on the command line without the slightest idea what to do.

---

### Post by manicka on 2006-04-24
I must admit to being bitten by the Arch bug recently and really like it as a distro. I find it incredibly fast, stable and packages are amazingly up to date, even when using just the stable repos. Pacman is an outstanding package manager and the AUR is just fantastic. It's like having the whole community as MOU's

That said though it's not for beginners. I had a friend talk to me today about his first experiences with Linux and he shared that he had recently been experimenting with Mandrake. Being a newbie I immediately gave him a set of Ubuntu CD's and sent him away to discover the joys of Ubuntu.

We truly are lucky to have so many fantastic Linux distros at our disposal. After all, it's all about using and loving Linux in the long run

---

### Post by hizaguchi on 2006-04-24
[QUOTE=briancurtin]have you checked out the arch wiki? there is a bunch of stuff on there about ALSA and it helped me out the first time i used arch. if you cant get it there, try the newbie forums on the arch board. the developers, TUs, and all regular users frequent that area and you should get some good help from there.[/QUOTE]
Yeah, I needed it to know how to get alsa working at all in the first place.  Who woulda thought you'd have to run alsaconf?  :)  I've just not been able to solve my random sound problems yet.  Gonna have to figure it out sometime though I guess.  I installed Ubuntu again yesterday and the slowness (with my measly 128 megs of ram) is just too bad for me to go back.  I mean, Gnome in Arch is faster than Openbox in Ubuntu for me... and uses about the same memory.  I still like Ubuntu better, but I'm hooked on the speed. :)

---

### Post by pelle.k on 2006-04-24
Acctually you dont have to run alsaconf. In fact it's better not to!...
Why? Because if you do, alsa put two lines in /etc/moprobe.conf which are most likely going to mess up sound for you instead. Comment those lines beneath "OSS Compability" out.
Remember to run alsamixer to activate output, because its NOT enabled by default. (i did this from kmix though :) )

To give you arch newbies a sort of rough guideline i will paste what i have done to get my default install up as quick as possible. (as you will notice i run kde :) )

((commands))
pacman -Sy (sync with mirrors)
pacman -S netselect (needed for sortmirrors)
netselect (sortmirrors script, adds fastest mirrors first in list from which pacman tries)
pacman -Su (update all)
pacman kde
pacman xf86-input-mouse xf86-input-keyboard
pacman alsa-lib alsa-driver alsa-oss alsa-utilities
 
((config files. use "su" to become root. use nano to edit))
Add - Modeline "1440x900" 102.28 1440 1480 1632 1800 900 902 904 947 (in /etc/X11/xorg.conf "monitor" device section to get my "unusual" resolution working)
Change - !gateway to gateway (remove the ! IF you USE a gateway/router in rc.conf)
Add - alsa dbus hal network (to #deamons in rc.conf)
Remove/comment out -  "OSS Compability" ( in modprobe.conf)

((MY local settings in /etc/rc.conf - adjust to your preference...))
	LOCALE=en_US
	HARDWARECLOCK="localtime"
	TIMEZONE=Europe/Stockholm
	KEYMAP=se-lat6

((This is ONLY to get my speedstep working))
pacman -S cpufrequtils
Add - speedstep-centrino, cpufreq_ondemand ( to #modules in /etc/rc.conf)
Add - cpufreq-set -g ondemand ( in /etc/rc.local)

((IF you want to add the community repository))
Uncomment - lines beneath #community in /etc/pacman.conf

((general tips))
I guess most of this applies if you want to install gnome too.
I have heard of people using the xorg.conf from their ubuntu installation. Using the dapper one is probably the most safe bet as it's xorg 7 too. Breezy does not use xorg 7. But i might work anyway. I adjusted the one generated from xorgconfig in arch to my liking. Having the old ubuntu one might prove useful as a template though. ATTENTION! If you've installed nvidia drivers in ubuntu and replaced "nv" with "nvidia", use nv or install nvidia with "pacman -S nvidia". Easy as pie :)
Using horizontal and vertical refresh rates from ubuntu xorg.conf can also save you from a lot of dispair if automatic monitor detection dosen't work...
Editing rc.conf should be pretty much self explainitory.
The arch WIKI howto:s section is a great resource too.

Hope this will help someone out. And please, dont turn this into a VS WAR thread. Ubuntu is more polished, stable and easy to use for most people. Arch is snappier and a very good way to learn a little more about linux, but lacks many GUI tools. It's also more bleeding edge. Both distros rock in diffrent ways. :)

---

### Post by hizaguchi on 2006-04-24
Which lines under OSS Compatability?  The part from alsaconf?  Or the weird stuff that comes from doing the CD (intead of FTP) install?

---

### Post by pelle.k on 2006-04-25
Well both "alsaconf" lines and "oss compability" are in most cases NOT necessary. My modprobe.conf is empty, i've never run alsaconf and my sound does work perfectly well.

---

### Post by geearf on 2006-04-25
alsa-driver is not needed for kernel 2.6.
But we should not go into a support thread here, it's an ubuntu forum.
I guess it's okay to speak about other distros, but maybe not giving tech help.

---

### Post by otake-tux on 2006-04-27
So far, I'm loving arch.  Got the wireless working after some work, battery was detected,  resolution is set though it took me a lot of work and I'm loving pacman.

Right now I'm trying to get the cpu frequency scaling.  I have an amd turion processor, does anyone know if this is supported?

---

### Post by egon spengler on 2006-04-27
How many of you have had no problems with automounting on arch? It's been nothing but hassle for me

---

### Post by Kindred on 2006-04-27
[QUOTE=otake-tux]So far, I'm loving arch.  Got the wireless working after some work, battery was detected,  resolution is set though it took me a lot of work and I'm loving pacman.

Right now I'm trying to get the cpu frequency scaling.  I have an amd turion processor, does anyone know if this is supported?[/QUOTE]

To use frequency scaling I added the modules powernow-k8 and cpufreq_ondemand to rc.conf and then in /etc/rc.local added: 

```
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

Mine's not a Turion, just a regular A64 but I gather it's the same method.  Good luck with that anyway.

[QUOTE=egon spengler]How many of you have had no problems with automounting on arch? It's been nothing but hassle for me[/QUOTE]

Well yeah, I used gnome for a bit and it was easy in that but i'm using xfce now and haven't got around to setting that up (it does seem like it might be tricky).

---

### Post by vipernicus on 2006-04-27
I had problems auto mounting from my external dvd rw only.  Once, I had usb and scsi enabled, and then dbus hal ivman, then it started working.

---

### Post by tseliot on 2006-04-27
[QUOTE=egon spengler]How many of you have had no problems with automounting on arch? It's been nothing but hassle for me[/QUOTE]
Add dbus and hal to the deamons' list like in this example:
```
DAEMONS=(syslog-ng network netfs crond dbus hal alsa cups gdm)
```

---

### Post by egon spengler on 2006-04-27
[QUOTE=tseliot]Add dbus and hal to the deamons' list like in this example:
```
DAEMONS=(syslog-ng network netfs crond dbus hal alsa cups gdm)
```[/QUOTE]

Thanks but I got it working already, what I meant was that it was hassle to get it to work. HAL recognises everything but or some reason gnome-volume-manager won't mount for me. I use ivman now which automounts but I can get the "execute" option to open the newly mounted drive in nautilus.

I tried both ```
 <ivm:Match name="ivm.mountable" value="true">
        <ivm:Option name="exec" value="nautilus $hal.block.device"" />
    </ivm:Match>

```

to mount everything

and

```
<ivm:Match name="hal.info.vendor" value="LaCie, Ltd'">
                <ivm:Option name="exec" value="/opt/gnome/bin/nautilus /media" />
        </ivm:Match>


```

to specifically mount my usb drive but no luck so far.

edit:
Well fixing the typo in the first example and copying the action config to ~/.ivman seems to help a little bit, still not properly opening nautilus yet though

---

### Post by rpgcyco on 2006-04-28
[QUOTE=foxy123]However after a while I got sort of disappointed with it, especially after I failed to update from Xorg 6.8 to Xorg 7.0. I made a couple attempt to fix it but got tired and install Dapper and have been happy since.[/QUOTE]

Yeah, that was a stinky time for Arch, though it all seems to be cleared up now. I had been using X.org 7 from testing for a little while before it was moved to current, but that caused complications of its own. The benefits of modular X.org were worth the trouble though, IMO. XGL & Compiz is mind numbingly easy to install and get running now.

[QUOTE=manicka]That said though it's not for beginners. I had a friend talk to me today about his first experiences with Linux and he shared that he had recently been experimenting with Mandrake. Being a newbie I immediately gave him a set of Ubuntu CD's and sent him away to discover the joys of Ubuntu.[/QUOTE]

True. I've already posted my views in this thread, it was a while ago, but they still stand. Arch is the perfect distribution for me, but if I hadn't cut my teeth on distros like Fedora Core and Ubuntu, I would have struggled and gave up.

Having said that, I recently helped a friend through an Arch install. I planned to let him do everything himself, finding and reading what to do etc, but I ended up doing most of it, especially X.org and fonts. I showed him how to update the kernel and hence the NVIDIA drivers.

However, I dread what will happen when a new initscripts package is released with important changes to rc.conf. I may need to help once again. If all else fails, Dapper is just around the corner, and while I haven't been following it much at all, most of what I've read seems positive.

[QUOTE=egon spengler]How many of you have had no problems with automounting on arch? It's been nothing but hassle for me[/QUOTE]

It seems to be working fine for me with CDs and my USB stick, in both GNOME and XFCE 4.3 SVN.

**Other Comments -**

As far as which is distribution is faster, I'll have to say Arch is. This is primarily because, as has already been mentioned, by _default_, only minimal services are started automatically, or installed for that matter.

I know it's possible to do a similar thing with Ubuntu's server install method, but I'm thinking that major packages like X.org compiled for i686 has something to do with it (in terms of performance in games anyway).

I've recently been trying out [Arch64](http://www.arch64.org/) (triple booting Windows with Arch32 and Arch64), which is coming along very well. It's fully useable, though it's pure 64 bit, with no 32 bit compatibility. The problem for lazy people, like myself, is that there are next to no user repositorys for it so far. :)

- Rpg Cyco

---

### Post by tseliot on 2006-04-28
[QUOTE=egon spengler]Thanks but I got it working already, what I meant was that it was hassle to get it to work. HAL recognises everything but or some reason gnome-volume-manager won't mount for me. I use ivman now which automounts but I can get the "execute" option to open the newly mounted drive in nautilus.

I tried both ```
 <ivm:Match name="ivm.mountable" value="true">
        <ivm:Option name="exec" value="nautilus $hal.block.device"" />
    </ivm:Match>

```

to mount everything

and

```
<ivm:Match name="hal.info.vendor" value="LaCie, Ltd'">
                <ivm:Option name="exec" value="/opt/gnome/bin/nautilus /media" />
        </ivm:Match>


```

to specifically mount my usb drive but no luck so far.

edit:
Well fixing the typo in the first example and copying the action config to ~/.ivman seems to help a little bit, still not properly opening nautilus yet though[/QUOTE]

Very weird, I haven't got any mounting issues in both KDE and GNOME. DVDs, USB sticks, etc. are all automounted flawlessly.

---

### Post by vipernicus on 2006-04-28
Turns out that in Arch, you don't even need ivman, all you have to do with add the plugdev group, and make yourself a part of it, and then everything is automounted automagically.

---

### Post by MrGreen on 2006-04-28
I loves Arch Linux ;-)

---

### Post by egon spengler on 2006-04-28
[QUOTE=vipernicus]Turns out that in Arch, you don't even need ivman, all you have to do with add the plugdev group, and make yourself a part of it, and then everything is automounted automagically.[/QUOTE]

I've done all of that and still no go.

Did make a breakthrough though, I had followed some dodgy advice and had put my "open nautilus" commands in the action file when they should be in the properties file. What was happening was that actions happen when the device is detected by hal and so it was trying to open nautilus to the mount point before the process of completing the mount was finished. Properties execute commands on change of device properties and so opening nautilus belongs there, i.e. when a devices property has changed to mounted *then* open it in nautilus. It's still not 100%, can't get it to open nautilus when any device at all is plugged in but I've got custom rules for my external hdd and my mp3 player which are the only things I use 90% of the time so I would say it's more than usable

---

### Post by dolny on 2007-09-28
I've switched to arch a long time ago, but I've encountered a big problem yesterday after getting an internet connection installed in my new flat - it won't detect my wifi. I mean, I can see it through lspci, but I cannot get it to work. Its kinda frustrating considering the fact that it worked flawlessly on Ubuntu :/

(Toshiba laptop, Atheros wi-fi card)

---

### Post by miggols99 on 2007-09-28
Have you have a look at the wiki?

[http://wiki.archlinux.org/index.php/Wireless_Setup#madwifi](http://wiki.archlinux.org/index.php/Wireless_Setup#madwifi)

---

### Post by regomodo on 2007-09-28
not bad Arch. Can get a reasonably lean install but despite barely using any RAM (12MB cli, 20MB openboxed) it doesn't feel any faster than a Gnomed Debian Etch, and my setup lacks usability.

Some people say that Arch is fast to boot but unless you spend hours finding out and selecting modules to boot and create a new kernel26.img (removing the udev hook) you'll get frustrated with udev uevents, at least i do. Plus, in my case, hwdetect was flawed. It brought up tonnes of modules that are not related to my laptop whatsoever (scsi? sata? They were never present in mkinitcpio.conf and this is a 9year old laptop we are talking about)

Some issues, which may now be rectified, with the wiki are confusing and some items are hit and miss to set up. The rt61 chipset being one of them. Unfortunately for me i got my wireless working sweet as a nut whilst pissed. It worked for ~a week but when i changed the kernel26.img (which i messed, pata=/=ide) i forgot how to make a kernel fallback. Now my wireless is a pig and can't get rutilt to work.

For me, atm, Ubuntu for simplicity but it'll be slow even with a server/icewm install. Arch Linux for distro hopping and learning something new. Debian Etch/Gnome for speed and usability and stability.

Sorry Arch linux fans. It's coming off and Debian is returning. Do wish i could use pacman instead of apt though.

---

### Post by gnuman on 2007-09-28
> **Gandalf said:**
> 
[list]
[*]Arch is 3 / 4 (maybe more) faster than Ubuntu, when i installed it, i couldn't beleive it, i felt i was using FreeBSD (yes i tried freeBSD its cool, but package system sucks)

Do you mean 1.75 times as fast?  Just wondering.  Gonna look into Arch, as I loves me command line....

:lolflag:

---

### Post by Sporkman on 2007-09-28
> **gnuman said:**
> Do you mean 1.75 times as fast?  Just wondering.  Gonna look into Arch, as I loves me command line....

:lolflag:

How can it be faster, when it uses the same kernel & core apps as every other distro?

---

### Post by pelle.k on 2007-09-28
> but unless you spend hours finding out and selecting modules to boot and create a new kernel26.img (removing the udev hook) you'll get frustrated with udev uevents, at least i do
regomodo, i am sorry you never quite got arch to work for you. However, you must understand that 99% of us never have had those problems you speak of.For me, udev take like 2 seconds to complete, the way it's supposed to work. That doesn't mean i don't belive you. That means i respect your stance, but you must understand that you've had some bad luck.

I've never had to edit mkinitcpio.conf, some udev rules, or messed with diffrent module setups *ever* since i first installed arch in 2005. I have since then successfully ran arch on 5 different machines, ranging from p2-400 up to core2duo (both laptops and regular desktop) machines.

---

