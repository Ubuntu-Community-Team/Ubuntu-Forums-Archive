---
title: "apt-get vs. pacman"
date: 2008-02-07
forum: The Cafe
---

### Post by sunexplodes on 2008-02-07
I'm thinking of giving Arch a try, but I was wondering about the package manager.

I've only ever used *ubuntu, so i'd like a bit of info on the big differences between the two. 

Thanks.

---

### Post by SupaSonic on 2008-02-07
I just tied Arch yesterday. Pacman seems ok, not much different from apt from what I've seen. Possibly even simpler, becuase apt syntax might be confusing for some - apt-get / aptitude /dpkg vs. pacman.

---

### Post by epimer on 2008-02-07
> **sunexplodes said:**
> I'm thinking of giving Arch a try, but I was wondering about the package manager.

I've only ever used *ubuntu, so i'd like a bit of info on the big differences between the two. 

Thanks.

They're broadly similar, but as stated above, syntax is perhaps a little simpler. 'pacman -Syu' to do a full upgrade, 'pacman -S foo' to install, 'pacman -Ss foo' to search, 'pacman -Rs foo' to remove package and unused remaining dependencies...

A big advantage comes through using a wrapper such as yaourt, which gives access to the AUR (Arch User Repository) as if it was just another repo enabled with pacman. So 'yaourt -Ss foo' will search through the AUR as well as your other enabled repos, and 'yaourt -S foo' will download the source, build it and install it (with a few prompts) straight away. It's a brilliant system. Easy access to packages as bleeding edge as you like.

I can't recommend Arch (+ KDEmod for a fellow KDE tweaker such as yourself :) ) highly enough for people who want a bit more control and a bit less bloat than a K/Ubuntu install. Switched months ago and don't see myself ever going elsewhere.

---

### Post by jaytek13 on 2008-02-07
> **epimer said:**
> 
I can't recommend Arch (+ KDEmod for a fellow KDE tweaker such as yourself :) ) highly enough for people who want a bit more control and a bit less bloat than a K/Ubuntu install. Switched months ago and don't see myself ever going elsewhere.

I tried it for a while and I just couldn't get into it. I don't mind tweaking, in fact I like to do it with things that I see as being useful, but having to spend hours searching through documentation just to get the fonts to look decent isn't my idea of learning. 

I'd love a distro that left all the control up to you but didn't insist your doing EVERYTHING. I will admit it was nice to have KDE set up and experience something like konqueror starting up instantly... but that wasn't enough to convince me to stay.

---

### Post by epimer on 2008-02-07
> **jaytek13 said:**
> I tried it for a while and I just couldn't get into it. I don't mind tweaking, in fact I like to do it with things that I see as being useful, but having to spend hours searching through documentation just to get the fonts to look decent isn't my idea of learning. 

I'd love a distro that left all the control up to you but didn't insist your doing EVERYTHING. I will admit it was nice to have KDE set up and experience something like konqueror starting up instantly... but that wasn't enough to convince me to stay.

Each to their own, of course. The point of Arch is to leave everything to the user, and that's what I like about it.

As per fonts, I simply followed the instructions in the wiki and I was all set. YMMV.

---

### Post by forrestcupp on 2008-02-07
> **epimer said:**
> They're broadly similar, but as stated above, syntax is perhaps a little simpler. 'pacman -Syu' to do a full upgrade, 'pacman -S foo' to install, 'pacman -Ss foo' to search, 'pacman -Rs foo' to remove package and unused remaining dependencies...
Maybe it *is* simpler, but it doesn't sound like it from what you say.  How is 'pacman -S foo' simpler than 'apt-get install foo'?  With pacman, I have to learn and remember that -S means install.  With apt-get, I have to remember that install means install.

---

### Post by epimer on 2008-02-07
> **forrestcupp said:**
> Maybe it *is* simpler, but it doesn't sound like it from what you say.  How is 'pacman -S foo' simpler than 'apt-get install foo'?  With pacman, I have to learn and remember that -S means install.  With apt-get, I have to remember that install means install.

