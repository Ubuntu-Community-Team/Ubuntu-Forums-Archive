---
title: "What distro is for me? I know I actually don't belong here"
date: 2009-03-25
forum: The Cafe
---

### Post by Neo_The_User on 2009-03-25
Hi. I compile everything from source and everything I do is not even remotely close the the "Ubuntu way." Here is what I would like:

A building system that fetches the source code and compiles everything for you
Suited for minimalists. Everything you have to build yourself.
I don't need a GUI at all.
I don't care how long it takes.

I know about Gentoo and LFS but I don't know how to use either of them very well. I find too much pointless docs in the handbooks for LFS and Gentoo and its frustrating. I don't want any kind of encrypted file system or any security at all really. Security is not my concern one bit. Is FreeBSD for me? I was really considering it awhile a go. Or OpenBSD or NetBSD.

I would seriously use Gentoo if I knew how to use emerge but I'm terrible at emerge. Does anybody know what FreeBSD is like? Like the actual preformace.

Here are my specs:

1 GB RAM
Some old ASUS Motherboard
AMD Athlon XP 2000+ Socket A (492 or something)
ATi Radeon 9800 PRO
350 Watt Power supply
26'' SOYO Windows Vista Certified 1920x1200 Progressive Scan Pearl series or something like that
VIA AC97 sound card (old)
80GB SATA Hard Drive

---

### Post by RiceMonster on 2009-03-25
Maybe try Lunar or Crux? They're source distros too.

---

### Post by Twitch6000 on 2009-03-25
You might want to try a minimal install of ubuntu.

Or try arch linux.

Slackware is another one that came to mind aswell <.<.

---

### Post by DeadSuperHero on 2009-03-25
I hear Slackware is a GREAT source distro. 

Or, if you like compiling things on a mostly Free Software system, gNewSense is one that I recommend, although you won't be able to get proprietary drivers to work.

---

### Post by RiceMonster on 2009-03-25
> **Twitch6000 said:**
> You might want to try a minimal install of ubuntu.

Or try arch linux.

Arch is a binary distro, though. It's got a build system, but if you want to compile everything, I'd recommend something else.

---

### Post by Chemical Imbalance on 2009-03-25
As OP mentioned, Slackware

---

### Post by Neo_The_User on 2009-03-25
Wow! gnewsense looks so awesome! based on debian and ubuntu, source based. Thanks a million!

My fav part:

"and for developers &#8212; the full GNU developer toolchain, GNU Emacs, a variety of compilers, debuggers and more."

I'm going to install right now!

---

### Post by Virgo53 on 2009-03-25
How about "Linux From Scratch"? :)

