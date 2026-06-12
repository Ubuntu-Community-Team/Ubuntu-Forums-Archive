---
title: "Testing Unstable Branch analogy"
date: 2010-08-17
forum: The Cafe
---

### Post by darrelljon on 2010-08-17
I don't understand the difference between Debian testing and unstable. Has rolling got anything to do with it? Are there any good analogies for how these are different?

---

### Post by LowSky on 2010-08-17
Testing means you have a seat belt and maybe a helmet, and there is a guy in a lab coat with a clipboard check off things and has an idea of what might go wrong and possible prevention.
Unstable means it was probably made in your garage while drinking. During your first use you might say something like "hey check this out" before you crash.

---

### Post by RiceMonster on 2010-08-17
Testing = version being prepared to be the next stable release.

Unstable = experimental - newest of the new

---

### Post by Austin25 on 2010-08-17
Ah, so someone like me would try using unstable for a web server.:lolflag:

---

### Post by XubuRoxMySox on 2010-08-17
For a web server? Mission critical? I'd use Stable I think. Unstable is "rolling" in that it stays up to date (at a little risk) without ever being frozen after lotsa testing. I read this analogy, and I think it was Snowpine who originally offered it (apologies to the originator if I guessed wrong) on another Linux board:

Pretend you're Michelle Obama. If you are "Mrs. Obama," you stay with the man you married. But if you are "Mrs. President," then when the next guy takes office, you're married to a stranger!

The first example is Unstable - stuff just upgrades as you go along. That's "rolling release." The second example is Testing or Stable. It changes completely at it's "end of term," when stuff from Unstable moves to Testing, and/or when Testing is frozen before being released as the new Stable.

Get it?

Trying to imagine being Mrs President,
Robin

---

### Post by Austin25 on 2010-08-17
> **dixiedancer said:**
> For a web server? Mission critical? I'd use Stable I think. Unstable is "rolling" in that it stays up to date (at a little risk) without ever being frozen after lotsa testing. I read this analogy, and I think it was Snowpine who originally offered it (apologies to the originator if I guessed wrong) on another Linux board:

Pretend you're Michelle Obama. If you are "Mrs. Obama," you stay with the man you married. But if you are "Mrs. President," then when the next guy takes office, you're married to a stranger!

The first example is Unstable - stuff just upgrades as you go along. That's "rolling release." The second example is Testing or Stable. It changes completely at it's "end of term," when stuff from Unstable moves to Testing, and/or when Testing is frozen before being released as the new Stable.

Get it?

Trying to imagine being Mrs President,
Robin
Yeah, I was making a joke on the fact the web server need to be a stable platform so they can run for years, where as an Unstable release won't run for more than a couple days at most.

---

### Post by Bachstelze on 2010-08-17
> **RiceMonster said:**
> Testing = version being prepared to be the next stable release.

Unstable = experimental - newest of the new

[unstable]("ftp://ftp.debian.org/debian/dists/unstable/") != [experimental]("ftp://ftp.debian.org/debian/dists/experimental/").

My personal impression is that using testing makes very little sense, unless you are engaged in bug squashing.  If your server is mission-critical, run stable.  If it's not, run unstable.

---

### Post by RiceMonster on 2010-08-17
> **Bachstelze said:**
> [unstable]("ftp://ftp.debian.org/debian/dists/unstable/") != [experimental]("ftp://ftp.debian.org/debian/dists/experimental/").

Oh, I was unaware there was an experimental branch as well.

---

### Post by gradinaruvasile on 2010-08-17
experimental is not a full branch like stable, testing or unstable. It has temporarily the latest versions of software in it for some preliminary testing. I think it was created because unstable broke often because of completely untested packages. Now unstable is said to be quite usable.
The scheme is like this:
Packages enter experimetal for some time and stay there if have critical bugs (like not being able to install/run etc), then cross into unstable where the bigger bugs are crushed (anyway they stay there for 1-2 weeks to see if some bugs appear) and then are put in testing.
From testing they dont go anywhere, they are upgraded and upgraded until freeze comes. In this situation no more features are added only bugfixes (experimental and unstable still works).
Testing becomes stable after the RC (release critical) bugs are fixed - there is no fixed timeline like the 6 months Ubuntu schedule, they take their time fixing everything to make a really stable system.
I now use Debian testing and i must say it is very stable and works better than Ubuntu (probably because most packages are in the main repos not in various PPAs).

---

### Post by Irthur Belle on 2010-08-17
level 0.?1 UTF-8 blocked... 
 
Western' loading... done.

level ?...
grep: menu.h: No such file or directory
grep: main.c: No such file or directory
...

---

### Post by snowpine on 2010-08-17
Whoa! I'm famous across forums. Thanks for the shout out Dixie. :)

STABLE (currently Lenny) is what Debian does best; it is an extremely, well, nother way to say it... "stable" operating system which means two things: 1st it is as bug-free as possible; 2nd it is static or frozen, meaning it gets only bug fixes and security patches. This is just like how Ubuntu works, except it comes out every 2 years (roughly) instead of every 6 months, so the quality control is a lot better but the packages are older. (If you need newer stuff you can get it from Backports.)

TESTING (currently Squeeze) is the alpha/beta/RC for the next stable release. They add new stuff from Unstable to Testing until it looks roughly release-worthy, then they "freeze" it for bug squashing. Ubuntu has a Testing branch too (currently 10.10 Maverick Alpha). 

UNSTABLE is where the newest "stuff" lives that hasn't made it to testing yet. It is constantly being updated as new app versions become available (so don't use it if you only have dial-up). Unstable is the closest thing Debian has to "rolling release" meaning there are no distinct "releases"--Unstable is always code-named Sid. Ubuntu does not have an Unstable branch of its own because it uses Debian's Unstable for this purpose.

I recommend Stable for most users, Testing for users who want to get involved testing and reporting bugs, and Unstable for users who want the latest untested stuff.

Note however that Debian is a very conservative project. Even the packages in the Unstable branch are, on average, equal or even slightly older than the corresponding packages in Ubuntu, Fedora, Arch, etc. Many users have positive experiences with Testing or even Unstable, and if you hang out on the Debian forums you'll hear things like "Debian Unstable is more stable than other distros' Stable releases."

---

### Post by darrelljon on 2011-01-07
So can I get old versions of Arch linux or old versions of Debian sid branch or is that a contradiction in terms?

---

### Post by earthpigg on 2011-01-07
> **darrelljon said:**
> So can I get old versions of Arch linux or old versions of Debian sid branch or is that a contradiction in terms?

In both cases, you'd need to find a mirror that was created 'back then' and not updated. Not unreasonable to create your own and then wait a while for it to be the 'old version'... I think a complete mirror of all of Ubuntu's repositories is a few dozen gb.

In the case of sid, though, it sounds like you would simply be stuck with bugs that have long since been fixed.

---

### Post by snowpine on 2011-01-07
> **darrelljon said:**
> So can I get old versions of Arch linux or old versions of Debian sid branch or is that a contradiction in terms?

Sure, but as soon as you updated your system, you'd be running the current versions of everything--that's pretty much the dictionary definition of "rolling release." :)

---

