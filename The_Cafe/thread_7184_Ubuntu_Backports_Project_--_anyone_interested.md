---
title: "Ubuntu Backports Project -- anyone interested?"
date: 2004-12-04
forum: The Cafe
---

### Post by jdong on 2004-12-04
Hey guys, I'm planning to start a 'backports' project for Ubuntu -- but only provide packages for *desktop* users, who constantly demand new versions of Firefox, Thunderbird, K3b and such!

I do not plan anything as far as servers, X, major apps (gnome/kde), etc --- those are best left to the Ubuntu team.


Would anyone be interested in helping me package?

---

### Post by TravisNewman on 2004-12-04
Nice idea! If I knew how to package I would ;)

---

### Post by mark on 2004-12-05
[QUOTE=jdong]Hey guys, I'm planning to start a 'backports' project for Ubuntu -- but only provide packages for *desktop* users, who constantly demand new versions of Firefox, Thunderbird, K3b and such!

I do not plan anything as far as servers, X, major apps (gnome/kde), etc --- those are best left to the Ubuntu team.


Would anyone be interested in helping me package?[/QUOTE]jdong - I don't know how to package, but I guess I could learn - or, I could be a "test-case" for *your* packages - I have a history of breaking stuff...<g>

---

### Post by poofyhairguy on 2004-12-05
[QUOTE=jdong]Hey guys, I'm planning to start a 'backports' project for Ubuntu -- but only provide packages for *desktop* users, who constantly demand new versions of Firefox, Thunderbird, K3b and such!

I do not plan anything as far as servers, X, major apps (gnome/kde), etc --- those are best left to the Ubuntu team.


Would anyone be interested in helping me package?[/QUOTE]

Great idea. The community thanks you!

---

### Post by jdong on 2004-12-05
yay, time to bug sourceforge for free stuff!

---

### Post by kastorff on 2004-12-05
Very good idea...as Hoary diverges more and more from Warty, it's far too easy to break Ubuntu Linux trying to get the latest versions of a few key apps.

---

### Post by stoneguy on 2004-12-05
Not sure just how I could fit in, but am interested.

---

### Post by HiddenWolf on 2004-12-05
Oh, that just might persuade me not to upgrade from hoary to the next unstable release, if you could make this work.

I don't like development releases, but I'd hate to be stuck with some package for 6 months if something better is available. :-)

---

### Post by jdong on 2004-12-05
It's definitely going to be a community-driven project -- you guys tell me what packages you want!


I'll start filing the Sourceforge paperwork tomorrow. Hopefully, they'll approve the project!

---

### Post by Infatuated_iPod on 2004-12-05
I would love to help in any way that i could, i am by all means a newbie, but i want to help in any way possible! :)

---

### Post by TravisNewman on 2004-12-05
jdong, something that is obviously necessary: testing.
It would be good to have an installation of the current stable release and the current development release, to see how they work in both. For some this is a bit of a hassle, if only one physical machine is available. Is there any way to set up a chrooted install of Ubuntu as it is now? I know how in Gentoo, since you do everything manually, but most definitely not in Ubuntu.

I'd definitely set that up on my machine if anyone knows how, and once it goes live I'll write up a how-to for setting up the chroot environment for the backports project specifically

---

### Post by jdong on 2004-12-05
chroots are chroots. They work the same way from distro to distro.


It IS an excellent idea. I'll probably have 3+ chroots when I start the project off..


P.S. Experience... Don't worry about it! I'm cramming the Debian Maintainer's guide and some APT repository howto's right now! LOL

---

### Post by TravisNewman on 2004-12-05
So if chroots are chroots, how do you install Ubuntu into the directory you want to chroot into? With Gentoo, doing it all manually, it's done exactly the same. Since there's an installer that you have to boot off of, how do you tell the installer to install to a different directory?

Well, I'll do some research when I get some free time, or start another topic, as this isn't the best place for it.

---

### Post by jdong on 2004-12-06
[QUOTE=panickedthumb]So if chroots are chroots, how do you install Ubuntu into the directory you want to chroot into? With Gentoo, doing it all manually, it's done exactly the same. Since there's an installer that you have to boot off of, how do you tell the installer to install to a different directory?

