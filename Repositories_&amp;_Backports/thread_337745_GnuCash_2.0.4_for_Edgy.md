---
title: "GnuCash 2.0.4 for Edgy?"
date: 2007-01-13
forum: Repositories &amp; Backports
---

### Post by Master One on 2007-01-13
I'm using Kubuntu Edgy Eft 6.10 and was just wondering, if there is any possibility to get the latest GnuCash version as a .deb file. The latest version in the repos is 2.0.1, and I don't assume it is the best idea trying to build it from source myself.

---

### Post by Tommy on 2007-01-29
I'm running into the same issue. There are some grave bugs in the 2.0.1 version (Latest available for Edgy 6.10) and the latest version for Dapper 6.06 is version 1.8.12. 

I tried to check out the current source and compile the software for Dapper but I had to give up -- too many unmet dependencies for me to deal with right now.

I don't have any idea how buggy GnuCash version 2.0.2 is -- that's the version currently in the queue for Ubuntu Feisty. So it's behind the times, too.

If anyone has successfully built GnuCash version 2.0.4 for Ubuntu 6.06 or 6.10, I'd like to know what it requires. It would be REALLY cool if there was a way to backport it to Dapper, but at this point if it could backport to Edgy that would be OK.

---

### Post by aanderse on 2007-01-29
hey i just compiled it (but for 64bit so sorry can't help you with the debs if you are using 32bit)

compiling it isn't actually that bad
if you want i can list all the packages you should install if you want to compile it, it is pretty straight forward


[edit]

i just checked on the fiesty package list and it looks like they only have gnucash version 2.0.2-3 ([http://packages.ubuntu.com/feisty/gnome/gnucash](http://packages.ubuntu.com/feisty/gnome/gnucash))
i really hope they get the newest version for feisty :\

---

### Post by rplantz on 2007-01-30
> **aanderse said:**
> hey i just compiled it (but for 64bit so sorry can't help you with the debs if you are using 32bit)

compiling it isn't actually that bad
if you want i can list all the packages you should install if you want to compile it, it is pretty straight forward\

I would appreciate your doing that. I'm running 2.01 on Edgy 64-bit and the bugs bug me.

I have yet to compile an application for my Ubuntu system and would like to learn how to do it. Any other pointers you can give me will be appreciated. I'm a knowledgeable user (retired programmer), so I don't need all the details. But some brief pointers would help.

TIA

---

### Post by Tommy on 2007-01-30
> **rplantz said:**
> I would appreciate your doing that. I'm running 2.01 on Edgy 64-bit and the bugs bug me.

I have yet to compile an application for my Ubuntu system and would like to learn how to do it. Any other pointers you can give me will be appreciated. I'm a knowledgeable user (retired programmer), so I don't need all the details. But some brief pointers would help.


I appreciate hearing from aanderse that the app compiles fine with little trouble. There is explicit information on compiling at the gnucash.org web site, but the steps are a bit out of date AND they didn't work so well on Dapper for PowerPC (my primary system). I'm not sure I can even update to Edgy on PowerPC. I ran the Edgy package on an Intel box and was using it from my Dapper system, but KABOOM! Crashes EVERY time.

I opened a bug against it -- [https://launchpad.net/bugs/82211](https://launchpad.net/bugs/82211) -- so maybe someone will have a look. If the Feisty package fixes the crashes maybe they can backport it to Edgy. OH and if you can subscribe to the bug and confirm that it affects you, too, maybe it will get the attention it deserves.

---

### Post by deadlydeathcone on 2007-01-31
I made some [gnucash 2.04 packages]("http://lightofcracker.com/ubuntu/gnucash-2.04.tar.gz") that will work on any architecture. Unfortunately they're only for edgy, but I'll see if I can get something built for dapper tomorrow.

---

### Post by rplantz on 2007-01-31
> **deadlydeathcone said:**
> I made some [gnucash 2.04 packages]("http://lightofcracker.com/ubuntu/gnucash-2.04.tar.gz") that will work on any architecture. 

So gnucash-common_2.0.4-1_all.deb will detect that I have an amd64 running in 64-bit mode and do the right thing?

I downloaded 2.0.4 and compiled and installed it following the given instructions. It was pretty straightforward. During the configure phase, I got lots of error messages saying things were missing. They were easy to fix. I used synaptic to search for the missing packages, then installed them. They were mostly libraries where I had not installed the -dev package.

Of course, one of the problems with doing it this way is that the upgrade is not recorded in my package management system. A project I plan to pursue soon is to learn how to create deb packages from source code.

---

### Post by deadlydeathcone on 2007-01-31
> **rplantz said:**
> So gnucash-common_2.0.4-1_all.deb will detect that I have an amd64 running in 64-bit mode and do the right thing?

Actually no, I misread a line in the control line. It's 386 only.

Here's how to recompile my package on another architecture (you'll need to have packaging tools installed; seveas made a [metapackage]("http://seveas.theplayboymansion.net/seveas/pool/edgy-seveas/seveas-meta/ubuntu-devel_6.10-2_all.deb") that will set everything up):

1) First, get the official source, and rename it so it can be packaged:

```
wget [http://www.gnucash.org/pub/gnucash/sources/stable/gnucash-2.0.4.tar.gz](http://www.gnucash.org/pub/gnucash/sources/stable/gnucash-2.0.4.tar.gz)
mv gnucash-2.0.4.tar.gz gnucash_2.0.4.orig.tar.gz
```

2) Download my [updated package information]("http://lightofcracker.com/ubuntu/gnucash-diffs.tar.gz"). Extract it to the same directory used for the gnucash source and create the source package like this:

```
tar -xvvzf gnucash-diffs.tar.gz
dpkg-source -x *.dsc
```

3) Finally, build the package:

```
cd gnucash-2.0.4/
sudo debuild -us -uc
```

If you have a gpg you can leave the -us -uc off of last command to sign the package.

Wait about a billion years until it finishes compiling and you'll automagically have a good debian package.

> **rplantz said:**
> Of course, one of the problems with doing it this way is that the upgrade is not recorded in my package management system. A project I plan to pursue soon is to learn how to create deb packages from source code.

There's a really good packaging tutorial in yelp. It's good stuff to know, and usually not all that difficult once you get the hang of things.

---

### Post by Max Ischenko on 2007-02-01
> **deadlydeathcone said:**
> 
3) Finally, build the package:

