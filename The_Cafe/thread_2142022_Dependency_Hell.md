---
title: "Dependency Hell"
date: 2013-05-04
forum: The Cafe
---

### Post by forrestcupp on 2013-05-04
How many people here remember the term "Dependency Hell"? For some reason, I just remembered that term and realized that we haven't had to worry about that for a very long time. It's amazing how much easier it is to run a functional Linux system without having to beat your brains out like we used to.

---

### Post by odiseo77 on 2013-05-04
I remember when I started using Linux, in 2004, I used a winmodem on a dial-up connection. It was a real hell making that thing work, but the good part is that I learned a lot from this experience. 

Oh, and yes, using Debian -- or pretty much any Debian based distro, or any modern and well supported distro -- I completely forgot about dependency hells. The wonders of repositories and apt-get ;)

---

### Post by buzzingrobot on 2013-05-04
It can still happen, on either deb or rpm distributions, if you blindly mix and match unofficial/nonstandard repos.

---

### Post by kevdog on 2013-05-04
I'd say most distro's dont have "dependency hell" -- apt, rpm, or other such repos.  Now if you do a lot of compiling from source -- way different story.

---

### Post by tgalati4 on 2013-05-04
True, add a few PPA's, try to compile newer versions of popular applications like audacity or gimp on an older distro and you are sure to descend into a dependency nightmare.  By compiling packages statically and including the newer libraries with the package you can sometimes get the newest applications to run.  After a while, though something will break.

For a routine user with a fresh install of Ubuntu or any Debian-based distro, you are generally protected from package dependency issues.  Upgrading in place is another issue.

---

### Post by codingman on 2013-05-04
dependency hell can still occur. It's uncommon though. Upgrading distros can leave you with dependency hell. Especially if you are testing.

---

### Post by Version Dependency on 2013-05-04
It's a very rare occurrence when using package managers like apt and yum.  Now building from source...you run into dependency problems all the time doing that.  Just do a search for "dependency hell" mentioned on the [Ubuntu]("https://www.google.com/search?client=ubuntu&channel=fs&q=gento+dependency+hell&ie=utf-8&oe=utf-8#safe=off&client=ubuntu&hs=uFT&channel=fs&sclient=psy-ab&q=site:ubuntuforums.org+%22dependency+hell%22&oq=site:ubuntuforums.org+%22dependency+hell%22&gs_l=serp.3...1868.4552.0.4918.12.12.0.0.0.1.126.1166.10j2.12.0...0.0...1c.1.12.psy-ab.7g50sPBCGSU&pbx=1&bav=on.2,or.r_qf.&fp=b5b20f7b3cf2835&biw=1680&bih=914") forums and the [Gentoo]("https://www.google.com/search?client=ubuntu&channel=fs&q=gento+dependency+hell&ie=utf-8&oe=utf-8#safe=off&client=ubuntu&hs=eFT&channel=fs&sclient=psy-ab&q=site:forums.gentoo.org+%22dependency+hell%22&oq=site:forums.gentoo.org+%22dependency+hell%22&gs_l=serp.3...31494.32723.2.33007.7.7.0.0.0.1.105.625.5j2.7.0...0.0...1c.1.12.psy-ab.-6POMuflgNs&pbx=1&bav=on.2,or.r_qf.&bvm=bv.45960087,d.eWU&fp=b5b20f7b3cf2835&biw=1680&bih=914") forums and compare.

---

### Post by Sam Mills on 2013-05-04
I installed slackware and it went well, until I needed apps, codecs, etc. It didn't last long on my hard drive. I just don't have the patience for finding dependencies I guess.

---

### Post by zer010 on 2013-05-05
The lst time I ran into dependancy issues was when I first started playing AssaultCube on 10.04(?).  Went to the website and grabbed the .deb and installed it, no issues reported.  No issues until I tried playing the game.  Started the game from the terminal and found out that it required newer versions of two libs. libopenal1 and libsdl-image1.2 it was.  Looked them up in synaptic and got up and running.  Haven't had that issue since at least 12.04.  It's been a real pleasure watching Ubuntu and Linux in general maturing to the great systems that they are today.  I only see it getting better from here on.  :D

---

### Post by buzzingrobot on 2013-05-05
> **Sam Mills said:**
> I installed slackware and it went well, until I needed apps, codecs, etc. It didn't last long on my hard drive. I just don't have the patience for finding dependencies I guess.

I used Slackware for a long time and rarely ran into dependency difficulties.  That said, once I get a system setup, I don't add very much to it. If you look at Slack again, check out Slackbuilds.org, which hosts scripted builds and lists the dependencies that need to be installed first.  Interestingly, those lists seem much shorter than the dependencies that would be installed for the same build in a deb or rpm distribution.

Dependency hell is really caused by the many versions of libraries, apps, etc., that exist, the frequency that new point releases are made, and the (rational) wish of developers to link dynamically rather than build fat static files. The longer the dependency chain -- A depends on B depends on C, etc., etc., -- the greater the chance the user will inadvertently install something from an "alien" source that will introduce circular and unresolvable dependencies.  In more than a few cases, the code is actually compatible, but the dependency resolver balks at not finding a version number or a naming convention it expects.

---

