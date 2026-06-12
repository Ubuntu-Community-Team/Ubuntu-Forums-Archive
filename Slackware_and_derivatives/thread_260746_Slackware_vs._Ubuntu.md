---
title: "Slackware vs. Ubuntu?"
date: 2006-09-19
forum: Slackware and derivatives
---

### Post by haxer on 2006-09-19
Whats the main different between slackware and Ubuntu? Apt-get? kde? gnome?:rolleyes:

---

### Post by bodhi.zazen on 2006-09-19
There are significant differences. KDE/Gnome are window managers and can theoretically be run on any distro.

Start here:

[Slackware](http://www.slackware.com/)

---

### Post by benfindlay on 2006-09-19
For one thing, the ubuntu desktop comes with X and GNOME installed. I believe when you install slackware you just get a terminal. Slackware's package handling is via tar balls, whereas ubuntu uses debs via the Synaptic Package Manager. Ubuntu will resolve dependencies for you, whereas slackware will not, so you are required to deal with the dependency resolution yourself (there may be a piece of software to add dependencies, but I don't know for definite, can someone confirm or deny this?)

Anyways, ubuntu is far more user friendly than pretty much ALL other linux distributions

---

### Post by skymt on 2006-09-19
Ubuntu is easy, Slackware is hard.
Ubuntu is automatic, Slackware is manual.
Ubuntu is up-to-date, Slackware is stable.
Ubuntu is graphically-oriented, Slackware is text-oriented.

Short answer: Ubuntu Just Works, Slackware makes *you* work.

---

### Post by xyz on 2006-09-19
I like the light-weight SLAXs which you can "slax copy2ram" thus freeing CD-ROM.

---

### Post by bodhi.zazen on 2006-09-19
Sorry, but some of the above is just not true, particularly "benfindlay".

Slackware comes with a number of window managers, KDE is most popular. By default Slackware boots to a CLI (not a gui). Log in and type "startx".

Slackware is not necessarily any harder then Ubuntu. Slackwre is different and you should not confuse familiarity with difficulty.

If you try Zenwalk (see below) you will be up an running very fast, no problem.

Package management is via slapt-get, a command line tool very simmilar to apt-get. You can download packages from many sources. Gslapt is a GUI front end for slapt-get. How is that harder then Ubuntu? It is not, just different.

At any rate, if you wnat a feel of Slackware I suggest you try Zenwalk. It is light, fast, and easy. It will out perform (faster) then Ubuntu. By default it uses XFCE, but you can easily install KDE or gnome. Or Fluxbox for that matter.

