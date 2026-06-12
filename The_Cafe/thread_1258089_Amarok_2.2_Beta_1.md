---
title: "Amarok 2.2 Beta 1"
date: 2009-09-04
forum: The Cafe
---

### Post by natedawg on 2009-09-04
The new Amarok beta is out with a lot of changes! Its a major improvement from 2.1 check it out!

[http://amarok.kde.org/en/releases/2.2/beta/1](http://amarok.kde.org/en/releases/2.2/beta/1)

---

### Post by speedwell68 on 2009-09-04
Does it have iPod support?

---

### Post by natedawg on 2009-09-04
Not sure how good the ipod support is. The feature log says it has support for copying aiff files to iPods.

---

### Post by hoppipolla on 2009-09-04
2.2 looks staggering to me :)

Should finally get me off Banshee! lol ^_^

---

### Post by tghazali on 2009-09-05
I've added the appropriate repositories to the software sources, reloaded packages and the update still won't appear in synaptic running on ubuntu jaunty. Any ideas?

---

### Post by maniacmusician on 2009-09-05
> **tghazali said:**
> I've added the appropriate repositories to the software sources, reloaded packages and the update still won't appear in synaptic running on ubuntu jaunty. Any ideas?

Well, I just checked around a bit on Launchpad -- it doesn't look like Amarok 2.2 has been packaged for Jaunty yet. Which repositories might you be referring to?

If you're talking about [Kubuntu Beta Backports]("https://edge.launchpad.net/~kubuntu-ppa/+archive/beta") or [Kubuntu Experimental]("https://edge.launchpad.net/~kubuntu-ppa/+archive/experimental"), the 2.2 packages there (uploaded by riddell) are for *Karmic (9.10)*, not *Jaunty (9.04)*.

Here's the [main Kubuntu PPA page]("https://edge.launchpad.net/~kubuntu-ppa"). The packages in those repositories are usually made by the Kubuntu developers, though of course they are still unofficial (i.e. unsupported, for testing purposes, with no guarantees of stability).

---

### Post by tghazali on 2009-09-05
Thanks, will try to compile from source then.

---

### Post by ikkefc3 on 2009-09-05
Or get the Amarok-Nigthly from the Neon project:
[https://launchpad.net/~project-neon/+archive/ppa](https://launchpad.net/~project-neon/+archive/ppa)

---

### Post by s1300045 on 2009-09-05
> **tghazali said:**
> Thanks, will try to compile from source then.

I tried, and it's complaining about mysqld not installed on my system. I did a sudo aptitude build-dep amarok but still. Do I want to compile my own mysql?

---

### Post by vikrant82 on 2009-09-05
Go for libmysqlclient16-dev (or libmysqlclient15-dev). Make sure you clean up build folder before you cmake again.

---

### Post by s1300045 on 2009-09-06
> **vikrant82 said:**
> Go for libmysqlclient16-dev (or libmysqlclient15-dev). Make sure you clean up build folder before you cmake again.

Thanks! I didn't know I have to clean the build folder. Now it's compiling!

---

### Post by s1300045 on 2009-09-08
I was able to compile from source, but amarok is not scanning the collection. I think it has something to do with libtag. Has anyone had any success yet?

---

