---
title: "When will mediawiki be upgraded?"
date: 2012-01-24
forum: Server Platforms
---

### Post by Revo- on 2012-01-24
Right now Ubuntu (Ubuntu 11.10) has installed Version: 1.15.5-3build1 of mediawiki. 

unfortunately, mediawiki is now at **1.18.1**, and a lot of extensions etc need at least 1.16.x

Please can anyone advise when Ubuntu will be able to apt upgrade mediawiki to the latest version?

Also, when it does upgrade, will it trash my custom themes and extensions?

---

### Post by sanderd17 on 2012-01-24
> **Revo- said:**
> Right now Ubuntu (Ubuntu 11.10) has installed Version: 1.15.5-3build1 of mediawiki. 

unfortunately, mediawiki is now at **1.18.1**, and a lot of extensions etc need at least 1.16.x

Please can anyone advise when Ubuntu will be able to apt upgrade mediawiki to the latest version?

Also, when it does upgrade, will it trash my custom themes and extensions?

Mediawiki is a package that is directly pulled from Debian SID.

So you should really ask this to the Debian packagers.

---

### Post by Revo- on 2012-01-24
Ah, that sucks. Those guys are slack :(

---

### Post by sanderd17 on 2012-01-24
[http://packages.debian.org/sid/mediawiki](http://packages.debian.org/sid/mediawiki)

The next version will probably be 1.15.5-7.

Even if you convince the Debian team to update the package (you can do it with a bug report I think, but I have never done it), it won't be included in 12.04 anymore, as the debianImportFreeze was Jan 12 ([https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule)).

---

### Post by Revo- on 2012-01-24
Will ubuntu start to take it over?

Its really somewhat that they even bothered to offer it if they are not going to support upgrading it and keeping it current. Basically left with an out of date POS now. Urgh...... means I might have to do some actual work to upgrade it!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by sanderd17 on 2012-01-24
I'm sorry if this frustrates you. But I can't help it.

I've discussed this with some previous Ubuntu users, and it looks like Canonical has a bunch of favourite packages (packages that are maintained by Ubuntu devs, get updates during the release, are checkes before they are put into the repos ...) and all other packages are just pulled from Debian to fill the repos.

Those other packages don't get bugfixes or upgrades.

It's frustrating, I know, but there's nothing I can do about it.

For you, I would suggest to move to another distro. If you move to Debian, you will be a bit behind, but nothing will break, all package will get the same amount of attention. 


I moved to Arch Linux. Arch has the reputation to have the most recent version of all packages in their repos. Most of the times, the repos are less than one day behind. Arch also has the magnificent Arch Build System. Where it's really easy to create your own packages (and submit them to the Arch User Repository). So in Arch, you can be sure you will alwyas have the most recent version of all packages. The disadvantage in Arch is just the same. It's rolling. So for servers, this can cause problems (Although reading the Arch wiki and the Arch forums solves the problems in all cases I have seen).

I don't know a lot about other distributions, so I can't advise for or against them.

---

### Post by Revo- on 2012-01-24
Thanks, so basically ubuntu is Debian with just a few tweaks and things that they could be bothered to throw in?


Oh well, it's just mediawiki I have an issue with so I can upgrade it manually, it's just frustrating that they give you the option to apt-get it, but at a really out of date version, and then no longer support it. Makes no sense.

Cheers

---

### Post by Erkkimon on 2012-10-27
This is a growing problem. All the time it becomes more difficult to survive using the MW installed using repositories. Any concrete ideas? Unfortunately I don't have the knowledge to maintain this package.

---

### Post by lisati on 2012-10-27
An article on updating MediaWiki manually can be found here: [http://www.mediawiki.org/wiki/Manual:Upgrading](http://www.mediawiki.org/wiki/Manual:Upgrading)

Hope this helps.

---

