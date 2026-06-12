---
title: "Questtion about debian testing"
date: 2010-01-11
forum: The Cafe
---

### Post by mamamia88 on 2010-01-11
is it much more unstable than debian stable?

---

### Post by juancarlospaco on 2010-01-11
Yes...

---

### Post by mamamia88 on 2010-01-11
really?  i need to replace xubuntu on my netbook because it keeps crashing and was thinking of going with either debian testing or stable.  i like the idea of testing because then it's a rolling release with newer packages

---

### Post by mdmarmer on 2010-01-11
see here [http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=2508&highlight=realms+debian](http://sidux.com/index.php?name=PNphpBB2&file=viewtopic&t=2508&highlight=realms+debian)

I have had no problems.  I run lxde on debian testing.  The smxi script will be very helpful for you if you want to run debian testing.  [http://techpatterns.com](http://techpatterns.com)  [http://smxi.org](http://smxi.org)  irc on oftc #smxi or #linux-smokers-club

Mike

---

### Post by cascade9 on 2010-01-11
'Testing' is pretty stable. Of course, its not going to be as stable as 'Stable', but its still very stable IMO. I've used it on and off for a while, and never had any major stability issues. 

Testing is a lot more breakable than stable though....

---

### Post by mamamia88 on 2010-01-11
you think sidux would run on a netbook?

---

### Post by snowpine on 2010-01-11
Debian Testing is the "release candidate" for the *next* Debian Stable release (currently Squeeze). So it is by definition less stable than Debian Stable. (In my experience, however, Debian Testing is more stable than any Ubuntu release, certainly fine for the average desktop user, maybe not for a mission-critical server.)

---

### Post by snowpine on 2010-01-11
> **mamamia88 said:**
> you think sidux would run on a netbook?

Of course, why wouldn't it? ;)

---

### Post by mamamia88 on 2010-01-11
don't know why it wouldn't run but figured since it debian unstable made stable it might not be the best choice for someone looking for a stable os.

---

### Post by snowpine on 2010-01-11
> **mamamia88 said:**
> don't know why it wouldn't run but figured since it debian unstable made stable it might not be the best choice for someone looking for a stable os.

I agree; Debian Unstable is a terrible choice if you're looking for a stable OS. I would recommend Debian Stable if you want the most stable.

---

### Post by slakkie on 2010-01-11
> **mamamia88 said:**
> is it much more unstable than debian stable?

In a way yes. But I have to admit, I find Debian unstable/testing really stable. Ubuntu development release snapshots are more likely to b0rk.

---

### Post by mamamia88 on 2010-01-11
so if all i care about is having the latest firefox, the latest open office, and the latestflash player installed how hard would it be to just upgrade manually on debian stable?

---

### Post by slakkie on 2010-01-11
> **mamamia88 said:**
> so if all i care about is having the latest firefox, the latest open office, and the latestflash player installed how hard would it be to just upgrade manually on debian stable?

On stable, have a look at the backports and/or compile it yourself:

```

# Backports
deb http://www.backports.org/debian lenny-backports main contrib non-free
#deb-src http://www.backports.org/debian lenny-backports main contrib non-free

deb http://www.debian-multimedia.org lenny main contrib non-free
#deb-src http://www.debian-multimedia.org lenny main contrib non-free

```

---

### Post by snowpine on 2010-01-11
> **mamamia88 said:**
> so if all i care about is having the latest firefox, the latest open office, and the latestflash player installed how hard would it be to just upgrade manually on debian stable?

"The latest" and "most stable" are mutually contradictory. You should think hard about what your top priorities are. I find that Ubuntu is an excellent compromise between relatively up to date and relatively stable (it fills this niche better than any of the Debians), but your mileage may vary. :)

---

### Post by mamamia88 on 2010-01-11
my main priorities are stability and security. if i have to upgrade a few applicatioins individually i will do

---

### Post by Xbehave on 2010-01-11
> **slakkie said:**
> On stable, have a look at the backports and/or compile it yourself:
If it's just a few apps couldn't you just pull them in from testing?

---

### Post by cascade9 on 2010-01-11
From what I've heard, mixing 'stable' and 'testing/unstable' is a bad, bad idea. 

Not to say its not possible. 

It would be eaiser, and safer, to just backport or d/l them and compile (if you had to) yourself like slakkie said.

---

### Post by slakkie on 2010-01-11
> **Xbehave said:**
> If it's just a few apps couldn't you just pull them in from testing?

Yes, you could, but it is considered bad practice to do so (although I also do it... *giggle*). But if the package is in backports, I would prefer that over mixing stable with testing.

---

### Post by mdmarmer on 2010-01-11
You could also look at Mepis
[http://www.mepis.org](http://www.mepis.org) [http://www.mepislovers.org](http://www.mepislovers.org)
Mepis is KDE based on debian stable with some newer packages.  There is a beta .iso available with KDE 4.

They have a community repository which has newer versions of many packages.

Mike

---

### Post by ssam on 2010-01-11
the 'stable' bit refers to things not changing. if you run debian stable, then you only get security and serious bug fixes.

you might find that debian unstable crashes less, because it has a much never version of xorg, or kernel or whatever, that fixes some bugs.

---

### Post by Zoot7 on 2010-01-11
I find Debian Testing to be pretty solid bar a few minor glitches here and there. My preferred option is to run purely Testing with a few packages pulled in from Unstable. It gives a good balance between being fairly up to date, rolling and "stable" IMO.

"Sid" is the one to avoid. From the Debian Site:
> "sid" is subject to massive changes and in-place library updates. This can result in a very "unstable" system which contains packages that cannot be installed due to missing libraries, dependencies that cannot be fulfilled etc. Use it at your own risk!

---

### Post by koenn on 2010-01-11
> **mamamia88 said:**
> so if all i care about is having the latest firefox, the latest open office, and the latestflash player installed how hard would it be to just upgrade manually on debian stable?

depends on whether those versions' dependencies can be satisfied from "stable" or not. If not, you'd also have to upgrade their dependencies, and you start risking incompatibility with already installed packages.

---

### Post by Project PWNED on 2010-01-11
> **mamamia88 said:**
> really?  i need to replace xubuntu on my netbook because it keeps crashing and was thinking of going with either debian testing or stable.  i like the idea of testing because then it's a rolling release with newer packages

Do a server install of Ubuntu, install OpenSSH server and install IceWM or IceWM-lite as your Window manager. This should be more stable for you. I was a long-time Debian user (since 2.0.36 kernel) and I like Ubuntu better for the better drivers/packages than what Debian stable has offered.

---

### Post by Hallvor on 2010-01-11
> **mamamia88 said:**
> so if all i care about is having the latest firefox, the latest open office, and the latestflash player installed how hard would it be to just upgrade manually on debian stable?

It depends of you want a very stable system, or if you can handle a little instability. If you need the newest - anything - Debian stable is a bad choice. (There is a backports repository where you can get some newer applications, though.)

You could run Debian testing - rolling release and newer packages, but you need to be a little more knowledgable.

A third choice is Debian unstable where packages are very frequently updated, before they are moved to testing if they meet certain criteria. But unstable is not recommended for noobs either.

---

### Post by Zoot7 on 2010-01-11
> **mamamia88 said:**
> so if all i care about is having the latest firefox, the latest open office, and the latestflash player installed how hard would it be to just upgrade manually on debian stable?
If those three are ***all*** you care about then yes you can simply install the .deb packages from both the Adobe site and Openoffice.org site, you won't find them in the repos though. Firefox is just a case of grabbing the tarball from the Mozilla site.
But in general as the others have said, Stable isn't the best choice if you want to be relatively up to date.

> **Xbehave said:**
> If it's just a few apps couldn't you just pull them in from testing?
Yes, but most Debian users (myself included) recommend you grab the source from the testing repos and compile it against Stable rather mixing Testing and Stable.

---