Well, I'll do some research when I get some free time, or start another topic, as this isn't the best place for it.[/QUOTE]

well, why not use rsync -avx / . to copy over the entire tree?

You might have to do a pointless mount --bind chroot_dir new_chroot_dir, just to create a new filesystem for rsync to skip!

---

### Post by jdong on 2004-12-06
New Projects Pending Review

    * Ubuntu Backports Project (UNIX name: ubuntu-bp, registered 2004-12-06 11:56)
      Number of business days registration has been pending: 0
      It may take up to 2 business days for new project registrations to be processed.



Cross our fingers!!

---

### Post by ubuntu-geek on 2004-12-06
Awesome Idea.. I'm in the game...

---

### Post by Alessio on 2004-12-06
[QUOTE=ubuntu-geek]Awesome Idea.. I'm in the game...[/QUOTE]
 Me too, but you must do an how-to for explain it :) I'm waiting..

---

### Post by jdong on 2004-12-06
Once the SF project is approved, I'll post site docs on how to backport packages...

Trust me, it's as easy as untarring, patching, and dpkg-buildpackage

---

### Post by HungSquirrel on 2004-12-06
Count me in.  I've only ever done RPM packaging, though.

---

### Post by gfg on 2004-12-06
I'm in too. I'll help in any way i can.

---

### Post by poofyhairguy on 2004-12-06
me too. I'll help if possible.

---

### Post by jdong on 2004-12-06
Ok, while the SF project is pending review...

The rough layout of the repository:

```

jdong@jd64:/var/apt/ubuntu $ find .
.
./dists
./dists/warty-backports
./dists/warty-backports/main
./dists/warty-backports/universe
./dists/warty-extras
./dists/warty-extras/universe
./dists/warty-extras/contrib
./dists/warty-backports-staging
./dists/warty-backports-staging/main
./dists/warty-backports-staging/universe
./dists/warty-extras-staging
./dists/warty-extras-staging/universe
./dists/warty-extras-staging/contrib

```

The main repository to focus on is warty-backports, which will contain backports of **prepackaged debian sid or ubuntu development packages ONLY**. In other words, take a Hoary .orig.tar.gz, apply the .diff.gz to the folder, then recompile it in a Warty environment... So not much work involved.


The -staging areas are like a 'testing' branch, to make sure everything works. Some testing will be done on the -staging area, so we don't release broken packages (uh oh...).

warty-extras is an area reserved for packages in addition to Ubuntu's. As a result, there's no 'main' component (duh). The universe component will include stuff **packaged by me**, while the contrib component will be **community contributed packages**.

I'm thinking about a **warty-updates** distribution with unofficial updated packages (i.e. home-brew updates not found in Debian's Sid or Ubuntu's dev branch), but that's on the horizon and sketchy.


---

Naming conventions:

Sticking with Ubuntu's super-long version strings,  I'll stick to this convention...

Let's take firefox as an example. The latest hoary version is:
 mozilla-firefox_1.0-2ubuntu3_i386.deb

When I port it over, it'll probably look like:
mozilla-firefox_1.0-2ubuntu3-warty+backportedfrom-ubuntu-hoary1_i386.deb

If I find my retardedness broke the backport, the next point release will be:
mozilla-firefox_1.0-2ubuntu3-warty+backportedfrom-ubuntu-hoary2_i386.deb

---

### Post by jdodson on 2004-12-06
[QUOTE=jdong]Ok, while the SF project is pending review...

The rough layout of the repository:

```

jdong@jd64:/var/apt/ubuntu $ find .
.
./dists
./dists/warty-backports
./dists/warty-backports/main
./dists/warty-backports/universe
./dists/warty-extras
./dists/warty-extras/universe
./dists/warty-extras/contrib
./dists/warty-backports-staging
./dists/warty-backports-staging/main
./dists/warty-backports-staging/universe
./dists/warty-extras-staging
./dists/warty-extras-staging/universe
./dists/warty-extras-staging/contrib

```

The main repository to focus on is warty-backports, which will contain backports of **prepackaged debian sid or ubuntu development packages ONLY**. In other words, take a Hoary .orig.tar.gz, apply the .diff.gz to the folder, then recompile it in a Warty environment... So not much work involved.


