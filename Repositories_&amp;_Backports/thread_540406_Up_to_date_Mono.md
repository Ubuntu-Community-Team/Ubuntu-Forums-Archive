---
title: "Up to date Mono"
date: 2007-09-01
forum: Repositories &amp; Backports
---

### Post by SniperSlap on 2007-09-01
Are there any repositories I can use to maintain more up to date versions of mono on my Feisty system?

One of the drawbacks of Ubuntu I find is that I'm always behind a few versions on their default repos.  Not all software groups have made .deb repos (and posted public keys!!!), so it immediately puts me in a position to have to lose all the package maintaining goodness we know and love....

---

### Post by nvivo on 2007-09-03
Hi. 

I have also been looking for a way to keep mono/monodevelop uptodate... it would be great if they could create a official repository for this stuff... But with Novel paying for it, I don't think they would put that in competition with OpenSuse...

Well, this is what I have found today:

deb [http://www.viraptor.info/repo](http://www.viraptor.info/repo) feisty-custombackports contrib
from
[http://www.viraptor.info/](http://www.viraptor.info/)

Looks like this guy created a backport repository from gutsy to feisty for mono... I didn't test, will test it tomorrow in a VM first...

Please, post anything else you can find. Mono is very uptodate (1.2.5) but monodevelop isn't.

---

### Post by apetresc on 2007-09-03
A similar issue was discussed, and solutions proposed, [in this thread](http://ubuntuforums.org/showthread.php?p=3273995).

---

### Post by SniperSlap on 2007-09-03
This doesn't really solve my problem as I'm on Feisty.

You would think some packages would be green-flagged once a .deb is prepared.  Looking at something like WINE, they manage to keep up to date packages out quite quickly along with their releases.

The idea of cutting edge not being stable is true to certain degress.  But in other respects, it can be a bit of a misdirection........

---

### Post by nvivo on 2007-09-07
I have been looking for an answer on this the last few days.  I have asked a lot of people about what would take to have a more updated version of mono on ubuntu, even if it is on backports or a different repository. If they need more people, need more requests, more help from the community... and simply didn't find anything useful.

Talked to the official Mono team, the Debian-mono team, the Ubuntu team... 

Miguel told me to talk to the package maintainers of mono on ubuntu or try OpenSuse...... 

The package maintainers for mono on ubuntu are the debian folks. They told me that I should ask the official ubuntu maintainers.

Asked them in the mailing list, and had no answers for days...

I think I'll probably install OpenSuse on a VM (although OpenSuse seems very polished, I simply like Ubuntu more..). At least I can get the latest Mono and Monodevelop ASAP.

I'm really sad that Ubuntu doesn't have a better supportfor Mono. "MS is evil" problems apart, .NET is a great development framework. 

Let's hope that with Silverlight release, people start looking for Moonlight and ubuntu team needs to update it more frequently to get working versions faster.

---

### Post by michaeljmcd on 2009-09-15
For anyone who may stumble across this later, the Mono project has a page on where to get up to date versions of Mono & friends for OSes other than the blessed three (Windows, OpenSUSE, and Mac):

[http://www.mono-project.com/Other_Downloads](http://www.mono-project.com/Other_Downloads)

There are some other repositories that can be used.

---

### Post by dinxter on 2009-09-28
it might also be worth looking through launchpad ppas for people maintaining more up to date versions of various packages. remember that these are unofficial and vary from stable, testing versions, svn versions etc from people who also range from package maintainers to all other sorts of ubuntu users so caveat emptor!
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