```
cd gnucash-2.0.4/
sudo debuild -us -uc
```

There's a really good packaging tutorial in yelp. It's good stuff to know, and usually not all that difficult once you get the hang of things.

Doesn't work for me:

```
make
make[1]: Entering directory `/tmp/gnucash/gnucash-2.0.4'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/tmp/gnucash/gnucash-2.0.4'
make: *** [build-stamp] Error 2
debuild: fatal error at line 1224:
debian/rules build failed
```

This is when I run with -d flag because it complained about certain unmet deps:

```

$ LC_MESSAGES=C sudo debuild -us -uc
dpkg-checkbuilddeps: Unmet build dependencies: libltdl3-dev libofx-dev (>= 1:0.8.0-8) m4 libdb3-dev liborbit-dev libungif4-dev libgnomevfs2-dev (>= 2.2.0) libgnomeprint2.2-dev (>= 2.8.0) libgnomeui-dev (>= 2.0.0) libgsf-gnome-1-dev (>= 1.12.2) libgtkhtml3.8-dev libgoffice-0-dev libgsf-gnome-1-dev
debuild: fatal error at line 983:
You do not appear to have all build dependencies properly met, aborting.
(Use -d flag to override.)
If you have the pbuilder package installed you can run
/usr/lib/pbuilder/pbuilder-satisfydepends as root to install the
required packages, or you can do it manually using dpkg or apt using
the error messages just above this message.