[[color=blue]Zen[/color][color=orange]walk[/color]](http://www.zenwalk.org/)

Zenwalk also has a Live CD which is very nice.

---

### Post by benfindlay on 2006-09-19
Yeah, I was referring to the normal install of each, which I thought was CLI for slackware. Didn't mean to imply that you can't use a GUI with it. Meant to say that ubuntu boots the GUI by default.

Difficulty is all relative. I'd say that how quickly you become "familiar" with something is a good measure of how easy, or user friendly it is, and from talking to people who have used both slackware and debian based systems, they've pretty much all agreed that debian is much more intuitive, user friendly and easy. Each to their own however.

I've read about Slapt-get and according to wikipedia: > slapt-get does not provide dependency resolution for packages included within the Slackware distribution Perhaps in terms of difficulty it is no harder, but its definitely harder work!

---

### Post by bodhi.zazen on 2006-09-19
> **benfindlay said:**
> Perhaps in terms of difficulty it is no harder, but its definitely harder work!

Thank you for your thoughtful response. Take a look at Zenwalk.

(FYI Zenwalk = Slackware light, it is a "fork" of Slackware).

---

### Post by benfindlay on 2006-09-19
So does zenwalk actually resolve dependencies for you? If so then that would be so much more convenient and definitely worth a look at! I should also imagine it would also be ideal for lower spec machines, if you ran fluxbox, xfce or ice-wm as your GUI.

Cheers for the reply

---

### Post by bodhi.zazen on 2006-09-19
> **benfindlay said:**
> So does zenwalk actually resolve dependencies for you? If so then that would be so much more convenient and definitely worth a look at! I should also imagine it would also be ideal for lower spec machines, if you ran fluxbox, xfce or ice-wm as your GUI.

Cheers for the reply

Yes, it resoles dependencies. Yes it is easy. Yes it is fast.

Zenwalk uses Netpkg, a GUI, for package management. It resolves dependencies.

[Netpkg](http://manual.zenwalk.org/en/ch03s04.html)

Try the Live CD.

If you have any problems, I would be happy to help.

---

### Post by haxer on 2006-09-19
Thx to you all seems that i started a nice "topic" all people wants to say something which i like becouse then im getting updated im a total noob but im willing to learn but my last question is .. if a newbie like me should start with slackware would it be to hard to me or should i stay in ubuntu untill ive got all my cards even ..? :-({|=

---

### Post by bodhi.zazen on 2006-09-19
> **haxer said:**
> Thx to you all seems that i started a nice "topic" all people wants to say something which i like becouse then im getting updated im a total noob but im willing to learn but my last question is .. if a newbie like me should start with slackware would it be to hard to me or should i stay in ubuntu untill ive got all my cards even ..? :-({|=

I advise you explore various distros, see what your options are. But not excessively. In that I mean learn the CLI. The CLI is distro independent and this is the difference between newbie's and learning Linux. Is there such a thing as mastering Linux?

Slackware/Arch/Fedora/SUSE all will teach you something. All have strenghts and weaknesses.

---

### Post by haxer on 2006-09-19
Whats the most user friendly of those? Looking at slackware i think its nice :) but is it at easy as ubuntu i already tried out suse 9.01 and that sucked really hard ... Slackware sounds intresting is there any good forums for it?

---

### Post by 3rr0r on 2006-09-19
Have you tried Back:Track ?  [www.remote-exploit.org](www.remote-exploit.org) is where you can get it.  It is based on slackware, but it primarily made for network security testing and the such  :rolleyes:

---

### Post by Irony on 2006-09-19
Zenwalk is very slick unfortunately I couldn't get my ATI card acceleration to work on it.

Apart from the ATI issue I found Zenwalk simple to install and easy to install programs from the repositories.

If you have Ubuntu installed then if you have a partition set aside you can install Zenwalk to it - skip the installing Lilo part and simply add a line to your /boot/grub/menu.lst something like;

[PHP]# This entry added by me as an example
# installation on /dev/hdb4
title		Zenwalk 2.01, hdb4
root		(hd1,3)
kernel		/boot/vmlinuz root=/dev/hdb4 ro
savedefault
boot[/PHP]

---

### Post by bodhi.zazen on 2006-09-19
> **haxer said:**
> Whats the most user friendly of those? Looking at slackware i think its nice :) but is it at easy as ubuntu i already tried out suse 9.01 and that sucked really hard ... Slackware sounds intresting is there any good forums for it?

User friendly distro's: Zenwalk, [PCLinxuOS](http://www.pclinuxos.com/news.php), SUSE 10 is an improvement, Fedora core 5 (see [fedora frog](http://easylinux.info/wiki/Fedora_frog)), and [Puppy Linux](http://www.puppylinux.org/user/viewpage.php?page_id=1).

**Did I mention [color=blue]Zen[/color][color=orange]walk[/color]? That is where I would start if you are interested in Slackware.**

---

### Post by haxer on 2006-09-19
Hmm.. what about knoppix then? Is both zenwalk and Slackware grapical at begining as Ubuntu?

---

### Post by bodhi.zazen on 2006-09-19
> **haxer said:**
> Hmm.. what about knoppix then? Is both zenwalk and Slackware grapical at begining as Ubuntu?

Knoppix is based on Debian and is thus very similar to Ubuntu.

By default Slackware boots to a CLI. You can easily configure Slackware to KDM (graphical log in).

Zenwalk boots to a graphical log in.

---

### Post by haxer on 2006-09-19
Hmm.. how to make Slackware graphical? And theres 2 disc actually 4 or 5 but do i only need 1 and 2 disc to make a complete installation? 1 is for "installation" and 2 "is for graphical" ? Looking at 10.2


And knoppix is something you would rekomend? Or is it naughty? :P

---

### Post by Anonii on 2006-09-19
[B][I][U]IMO
[/U][/I][/B]
I dont really like Knoppix. Knoppix is freaking great to show your friends the world of Linux and experience their great LiveCD but in a stable every-day system, I'dnt reccomend it. With Ubuntu you get the same advantages as in Knoppix (LiveCD, APT etc) and its better supported and the community is great,

---

### Post by haxer on 2006-09-19
> **Anonii said:**
> [B][I][U]IMO
[/U][/I][/B]
I dont really like Knoppix. Knoppix is freaking great to show your friends the world of Linux and experience their great LiveCD but in a stable every-day system, I'dnt reccomend it. With Ubuntu you get the same advantages as in Knoppix (LiveCD, APT etc) and its better supported and the community is great,

But how about Slackware?:?:

---

### Post by haxer on 2006-09-19
Please help :=)

---

### Post by bodhi.zazen on 2006-09-19
> **haxer said:**
> Hmm.. how to make Slackware graphical? And theres 2 disc actually 4 or 5 but do i only need 1 and 2 disc to make a complete installation? 1 is for "installation" and 2 "is for graphical" ? Looking at 10.2


And knoppix is something you would rekomend? Or is it naughty? :P

Install Slackware. As a part of the install install KDE.

The default is to boot to init 2 which is CLI. Change the default to init 4. You can do this via grub or via slackware.

It is not hard.

Edit inittab, change it to read:

# Default runlevel.
id:4:initdefault:

---

### Post by xpod on 2006-09-19
> slapt-get, 

I just love some of the terms and package names we got.
Ive felt like one of those every time Ubu has got the better of me:D 
Brilliant.
I`m killing our m.e eventually but will be sticking to the Ubu family of distro`s......."keeping it IN the family" so to speak:D 

Happy hunting....

---

### Post by bodhi.zazen on 2006-09-19
> **xpod said:**
> I just love some of the terms and package names we got.
Ive felt like one of those every time Ubu has got the better of me:D 
Brilliant.
I`m killing our m.e eventually but will be sticking to the Ubu family of distro`s......."keeping it IN the family" so to speak:D 

Happy hunting....

:shock: xpod you always struck me as a slacker :shock:

I hope you enjoy Slackware. Not to harp, but I will anyway....

Slackware 10.2 is somewhat outdated and I would advise Zenwalk for the time being. You do know Slackware 11.0 is in RC5? I am anxiously awating Slackware 11.0.

For all your slackware needs:

[Linux Packages](http://www.linuxpackages.net/)

Enjoy.

---

### Post by xpod on 2006-09-19
> xpod you always struck me as a slacker 


OI!!...i meant i usually felt like a "slapt-get"....not a "slacker":D 

Dont get the chance to be a "slacker" round here mate...[-X :D 

Of course if your having trouble with the meaning...."slapped git":D

EDIT...between THIS community and my OWN bloody community im run off my feet

---

### Post by clarkth on 2006-09-19
> **bodhi.zazen said:**
> I suggest you try Zenwalk. It is light, fast, and easy. It will out perform (faster) then Ubuntu. By default it uses XFCE, but you can easily install KDE or gnome. Or Fluxbox for that matter.

I use ZenWalk for a PII box with 128 MB RAM and it works great.  I highly recommend it for ease of use and usability with older hardware.

---

### Post by ruhar on 2006-09-20
> Slackware sounds intresting is there any good forums for it?

There is an *official* Slackware forum:
linuxquestions.org/questions/forumdisplay.php?f=14

This is an excellent Slackware resource and contains a ton of helpful info including howtos, etc.  

My favorite (starting out) Slackware reference that will get you up and running a full Desktop install is:
[http://www.bitbenderforums.com/vb22/showthread.php?postid=311808](http://www.bitbenderforums.com/vb22/showthread.php?postid=311808)

IMHO this is an invaluable starting point reference.

Also there is an excellent freenode.org irc channel (##slackware)
that provides an excellent source of information as well.

Good luck and happy Slackin'

---

### Post by haxer on 2006-09-20
Thx to all of you i love this forum :) Did you all know that slackware is swedish invented? :) thats right we swedes are the greatest and linus is from finland that like 130 "swedish miles" from me

---

### Post by bodhi.zazen on 2006-09-20
Ruhar: Nice link, thank you :)

---

### Post by ruhar on 2006-09-20
> Did you all know that slackware is swedish invented? 

Not sure what you mean.  Slackware is and has always been maintained by a single guy, Patrick Volkerding:
[http://en.wikipedia.org/wiki/Patrick_Volkerding](http://en.wikipedia.org/wiki/Patrick_Volkerding)

---

### Post by haxer on 2006-09-20
Omg i think i have mixed it up with SOT sry guys im confused thanks for correcting me :)

---

### Post by Brunellus on 2006-09-20
I am moving this thread to 'other OS talk'

---

### Post by bonzodog on 2006-09-20
I would also recommend Zenwalk, it boots to gdm, like Ubuntu, and has all the GUI tools needed. 

Zenwalk 3.0 is also completely uptodate, and is using 2.6.17.11 kernel and Xfce 4.4 Beta2 for desktop. 
Netpkg is good now, has had many improvements recently, and there is more than one repo now.

---

### Post by haxer on 2006-09-20
How about FreeBSD?

---

### Post by bodhi.zazen on 2006-09-20
> **haxer said:**
> How about FreeBSD?

Free BSD is also nice. Try a live cd [Frenzy](http://frenzy.org.ua/en/releases/1.0/download.shtml)

I would advise [Desktop BSD](http://www.desktopbsd.net/) if you HD install (you can install Frenzie, I have, it runs just fine, but it is Fluxbox and it takes some post-install configuration).

---

### Post by kazuya on 2006-09-21
Zenwalk is a gem like Vector linux. I like Zenwalk though because it has many tools for installing softwares at your disposal. 

I run Zenwalk on my Pentium III 128 MB Sony laptop, and the speed at which I launch , run , watch movies, etc is almost equal if not greater than the speed at which I run most other distros on a newer PC with 512 MB RAm or 1 GIG of RAM.

It something to be experienced. Now I had to install vlc since that was easier to get running very fast with just vesa settings than with the default gxine.

I am sure with Zenwalk 3.0 a lot more improvement has been made. 

I did not see the need for Zenwalk 3 as 2.8 was already awesome. 

I like the Ubuntu community and the ease of updating distro, but the speed of Zenwalk is rather intoxicating while still maintaining a lot of functionalities like playing videos, surfing web, playing games.., etc.

Plus the distro really shows you how to manage your desktop. I find it easier to configure than Xubuntu, and faster as well than Xubuntu. 

Alas, netpkg is very good, but their repo is slightly less than debian or ubuntu.

But, just about anything you can install or get in Ubuntu, you can certainly a tar for it. I prefer the slackit to linuxpackages for where to get my .tgz packages for install. 

Ubuntu is still easier for a newbiw than Zenwalk. But for someone, wanting to know more of linux, but wanting a distro that is easy to install and already just works while giving raw power in your hands through CLI and other pkgtools.. This is definitly one of the ones to go for. 

Moreover, the distro although slack-based is rather bleeding-edge and yet stable.

Give it a try.

---

### Post by bodhi.zazen on 2006-09-21
kazuya: Zenwalk used to be my primary OS.

Then I found [Arch](http://www.archlinux.org/) Linux.

[Arch Linux Install guide](http://www.archlinux.org/static/docs/arch-install-guide.html)

---

### Post by ruhar on 2006-09-21
I've also been running Arch lately after quite a while with Slack.  I think Arch has a very bright future.  I think I'll definitely give Slack 11 a fair look though when it comes out.  Arch seems to be the best of all worlds (fast, lean, strong package management, good community, KISS design principles...)

---

### Post by Neo40 on 2006-09-21
I installed Zenwalk 3 and so far I really like it. The only problem I have is fonts. With my 17" lcd diaplay at 1280x1024@60 Hz, the fonts dont look so clear than my Xubuntu machine. Here, I found some howto to improve fonts but if I try them on Zenwalk, it seems to happen nothing. Maybe someone can tell me  where I can find some helps to improve fonts for zenwalk (or Slackware)?
Thanks

---

### Post by victorche on 2006-10-05
> **ruhar said:**
> I've also been running Arch lately after quite a while with Slack.  I think Arch has a very bright future.  I think I'll definitely give Slack 11 a fair look though when it comes out.  Arch seems to be the best of all worlds (fast, lean, strong package management, good community, KISS design principles...)

You can do that now ;)

It is 11.0 and it is released!

Happy slacking ;)

---

### Post by ruhar on 2006-10-06
w00t!!!!!!!
Installed it the night it came out.  I am really digging Slackware 11.  Its really responsive and the packages are very up to date.  As up to date as I need. :)

---

### Post by pmccartney on 2007-02-13
I see that it's been a while since anyone has commented on this thread, but I wanted to add my two cents to offer newcomers something else to read and think about.

I started using Linux back in 1996... with Slackware (Kernel 1.2) which came bundled with a book I had purchased.

With the aid of Running Linux (First Edition), Slackware at that time really wasn't any more difficult to install on a new PC than Windows 95 was. I should know because I use to custom build computers for a living, and I probably loaded Win95 (floppy version) at least 20 times during any given week. It was really bad whenever we had to load MS Office from floppies as well. The point is that the installation and configuration times were about the same, especially when you take into consideration how we had to manually configure peripherals and load drivers ourselves. The more times I installed Slackware, the easier it became. I admit that Slackware can seem a little more intimidating to install than any of the other Linux distributions, but it's all a matter of how much you are willing to learn along with how much control you want over your system. If you think about it in terms of Windoze users, the reality is that they don't have any control whatsoever. With Ubuntu, you have control, but you are limited on what you can do based on how much you really know about your system. With Slackware, you have total control, and you learn more about your system so you're able to maintain that level of control a little better.

Anyway, I've watched Linux grow up over the years, and it's been a real pleasure to see all the changes that have taken place during that time. I've tried many different distributions including Red Hat, Mandrake, SuSE, Stampede, Debian, Gentoo, Mepis, (k)ubuntu, Sabayon, Vector, FreeBSD, OpenBSD, NetBSD, Caldera, Turbolinux, and a few others that I can't seem to remember at the moment.

The point is that you should try a handful of different distributions before deciding on which one may be right for you. Ubuntu is a great user-friendly distribution that simplifies a lot of things for you. It's a good way to be introduced into how Linux works, and it is a great starting point for those who are interested in learning about an alternative OS that will work with their existing hardware. However, after giving Linux a chance, and the new Linux convert feels that they want more control and performance out of their equipment, then I suggest taking the next leap of faith, and that is to learn how to install and configure Slackware. Just like anything else about Linux that's found online, there are plenty of links to all the necessary information regarding Slackware, it just requires some investigation on your behalf.

On a different note, if you've ever used DOS and hated it or if you've never used DOS and don't know what DOS is, I suggest staying with something like Ubuntu. Also keep in mind that the main purpose for an operating system is to provide a way for humans to interface with a computer in order for it to perform the various tasks that we want it to do.

I am currently running three different distributions on three different systems. I have an HP Pavilion dv5030us Laptop that I'm still testing Ubuntu on, and so far I'm liking it. I also have openSUSE 10.2 (AMD-64) running on one of my desktop PCs (which I'm about convert to either Slackware or Ubuntu), and I have another desktop PC running Slackware 11.0 which runs circles around the openSUSE system. Keep in mind that the Slackware system is running on a slower AMD-32 processor, has less memory, and it has an nVidia graphics card with only 64MB as opposed to the 256MB nVidia graphics card on the openSUSE system. Yet, they're both running KDE 3.5, and have roughly the same amount of packages installed.

Now, the way I have my systems set up might not appeal to some of you, and I don't want them to, but with all the preceding information I've offered, all I can say is that you have to decide for yourself which distribution and configuration is right for you.

:) Happy Computing!

---

### Post by imalltech on 2007-02-22
Hello all, 

no onne has posted in a while but to encourage those who are looking into the world of linux. 

I'm also a newbie who just started 2 days ago, I have tried to use Fedora core, OpenSuse, and now im using Kubuntu.

I have become a linux lover just for the simple fact that this is so Open and there is an humangous amount of options. 

But for newbie linux lovers like myself its like suffering from ADD you go from one to another in a matter of minutes.

I have come like Kubuntu, but it has crashed on me a couple of times which i was extremely surprised. I know for a fact its something im doing wrong though. Messing around with in the Roots folder. 
Because its a beautifull OS.

Im about to try out knoppix or slackware not sure yet! LIke i said ADD!!!! 

Think about it when was the first time you tried Windows, there is a first time for everything and if you stick to it you will eventually get savvy at anyting.

Good luck hunting for your favorite linux distro.

thanks

---

### Post by kazuya on 2007-02-22
It is hard. I have used the major types of linux except source and LFS.
I haved loved too many and find myself returning to some old loves.

Favorite distro right now bar none is pclinuxos2007test. I have gotten Beryl working exceptionally better on that distro than in any other distro except Sabayon.

Pclinuxos is just easier to work with and is very pleasing to the eyes. 

Now, I equally love Linux Mint, Mepis, Ubuntu, Sabayon, Zenwalk {speed}, Vector Linux, Wolvix, and who knows what the future might bring.

Now on a older system with 256MB and below, only Wolvix, Vector, and Zenwalk would be contenders. The slack distros just dominate on older hardware.

Ubuntu, Mepis, and surprisingly the slack distros have very good detection.

---

### Post by StarsAndBars14 on 2007-03-08
Well, I switched to Slackware 11 just yesterday and I can notice a few things right off the bat:

**Packages**

.  No package repository
.  Apt-get has been replaced with installpkg.
.  Basic package operations are made with pkgtool.

**Kernel**

. 2.4.33.3 is default in Slackware 11, 2.6.17.13 is in the /extra section.. 
. Faster boot time
. Faster system in general than Feisty or Edgy

**Window manager**

. KDE 3.5.4 = teh lose.  I'm installing 3.5.6 with konstruct as I type this.
. XFCE 4.2.3.2 = Nice

All in all, its okay.

---

### Post by bonzodog on 2007-03-08
There *is* a package repository...but heres the stinker; you need to find it and get gslapt which will also require slapt-get from it.

[http://linuxpackages.net](http://linuxpackages.net)

It's in there, and is all community built packages. I have to admit it, but the community likes to build their own stuff when they can, and provides packages to make life easier for others.

---

### Post by StarsAndBars14 on 2007-03-10
Yeah I just hope its safe to run gslapt via the root password.
  :P

---

### Post by justaguynpc on 2007-03-16
I used slackware early on in my Linux experience.  I liked it, though didn't know much about Linux, as a whole.  One asset it has going for it is the "vanilla" desktop (KDE).  

The KDE you see in Slackware is pretty much unaltered in any way, shape or fashion.  No "branding" or modifications made to the version released from the developers.  I did like that!

Cheers

---

### Post by ayoli on 2007-03-16
forgive me, i didnt take time to read the whole thread. Anyway, i think slackware is one of the best distro to dive into linux, learn how to conf everything. It's also the distro which is the most closer to unix i think. I use it for servers only because it's the easier distro for that and really stable, before i had a slack with gnome but i think distros like ubuntu, sabayon, knoppix are better for that. I don't want to waste time to know how to install/conf each soft/lib/* to have a nice desktop.
the only problem with this dist is that it's based on one (good) man (patrick volkerding), and it could disappear with him (hope not)

---

### Post by ayoli on 2007-03-16
> **bonzodog said:**
> There *is* a package repository...but heres the stinker; you need to find it and get gslapt which will also require slapt-get from it.

[http://linuxpackages.net](http://linuxpackages.net)

It's in there, and is all community built packages. I have to admit it, but the community likes to build their own stuff when they can, and provides packages to make life easier for others.

not really recommended to add community repos to slpt-get, cause of dep problems, i 'll recommend to manually upgrade with installpkg utility.
btw, i prefer swaret instead of slapr-get

---

### Post by mephisto786 on 2007-03-20
Few misconceptions seem to crop upabout slackware here.....one, gslapt is not officially supported. The included slackpkg tool is, and works with the older pkg tools and syncs you to the online repo for updates.

It is one of the fastest distros, and with slackware 11, is also upon release one of the most up to date.....tho the releases tend to be about a year apart. For a more bleeding edge slackbox, use the current changelog....which will keep you in sync up till the next release with the latest.

distros like SUSE and ubuntu have occaisonally crashed , prolly due to a runaway app or process....i have never seen slackware crash since version 10.2......stability is one of its selling points, as is speed.

One reason there are no dep finding tools supported is because of the vast number of libs, and tools already included in a slackware full install (cd one has gui, but for KDE you need disk 2 as well.....since the 11 release, because KDE has grown so much of late. There are no dev pkgs in slackware, since debian tends to 'break down' apps from some of their libs and dev pkgs. Most slackware packages, when you install with the cli tools or with k package already have their dependencies onboard. If it doesn't run try firing up with the cli and it will tell you what is missing...you will seldom find a pkg requireing more than one or two extra pkgs......as opposed to the equally great but different apt utilities which pull in libs and other needed pkgs. If you want to keep slack 11 up to date, change your sources to current, which is similar to the idea of unstable / testing in debian based.

Yes, there is more learning and file configuration, and very little tweaking of upstream packages compared to morecustomized distros.......kde for slackware will be very close to the original unpatched kde release, without customization making it more slackish......and configuring your system under the hood is a great way to know what lies under distros exterior and how to tweak the engine.

gslapt and and swaret are unsupported but like 'easy ubuntu' or automatix, many use them for ease of package installs etc. And places like Linux packages supply binaries not in the slackware repo. But most users prefer to compile new apps so it runs according to their own systems configuration.....much like the idea of gentoo. Still, one has a choice.

Derivs, like zenwalk, and vector, slax and the excellent BackTrack for pen testing are based on this , with a few tweaks in the way that ubuntu is a customized debian, basically. Testing them out for ease of install and use will give you a taste of slacklife......but defiintiely try out slackware at some point to see if it suits what you want in an OS. Personally I like having slack on a production box and dual booting kubuntu and bsd on the laptop. Ubuntu is great for running a very gui, automatic system which is up to date. But I trust slackware for stability on my produciton machines ........btw, years ago,  Patrick Volkerding was quite ill, and way back then assured us there are plans in place for the distro to continue should anything happen to him. Just as, I am sure, the Linux kernel will continue without Linus.......

Depends on what you want to do with your box, and how much you want to work / learn. Ive always found a box with slackware and ubuntu dual booted to be the best of both worlds.........

cheers

---

### Post by Hevoos on 2007-03-22
Could someone tell me how to use this installpkg tool for keeping your system up to date? I've tried Slackware 11 a little and I really liked it, I also have to admit it was very user-friendly. Some things were almost easier than in Ubuntu, and you knew exactly were you installed all packages. 

Did not figure out how to install the nvidia drivers anyway, but got almost everything else to work. Don't be afraid to try it, I am almost a complete newbie to linux (I am a windows power-user though) and I got it to work. ;)

---

### Post by ayoli on 2007-03-22
> **Hevoos said:**
> Could someone tell me how to use this installpkg tool for keeping your system up to date? I've tried Slackware 11 a little and I really liked it, I also have to admit it was very user-friendly. Some things were almost easier than in Ubuntu, and you knew exactly were you installed all packages. 

Did not figure out how to install the nvidia drivers anyway, but got almost everything else to work. Don't be afraid to try it, I am almost a complete newbie to linux (I am a windows power-user though) and I got it to work. ;)

i think installpkg tool only install packages, official package manager tool is [slackpkg]("http://slackpkg.sourceforge.net/")
but use it carefully if you upgrade from version 11 to current because of big changes, especially:
[LIST]
[*] upgrade slackpkg with slackpkg: slacpkg upgrade slackpkg
[*] run "slackpkg update && slackpkg update gpg"
[*] downloads packages dialog et aaa_terminfo: slackpkg download dialog && slackpkg download aaa_terminfo
[*] upgrade pkgtools with slackpkg: slackpkg upgrade pkgtools
[*] install dialog et aaa_terminfo with installpkg
[*] bin package has been exploded in many packages so you have to manually install package which
[*] after sysvinit and udev upgrade, don't forget to install new sysvinit-script package and manage all .new files in /etc (if you don't do that you should never reboot)
[/LIST]

---

### Post by Hevoos on 2007-03-23
That sounds complicated. Is there any good guide or howto that explains how the slackpkg works?

And is there any other way to save all your programs you've installed manually and upgrade the rest?

---

### Post by ayoli on 2007-03-23
> **Hevoos said:**
> That sounds complicated. Is there any good guide or howto that explains how the slackpkg works?

And is there any other way to save all your programs you've installed manually and upgrade the rest?
usually slackpkg is really simple to use, i've post these instruction _only_ because there was a major upgrade from slack 11 to current after six month without upgrades.
Slack is IMHO a really simple distrib to use if you're not afraid about editing some config files and manipulate CLI.
there is some slackware forums in many languages where you may find some good info, and also man, but slakpkg is simple to use most of the time.
cheers.

---

### Post by SunnyRabbiera on 2007-05-16
I have been thinking of switching to slack, or a slack varient.
Ubuntu is great, but I am interested in Zenwalk.
Zenwalk, PClinux and Sabayon are on my "distros to hop to next" list.

---

### Post by bodhi.zazen on 2007-05-17
> **SunnyRabbiera said:**
> I have been thinking of switching to slack, or a slack varient.
Ubuntu is great, but I am interested in Zenwalk.
Zenwalk, PClinux and Sabayon are on my "distros to hop to next" list.

Zenwalk and PCLinux are awesome. You might also like Wolvix and SAM.

If you try Wolvix, go for the beta, Desktop Edition, version 1.1.0

SAM is PCLinux + XFCE + a few "non-free" enhancements like flash and java

+1 Sabayon as well :twisted:

---

### Post by RAV TUX on 2007-05-24
> **bodhi.zazen said:**
> Zenwalk and PCLinux are awesome. You might also like Wolvix and SAM.

If you try Wolvix, go for the beta, Desktop Edition, version 1.1.0

SAM is PCLinux + XFCE + a few "non-free" enhancements like flash and java

+1 Sabayon as well :twisted:

Wolvix simple rocks, Sabayon has become a benchmark for Linux quality and dependability

---

### Post by Drakeo on 2008-01-02
Well slackware is stable and I can take a Ubuntu kernel put it in a seperate directory in slackware configure it and build it. Then I build modules for programs that are not on the Ubuntu aptget. now like any one control is a big thing. so if I compile with say a 3.6- gcc and then i apt-get a program that needs a 4.1- gcc well like a good boy apt-get does all the dependencies right and now I have the up  dated 4.1_ gcc. this realy hurts me why. well all the cool stuff I compiled is compiled with 3.6 etc. and now my whole system is 4.1- does any one see the issue. 
 So here is the deal all linux systems are made to be controled by the user not visa versa such will be the down fall of win 98 lol. the idea that if i want to up date my whole system for one program. and am left with a buch of dead compiled programs only good to send back to the last 6 Ubuntu updates thats ok. Ubuntu is good stuff I use it I like it but when it comes to ease of dependencies for compiling I need to be in total control. so as all my systems I do my own dependencies even on Ubuntu. this has made MY Huge U lighter faster and very reliable. as for gnome it's ok  slack came with bith for years . keep up the good work Ubuntu because everyone that wants that one click O/s has wiped out the windows C drive all to many times.

---

### Post by octavianus on 2008-12-26
Many people say that Slackware is a highly stable disto.I would like to try Slackware in the Virtual Box. My question is if there is any Slackware based distro out there which is easy to operate like Ubuntu but still stable like Slackware. I have tried Goblinx but I was disappointed as it would not boot in my Acer 5610. Otherwise , I am already very happy with my currrent Intrepid Ibex.Thank you.

---

### Post by Sorivenul on 2008-12-26
> **octavianus said:**
> Many people say that Slackware is a highly stable disto.I would like to try Slackware in the Virtual Box. My question is if there is any Slackware based distro out there which is easy to operate like Ubuntu but still stable like Slackware. I have tried Goblinx but I was disappointed as it would not boot in my Acer 5610. Otherwise , I am already very happy with my currrent Intrepid Ibex.Thank you.

You could try Zenwalk or SLAX. Both are very clean and easy to use. Both have Live versions you can test, or you can load them in VirtualBox. If you don't feel comfortable learning the "Slackware way", which is, IMO, vastly different from the "Debian/Ubuntu way", stick with your current install.  If it isn't broken, don't fix it.

---

### Post by andrew.46 on 2008-12-27
Hi octavianus,

> **octavianus said:**
> My question is if there is any Slackware based distro out there which is easy to operate like Ubuntu but still stable like Slackware.

You may find that the difficulty of Slackware is something of an urban legend. I would not call Slackware more *difficult* than Ubuntu instead it is *different* to Ubuntu. Different mindset required, different community but still Linux, still KDE etc etc. I would suggest trying the original Slackware and its new release version 12.2.

All the best,

Andrew

---

### Post by octavianus on 2008-12-27
> **andrew.46 said:**
> Hi octavianus,



You may find that the difficulty of Slackware is something of an urban legend. I would not call Slackware more *difficult* than Ubuntu instead it is *different* to Ubuntu. Different mindset required, different community but still Linux, still KDE etc etc. I would suggest trying the original Slackware and its new release version 12.2.

All the best,

Andrew

Thank you Andrew. I am surely going to give the original Slackware a try. Why not going after a new challenge and learn something new out of it ? That is all about the Linux movement and that makes the Linux community so different than the MS or Mac. The most beautiful things in life are not for mediocre anyway. I will let you know how it goes.

---

### Post by octavianus on 2008-12-27
> **Sorivenul said:**
> You could try Zenwalk or SLAX. Both are very clean and easy to use. Both have Live versions you can test, or you can load them in VirtualBox. If you don't feel comfortable learning the "Slackware way", which is, IMO, vastly different from the "Debian/Ubuntu way", stick with your current install.  If it isn't broken, don't fix it.

 Hi Sorivenu,

I have downloaded the Slax live cd and run it from RAM. It went total flawless and I am very impressed. I played MP3  music and some MP4 video files without any issue. All of my hardwares were also correctly detected.
However , I did not see any option of HDD installation. My next test will be Zenwalk before going after the real Slackware.

---

### Post by Sorivenul on 2008-12-27
> **octavianus said:**
> Hi Sorivenu,

I have downloaded the Slax live cd and run it from RAM. It went total flawless and I am very impressed. I played MP3  music and some MP4 video files without any issue. All of my hardwares were also correctly detected.
However , I did not see any option of HDD installation. My next test will be Zenwalk before going after the real Slackware.

SLAX is meant to be run as a LiveCD, but there is a way to install it from either the CD or the USB version, though it can be involved. Search the SLAX forums if this interests you.

Also, Zenwalk comes in "Live" and "Install" versions as well. 

In addition, you should know that Slackware or derivative will install LILO over your current GRUB configuration, though most do a fine job of detecting other systems if you are dual-booting.

---

### Post by kk0sse54 on 2008-12-29
Zenwalk is a great distro, otherwise some other slackware derivatives would be Vector Linux (uses slapt-get I believe but it's been a while) and Frugalware (uses pacman as a package manager). There's also BlueWhite64 which is an unofficial port of slackware to x86_64 otherwise I'd recommend installing a minimal install of Slackware and then install slackpkg and build from there using one of the slackware mirrors. After you create a functional desktop, become friends with slackbuilds and your life of installing additional software will be so much easier :).

---

### Post by octavianus on 2008-12-29
> **C!oud said:**
> Zenwalk is a great distro, otherwise some other slackware derivatives would be Vector Linux (uses slapt-get I believe but it's been a while) and Frugalware (uses pacman as a package manager). There's also BlueWhite64 which is an unofficial port of slackware to x86_64 otherwise I'd recommend installing a minimal install of Slackware and then install slackpkg and build from there using one of the slackware mirrors. After you create a functional desktop, become friends with slackbuilds and your life of installing additional software will be so much easier :).


Believe it or not , the current Intrepid Ibex is the most stable "Desktop" distro I have ever seen giving the number of tasks it does at a time. How many "Desktop" distros out there that can execute so many tasks simultaniously and non stop but remains calm and stable ?
 For my work , I need to keep at least 10 applications open at the same time and Ibex never minds.
I even rate this Ubuntu Ibex above Hardy in term of efficiency and stability.

Slackware and derivatives are fantastic for the developers without any doubt who need very stable environment for their developing works. I believe that many Ubuntu developers themselves use Slackware and that is why we get so outstanding distro like Intrepid Ibex which is a perfect desktop environment for a Defence analyst like myself.

---

### Post by ZBREAKER on 2008-12-30
Slackware is extremely cool. I started my linux journey some years ago with the 'buntus (which I still love) , but currently run both Sidux and Slackware 12.2. I've learned more about linux in the last few months using these 2 then I did in the previous 2 years. It has been a trip worth every step of the way!

---

### Post by Antman on 2008-12-30
> **ZBREAKER said:**
> currently run both Sidux and Slackware 12.2. I've learned more about linux in the last few months using these 2 then I did in the previous 2 years. It has been a trip worth every step of the way!
+1 sidux and Slackware are both awesome. I would still be running sidux on my laptop now, but since my ATI drivers were having issues with the sidux kernel, I gave up on it for now.

---

### Post by gjoellee on 2008-12-30
Slackware is used by people who know Linux, due to the minimal system, Slackware is actually faster then Arch Linux in some places. Slackware is however harder to use, you install source packages and must find the dependencies yourself which can be a real pain in your butt.

---

### Post by andrew.46 on 2008-12-30
Hi gjoellee,

> **gjoellee said:**
> [...] you install source packages and must find the dependencies yourself which can be a real pain in your butt.

It is not actually such a burden, dependencies are usually explicitly mentioned on websites for software as well as itemised in documents in the source code itself. It is only a small amount of homework usually. There is also a wealth of wrapper scripts available for the source code that makes life much easier.

Reading back through this thread I see there is a fair bit of talk about some of the dependency tracking tools available for slackware. I am pretty sure however that the vast majority of users do not use these tools and are quite happy with installpkg, removepkg and pkgtool which do *not* check dependencies.

Andrew

---

### Post by Antman on 2008-12-30
> **andrew.46 said:**
> hi gjoellee,



it is not actually such a burden, dependencies are usually explicitly mentioned on websites for software as well as itemised in documents in the source code itself. It is only a small amount of homework usually. There is also a wealth of wrapper scripts available for the source code that makes life much easier.

Reading back through this thread i see there is a fair bit of talk about some of the dependency tracking tools available for slackware. I am pretty sure however that the vast majority of users do not use these tools and are quite happy with installpkg, removepkg and pkgtool which do *not* check dependencies.

Andrew
+1

---

### Post by ZBREAKER on 2008-12-31
+2

Absolutley....the dependency issue was probably the scariest thing with Slack at first. But as I learned with time, it basicallly became a non-issue given the massive amount of programs which come with the distro and the excellent quality of packages from other sources such as SlackBuilds and Slacky.eu.

---

### Post by octavianus on 2009-01-02
How big is the chance that one day we will see a Slackware derivative similar to what Ubuntu has become from Debian ?

---

### Post by jrusso2 on 2009-01-02
Slackware is a total pain in the butt but its much better then Ubuntu, does not come with Gnome, Pat V hates it and won't allow Gnome.  Once you use Slackware its much faster then Ubuntu and most stable.

---

### Post by Antman on 2009-01-02
> **octavianus said:**
> How big is the chance that one day we will see a Slackware derivative similar to what Ubuntu has become from Debian ?

I guess when a billionaire decides to fund Zenwalk or Vector Linux. :wink:

---

### Post by kk0sse54 on 2009-01-02
> **jrusso2 said:**
> ...does not come with Gnome, Pat V hates it and won't allow Gnome.

Good, me too :D

---

### Post by andrew.46 on 2009-01-02
Hi jrusso,

> **jrusso2 said:**
> Slackware [...] does not come with Gnome, Pat V hates it and won't allow Gnome.

The text of the changelog that speaks of this can be seen here:

[http://slackwiki.org/GNOME](http://slackwiki.org/GNOME)

where reasons other than 'hate' are mentioned :-). Gnome can still be used with Slackware, as is pointed out on this page, it is simply not part of the *official* distribution.

Andrew

---

### Post by Maarek Stele on 2009-01-06
I find that Slackware is for a true Linux user that will customize their software to fit their needs and write most of the configurations on their own.  I have "tried" it but always had trouble trying to get an ATI RADEON card to work in Slackware in X windows.

---

### Post by SunnyRabbiera on 2009-01-06
Slackware is the old man on the hill when you think linux, he is odd, he is strange and very... eccentric.
I always thought slack was a good distro, but I am definitely not ready for it!

---

### Post by Vince4Amy on 2009-01-06
> **Maarek Stele said:**
> I find that Slackware is for a true Linux user that will customize their software to fit their needs and write most of the configurations on their own.  I have "tried" it but always had trouble trying to get an ATI RADEON card to work in Slackware in X windows.

Getting ATI Cards to work in Slackware is quite easy, just download the ATI Driver from the ATI website and for simplicity sake save it as installer.run.

Then do enter the following:

```
su
``` - Login as root.

```
sh installer.run --buildpkg Slackware/All
```

Install the two packages that were generated using installpkg and then enter this command to configure X:

```
aticonfig --initial -f
```

Add this to xorg.conf

```
Section "DRI"
Mode 0666
EndSection
```

You can then restart X or reboot.

---

### Post by civillian on 2009-01-06
Slackware, although 'stable' is a bit too outdated for me, and the fact that it is maintained by (primarily) only Patric Volkerding (or whatver he's called) means that when he stops, it may well die (similar to Gentoo's projected decline)...

---

### Post by Vince4Amy on 2009-01-06
> **C!V!NT said:**
> Slackware, although 'stable' is a bit too outdated for me, and the fact that it is maintained by (primarily) only Patric Volkerding (or whatver he's called) means that when he stops, it may well die (similar to Gentoo's projected decline)...

I wouldn't call it outdated (The software packages). None of the packages I use on there are extremely old and some software is updated quicker than Ubuntu for example Thunderbird 2.0.0.19. Also no other distro has given me this much customisability with so much ease. It's also quite difficult to completely mess Slack, most mistakes can be reversed.

Also if Pat ever decided to give up I'm sure there will be someone else willing to take the project up.

---

### Post by kk0sse54 on 2009-01-08
> **C!V!NT said:**
> Slackware, although 'stable' is a bit too outdated for me, and the fact that it is maintained by (primarily) only Patric Volkerding (or whatver he's called) means that when he stops, it may well die (similar to Gentoo's projected decline)...

Gentoo hasn't had a benevolent dictator since 2004 I believe  yet it still around and healthy (despite projected disappearance of the Gentoo Foundation about a two years ago).I think the same will happen with Slackware in that it will be around after Pat ever steps down whener that happens. Otherwise Slackware is hardly dated at all, it uses KDE3 for stability reasons (which I totally agree with) yet also offers packages to install KDE4. Slackware itself isn't built from the bleeding edge but is supposed to provide a solid stable distro. Outside of the very small slackware vanilla repo places like slackbuilds.org provide very up to date slackbuilds for installing additional software. It's not like installing Debian with it's year(s) old software all in the name of stability which is fine if that's what you require.

---

### Post by jrusso2 on 2009-01-08
> **C!oud said:**
> Gentoo hasn't had a benevolent dictator since 2004 I believe  yet it still around and healthy (despite projected disappearance of the Gentoo Foundation about a two years ago).I think the same will happen with Slackware in that it will be around after Pat ever steps down whener that happens. Otherwise Slackware is hardly dated at all, it uses KDE3 for stability reasons (which I totally agree with) yet also offers packages to install KDE4. Slackware itself isn't built from the bleeding edge but is supposed to provide a solid stable distro. Outside of the very small slackware vanilla repo places like slackbuilds.org provide very up to date slackbuilds for installing additional software. It's not like installing Debian with it's year(s) old software all in the name of stability which is fine if that's what you require.

All the people I have known that were Gentoo developers and users have since left.

---

### Post by kk0sse54 on 2009-01-08
> **jrusso2 said:**
> All the people I have known that were Gentoo developers and users have since left.

While I agree that there has been a lot of in fighting over the years between developers and sometimes there seems to be no clear direction, however with weekly stage3 tarballs rolling out and an active forum and IRC I'd say Gentoo is far from dead.

---

### Post by octavianus on 2009-01-11
what is the fundamental difference of Slackware kernals than that of Ubuntu/Debian ?
What about the files hierarchy in Slackware in comparison to Ubuntu/Debian ? 
I can understand that all the control a user enjoy in Slackware is also possible in Ubuntu because Ubuntu is basically made of Linux kernals like Slackare.

---

### Post by kk0sse54 on 2009-01-11
> **octavianus said:**
> what is the fundamental difference of Slackware kernals than that of Ubuntu/Debian ?
What about the files hierarchy in Slackware in comparison to Ubuntu/Debian ? 
I can understand that all the control a user enjoy in Slackware is also possible in Ubuntu because Ubuntu is basically made of Linux kernals like Slackare.

Slackware is one of the only Linux distros to still use the vanilla Linux Kernel and while the same level of control can probably be done in Ubuntu it's much harder since it's covered up. Slackware you are expected to do all your configuration through editing text files so there's no default  GUI tools avaliable to help you because it's designed to be as simple as possible. Thus you almost can't compare the amount of control because they have two different purposes, Slackware aims to adhere to the KISS philosophy while Ubuntu attempts to ease the transition of newcomers to linux by attempting to provide a user friendly distro.

---

### Post by OverlordManny on 2009-01-22
Well one difference in {U,K,X}buntu and Slackware is the boot up and it's configuration. Ubuntu (and it's derivatives) as well as many other *nix distros use SysV style boot configs, while Slack uses BSD style by default (I say default because the beauty of Slackware is it doesn't make you conform to anything... at all!). While this is not really a major thing, it really confused me when I first started using Slackware since I was used to SysV style. 

   I need to say I think Ubuntu is great; it's what helped me enter the linux/gnu world as my main OS and I still use it on 2 of my machines, but I feel I've out grown it fast. I think that the comparison between the Ubuntu and Slackware is almost apples to oranges. Slackware has a niche audience, it's for people who want to "play", explore, and configure to their hearts content, that's not to say it isn't usable as a primary desktop though. If you like to be in control of everything your machine does, want to and are willing learn how linux/gnu OS's work, or find yourself with a constant desire to "tweak something" (and I do) then Slack is for you. If you want to have a system that "just works" and you don't care how it works or you don't care what apps open your files as long as they open, then I'd say stick with Ubuntu. It's a personal choice that you have to make for yourself.

Just my 2 cents.

---

### Post by OverlordManny on 2009-01-22
Oh one more thing. If your intentions are to learn linux/gnu then get away from GUI based OS's like Ubuntu, Suse, Mandriva. etc. Drop yourself into a CLI environment and fight your way out, lol. A couple of weeks with Slackware, Gentoo, or LFS (if you're brave and REALLY wanting to learn) will increase your CLI skills quickly. You can use those GUI based OS's for years and never learn anything. Really!

---

