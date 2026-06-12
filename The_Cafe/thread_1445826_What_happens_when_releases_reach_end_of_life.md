---
title: "What happens when releases reach end of life?"
date: 2010-04-03
forum: The Cafe
---

### Post by standingwave on 2010-04-03
Does the Update Manager start nagging the user to upgrade? I've never held onto a release long enough to experience this.

---

### Post by rudihawk on 2010-04-03
> **standingwave said:**
>  I've never held onto a release long enough to experience this.

Me too!

---

### Post by howefield on 2010-04-03
> **standingwave said:**
> Does the Update Manager start nagging the user to upgrade? I've never held onto a release long enough to experience this.

Update Manager should inform you that a new upgrade is available. 

Load update manager up and check Settings > Updates tab to see the Release upgrade options that are flagged to show.

---

### Post by mickie.kext on 2010-04-03
> What happens when releases reach end of life?

They go to big decompiler in the sky :)

---

### Post by standingwave on 2010-04-03
> **mickie.kext said:**
> They go to big decompiler in the sky :)Sounds nicer than bit rotting in the grave.

---

### Post by Dayofswords on 2010-04-03
see this
[http://ubuntuforums.org/showthread.php?t=1441659](http://ubuntuforums.org/showthread.php?t=1441659)
it may give an idea on what happens

---

### Post by standingwave on 2010-04-03
> **howefield said:**
> Update Manager should inform you that a new upgrade is available. Thanks. What I'm curious  is how periodically this happens, random times or just at start-up? Perhaps it depends on the  release.

---

### Post by howefield on 2010-04-03
> **standingwave said:**
> Thanks. What I'm curious  is how periodically this happens, random times or just at start-up? Perhaps it depends on the  release.

If update manager is set to show new distribution releases, it'll remind you every time you load it up, (assuming a newer releases is available).

---

### Post by oldos2er on 2010-04-03
> **standingwave said:**
> Thanks. What I'm curious  is how periodically this happens, random times or just at start-up? Perhaps it depends on the  release.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Wiebelhaus on 2010-04-03
Nothing other than the repositories die and you'll be notified to upgrade and if you want to keep using that version disable updates.

---

### Post by snowpine on 2010-04-03
Ubuntu is a fast-moving distro. If you want to be an Ubuntu user, it's in your best interest to follow the progress of the distro and stay on top of upgrades, otherwise you'll get left behind.

Fortunately, there are the LTS (long term support) releases for those who prefer to upgrade every 2 years instead of every 6 months. This month's 10.04 will be an LTS.

---

### Post by techunit on 2010-04-03
I would agree if you don't like upgrading as much I would recommend that you install the next LTS (10.04) and you will get updates for up to 3 years.

---

### Post by phibxr on 2010-04-03
> **mickie.kext said:**
> They go to big decompiler in the sky :)

This made my night. :D

---

### Post by Artemis3 on 2010-04-03
> **standingwave said:**
> Does the Update Manager start nagging the user to upgrade? I've never held onto a release long enough to experience this.

Basically, you won't be able to update or install stuff anymore, they take down the repository... You don't want this to happen, unless you are willing to backup / install fresh a newer release from CD etc.

They are a bit more lenient with the LTS which lasts longer, but if you are not using an LTS release, update ASAP. When the next LTS appears, update to that.

---

### Post by cariboo on 2010-04-03
Actually everything gets moved [here]("http://old-releases.ubuntu.com/releases/"), so the packages are still available, think of it as an old folks home for releases. :)

---

### Post by cubeist on 2010-04-03
I am still using feisty fawn on a laptop.  That version seemed to work the best with the hardware.  Basically nothing about the OS is different from the day I installed it, and I don't really worry about newer software.  The hardware will die long before the OS does on that laptop...

---

### Post by Pikestaff on 2010-04-08
> **cubeist said:**
> I am still using feisty fawn on a laptop.  That version seemed to work the best with the hardware.  Basically nothing about the OS is different from the day I installed it, and I don't really worry about newer software.  The hardware will die long before the OS does on that laptop...

Yeah, I've still got Dapper (6.06) on my laptop-- it's the ONLY version of Ubuntu I've managed to get wireless working with.  I haven't noticed anything different about it since it reached EOL last summer.  Though, I don't use my laptop very often.

---

### Post by Tristam Green on 2010-04-08
Let's make sure we're on the same page:

Are you talking about when an upgrade is available, i.e. in the normal six-month cycle of Ubuntu?  Or are you actually talking about Software End-of-Life, when support for the software *stops*?

If it's the latter, (official) support stops.  That's all.  No more patches, no more updates.  Either upgrade to a newer supported version number, or risk security vulnerabilities on your system.

If it's the former, developers still generally release security patches for it until the actual end-of-life.

---

### Post by forrestcupp on 2010-04-08
They ceremoniously bury a dead animal with the code name of that version.  When Hoary Hedgehog reached the end of its life, they buried a dead hedgehog and performed their official Ubuntu rites over the grave. ;)

> **Tristam Green said:**
> 
If it's the latter, (official) support stops.  That's all.  No more patches, no more updates.  Either upgrade to a newer supported version number, or risk security vulnerabilities on your system.Tristam & cariboo are right.

You can still install the OS and even install things from the repos.  They just don't do any work on it anymore.  It won't keep nagging you anymore than it did when it was still alive.

---

### Post by leorolla on 2010-04-27
You also get less support from the community.

If you are trying to install Ubuntu 5.04 on a brand new laptop, and suppose you can't get sound or wireless working, and you come to this or any other forum asking for help, I guess what will happen: maybe ubber geeks will reply your thread trying to solve the 5.04 problem just for the fun of it, and most people will reply it just telling you to get 10.04.

---

### Post by Condor Cluster on 2011-07-30
Going to have to turn this into one of the undead 'zombie' threads...

When a LTS reaches EOL (eg Lucid), can you just update to the next (10.04=>12.04), or are you forced to install from scratch?
I can imagine that an update of that magnitude would cause a whole heap of problems though, with applications and ppas all different.

Do a lot of people still use out of date releases, although they are no longer updated, they work how people want them to, and people are happy with it. I'm sure a lot of people are still rocking on XP on their machines...

\\:D/

---

### Post by Paqman on 2011-07-30
> **Condor Cluster said:**
> 
When a LTS reaches EOL (eg Lucid), can you just update to the next (10.04=>12.04), or are you forced to install from scratch?
I can imagine that an update of that magnitude would cause a whole heap of problems though, with applications and ppas all different.


You can always update from one LTS straight to the next. If you're on a non-LTS, you have to upgrade through every release on the way. I would imagine the LTS > LTS upgrade path is very thoroughly tested, as it'd be used by a lot of lucrative enterprise customers.

As for PPAs, they're disabled during the upgrade process so that they don't interfere. After the system is set up you have to re-enable them yourself and get the new packages.

---

