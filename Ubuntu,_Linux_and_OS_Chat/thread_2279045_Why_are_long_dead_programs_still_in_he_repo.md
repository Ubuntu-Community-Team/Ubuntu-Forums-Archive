---
title: "Why are long dead programs still in he repo?"
date: 2015-05-20
forum: Ubuntu, Linux and OS Chat
---

### Post by monkeybrain20122 on 2015-05-20
Just found out qtoctave is still in vivid's repo. This is a qt gui for gnu-octave which has stopped development since 2012 and the version in repo works only with octave 3.6. The default version of octave in vivid is 3.8.2. So this is a completely useless program and it may not install if one tries. Why is it still in the repo? I am sure there are others like it too. So this is proves the statement that applications in the official repo is supported and tested by ubuntu dev is not true in general.

---

### Post by sudodus on 2015-05-20
You are welcome to join a group that looks after application programs in the repo (or create such a group if we cannot find one). If you want to, I can try to find a person, that knows more about it. Or you can try directly via the Ubuntu Quality mailing lists.

I could add Unetbootin to your list. The version from the developer's PPA works between older versions and newer versions, while the version in Ubuntu's repository does not work (at least not the version in 12.04 LTS, I tested a few weeks ago).

---

### Post by monkeybrain20122 on 2015-05-20
> **sudodus said:**
> You are welcome to join a group that looks after application programs in the repo (or create such a group if we cannot find one). If you want to, I can try to find a person, that knows more about it. Or you can try directly via the Ubuntu Quality mailing lists.

I could add Unetbootin to your list. The version from the developer's PPA works between older versions and newer versions, while the version in Ubuntu's PPA does not work (at least not the version in 12.04 LTS, I tested a few weeks ago).

It would be good if there is a place on launchpad to report these programs. It is important for quality control since we (well, not I personally) always tell new users to stick to the Software Centre instead of ppas because the applications are well tested blah blah..  It is easier for things like qt-octave, they can simply get rid of them, in any case they do no harm, only take up space. But other outdated packages from still maintained software (like old version of unetbootin) probably come from Debian, they are not upgraded since Debian hasn't done it.

---

### Post by mastablasta on 2015-05-20
agreed. a place to report that the porgram is not working would be good enough. there are also many game there that actually do not work at all. - in official repos.

not just, report someone should act on it. and clean it out of the repos if report is true.
checking the software's review in software center is a good place to start. some are full of: "does not install", "does not work"...

---

### Post by QIII on 2015-05-20
Use apport (ubuntu-bug) and add in your message that you suggest it be removed from the repo.

---

### Post by cariboo on 2015-05-20
I'd suggest that the best place to get rid of out of date packages is Debian, as the Ubuntu repositories are based on it.

Several years ago I tried to get an unmaintained package removed from the repositories, exactly the opposite happened, because of the bug report, and the ensuing conversations, more people downloaded the package, moving it further up in the popcorn rankings

---

### Post by mastablasta on 2015-05-21
even if it's Debian that houses them, there is no reason for Ubuntu not to filter them. especially when they do not work.

---

### Post by ian-weisser on 2015-05-21
Here's an example of how to remove a dead package from Debian: [https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756408](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=756408)

Use the version number as a guide to determine if packages come from Debian:
```
$ apt-cache show hello | grep Version
Version: 2.9-[COLOR=#ff0000]**2**[/COLOR]                ## If the number after the dash isn't '0', then it comes from Debian

$ apt-cache show lxd | grep Version
Version: 0.7-[COLOR=#ff0000]**0**[/COLOR]ubuntu1         ## This doesn't come from Debian
```

Debian has a specific process to prevent archive breakage, and the change will eventually propagate to Ubuntu as well. It starts with a bug report.

The first place to start is with the upstream maintainer. Contact them and find out what's going on. That's what maintainers are for.
```
apt-cache show <packagename> | grep Original-Maintainer
```

The discussion with the maintainer could turn out several ways. Maybe they don't want to maintain it anymore (opportunity for you to step up and take over). Maybe they need help. Maybe they agree that upstream is dead.

The bug reporter (ideally that upstream maintainer) should do all the homework, and prove to the Archive Admins that the project really is dead. The AAs are way too busy to do that research.

---

### Post by grahammechanical on 2015-05-21
I am thinking of the future Ubuntu Snappy Personal version of Ubuntu where all the applications in the software centre/app store are snap apps. A lot of applications that are presently in the software centre will need to be converted from deb packages to snap packages. It will be an opportunity for a clear out.

Applications that are no longer maintained will not be converted by the developer/maintainer. So, those applications will not be in the app store. Some developers will not be interested in converting their applications which leaves it to the community to do the conversion. But why waste time converting applications that do not work? So, for anyone in the community wanting to get involved in converting debs to snaps the first rule will be: test the application to see if it works. The second rule will be: If it does not work then junk it.

Regards.

---

### Post by sudodus on 2015-05-21
Thanks for a good 'how-to' *ian-weisser *:-)

-o-

I can add the following information from *Nicholas Skaggs* at Canonical:

Q: What/who are MOTUs and where can I find a relevant MOTU for this task?

A: [https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

Q: I guess the package maintainer might be a different person than the
developer - for example in the case of Unetbootin.

A: Look at the maintainers here [for example]: [http://packages.ubuntu.com/vivid/qtoctave](http://packages.ubuntu.com/vivid/qtoctave)

-o-

So it is served for you on a plate, *monkeybrain* :-)

Best regards
Nio

---

### Post by AllenGG on 2015-05-21
RE>  **Grahammechanical, says>  **[INDENT]                     "I am thinking of the future Ubuntu Snappy Personal "
... is possibly the best short explanation of "Snappy" , to date.
Old, outdated , apps, and add-ons in the repository (s) will disappear with Snappy.
The real question is, "when will Snappy" be sufficiently developed for the average user ?
AGG....[IMG]http://ubuntuforums.org/images/icons/icon6.png[/IMG] [/INDENT]

---

### Post by William_Soukup on 2015-05-28
QTOctave is on github, but no activity since 3/2012.

---

