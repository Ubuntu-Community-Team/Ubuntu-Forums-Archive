---
title: "Ubuntu isn't bleeding edge enough for me"
date: 2007-06-20
forum: Repositories &amp; Backports
---

### Post by redxii on 2007-06-20
I'm the guy who needs the absolute latest updates for each program.

Ubuntu only includes VLC 0.8.6 while 0.8.6c is out.
No Pidgin 2.0.2. No Pidgin
No Thunderbird 2.0.0.4
No OpenOffice 2.2.1
etc

Compiling is not an option, that is too difficult for my skill level. 

Scrounge around the internet for these updated packages from questionable sources? You said with apt-get, the be-all end-all, I wouldn't have to do that any more.

Or should I stick with Windows? Programs may not be centrally managed, but I, not the distro dev, get to say what gets installed, what version and when.

I already tried Automatix2 but it still has out of date packages.

---

### Post by Motoxrdude on 2007-06-20
The repositories aren't always "bleeding" edge because the host has to compile everything there selfs so it is not always up-to-date. This is how every distro is. If you google, you can probably get the latest debs to install.

EDIT: That and what difference does it make? I am almost positive that if you can't compile anything then you wouldn't tell the difference in the repo's and latest software.

---

### Post by Jonne on 2007-06-20
You can try [www.getdeb.net](www.getdeb.net) . It has more recent packages for a lot of software (Thunderbird seems to be missing, unfortunately).

You just download the .deb file, and install it (as if it were an .msi on Windows). Using .debs has the advantage that if a newer package becomes available in backports or a the next version of ubuntu comes out, your next upgrade will upgrade to the ubuntu version again.

There are also other distro's that are similar to Ubuntu that don't have a release cycle, they just constantly upgrade packages when they become available. [Arch Linux](http://www.archlinux.org/) is one of them (I don't know how good it is, but some people seem to like it). I don't personally really  mind Ubuntu's 6 month release cycle, even though I think backports of common apps should be made available faster, like Thunderbird 2.

---

### Post by yota on 2007-06-20
Ubuntu is not a bleeding edge distro: has a release cycle of 6 moths .
If you want to have always the latest and greatest you can try rolling-on distros like debian unstable or gentoo ~arch for instance.

---

### Post by Xappe on 2007-06-20
> **yota said:**
> Ubuntu is not a bleeding edge distro: has a release cycle of 6 moths .
If you want to have always the latest and greatest you can try rolling-on distros like debian unstable or gentoo ~arch for instance.

or Sidux - Debian Sid made somewhat easy to use

---

### Post by paparucino on 2007-06-20
> **Motoxrdude said:**
> 
EDIT: That and what difference does it make? I am almost positive that if you can't compile anything then you wouldn't tell the difference in the repo's and latest software.
He can tell his friends he has the last release.

---

### Post by Kobalt on 2007-06-21
> **redxii said:**
> I'm the guy who needs the absolute latest updates for each program.

Ubuntu only includes VLC 0.8.6 while 0.8.6c is out.
No Pidgin 2.0.2. No Pidgin
No Thunderbird 2.0.0.4
No OpenOffice 2.2.1
etc

Compiling is not an option, that is too difficult for my skill level. 

Scrounge around the internet for these updated packages from questionable sources? You said with apt-get, the be-all end-all, I wouldn't have to do that any more.

Or should I stick with Windows? Programs may not be centrally managed, but I, not the distro dev, get to say what gets installed, what version and when.

I already tried Automatix2 but it still has out of date packages.
There are some good repositories proposing such softwares... You should maybe have asked for that. 

PS: to me, a bleeding edge distro isn't just Pidgin, TBird or OpenOffice.. it's also about the kernel and the system..

---

### Post by insane_alien on 2007-06-21
I used to be the same i wnted the latest everything. then i asked my self a few questions.

1/ Why do you need the latest release of <insert software name>?
2/ Is the installed version incapable of doing what i want?
3/ Do i really need the new <feature>?
4/ Does the new version fix existing problems that i encounter?
5/ Am i going to use it?

A lot of the time i found the answers to these questions was no. there isn't much point.

if on the other hand the answer to one of these questions is yes then you can go find the newest version.

and you really should learn to compile stuff, it is useful.

---

### Post by tgalati4 on 2007-06-21
Except for old, or unsupported applications, just about all current packages are undergoing changes and improvements.

You can always download the latest snapshot of OpenOffice and compile it so it runs properly on your machine.  The newer version may have new languages (that you may not be interested in).  The newer version could be Alpha or Beta software, meaning it's not ready for the casual user.

You may not want to add software that is buggy and causes the rest of the system to act strange.  If you stick to the repositories then you will have a more stable system.

If there is one particular application that you need an update of, you can always compile it yourself and report to others on the forums how well it works.

How often did the Window's service packs come out?  How long did you have to wait for Word or Excel updates?

---

### Post by zgornel on 2007-06-21
> **redxii said:**
> I'm the guy who needs the absolute latest updates for each program.

Ubuntu only includes VLC 0.8.6 while 0.8.6c is out.
No Pidgin 2.0.2. No Pidgin
No Thunderbird 2.0.0.4
No OpenOffice 2.2.1
etc

Compiling is not an option, that is too difficult for my skill level. 

Scrounge around the internet for these updated packages from questionable sources? You said with apt-get, the be-all end-all, I wouldn't have to do that any more.

Or should I stick with Windows? Programs may not be centrally managed, but I, not the distro dev, get to say what gets installed, what version and when.

I already tried Automatix2 but it still has out of date packages.
No compilation, no bleeding edge! period. :D :D Windows is much more bleeding edge...

---

### Post by Old Pink on 2007-06-21
I've linked to Pidgin 2.0.1 .deb files here at my blog: [http://www.mbhoy.com/14-06-2007/pidgin-201](http://www.mbhoy.com/14-06-2007/pidgin-201)

And hosted a "transition package" that will update your GAIM to Pidgin, after installing the Pidgin .deb :)

