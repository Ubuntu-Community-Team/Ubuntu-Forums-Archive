---
title: "slitaz and apt"
date: 2009-03-26
forum: The Cafe
---

### Post by jacob01 on 2009-03-26
i was wondering if it would be possible to install apt onto slitaz. it has tazpkg and dpkg but im alot more familiar with apt.


sorry if this is the wrong place for this thread.

---

### Post by dragos240 on 2009-03-26
if it's not debian based, then it can't have apt, although, if debian provides source, perhaps.

---

### Post by Twitch6000 on 2009-03-26
> **dragos240 said:**
> if it's not debian based, then it can't have apt, although, if debian provides source, perhaps.

incorrect... PClinuxOS is not debian based yet it has apt-get.

@op it is probably possible through some tweaking.

---

### Post by cardinals_fan on 2009-03-26
I have a few thoughts on this matter.  It has been discussed on the SliTaz Forums, so you can look over there for more perspectives.

SliTaz isn't descended from Debian and is not designed to use APT.  This was by choice.  Debian packaging is really quite clumsy compared to SliTaz (I mean no offense, but I have yet to see anything comparable to Tazwok for any distro).  The tools included in SliTaz are made to do the best job possible with the resources available.

Familiarity is always comforting, but it isn't necessarily good.  I would certainly have been more familiar if I had just kept using Windows 95 (my first OS), but I also would have missed out on a great many evolutions and changes.  With all of that said, it may be possible to install APT with dpkg.  I have successfully installed RPM (the original and long since discontinued package manager, not the format) on SliTaz in the past, and it might be possible with APT too.  However, I don't recommend it.  The distro just isn't meant to be run with Debian packages.  But it's up to you to decide.

---

### Post by init1 on 2009-03-26
> **dragos240 said:**
> if it's not debian based, then it can't have apt, although, if debian provides source, perhaps.
Fedora has apt, and it's not Debian based. I'm sure it would be possible to port apt to SliTaz, but I don't really see the need to. Instead of typing
```

apt-get install

```
you type
```

tazpkg get-install

```

---

### Post by snowpine on 2009-03-27
I agree with the above; SliTaz has tazpkg, which is a fantastic package manager. Well worth the effort to learn. :)

---

### Post by smartboyathome on 2009-03-27
SliTaz *can* use apt, but you won't be able to install many packages, use any repos, etc with it, as it won't have all the packages available, nor in all the right positions.

---

### Post by jacob01 on 2009-03-27
yeah that was why i was trying to get apt because i thought i would have a more up to date repository with more packages.

edit i was unable to find the correct package

---

### Post by init1 on 2009-03-27
> **jacob01 said:**
> yeah that was why i was trying to get apt because i thought i would have a more up to date repository with more packages.

edit i was unable to find the correct package
Yeah, Slitaz doesnt have th best repos, but you can still compile from source

---

### Post by jacob01 on 2009-03-27
> **init1 said:**
> Yeah, Slitaz doesnt have th best repos, but you can still compile from source

yeah

---

### Post by cardinals_fan on 2009-03-27
> **init1 said:**
> Yeah, Slitaz doesnt have th best repos, but you can still compile from source
Post a request in the Requests subforum.  Many of the packages in the repos are the result of requests.

---

