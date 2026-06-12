---
title: "Does RPM hell exist anymore?"
date: 2005-04-14
forum: The Cafe
---

### Post by dermotti on 2005-04-14
Does RPM hell exist anymore? With programs like YUM and RPM support under kpackage/synaptic is appear to be on par with Debian. 

LEts here it!

---

### Post by Stormy Eyes on 2005-04-14
Personally, I'm afraid to find out. :)

---

### Post by jdong on 2005-04-14
RPM Hell is really a myth. Nowadays, most distros (ok, practically ALL) have a packaging frontend like APT or YUM or SMART or YAST, etc that takes care of finding dependencies intelligently.

The problems usually happen when you install a Debian deb on Ubuntu, a Redhat RPM onto Mandrake, etc. Just because they have the same extension **DOES NOT** mean they are compatible!

---

### Post by dermotti on 2005-04-14
Thats what i thought.....yet i still see people thinking rpms are how they used to be a few years back.

How about slackware? i hear hey have a package management tool also, anyone have any experience with it?

---

### Post by az on 2005-04-14
RPM hell is not really the correct term.

Dependancy heck is more accurate.  It describes the differences between proprietary software and FLOSS.

With proprietairy software, you get no choice.  There is ony one kernel (although you do not know about it) and there are only one set of shared libraries to use.  The software on your system gets updated by the software distributer when they decide to release new versions and you get very little say in what happens.

It is very easy for a user to administer a system in such an environment because there is nothing to decide.

In FLOSS, there are usually many ways of doing things (Postfix or Exim, KDE or Gnome, kernel 2.4 or 2.6).  When there are more choices, you cannot avoid things being more complicated.
In order for something to compile, you must provide all the dependancies.  If you just distribute the binaries, you must also provide the binary dependancies.

In modern distributions, the package management is much more advanced, so these issues are ironed out for you.  Also, if you want nothing to do with the complicated world of dependancies, you have the choice to just stick to software provided by your distribution.  Like in Windows.

---

### Post by HungSquirrel on 2005-04-14
Dependency heck can be a pain in distros that don't come with intelligent package management by default.  The last time I tried a major RPM-based distro, that still applied.  When I first saw the wonders of apt, I was hooked.  If it weren't for intelligent package managers like apt, I'd still be a Windows user...!

---

### Post by jdodson on 2005-04-14
when i run fedora i really dont have the rpm issues i had before.  

installing apt over it is a breeze(albiet WAY, and i mean WAY slower than debian apt-get like many orders of magnitude slower than deb apt).  i had no problems with fedora using sites like [http://www.fedorafaq.org/](http://www.fedorafaq.org/) which are similar to [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

in the end, the upgrade and install slowness really turned me off to fedora.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=dermotti]Does RPM hell exist anymore? With programs like YUM and RPM support under kpackage/synaptic is appear to be on par with Debian. 
[/QUOTE]

As a former Fedora Core (and Mandrake 10.1 and Suse 9.2) user, I will say that RPM hell does exist. But it is not the fault (and was never the fault) of the software used to get packages. Yum and Urmpi and the RPM Apt-get all do their job wonderfully. 

RPM hell occurs because the official Fedora repos are not big enough. In the official repo (and on the install cds) there are only a few thousand packages. If everything you need is there then you won't ever see this hell, but if its not you are in for a ride. If the official servers doesn't have what you want (happened within the first day for me, I love my Bittornado), you have to add third party repos to get these packages. Problem is that these Repos (mostly talking about Fedora right now) don't play well with each other and they don't play well with the official repo. RPM hell happens because the default YUM server simply does not have enough of them so you are forced to risk your machine to get the packages you want. More than once in Fedora I broke stuff when I added thrid party repos and tried installing things I desired. The biggest reason why I left Fedora is because it didn't have enough packages that worked well together; I hate installing things from tarballs.

Of course, even Ubuntu and Debian are not immune to this. Despite having many more packages on the server (Fedora has like 4000 at most and Ubuntu has 14000+), there are some that lots of people want that are not there. So you have to add third party repos and open yourself to Deb hell. This is the problem that everyone that has tried to install mplayer recently while having the Marillet repo on the sources.list has experianced. 

Neither sort of hell will be fixed until every open source app anyone could possibly want is in the main (or universe or whatever) repo. It hasn't happened with Ubuntu (I can't find a decent GUI wireless app in the Universe to save my soul), and it might be impossible to achieve.

---

