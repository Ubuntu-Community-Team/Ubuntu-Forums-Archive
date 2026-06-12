---
title: "Adding Debian APT repositories"
date: 2005-04-09
forum: Repositories &amp; Backports
---

### Post by goofrider on 2005-04-09
I added Debian Testing in my sources.list, and pinned it to Pin-Priority 350. Most pacakges seems to be tracking Hoary just fine this way, even when Debian Testing may have a newer package.

Take *adduser* for instance:
```

3.63 (testing)
3.59 (now)

```

An *apt-get upgrade* or *apt-get dist-upgrade* will not upgrade to the newer Testing package. This is the correct behavior, and all the other packages seems to pin correctly.

However, apt-get and Synaptic keeps trying to upgrade *libkdenetwork2*.


```

4:3.3.2-2 (testing)
4:3.3.2-1ubuntu3 (now)

```

Anyone knows how I can get it to pin correctly?


Also, where should I put **APT::default-release**??? I don't have an */etc/apt/apt.conf* file, but I have a */etc/apt/apt.conf.d/**. None of the files in */etc/apt/apt.conf.d/** have *APT::default-release* sepecified.

---

### Post by az on 2005-04-09
Not a good idea.

You cannot mix repositories like that.

Why not just install Sarge with the Sarge installer?

---

### Post by goofrider on 2005-04-10
[QUOTE=azz]Not a good idea.

You cannot mix repositories like that.

Why not just install Sarge with the Sarge installer?[/QUOTE]


Because I'm not trying to run Sarge. I'm just pulling a few packages from Sarge that doesn't exist in Ubuntu's repo. And this isn't specific to Sarge either, me adding Sarge's repo is just an exercise of Apt pinnning for me, I'll add Sid too eventually... Actually I just did today, Pin-Priority 300 for Sid. So far so good, nothing breaks and nothing tries to upgrade to Sarge or Sid when I *dist-upgrade*.

The only package that's not following my pin-prioirty is *libkdenetwork2*.

Lots of people mix Sarge and Sid, I don't see why I can't mix Hoary with Sarge/Sid as long as I use Hoary as the default release, pin other repos carefully and only pull a handfull of packages from Debian and only when these packages are not found in Hoary.

I'm well aware of the risk, but it's a decision that I can make myself. It would've been better if you acknowledge that I'm trying to educate myself to get it done correctly instead of telling me I can't do that.

---

### Post by c_dog on 2005-04-10
Problem is that Hoary is really based on Sid, not Sarge. Mixing any others right now other than marrillat, videolan, and the Mutliverse is !not! a good idea. Like most of us that learned the hard way mixing the repositories it seems to almost always end up in a clean install. I well, guess the only way to learn is to make mistakes.

---

### Post by az on 2005-04-10
Hoary started off as Sid, but has been patched.  Not all of the patches make their way back into debian.  Do not use debian archives, use universe.

It is somewhat better to mix Sid with Sarge because they both are the same distribution.  Ubuntu and Debian have similarities, but one is not the other, so  you cannot mix.  Well, you can, but you end up with problems.  If you ask for support in relation to those problems, you will get the answer to the problem: Do not mix repositories!


"It would've been better if you acknowledge that I'm trying to educate myself to get it done correctly instead of telling me I can't do that."

I am very happy you are learning about pinning.  That is a good thing.

What do you have against universe?  Also, why then, do you not want to try pure debian?

---

### Post by goofrider on 2005-04-10
[QUOTE=azz]

What do you have against universe?  Also, why then, do you not want to try pure debian?[/QUOTE]

Oh I do use universe, but there are some things that are simply not there. FWIW, I try very hard to pin everything correctly, and only install Debian packages rarely. On top of that, I always double-check the version # in Synaptic whenever I install a package even if I think it came from Ubuntu, just in case the pinning broke and try to install a Debian package instead.

To top that off, I never let Synaptic or apt-get to automatically install any dependencies unless I have manually checked that they'll be versions that come from the Ubuntu archive as well. And I disable the Debian repos in sources.list whenever I do dist-upgrade or any other large scale upgrade (like upgrading Xorg, KDE or Gnome).

So all in all, I'm only allowing myself to install isolated packages from Debian with all their dependencies satified by Ubuntu packages.

I'm aware that Ubuntu is based on Sid and it's probably much safer to import Sid and only Sid from Debian. Right now I'm pretty much just messing around and testing compatibily. I'll probably import Sid only once I'm done with experimentation.

If anyone else out there want to import the Debian repo, please import Sid only and make sure u pin Debian packages with a Pin-Priority under 500 (given that hoary-updates and hoary-security will be default to 500 if you don't pin them). And import Sid at your own risk.

In any case, I'd still like to know where should I define **APT::default-release** since I don't have an apt.conf file???? If I add a new fragment in apt.conf.d, do I have to use an update tool to build the apt.conf?

---

### Post by goofrider on 2005-04-10
[QUOTE=goofrider]

In any case, I'd still like to know where should I define **APT::default-release** since I don't have an apt.conf file???? If I add a new fragment in apt.conf.d, do I have to use an update tool to build the apt.conf?[/QUOTE]


OK I figured it out. I guess I was just nervous because there isn't a default *apt.conf* and I didn't want to create a new one and somehow overrides default settings.

Creating a new apt.conf in /etc/apt/ with:
```


APT::default-release="hoary";

```

works just fine. I used *sudo apt-config -dump* to double-check it and apt apparently merges my *apt.conf* with *apt.conf.d/** fragments nicely.

---

### Post by gflores on 2005-04-11
[QUOTE=c_dog]Problem is that Hoary is really based on Sid, not Sarge. Mixing any others right now other than marrillat, videolan, and the Mutliverse is !not! a good idea. [/QUOTE]

Is marrillat safe to add to the sources list? I've been hearing conflicting reports.

---

### Post by dutler on 2006-02-06
Thanks for answearing my apt.conf vs apt.conf.d question. 

Maybe instead of adding a Debian repo for just a few packages, you could run a local repo with apt and the manually download  Debian packages? AND if all goes well or after you have mod the pkg, you can submitt them to the Ubuntu repos....?

Im trying to figure out pinning to, but not haveing much success. Sounds like guys know quite about it, can you take a gander at [http://ubuntuforums.org/showthread.php?p=709775#post709775](http://ubuntuforums.org/showthread.php?p=709775#post709775) ?

br / dutler

---