```

Is it possible to build the package for Edgy? 

Why on earth did the universe doesn't have the latest bug-fix release available?

---

### Post by Tommy on 2007-02-01
> **Max Ischenko said:**
> Why on earth did the universe doesn't have the latest bug-fix release available?

It's up to a volunteer somewhere along the supply chain. The person who usually makes the Debian package is a couple of versions behind. 

Almost all Ubuntu packages started out their lives as Debian packages (though as Ubuntu has improved more have gone the other way).

So that should spur one of us to learn enough to contribute the latest package ourselves! 

I believe anyone can do it, but it requires a trusted person to ensure it's up to Debian/Ubuntu standards and approve the submission before it becomes officially available to everyone.

---

### Post by deadlydeathcone on 2007-02-01
> **Max Ischenko said:**
> Doesn't work for me:

```
make
make[1]: Entering directory `/tmp/gnucash/gnucash-2.0.4'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/tmp/gnucash/gnucash-2.0.4'
make: *** [build-stamp] Error 2
debuild: fatal error at line 1224:
debian/rules build failed
```

I completely forgot about dependencies. Running:

```
sudo apt-get build-dep gnucash
```

will automatically fetch all them all. Before you try to package it again the package will have to be cleaned with:

```
sudo debuild clean
```

---

### Post by clw on 2007-02-04
I found GnuCash v2.0.4 for dapper in this German repository:
[http://www.geole.info/Deb-Packages-for-Ubuntu-Dapper.16.0.html?&l=1]("http://www.geole.info/Deb-Packages-for-Ubuntu-Dapper.16.0.html?&l=1")

---

### Post by Tommy on 2007-02-05
> **clw said:**
> I found GnuCash v2.0.4 for dapper in this German repository:
[http://www.geole.info/Deb-Packages-for-Ubuntu-Dapper.16.0.html?&l=1]("http://www.geole.info/Deb-Packages-for-Ubuntu-Dapper.16.0.html?&l=1")

That sounds quite interesting, HOWEVER I am quite skeptical for two reasons:

1) I don't ever add repositories to my system unless I have some sort of independent verification of who is responsible for them. I can't tell much about this one -- I would be concerned that it might contain malware of some sort....

2) I believe others have found it impossible to install GnuCash 2.0.4 in Ubuntu Dapper 6.06 because of serious cross-dependency issues. I would be interested in knowing how this person resolved those issues.

---

### Post by clw on 2007-02-05
Well maybe I'm more trusting than you but I installed it... 

1) Regarding trusting the geole.info repository, it seems to be widely used by the Freevo community and Georg Leonhardt, the guy behind it, is a packager for ubuntu universe.

2) The GnuCash v2.0.4 package works perfectly for me on xubuntu dapper, so Georg appears to have resolved the issues you mention. Why not contact him to find out if you are interested?

---

### Post by Tommy on 2007-02-07
> **clw said:**
> Why not contact him to find out if you are interested?

I wrote, but no reply yet (couple of days). I found him registered in Launchpad as a packager for Universe, but it looks like he hasn't (yet) contributed any packages... maybe Gnucash will be the first?

As I thought carefully about it, the problem I had was compiling for PowerPC, and my dependency issue was with a compile-time dependency NOT a runtime dependency. Since the .deb on the geole.info repository is for Intel it may be trivial for that architecture. OR maybe it requires compilation on a later version of Ubuntu in order to run under Dapper. And since I'm stuck on Dapper on that box, I may be stuck on Gnucash 1.x.

I'm glad it works for you!

---

### Post by Tommy on 2007-02-08
I just received a reply from Georg Leonhardt, and he said he would try to submit the 2.0.4 package for Dapper Backports. I told him the backport had already been rejected [https://launchpad.net/dapper-backports/+bug/52486](https://launchpad.net/dapper-backports/+bug/52486) (for a technical reason I don't understand), but I thanked him for the work he's done.

---

### Post by shomati_sen on 2007-02-09
Hi,

I built Gnucash 2.0.3 and 2.0.4 for Edgy and have been using it along with online banking since Dec. The main thing that I needed was to to build libofx and aqbanking since the versions in Edgy don't work for online banking. To build aqbanking, I downloaded and built gwenhywfar-2.4.1 and libofx-0.8.2. 

Shomati

---