### Post by dataw0lf on 2005-04-14
RPM Hell doesn't exist anymore?  Try the equivalent of a dist-upgrade from FC1 to FC2, and watch the tracebacks fly.  (I just spent 2 hours fixing it on my work machine)

---

### Post by jdong on 2005-04-14
[QUOTE=dataw0lf]RPM Hell doesn't exist anymore? Try the equivalent of a dist-upgrade from FC1 to FC2, and watch the tracebacks fly. (I just spent 2 hours fixing it on my work machine)[/QUOTE]
Ok, first of all, this has never been supported by Redhat/Fedora. Their upgrades are always done via CD-ROM by running a force-overwrite install of all the RPM's you already have installed, plus the common install groups (basically a brute-force upgrade)

Secondly, Yum was never designed to be that smart of a package manager. Also, RPM's do not provide enough header info to properly support a rolling-versions distribution.

APT4RPM *can* do dist-upgrades quite well. I've done some from FC2->FC3, and SuSE 9 =>9.2. However, breakages midway are a LOT harder to recover from in RPM distros than in Debian distros.

---

### Post by poofyhairguy on 2005-04-14
[QUOTE=jdong]

Secondly, Yum was never designed to be that smart of a package manager.[/QUOTE]

Correct. The badass native RPM tool is URMPI. It can upgrade like a champ!

---

### Post by bvc on 2005-04-14
[QUOTE=jdong]Secondly, Yum was never designed to be that smart of a package manager. Also, RPM's do not provide enough header info to properly support a rolling-versions distribution.

APT4RPM *can* do dist-upgrades quite well. I've done some from FC2->FC3, and SuSE 9 =>9.2. However, breakages midway are a LOT harder to recover from in RPM distros than in Debian distros.[/QUOTE]rpms can have enough header info and do in mdk rpms but it was never accomplished with any other pkg manager but urpmi.

apt4rpm is fine for fedora and suse but was/is very bad on mandrake. I currently have an install that is at ML-10.2>cooker that has been upgraded since ML-9.1. I think the ability to recover is based on ones knowledge of the pkg manager. Even though I've used debian for 2 years it has only become my main as of about 7 months ago, and I didn't try to recover the 2 times sid wacked out on me. Mandrake, on the other hand, I've used for 4 years and can do anything I want with installs and recovery.

---

### Post by jdong on 2005-04-14
[QUOTE=bvc]rpms can have enough header info and do in mdk rpms but it was never accomplished with any other pkg manager but urpmi.
.[/QUOTE]

I've never used Mandrake that much...

I was going on knowledge/experience with SuSE and Fedora, whose RPM's Replaces, Provides, Conflicts fields certainly do not provide APT enough information to perform clean updates!

---

### Post by dataw0lf on 2005-04-14
[QUOTE=jdong]Ok, first of all, this has never been supported by Redhat/Fedora. Their upgrades are always done via CD-ROM by running a force-overwrite install of all the RPM's you already have installed, plus the common install groups (basically a brute-force upgrade)

Secondly, Yum was never designed to be that smart of a package manager. Also, RPM's do not provide enough header info to properly support a rolling-versions distribution.

APT4RPM *can* do dist-upgrades quite well. I've done some from FC2->FC3, and SuSE 9 =>9.2. However, breakages midway are a LOT harder to recover from in RPM distros than in Debian distros.[/QUOTE]

I don't see how this invalidates it being 'RPM Hell'.  You've just said that RPMs are inflexible, not designed well, and it takes something like APT4RPM for it to work properly. That qualifies, to me, as 'RPM Hell'.

---

### Post by bvc on 2005-04-14
[QUOTE=jdong]I've never used Mandrake that much...

I was going on knowledge/experience with SuSE and Fedora, whose RPM's Replaces, Provides, Conflicts fields certainly do not provide APT enough information to perform clean updates![/QUOTE]I was agreeing with you on apt4rpm!
I also don't think that urpmi is 'quite' as good at it as apt on a debian, but to answer the  thread starter it is very, very close.

You can pop over to mandrakeusers.org and find users in rpm/dep hell, but as I stated in another thread here, they, whether new or not, do not know what they are doing and just need a little guidence usually because of bad mirrors. This is the problem that has plagued mandrake for quite sometime concerning rpms. So there is the occasion that urpmi screems "it's not there" and it's not, but a simple google/rpm search will give it to you to install with the rpm command. So, the user thinks they are in dep hell but its really in mirror hell. This is of course just mandrake but I speak of it because if it were not for the bunked mirror issues, so many wouldn't have the problems they do have with urpmi.

---