---

### Post by Old Pink on 2007-06-21
> **redxii said:**
> Or should I stick with Windows? Programs may not be centrally managed, but I, not the distro dev, get to say what gets installed, what version and when.

You have more of a say in what gets installed, what version and when with Linux. Heck, it's open source you could even be ahead of the original devs if you tried hard enough.

Pull your finger out, put some effort in, learn how to compile.

All you need to do is extract (can be done in GUI) and read the readme, which usually consists of going:
[LIST]
[*]cd /dir/ect/ory/
[*]./configure
[*]make
[*]sudo make install[/LIST]It's pretty damn simple, really. Why not try upgrading to Gutsy now, and have the most bleeding edge updates handed to you by the hour. But don't come crying to us when it breaks your system.

Ungrateful ****.

---

### Post by maddog39 on 2007-06-21
If you really want all the latest stuff, I'd suggest Arch Linux as they always update to the latest packages as soon as they are out. Although its designed for advanced users, there is an awsome step-by-step beginners guide in their wiki. You dont have to compile anything either. :)

---

### Post by Old Pink on 2007-06-21
How hard is it to follow these simple instructions for Pidgin 2.0.2 compilation? >   1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.

  2. Type `make' to compile the package.

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.

  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

Seriously, it's a three step install. Configure, Make, Make Install.

---

### Post by gimfred on 2007-06-22
> **zgornel said:**
> No compilation, no bleeding edge! period. :D :D Windows is much more bleeding edge...
umm... Windows? Bleeding edge? People, Windows may be many things to many people, but bleeding edge it can never be, unless you are the top dog developer AT MICROSOFT. Vista is now nearly six months after release, how long before the next **major** upgrade? I think Canonical system is better, the best of both worlds.

---

### Post by zgornel on 2007-06-22
> **gimfred said:**
> umm... Windows? Bleeding edge? People, Windows may be many things to many people, but bleeding edge it can never be, unless you are the top dog developer AT MICROSOFT. Vista is now nearly six months after release, how long before the next **major** upgrade? I think Canonical system is better, the best of both worlds. Obviously it was a joke.

---

### Post by Lord Illidan on 2007-06-22
Just learn to compile your own stuff..

---

### Post by DizzyTech on 2007-06-22
Yes, but the point of having an easy-to-use, user-friendly distro is to **not** have to compile.  Normal users should never need to install build-essential or anything like it.

Ubuntu follows a very good process:  if a new version is released that fixes a major bug (sometimes) or patches a major security bug (always), it's put in the repo.  Otherwise, devs would never be able to create a new version of the distro, considering they would be constantly recompiling the over **21,000 packages** in the repos.

So, pick and choose:  stability and innovation, or bleeding-edge and convenient (for you)?

---

### Post by Rotarychainsaw on 2007-06-25
Compiling is really not that hard. I mean, I stick to easy stuff like new pidgin and stuff like that, but it's really not that bad.

---

### Post by smartboyathome on 2007-06-25
Some people don't like using the command line. This is where ubuntu comes in (being user friendly) and makes a GUI for compiling.

Also, from my experience, compiling is not a very good way to install stuff. For example, I tried to install SuperKaramba, it had dependancies which I did not know about, and had to install one-by-one.

---

### Post by ShirishAg75 on 2007-06-25
> **smartboyathome said:**
> Some people don't like using the command line. This is where ubuntu comes in (being user friendly) and makes a GUI for compiling.

Also, from my experience, compiling is not a very good way to install stuff. For example, I tried to install SuperKaramba, it had dependancies which I did not know about, and had to install one-by-one.

That is what learning is all about. Also its very much true what somebody else said the latest stuff is always in the alpha software, where its ok if things break, and you would not want the latest <insert software name> breaking other stuff. The first thing one learns in linux is inter-dependance. It is good as well as bad but that is life. 

Another thing, there are something like 65-70 odd developers who do pro-bono (for free) work for ubuntu & some of them also work upstream (debian) <insert software name> , then there is the roughly 30000 odd bugs which are there in launchpad & just updating to a newer version may not be the answer each time. For e.g. there is the hard disk IDE bug  [https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96693](https://bugs.beta.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/96693)
which we still suffer from , the problem surfaced in 2.6.20 & is still persistent in 2.6.22-6-generic to date. As one can see there is a fix committed status for quite some time now, but getting that fix released might take another two releases (either debian, or linux kernel or if the ubuntu devs. are waiting for something else.)

On Windows front they follow something called a first tuesday of the month & you would never get the acknowledgement or asking to try this & that to narrow down the problems within an hr. or 2. More so if you are on IRC. 

The idea is not to say that windows is bad or something, its that there are differences involved & one should take that into account. 

For bleeding edge, its simple, as soon as the release hits stable, wait for a month & then join the next alpha , you will get the latest release. Also if you want a package to be constantly updated tell the maintainers about the existence of new package & ask if it can be put in the backports.

Disclaimer :- I am not a developer or anything. Most of the stuff is from what I have read & understood from various sources not limited to the wiki, help documentation, forums, IRC, launchpad & the mailing lists. Some of the content might be factually wrong as I have never been into any kind of development & only the developers might be able to give a better picture of the same.

---