[http://www.linuxfromscratch.org/]("http://www.linuxfromscratch.org/")

Oops! Sorry 'bout that!

---

### Post by kk0sse54 on 2009-03-25
> **Neo_The_User said:**
> Hi. I compile everything from source and everything I do is not even remotely close the the "Ubuntu way." Here is what I would like:

A building system that fetches the source code and compiles everything for you
Suited for minimalists. Everything you have to build yourself.
I don't need a GUI at all.
I don't care how long it takes.

I know about Gentoo and LFS but I don't know how to use either of them very well. I find too much pointless docs in the handbooks for LFS and Gentoo and its frustrating. I don't want any kind of encrypted file system or any security at all really. Security is not my concern one bit. Is FreeBSD for me? I was really considering it awhile a go. Or OpenBSD or NetBSD.
How is documentation pointless? If you seriously think Gentoo has too much pointlesss docs then you need to stop right now and think if you really want to run a source based distro. As for BSD, I recommend all of them although I use NetBSD myself.

> I would seriously use Gentoo if I knew how to use emerge but I'm terrible at emerge. Does anybody know what FreeBSD is like? Like the actual preformace.
If you can do apt-get in Ubuntu or make install clean then you could very easily do emerge -av <package>. The tricky part for the first time Gentoo user is getting used to the concept of USE flags. This is where those useless docs come in handy :roll:

Otherwise I highly recommend both Gentoo and NetBSD, and you might also want to look into Crux. Arch linux can be a great system to if you use yaourt  and abs.

---

### Post by perlluver on 2009-03-25
Another vote for Slackware, you can get scripts from [http://www.slackbuilds.org](http://www.slackbuilds.org), or you can compile it yourself.  It will install with Fluxbox, Blackbox, or if you just want a terminal it is installed to just start up to a terminal.  I am currently running and love it.

---

### Post by Neo_The_User on 2009-03-25
...gNewSense kept giving me squashfs errors. ugh.

slackware i cant use because i only have CDs and i cant install the boot loader with just the CDs. as for emerge -av, I was more so talking about the build-dep command in debian. i believe -av is just to install. I used to use arch but i cant compile mesa and all that from git. crux... hmm. crux? like arch probably so i won't like it. ill burn gnewsense one more time and if it still doesn't work, i'll just switch to gentoo and learn how everything works inside and out.

---

### Post by kk0sse54 on 2009-03-25
> **Neo_The_User said:**
> ...gNewSense kept giving me squashfs errors. ugh.

slackware i cant use because i only have CDs and i cant install the boot loader with just the CDs.
If you are referring to the Lilo bootloader then yes you can install it perfectly fine using just CDs
>  as for emerge -av, I was more so talking about the build-dep command in debian.
emerge --onlydeps should do the trick available from the ever ready emerge man document. 
>  I used to use arch but i cant compile mesa and all that from git. crux... hmm. crux? like arch probably so i won't like it. .
What exactly were you having problems with, you should be able to manually compile perfectly fine from git. And no Crux is not like Arch.

---

### Post by cardinals_fan on 2009-03-25
**CRUX**: CRUX really sounds perfect for you.  It is extremely simple and requires the user to do everything themselves.  I have used CRUX a good deal and was very impressed by the elegance and customizability.  It is source-based (though the install is binary - a good thing in my book, as you can always recompile it all later).  CRUX is a good distro to play with kernel compilation on.  You'll love the useful but concise CRUX Handbook.  CRUX is a blank slate; do with it what you will.
[B]
NetBSD[/B]: My overall #1 operating system.  NetBSD is overwhelmingly stable, simple, and powerful.  This system is designed for the long haul.  The emphasis on portability means that NetBSD focuses on code correctness and simplicity.  Pkgsrc, the software installation system, is source-based, though there are lots of binaries available.  It takes a certain type of person to appreciate NetBSD, but those of us who do almost never find something that they like more.  NetBSD 5 looks like it will be a great release.
[B]
SliTaz[/B]: If you don't need a GUI and compile everything, why would I suggest an LXDE system with binary packaging?  Answer: because SliTaz has the most concise and elegant system design of any *Linux* distro I've used (NetBSD is still tops).  You can build your own packages from source with Tazwok or just compile normally - either way, the system has almost no cruft or fancy tools to get in your way.  This distro is great for minimalists or those who want a system that they can tweak without breaking.  It has become a comfortable #2 for me.

---

### Post by Neo_The_User on 2009-03-25
NetBSD vs FreeBSD vs OpenBSD. I can't figure it out. And slitaz... I actually have that burned somewhere... heh

Does anybody know the difference between the 3 BSDs? What are the advantages and disadvantages? I'm not wasting my last 10 CDs or so. :/ Just one perfect distro that I never used before (i pretty much hate them all so far the ones i've tested.)

Ones I tested:

Ubuntu, Xubuntu, Kubuntu (6.06 - 9.04) - My favorite is Xubuntu and its the one I hate the least. I only hate like... 1 / 10 of it.
SliTaz
Fedora 4 - 11 Alpha
Arch Linux
Red Hat (When it was free)
OpenSuse 10.2 - 11.1
Gentoo
Slackware
Debian etch and a half - experimental

---

### Post by bhishan on 2009-03-25
[http://ubuntuforums.org/showthread.php?t=1106404](http://ubuntuforums.org/showthread.php?t=1106404)

---

### Post by Skripka on 2009-03-25
> **Neo_The_User said:**
> NetBSD vs FreeBSD vs OpenBSD. I can't figure it out. And slitaz... I actually have that burned somewhere... heh

Does anybody know the difference between the 3 BSDs? What are the advantages and disadvantages? I'm not wasting my last 10 CDs or so. :/ Just one perfect distro that I never used before (i pretty much hate them all so far the ones i've tested.)

Ones I tested:

Ubuntu, Xubuntu, Kubuntu (6.06 - 9.04) - My favorite is Xubuntu and its the one I hate the least. I only hate like... 1 / 10 of it.
SliTaz
Fedora 4 - 11 Alpha
Arch Linux
Red Hat (When it was free)
OpenSuse 10.2 - 11.1
Gentoo
Slackware
Debian etch and a half - experimental

Here's a linky to a forum no one is at all familiar with....

[http://grubbn.org/otheros/forumdisplay.php?fid=13](http://grubbn.org/otheros/forumdisplay.php?fid=13)

---

### Post by MikeTheC on 2009-03-25
Why not Gentoo? I'm told its "Emerge" utility is the bomb.

---

### Post by Neo_The_User on 2009-03-25
> **bhishan said:**
> [http://ubuntuforums.org/showthread.php?t=1106404](http://ubuntuforums.org/showthread.php?t=1106404)

just so you know, i'm not a windows user at all. never have been, never will be.

ahahaha Skripka its funny. i found 3 people already that go to that forum that posted here. HAHAHA!!

MikeTheC, emerge is... i perfer ./configure --prefix =/usr, make, sudo make install reboot method better.

---

### Post by cardinals_fan on 2009-03-25
> **MikeTheC said:**
> Why not Gentoo? I'm told its "Emerge" utility is the bomb.
Literally.

Anyway, I'll try to provide some quick info on the BSDs.  You can get more detail at the link above.

FreeBSD: The most established and most popular BSD.  It focuses on performance, and is therefore only available for a few architectures.  Stability is also great.  The Ports collection (source-based) is gigantic, with at least 18,000 ports.  FreeBSD is popular both on desktops and servers and has the best software support of the lot (Opera and others write FreeBSD versions).  FreeBSD also has lots of derivatives.  The two best-known projects are DesktopBSD and PC-BSD.  Both provide a KDE desktop over FreeBSD and target users who want an out-of-the-box GUI.

NetBSD: My personal favorite.  Focuses primarily on portability.  If you don't need to run it on a toaster, why do you care?  Because in order to be portable, NetBSD is extremely simple and aims for code-correctness.  Pkgsrc (also source-based) has a large number of packages available (~7000-9000 with work-in-progress packages).  While FreeBSD is distributed on large CD/DVD images, NetBSD is just one minimal base system to which you can add.

OpenBSD: Aggressively targets security with frequent code audits and a high level of paranoia in the default base system.  Has fewer packages than the others and focuses on binaries, though you can of course still compile apps yourself.  Holds to philosophy of free/open source apps very strictly.  Distrubuted in one lightweight base iso, like NetBSD (from which it is distantly descended).

DragonFlyBSD: The newest major BSD, DragonFlyBSD is a revolutionary project.  It has aggressive goals and is in rapid flux.  The leader, Matthew Dillon, is a former FreeBSD dev who forked the project to focus on his own ideas for SMP support and multithreading.  DragonFly is a powerful OS for those who want to harness the full power of their computers.  The new filesystem, HAMMER, has many of the features in the much-vaunted ZFS and is a fascinating project.  Uses Pkgsrc from NetBSD, but with fewer packages.

All the BSDs are capable of running most Linux apps through Linux compat layers (better than WINE but not as reliable as native), and you can of course compile POSIX-compliant apps natively.

---

### Post by Neo_The_User on 2009-03-25
I don't need any bit of portability. I think i'll go with FreeBSD. Is it good for development purposes and compiling? If so, I'll take my Mesa dev projects to FreeBSD and learn BSD for once.

...if only gnewsense or whatever worked

---

### Post by kk0sse54 on 2009-03-25
> **Neo_The_User said:**
> NetBSD vs FreeBSD vs OpenBSD. I can't figure it out. And slitaz... I actually have that burned somewhere... heh

Does anybody know the difference between the 3 BSDs? What are the advantages and disadvantages? I'm not wasting my last 10 CDs or so. :/ Just one perfect distro that I never used before (i pretty much hate them all so far the ones i've tested.)


Who says you need to use cds? Try them out in a virtual machine through vmware.

---

### Post by hewbert on 2009-03-25
Well, I've been a FreeBSD users for a few years now.  You can do a very minimal install and build from there.  Ports are a snap.  Things make sense.  Kernel is easy as hell to compile, comparatively.  I've always felt more... comfortable in the BSD community too.

That's my 2 cents.

---

### Post by cardinals_fan on 2009-03-26
> **Neo_The_User said:**
> I don't need any bit of portability. I think i'll go with FreeBSD. Is it good for development purposes and compiling? If so, I'll take my Mesa dev projects to FreeBSD and learn BSD for once.

...if only gnewsense or whatever worked
As I already explained, the tasks necessary to achieve portability (code cleanliness + correctness) benefit you anyway.  However, FreeBSD is a very worthy choice, and I think you'll like it - if your hardware works.  Many people develop on FreeBSD, and it is a fine platform.  Just remember that it can be a bit different and requires an open mind.

I don't see why you would want gnewsense, since it's just Ubuntu with nothing proprietary.

---

### Post by Neo_The_User on 2009-03-26
FreeBSD it is!

---

### Post by smartboyathome on 2009-03-26
> **Neo_The_User said:**
> NetBSD vs FreeBSD vs OpenBSD. I can't figure it out.

FreeBSD: Tries to be easiest.
NetBSD: Tries to be the most portable (they are so portable that they are available on a toaster!).
OpenBSD: Tries to be the most secure.

Code is shared between the three.

---

### Post by Neo_The_User on 2009-03-26
What do you mean "toaster?"

---

### Post by Delever on 2009-03-26
You may love AUR build system in Arch linux, which can download and compile things, and integrates that into package management well. However it has tons of software already packaged. 

[http://aur.archlinux.org/index.php](http://aur.archlinux.org/index.php)

It was fun for me, but I simply don't have enough time...

EDIT: ah, well, you even more hardcore... good luck then :D

---

### Post by sertse on 2009-03-26
There's no hidden meaning in toaster

It's just that NetBSD's code is so portable you can just as easily install it on a toaster...those things you put bread in. ;)

---

### Post by smartboyathome on 2009-03-26
> **Neo_The_User said:**
> What do you mean "toaster?"

I mean an actual toaster, something you toast bread in. See [here]("http://www.embeddedarm.com/software/arm-netbsd-toaster.php") to see that toaster. :)

---

### Post by Daisuke_Aramaki on 2009-03-26
Crux would be ideal. If you want to use another source based distro replacement for gentoo, then you should seriously consider Lunar or SourceMage. Both Lunar, and SourceMage were forked out of Sorcerer Linux. The idea of casts and spells are still the driving force behind SourceMage, for instance. But setting up Sorcerer Linux in the beginning will be quite a challenge. If you are up to it, then go ahead with Sorcerer directly. Otherwise give Lunar Linux a shot! Most of my boxes run Lunar, Sorcerer and FreeBSD these days. And my main work machines are powered by Lunar and Sorcerer. 

Sorcerer's Grimoire (package db) gets updated almost every two days. Lunar's moonbase gets updated once a week. Same is with Sourcemage. If you intend to give any of these distros a shot, you can get in touch with me in case there is any problem setting them up!

Good Luck!

---

### Post by Zlatan on 2009-03-26
> **Neo_The_User said:**
> Hi. I compile everything from source and everything I do is not even remotely close the the "Ubuntu way." Here is what I would like:

A building system that fetches the source code and compiles everything for you
Suited for minimalists. Everything you have to build yourself.
I don't need a GUI at all.
I don't care how long it takes.

I know about Gentoo and LFS but I don't know how to use either of them very well. I find too much pointless docs in the handbooks for LFS and Gentoo and its frustrating. I don't want any kind of encrypted file system or any security at all really. Security is not my concern one bit. Is FreeBSD for me? I was really considering it awhile a go. Or OpenBSD or NetBSD.

I would seriously use Gentoo if I knew how to use emerge but I'm terrible at emerge. Does anybody know what FreeBSD is like? Like the actual preformace.

Here are my specs:

1 GB RAM
Some old ASUS Motherboard
AMD Athlon XP 2000+ Socket A (492 or something)
ATi Radeon 9800 PRO
350 Watt Power supply
26'' SOYO Windows Vista Certified 1920x1200 Progressive Scan Pearl series or something like that
VIA AC97 sound card (old)
80GB SATA Hard Drive

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)
:)

---

### Post by binbash on 2009-03-26
gentoo for sure.

---

### Post by chris200x9 on 2009-03-26
> **binbash said:**
> gentoo for sure.

+1

---

### Post by Neo_The_User on 2009-03-26
I switched to ArchLinux and I'm using makepkg and ABS and all this stuff 24/7, I love it. It's like Ubuntu sort of except with a different package manager and compiling from source is actually supported!!! I love the makepkg system as you can compile from source, then run it through the package manager (pacman) to check for dependency errors. It's so totally awesome!

...Now compiling mesa from git on arch is going to be the hardest part of all. :/

FYI i did not ask for any support for arch linux as i will figure the mesa thing out myself, resulting in me not going off topic.

Thanks all.

---