That example is fair enough. But I find it easier to do 'pacman -Syu' than 'apt-get update && apt-get upgrade' (or even ...apt-get dist-upgrade' at the end  too, e.g. for kernel updates). Searching from within apt-get is, imo, clunky too, with it being 'apt-cache search' and not 'apt-get search'. IIRC, aptitude is a bit easier because it's just 'aptitude install foo' or 'aptitude search foo'.

I'm not knocking apt-get as a package manager. For reasons of sheer laziness, I still have a Feisty server running, and I find using apt-get to install new programs on it just a little bit clunkier than using pacman on my laptop.

---

### Post by Miguel on 2008-02-07
Pacman is OK. It's much better than what I remember from rpm (my first distro was mandrake 10.0) but it's still not as cool as apt(itutde).

What's really great in Arch is AUR+Pacman, which gives you tremendous power to build lots of packages easily. Furthermore, having a rolling release distro means you're not looking forward as much for the next big release. Another bloody cool thing about arch is the ease to configure the services you want running or not. 

In my experience, however, Arch has also a few cons. First of all, you have to know what you are doing. Else, you risk having a system with the latest bash and nothing else. Also, the general quality of its packages seem **to me** lower than those of ubuntu, at least the gnome packages.

---

### Post by Arkenzor on 2008-02-07
I myself just switched to Arch, pacman seems pretty ok for now. I miss the gui though, it's much harder to find a package for a specific function without one (with Synaptic simply search for what you want - system monitor, bittorent, x*%&$ reader, whatever and make your choice).

As for everything else, I find Arch much easier to learn than any other user-centric (as they say) distro I've ever tried, mostly because their wiki is actually helpful (really).

---

### Post by bryonak on 2008-02-11
Just a quick line concerning aptitude / apt-get.
IMO the following should be done by default:
```

sudo mv /usr/bin/apt-get /usr/bin/apt-get-SUSPENDED &&
echo echo just use aptitude! > /usr/bin/apt-get &&
chmod 755 /usr/bin/apt-get

```

 ;)

same for apt-cache, -config, -key, -mark and all those other redundant tools!

---

### Post by Kingsley on 2008-02-11
> **bryonak said:**
> Just a quick line concerning aptitude / apt-get.
IMO the following should be done by default:
```

sudo mv /usr/bin/apt-get /usr/bin/apt-get-SUSPENDED &&
echo echo just use aptitude! > /usr/bin/apt-get &&
chmod 755 /usr/bin/apt-get

``` ;)

same for apt-cache, -config, -key, -mark and all those other redundant tools!
ooooh
apt-get got suspended. I hope his mother doesn't find out.

---

### Post by Tenken on 2008-02-11
Pacman is really easy to use, but so is apt-get. It's really 6 of one half dozen of the other. After setting up Arch, I found myself typing pacman  in Ubuntu though :).

---

### Post by fwojciec on 2008-02-11
Most people who talk about pacman forget that pacman package actually includes another application called makepkg.  This app is used to make all packages in Arch linux -- you run makepkg in a directory containing a script called PKGBUILD that contains specific information on how to pull the sources and compile them into a package that can be later installed/managed with pacman.  Since the PKGBUILDs for all Arch packages are available through something called ABS (Arch Build System) the users have full control over how the packages they use are compiled since when they don't like the default provided by the developers they can always edit the appropriate PKGBUILD and recompile the package with their specific tweaks and optimizations.  The makepkg tool also enables the community to contribute to the distro in a meaningful way -- by sharing PKGBUILDs that can be used by other users (this is called AUR -- the Arch User Repository).

To me this is the greatest advantage of pacman/makepkg way of doing things when compared to Debian tools and apt-get.  In Debian (and also Ubuntu) making a package is an involved and arcane process that's always been beyond my comprehension and abilities -- in Arch building my own packages is much, much easier.