The -staging areas are like a 'testing' branch, to make sure everything works. Some testing will be done on the -staging area, so we don't release broken packages (uh oh...).

warty-extras is an area reserved for packages in addition to Ubuntu's. As a result, there's no 'main' component (duh). The universe component will include stuff **packaged by me**, while the contrib component will be **community contributed packages**.

I'm thinking about a **warty-updates** distribution with unofficial updated packages (i.e. home-brew updates not found in Debian's Sid or Ubuntu's dev branch), but that's on the horizon and sketchy.


---

Naming conventions:

Sticking with Ubuntu's super-long version strings,  I'll stick to this convention...

Let's take firefox as an example. The latest hoary version is:
 mozilla-firefox_1.0-2ubuntu3_i386.deb

When I port it over, it'll probably look like:
mozilla-firefox_1.0-2ubuntu3-warty+backportedfrom-ubuntu-hoary1_i386.deb

If I find my retardedness broke the backport, the next point release will be:
mozilla-firefox_1.0-2ubuntu3-warty+backportedfrom-ubuntu-hoary2_i386.deb[/QUOTE]

i think this is great.  however i wonder what you might add that this does not:

[http://www.ubuntulinux.org/wiki/BreakMyUbuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu)

---

### Post by jdong on 2004-12-06
[QUOTE=jdodson]i think this is great.  however i wonder what you might add that this does not:

[http://www.ubuntulinux.org/wiki/BreakMyUbuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu)[/QUOTE]

GAIM's getting old; mono isn't too up to date; scribus, abiword are both getting old, the list goes on of stuff that have been demanded for in this forum but nobody has addressed.... K3b is quite a few versions old....

---

### Post by castrojo on 2004-12-06
I'm all for backports of a few selected apps, but there should be a concerted effort to consolidate all these packaging efforts.

It'd be nice to have one deb line with everything I need that's QA'd and tested with Warty. Personally for me, something like Firefox and Tbird 1.0 to hold me over until Hoary. 

Speaking of ... what is the plan for testing packages? What about reporting bugs? Packaging requests? Regression testing? Web of trust? Bugzilla? Mailing list? Has anyone checked to see how backports.org does business? What have they learned? How can that help us? Anyone experienced with packaging willing to have some kind of mentoring system? etc. etc. etc.

I'm just bringing this up now because it would suck to end up like Fedora, half a dozen people packaging the same stuff, it's all incompatible, and everyone blames the other packagers for whatever breakage happens when a user adds 5 repositories and blows up their system.

I guess what I'm trying to say is that if we (as in the collective Ubuntu users) are going to do this, it needs to be done right and all together in a way that's as high quality as Ubuntu itself. This will be difficult.

---

### Post by jdong on 2004-12-06
Just as proof-of-concept that I'm not APT-illiterate, I backported GAIM (a relatively small package) from Hoary to Warty, and it installs perfectly from a local APT source! YAY:

```

jdong@jd64:/var/apt/ubuntu $ dpkg-query  -p gaim
Package: gaim
Priority: optional
Section: net
Installed-Size: 9596
Maintainer: Robert McQueen <robot101@debian.org>
Architecture: i386
Version: 1:1.0.3-1-warty+backportedfrom-ubuntu-hoary1

```
Tada! go superlong version names!!


NOTE: I'm working on a bunch of shell scripts to simplify Packages.gz updating... work with my improvisational shell scripting here!

---

### Post by jdong on 2004-12-06
[QUOTE=whiprush]I'm all for backports of a few selected apps, but there should be a concerted effort to consolidate all these packaging efforts.

It'd be nice to have one deb line with everything I need that's QA'd and tested with Warty. Personally for me, something like Firefox and Tbird 1.0 to hold me over until Hoary. 

Speaking of ... what is the plan for testing packages? What about reporting bugs? Packaging requests? Regression testing? Web of trust? Bugzilla? Mailing list? Has anyone checked to see how backports.org does business? What have they learned? How can that help us? Anyone experienced with packaging willing to have some kind of mentoring system? etc. etc. etc.

I'm just bringing this up now because it would suck to end up like Fedora, half a dozen people packaging the same stuff, it's all incompatible, and everyone blames the other packagers for whatever breakage happens when a user adds 5 repositories and blows up their system.

I guess what I'm trying to say is that if we (as in the collective Ubuntu users) are going to do this, it needs to be done right and all together in a way that's as high quality as Ubuntu itself. This will be difficult.[/QUOTE]

I see your point.

Testing Packages:
Packages will be held off in a staging section while we test them. For the warty-backports section, I'll be personally compiling and packaging the backports. Bug reporting and Feature requests will be done through standard Sourceforge Project Services methods. So will the bugreporting.

As far as I see, backports.org is a one-man packaging effort with community testing.

---

### Post by jdong on 2004-12-06
STATUS:

repo update script working. It was quite easy... lol


I'm gonna experiment with more of the packages I want to see.

---

### Post by JonAtkinson on 2004-12-06
I have some experience packaging Debian packages.

I'd like to help :-)

Are you planning on setting up a mailing list or something?

--Jon

---

### Post by jdong on 2004-12-06
[QUOTE=JonAtkinson]I have some experience packaging Debian packages.

I'd like to help :-)

Are you planning on setting up a mailing list or something?

--Jon[/QUOTE]

As soon as I get my resources from SF, I'll set up mailing lists... though I personally like to keep as much as possible to the Bug Tracker system... easier to manage, easier to access.

---

### Post by kleeman on 2004-12-06
It might be worth running a poll at some point to measure demand. My votes in order would be:

1) Firefox
2) k3b
3) abiword
4) scribus
5) lyx (1.3.5 is in hoary?)
6) kate

