---
title: "Rolling versus Non-Rolling?"
date: 2018-01-12
forum: Ubuntu, Linux and OS Chat
---

### Post by epicdragon44 on 2018-01-12
Hello everyone!

Despite having used Linux (all the major distros, from Ubuntu to Fedora to SUSE) I'm still a relative newbie, so here comes a question I've been wondering for some time:
What exactly is the difference between rolling and non-rolling releases?

I know that a rolling release lets you upgrade versions quickly and in-operating system, and that they normally have a quicker release schedule and shorter lifespan. However, I've realized that you can upgrade between Ubuntu releases, which are non-rolling, in-operating system as well. Furthermore, Ubuntu (like Fedora for instance) has quick releases biannually and short lifespans (except for LTS releases). So what exactly distinuguishes them, I guess?

Thanks all!

---

### Post by thyrson on 2018-01-12
The difference, I think, is as already mentioned by you. The  rolling-releases (LTS) are always ready to get the latest software, and  I think then at LTS, here the long-term rather attacks, so security  updates and important updates to keep the system long-term stable and  free from " teething problems ".

I have no other explanation or conclusion either.

With Fedora (RH) that is so, that the whole software with current numbers  only in the Fedora-build go before it moves into the actual Red Hat OS. At least I remember that, so I think it's the same, with the Rolling / Non-Rolling of Ubuntu. I'm not sure, but at least it would be an approach to an explanation.

---

### Post by grahammechanical on 2018-01-13
Every Ubuntu release has a 26 week development period during which the distribution is updated daily. Each Ubuntu release starts out as a new code branch of the latest release and is then worked on until it becomes the next Ubuntu release.

So, right now Ubuntu 17.10 is being developed daily into Ubuntu 18.04. The development team create daily ISO images of the development release which are a snapshot of the code at that point in the 26 week period. We can install these ISO images in the same way as released versions of Ubuntu. It is a way of testing the development version before it becomes the next version. 

The Ubuntu development version can be thought of as a rolling release for the 26 period of its development. Once a Ubuntu version is released it gets very few updates except for security fixes. A lot of people prefer the stability on a non-rolling fixed support term release over a rolling release version because the rolling release may break because the latest code may have very little user testing prior to being uploaded to the repository. With a rolling release the user is the tester.

Regards.

---

### Post by pauljw on 2018-01-14
It just depends on which rolling release system you're using.  I cut my teeth on PCLinuxOS which is a rolling release.  The lead dev, Texstar, is extremely conservative with the upgrades.  He and his team of testers put everything through it's paces quite thoroughly prior to placing them in the public repositories.  More of a "newest stable" version rather than just "newest."  With a rolling release, by keeping your system updated you will move from release to release almost invisibly.  Where in a non rolling release such as Ubuntu, you only update within a particular release.  You must purposely upgrade from one release to the next.  Sometimes this doesn't work out so well and many recommend doing a clean install to the next release because of that.

---

### Post by DuckHook on 2018-01-14
> **epicdragon44 said:**
> &#8230;What exactly is the difference between rolling and non-rolling releases?&#8230;
The fundamental difference between a rolling release philosophy and a non-rolling release philosophy is this:

A rolling release has no such thing as a "version". There is only one installation candidate. Conceptually, it lives forever. The OS itself, along with its entire app ecosystem, are kept continually updated on a schedule of its developers' choosing. These updates can be either aggressive or conservative, but the release rolls along on that schedule perpetually, like an endlessly flowing river.

In contrast, non-rolling releases like Ubuntu have a limited lifetime. They have a birth date and a death date. Moreover, any given version's ecosystem is largely frozen once that version is out of beta. Aside from security upgrades and a small subset of key apps, nothing gets changed after the birth date. And once the version reaches end of life, it doesn't get any updates at all&#8212;even security updates&#8212;it is just unceremoniously buried. This is why Ubuntu has LTS versions and overlapping standard versions. They are all at various stages of their lifetimes.

---

### Post by Frogs Hair on 2018-01-15
Manjaro has what they call stable and unstable rolling releases so I guess it would be the difference between fringe and bleeding edge packages/programs. Deepin is a rolling release with versions that have beta and stable periods though the updates are small in size compared to an Ubuntu upgrade. Deepin also has many it's own applications rather than the latest gnome based applications coming down stream.

---

### Post by Chanath on 2018-01-17
In the deb world, Debian Testing could be considered a rolling release. The repos can be named either buster or testing in /etc/apt/sources.list. The Buster repo would get a freeze, when it is about to move to the next Debian stable for few weeks. The Debain stable is now called Stretch, and then it would be called Buster. If you keep the repo name as testing all the time, in the frozen time, when Buster would become the new Debain stable, there won't be any updates/upgrades. After few days, the "testing" would start getting updates, and your Debian Testing install would go rolling, until the next freeze, which might come in 3 or so years. ([https://wiki.debian.org/DebianTesting](https://wiki.debian.org/DebianTesting))

---

### Post by Chanath on 2018-01-19
I am running a fully up to date Debian Testing installation for last few years, which is a rolling installation. It get updated once a day.

---