---

### Post by SunnyRabbiera on 2008-02-11
Yeh but pacman has its downsides... I really dont like it, it sometimes seems slow and seems to have a mind of its own.

---

### Post by fwojciec on 2008-02-12
> **SunnyRabbiera said:**
> Yeh but pacman has its downsides... I really dont like it, it sometimes seems slow and seems to have a mind of its own.

Everyone is entitled to their own opinion, I suppose, but you should really give something more than vague assertions in support of your strong claims (that strike me as entirely unfounded.)

Speed -- whatever might be said about pacman's downsides its speed of operation cannot be raised as an argument against it.  Here is a little example of a typical operation -- timed:
```
$ time yes | sudo pacman -S terminal
resolving dependencies...
looking for inter-conflicts...

Targets: vte-0.16.12-1  hicolor-icon-theme-0.10-1  terminal-0.2.8-1  

Total Download Size:    1.07 MB

Proceed with installation? [Y/n] :: Retrieving packages from extra...
 vte-0.16.12-1-x86_64     749.1K  187.2K/s 00:00:04 [###################################################################################] 100%
 hicolor-icon-theme-0...    7.9K   19.6K/s 00:00:00 [###################################################################################] 100%
 terminal-0.2.8-1-x86_64  343.3K  163.4K/s 00:00:02 [###################################################################################] 100%
checking package integrity...
(3/3) checking for file conflicts                   [###################################################################################] 100%
(1/3) installing vte                                [###################################################################################] 100%
(2/3) installing hicolor-icon-theme                 [###################################################################################] 100%
(3/3) installing terminal                           [###################################################################################] 100%

real    0m8.940s
user    0m0.090s
sys     0m0.167s
$ time yes | sudo pacman -Rscn terminal
loading package data... done.
checking dependencies...

Targets: terminal  vte  hicolor-icon-theme  

Do you want to remove these packages? [Y/n] 
(1/3) removing terminal                             [###################################################################################] 100%
(2/3) removing vte                                  [###################################################################################] 100%
(3/3) removing hicolor-icon-theme                   [###################################################################################] 100%

real    0m0.222s
user    0m0.030s
sys     0m0.100s
```

The first operation involves resolving dependencies, checking for conflicts with other packages, pulling the necessary packages from the repo (1MB of packages in this case) and installing the packages -- the total time is about 9 seconds.  That's pretty good, I think.

The second operation involves removing terminal and the packages that were installed as its dependencies, the configuration files of all the packages involved and so forth.  Again -- pacman needs to figure out which packages ought to be removed since I'm only specifying the "terminal" package in the command.  The total time for that operation is about a quarter of a second.  That's certainly not slow.