---

### Post by jdong on 2004-12-06
Once I get the sf project, you guys can ask for whatever you want, at the Feature REquests tracker.



I'll probably use Apache stats to determine popularity.

---

### Post by Rancoras on 2004-12-06
I can see it now, jdong, the texstar of the Ubuntu community.

---

### Post by Alessio on 2004-12-06
When you have finished an Howto, put it here [http://www.ubuntulinux.org/wiki/BreakMyUbuntu](http://www.ubuntulinux.org/wiki/BreakMyUbuntu)

---

### Post by jdong on 2004-12-06
[QUOTE=Rancoras]I can see it now, jdong, the texstar of the Ubuntu community.[/QUOTE]

and I was thinking that, too! LOL

---

### Post by jdong on 2004-12-06
Firefox is done compiling, LMAO (actually, I didn't check for a while as I worried about gravitational fields around slanted cones for a test tomorrow)

ANYWAY,

I was thinking about other archs. I can easily provide binary-i386's, but the other archs, not so easy. I have an Athlon64,but  I personally don't like 64-bit linux... And I don't have a mac!!


Anyone willing to cooperate in the other archs?

---

### Post by regeya on 2004-12-06
[QUOTE=jdong]Firefox is done compiling, LMAO (actually, I didn't check for a while as I worried about gravitational fields around slanted cones for a test tomorrow)

ANYWAY,

I was thinking about other archs. I can easily provide binary-i386's, but the other archs, not so easy. I have an Athlon64,but  I personally don't like 64-bit linux... And I don't have a mac!!


Anyone willing to cooperate in the other archs?[/QUOTE]

jdong, if you'd get rid of that inane sig, I'd consider helping. ;)  Just kidding.

I wish I could help with other architectures.  If I can help in any way with the backporting process I'll be more than happy to lend a hand, when I can.

I'll add something to the mix, and this one isn't very big: dvd+rw-tools.  The version in Warty doesn't work with the stock Warty kernel.  I installed the dvd+rw-tools from hoary, and I don't know if there are any issues with doing this, but the less potential problems the better.

If I can figure out how to make "official" Ubuntu packages, I'd be willing to compile the latest libogg and libvorbis for inclusion.  libvorbis-1.1 has a lot of improvements.

Are you planning on just providing .debs much like the Debian Backports project does, or do you plan to provide an Apt repository?

Also, do the Ubuntu package maintainers use special CFLAGS?

---

### Post by jdong on 2004-12-06
[QUOTE=regeya]jdong, if you'd get rid of that inane sig, I'd consider helping. ;)  Just kidding.

I wish I could help with other architectures.  If I can help in any way with the backporting process I'll be more than happy to lend a hand, when I can.

I'll add something to the mix, and this one isn't very big: dvd+rw-tools.  The version in Warty doesn't work with the stock Warty kernel.  I installed the dvd+rw-tools from hoary, and I don't know if there are any issues with doing this, but the less potential problems the better.

If I can figure out how to make "official" Ubuntu packages, I'd be willing to compile the latest libogg and libvorbis for inclusion.  libvorbis-1.1 has a lot of improvements.

Are you planning on just providing .debs much like the Debian Backports project does, or do you plan to provide an Apt repository?

Also, do the Ubuntu package maintainers use special CFLAGS?[/QUOTE]

Sig -- No, that's staying! It captures a great moment and ties in with Debian!

Dvd+rw-tools -- sure.

I plan to abuse (err, use) sourceforge to provide an **APT repository**. The backports.org project also provides an APT repository!

CFlags -- I think that's built into the debian/rules file. I stick with default -- I don't want to cause mysterious program failures because of a bad CFlag choice.

---

### Post by poofyhairguy on 2004-12-07
Well..my hoary crashed again tonight...so I'm going back to warty.

I volunteer to be an official tester.

Bring it on.

---

### Post by daniels on 2004-12-07
Hi guys,
Unfortunately, if you use backports -- despite the fact they originally come from Hoary -- we won't be able to support you through our BTS at all.  I would say the most productive thing to do in this case would be to just test Hoary; it's a little bit more unstable, but you do get support and fixes from all our developers, and it saves you guys all the effort of creating and backporting the packages (for reference, Firefox takes a *LONG* time to build), and especially also resyncing new versions back from Hoary.

I would most strongly suggest you test Hoary, so that way we can have a stable, tested, and kick-arse platform to release from in six months.  If everyone just sorta tests from random builds from other projects, then we have no feedback on the official packages, and you lack the instant gratification effect.

---

### Post by jdong on 2004-12-07
[QUOTE=daniels]Hi guys,
Unfortunately, if you use backports -- despite the fact they originally come from Hoary -- we won't be able to support you through our BTS at all.  I would say the most productive thing to do in this case would be to just test Hoary; it's a little bit more unstable, but you do get support and fixes from all our developers, and it saves you guys all the effort of creating and backporting the packages (for reference, Firefox takes a *LONG* time to build), and especially also resyncing new versions back from Hoary.

I would most strongly suggest you test Hoary, so that way we can have a stable, tested, and kick-arse platform to release from in six months.  If everyone just sorta tests from random builds from other projects, then we have no feedback on the official packages, and you lack the instant gratification effect.[/QUOTE]

That is a valid concern for a developer. However, that's why I'm backporting less than 20 packages altogether. There's still gonna be people who like ALL the updates that Hoary has; I know I'm one of them. Just some people want a pseudo-production computer (if that's even possible!), with some updates for the apps they actually need...

Especially this early in Hoary, there's too much development activity for most people to live on!


I hope this won't tick off the developers too much...

---

### Post by dmatrix on 2004-12-07
I have been running Hoary as well and been backporting things back into Warty. I do run production desktops and servers with Warty and do not want to break them with Hoary at this point. That is why I am backporting. Since I have backported packages from Sid into Woody its a fairly easy process to accomplish (with a few packages being the exception).

So here is what I have done on a updated clean Warty box:
- add this line to /etc/apt/sources.list
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
- sudo apt-get update ; sudo apt-get install build-essential
- mkdir src ; cd src
- sudo apt-get --compile source mozilla-firefox

The first time thru there will more than likely be some missing development packages. Just apt-get all the ones that it complains about, then remove all the sources and try again.

Using this method I have backported this so far and fairly quickly on a modern box:
mozilla-firefox 1.0-2
mozilla-thunderbird 0.9-6
rox-filer 2.0.1
gnome-ppp

I am working on a Gaim 1.1.0 build right now that was a little trickier. I had to edit debian/control and change it from libgnutls11-dev to libgnutls10-dev and so far it is compiling.

So after you get all your new Warty backported debs built to setup an apt repo all you have to do is either install apache or proftpd and point it to the folder where all your debs are.
Then run a command similar to this and you have an apt repo for easy quick installation of your newly backported packages:
dpkg-scanpackages warty /dev/null | gzip -9c > warty/Packages.gz

Now add a new line to your /etc/apt/sources.list simliar to this:
deb [ftp://YourHostName/](ftp://YourHostName/) warty/

and you are now in business.

---

### Post by regeya on 2004-12-07
[QUOTE=dmatrix]
- sudo apt-get update ; sudo apt-get install build-essential
- mkdir src ; cd src
- sudo apt-get --compile source mozilla-firefox[/QUOTE]

Thanks for pointing this out.  I had been doing apt-get source mozilla-firefox then dpkg-buildpackage.  I guess I hadn't checked the apt-get manpage closely enough.  
 :D 

And to those who're concerned about the backporting going on:  Maybe some people will expect their system to upgrade cleanly; I have to think that most of us are aware that we're potentially fudging up our systems  by donig this.  And I'll be damned if I'm installing Hoary just to run the latest Firefox, Scribus, and k3b. :P

---

### Post by daniels on 2004-12-07
[QUOTE=jdong]That is a valid concern for a developer. However, that's why I'm backporting less than 20 packages altogether. There's still gonna be people who like ALL the updates that Hoary has; I know I'm one of them. Just some people want a pseudo-production computer (if that's even possible!), with some updates for the apps they actually need...[/QUOTE]Unfortunately, this isn't a given: Firefox 1.0, for example, is actually buggier than Firefox 0.9.3.  You also get strange interaction issues; f.e. if you backport xorg without xresprobe, things will probably break badly.  I understand this is a bad example since you've stated you won't be touching stuff like X, but the interactions really are incredibly subtle, and I'm worried that this could lead to breakage that we haven't seen thus far.

I don't want to discourage you or dampen your enthusiasm in any way, but I just think that it will lead to more incredibly subtle and damaging bugs than anyone thought (e.g. where 'upgrading' from Firefox 0.9.3 to 1.0PR1 led to Firefox segfaulting every time a click caused a JavaScript popup window), and will just be more problematic than anything, especially as six months really isn't long for the bleeding edge if you're desperate for the newest version of Firefox.

---

### Post by jdong on 2004-12-07
Yes, but you have to admit it's better than the current idea of switching sources.list to Hoary, install firefox, then go back to Warty...


Either way, I'll start the project, and if it doesn't work out and too many things break, I'll scrap the efforts.


Backports would probably end as soon as the first preview release of Hoary is released.

---

### Post by arekmenner on 2004-12-07
Sign me up. If you need anything beyond actual compiling, I can work with it, as well.

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=jdong]Yes, but you have to admit it's better than the current idea of switching sources.list to Hoary, install firefox, then go back to Warty...


Either way, I'll start the project, and if it doesn't work out and too many things break, I'll scrap the efforts.


Backports would probably end as soon as the first preview release of Hoary is released.[/QUOTE]

As long as you only backport of few programs, plenty of people will one day use hoary just to get the Xorg. I'll use hoary after helping you test these backports, I miss daily updates.  I just wish Hoary wasn't so unstable.

---

### Post by regeya on 2004-12-07
[QUOTE=jdong]Yes, but you have to admit it's better than the current idea of switching sources.list to Hoary, install firefox, then go back to Warty...[/QUOTE]

You are aware that you can have both warty and hoary in sources.list, and pin warty at a higher priority, right?  That'd be a better way of doing it, IMHO...at least easier...

...naturally, though, as Hoary diverges further from Warty, you'd have more problems, though (I already was) which is why I'm glad you're wanting to put together a repository of prebuilt backports. :D

Has the Sourceforge application gone through?  Know anything about the status?

---

### Post by jdong on 2004-12-07
[QUOTE=regeya]You are aware that you can have both warty and hoary in sources.list, and pin warty at a higher priority, right?  That'd be a better way of doing it, IMHO...at least easier...

...naturally, though, as Hoary diverges further from Warty, you'd have more problems, though (I already was) which is why I'm glad you're wanting to put together a repository of prebuilt backports. :D

Has the Sourceforge application gone through?  Know anything about the status?[/QUOTE]

1. Yes, I know all about pinning :). However, as Hoary gets new libraries, you'll be forced to mix more and more Hoary libs with Warty, until your Warty is no longer Hoary. Plus, some newly mixed libs may not get security updates and such.

2. The application is still pending review.

---

### Post by jdong on 2004-12-07
[http://sourceforge.net/projects/ubuntu-bp/](http://sourceforge.net/projects/ubuntu-bp/)

YAY, we're approved!

---

### Post by jdong on 2004-12-07
[http://ubuntu-bp.sourceforge.net/](http://ubuntu-bp.sourceforge.net/)

Add the backports lines as directed.

Let's get Firefox, K3b, and friends out of staging!!

---

### Post by TravisNewman on 2004-12-07
So is there going to be a restricted and a universe as well?

---

### Post by kleeman on 2004-12-07
Anything there yet? I added the lines as directed and apt reports it ignores the main and universe repository of warty-backports-staging
Great job by the way!  :-D 
I think if only a select set of packages are there then
development of hoary won't be affected...I got addicted to regular updates with Fedora.

---

### Post by jdong on 2004-12-07
[QUOTE=panickedthumb]So is there going to be a restricted and a universe as well?[/QUOTE]

There's a universe;

i'm not sure about restricted and multiverse.... Not sure if SF.net would approve of that. Will ask them.

---

### Post by TravisNewman on 2004-12-07
AH yeah I meant to say multiverse :)

---

### Post by jdong on 2004-12-07
[QUOTE=kleeman]Anything there yet? I added the lines as directed and apt reports it ignores the main and universe repository of warty-backports-staging
Great job by the way!  :-D 
I think if only a select set of packages are there then
development of hoary won't be affected...I got addicted to regular updates with Fedora.[/QUOTE]

Oops, I assumed SF.Net servers were still running Debian, where I could just call dpkg-deb... so much for that!

Fixed now... Using rsync to sync package lists.


Staging should have k3b 0.11.7, firefox 1.0, and Gaim 1.0.3.

---

### Post by jdong on 2004-12-07
GOD is SF slow @ downloading!

---

### Post by poofyhairguy on 2004-12-07
[QUOTE=jdong]GOD is SF slow @ downloading![/QUOTE]

I second that. Five hours for Firefox.

---

### Post by kleeman on 2004-12-07
I'll second that! apt picked up k3b k3blibs mozilla-firefox and gaim for upgrade but I gave up - the d/l speed here said gaim would take 7 hours yikes!

---

### Post by jdong on 2004-12-07
Yeah, I'm workin with the SF.net people. Apparently, they won't let you serve stuff from your project web services without getting approval.

I knew this, so I mentioned it **very very clearly** in my application, and asked them if it was OK. No response; they just approved the project and ignored that request.

Anyway, I filed another support ticket, and they've been pretty snappy to respond so far!

Hopefully by tomorrow you guys can get your updated K3b and Firefox.


P.S. Firestarter 1.0 is backported, too! YAY

---

### Post by jdong on 2004-12-07
Things look good now; getting 285KB/s!

---

### Post by jdong on 2004-12-07
If someone'd like to add a section about the backport repositories in the Wiki, please do so! Thanks!

oh yeah, put the standard big-fat-warning about the -staging section!

---

### Post by dare2dreamer on 2004-12-08
If I can get a vote in, I'd love to see an up to date package for inkscape.

---

### Post by jdong on 2004-12-08
Sure. I'm working on xine/gxine right now, inkscape is next on the list.

P.S. It seems like SF.net hasn't resolved the slowness issue yet; sorry!

P.P.S: Speed issues seem sporadic! Try restarting the download multiple times.

---

### Post by Alessio on 2004-12-08
Preconfiguring packages ...
(Lettura del database ... 61645 file e directory attualmente installati.)
Preparativi per il rimpiazzo di gaim 1:1.0.0-1ubuntu1.1 (usando .../gaim_1%3a1.0.3-1-warty+backportedfrom-ubuntu-hoary1_i386.deb) ...
Spacchetto il rimpiazzo di gaim ...
Configuro gaim (1.0.3-1-warty+backportedfrom-ubuntu-hoary1) ...

I've installed gaim :)
Two things:
1) An howto for help you
2) A list of package released or in testing..
3) We make packet request  here?