Here is how long it takes to check if there are any updates for my system (note that I'm using 5 different repositories, which is more than most users would use):
```
$ time sudo pacman -Syu
:: Synchronizing package databases...
 testing is up to date
 core is up to date
 extra is up to date
 community is up to date
 filip is up to date
:: Starting full system upgrade...
 local database is up to date

real    0m2.582s
user    0m0.097s
sys     0m0.150s
```
I think I've made my point here.

My sense is that what you might have been referring to when you had mentioned "slow" was not the speed of pacman itself but the download speed of the mirror you happened to be using (you can always use a different one, you know) -- that would be my guess.

As for pacman "having a mind of its own" -- well, software doesn't have a mind.  The subjective perception of it having a mind can be attributed to either of two things -- it can either be the result of bugs in the software or it can be the result of the user's misuse of the software.  There are certainly bugs in pacman, but none of them are of the kind that would result in frequent unpredictable behavior.  My personal experience with this program, in fact, makes me consider it a precision tool that that does exactly what it is asked to do and performs everything in a wonderfully elegant, logical and transparent manner.

---

### Post by bwtranch on 2008-02-16
> **SunnyRabbiera said:**
> Yeh but pacman has its downsides... I really dont like it, it sometimes seems slow and seems to have a mind of its own.
It's as slow as you have equipment for, I think. Mine usually runs about 990Kbits/s. And maybe it needs a "mind".

---

### Post by k2t0f12d on 2008-02-16
I would have tried to use [COLOR="Blue"][FONT="System"]dpkg[/FONT][/COLOR] to manage the GNU/Linux system whose build system I am designing.  Except, IIRC building [FONT="System"][COLOR="Blue"]dpkg[/COLOR][/FONT] and the software related to it and getting it to work is an unimitigated migraine from hell.  [COLOR="Blue"][FONT="System"]pacman[/FONT][/COLOR] only requires the [FONT="System"][COLOR="Blue"]libtar[/COLOR][/FONT] libraries to build, automatically makes a static and dynamically linked binary, and has a [FONT="System"][COLOR="Blue"]bash[/COLOR][/FONT] shell scripted package builder with which to create packages from source.  If I weren't dedicated to creating everything from source and learning how every single part of the GNU operating system *plus* Linux works, I'd definately give Arch a try.

---

### Post by eljoeb on 2008-02-16
I like how pacman can send you messages after you install stuff.  It can send you messages about other important packages for the program or other configuration issues.  I jumped ship on Ubuntu/Debian pretty quick, so I'm not sure apt does that.

As for the simplicity of commands for each, that's probably the lamest reason to dislike one over the other.

---

### Post by ice60 on 2008-02-16
> **Arkenzor said:**
> I miss the gui though, it's much harder to find a package for a specific function without one (with Synaptic simply search for what you want - system monitor, bittorent, x*%&$ reader, whatever and make your choice).i'm sure i saw a post in the arch forums about a new frontend someone just made, it was about 10 days a go. i don't use arch so i didn't pay much attention to it, i was looking for something else at the time.

---

### Post by Kareeser on 2009-05-09
Hate to drag up an old thread, but having tried arch for the first time yesterday, I've noticed that pacman seems slower in initiating the download of packages.

As in, after downloading a package, it will stall for a fraction of a second while preparing the second download. As far as I know, apt-get downloads packages quickly, with no "downtime" in between.

Now, this might actually all be explained by using a faster mirror, I'm not sure. The normal mirror I use in Ubuntu does't host arch repositories, unfortunately.

---

### Post by RiceMonster on 2009-05-09
Pacman is one of the reasons I use arch. It's simple and does everything I could ever want. The build system for packages is a huge added bonus, because it's so easy to create a package. That's why there's so many additional packages in the AUR. Plus, it doesn't puke all over your terminal like apt-get or especially aptitude does.

Still, they're both good package managers as it is.

---

### Post by Skripka on 2009-05-09
> **Kareeser said:**
> Hate to drag up an old thread, but having tried arch for the first time yesterday, I've noticed that pacman seems slower in initiating the download of packages.

As in, after downloading a package, it will stall for a fraction of a second while preparing the second download. As far as I know, apt-get downloads packages quickly, with no "downtime" in between.

Now, this might actually all be explained by using a faster mirror, I'm not sure. The normal mirror I use in Ubuntu does't host arch repositories, unfortunately.

I'd say try a different mirror.  Pacman is quite speedy here

---

### Post by HeadHunter00 on 2010-06-09
i used arch linux for a while. its pretty good, but some things i just couldnt seem to get to work, so i switched back to ubuntu again. what i liked about pacman was that you could delete the exclusive lock and it wont give an error like dpkg.

---

### Post by smellyman on 2010-06-09
Arch and pacman are great, but  I use Arch mostly for fun.  More of a testing ground of trying different DE's, WM's, DM's etc........

---

### Post by K.Mandla on 2010-06-09
[QUOTE=Wil Shriner]I want to die in my sleep like my grandfather ... not screaming and yelling like the passengers in his car.[/QUOTE]
Thread closed. Necromancy, twice over.

---