---

### Post by jdong on 2004-12-08
[http://sourceforge.net/news/?group_id=125877](http://sourceforge.net/news/?group_id=125877)

All new packages -- staging and released, will be announced in the project news area. You can always use a web browser to view the repository.

New package requests go into the Release Feature Requests (RFE) tracker: [http://sourceforge.net/tracker/?group_id=125877&atid=704005](http://sourceforge.net/tracker/?group_id=125877&atid=704005)

After you test a package in -staging and it works, file a bug report in the bugs tracker, with category 'Tested and Working': [http://sourceforge.net/tracker/?group_id=125877&atid=704002](http://sourceforge.net/tracker/?group_id=125877&atid=704002)


Do not post requests or problems here!

---

### Post by kleeman on 2004-12-08
OK I tried abiword 2.2.1 and it seems OK. How much testing do you want before it is flagged as OK? I opened about 6 different documents (MS word and .abw files) and it works fine. I can hold off for a week if you like...

---

### Post by jdong on 2004-12-12
Well, I first do check debian's bug database and Ubuntu's bugzilla for any outstanding issues.

If it seems to run fine for your daily purposes, then there are probably no packaging or library issues.

---

### Post by JonAtkinson on 2004-12-13
Jdong,

I'm considering starting work on a gaim-encryption pacakge later on this evening. The current (unofficial) debs suffer from an unresolvable dependency with libstartup-notification0, so I'm aiming to fix that. I'd like to work on a pure 'Warty version', but I'm also going to put together a version which is compatible with the gaim backport, (specificly the version I'm running: gaim_1.1.0-1-warty+backportedfrom-ubuntu-hoary1_i386.deb)

Once this is done, would you consider it for acceptance into warty-backports?

Let me know either way, you can email me at jatkinson at gmail dot com.

Cheers.

--Jon

---

### Post by jdong on 2004-12-13
[QUOTE=JonAtkinson]Jdong,

I'm considering starting work on a gaim-encryption pacakge later on this evening. The current (unofficial) debs suffer from an unresolvable dependency with libstartup-notification0, so I'm aiming to fix that. I'd like to work on a pure 'Warty version', but I'm also going to put together a version which is compatible with the gaim backport, (specificly the version I'm running: gaim_1.1.0-1-warty+backportedfrom-ubuntu-hoary1_i386.deb)

Once this is done, would you consider it for acceptance into warty-backports?

Let me know either way, you can email me at jatkinson at gmail dot com.

Cheers.

--Jon[/QUOTE]
Ok, I'll consider it for inclusion.

P.S. about libstartup-notification --- I compiled gaim 1.1.0 against warty's version of that. GAIM does depend on a higher version though... let me know exactly the problem,.

---

### Post by shimon on 2004-12-13
i start such a thing when warty frozze rebuilding from the debian reps some stuff

---

### Post by shimon on 2004-12-14
can you back port kernel 2.6.9 my friend needs it for a driver and so do a lot more of other people

---

### Post by flibblesan on 2004-12-14
JDong, you are a backporting God! Thank you so so much for these!

---

### Post by jdong on 2004-12-14
[QUOTE=shimon]can you back port kernel 2.6.9 my friend needs it for a driver and so do a lot more of other people[/QUOTE]
 Backporting a kernel will break Warty's ABI, something I really don't want to do! Also, 2.6.9 in Hoary was just released, plus there seems to be issues with NVidia/GLX and this new kernel...

So, no, not right now.

---

### Post by xerxian on 2004-12-15
I have backported (using dmatrix's method [here](http://www.ubuntuforums.org/showpost.php?p=30326&postcount=42)), firefox for amd64, let me know if anyone wants it and I will upload it somewhere.

I'm also backporting other packages like gaim.

---

### Post by jdong on 2004-12-15
[QUOTE=xerxian]I have backported (using dmatrix's method [here](http://www.ubuntuforums.org/showpost.php?p=30326&postcount=42)), firefox for amd64, let me know if anyone wants it and I will upload it somewhere.

I'm also backporting other packages like gaim.[/QUOTE]

I want to hold off on AMD64 inclusion for the ubuntu backports project for now... I need to think through how to support other architectures.

---

