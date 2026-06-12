---
title: "Ubuntu source code (web browsable)?"
date: 2011-11-08
forum: Ubuntu Dev Link Forum
---

### Post by Jonathan L on 2011-11-08
Dear All

Is there a convenient and official place for browsing the whole Ubuntu source trees in one place?  I'm speaking of something like gitweb or websvn interface, for looking at the history and current versions of files.

Thanks all.

Kind regards,
Jonathan.

---

### Post by Jonathan L on 2011-11-11
Hi again ... shameless bump!  Someone must know where the source code is found easily!

Kind regards,
Jonathan.

---

### Post by ikt on 2011-11-11
> **Jonathan L said:**
> Hi again ... shameless bump!  Someone must know where the source code is found easily!

Kind regards,
Jonathan.

Besides launchpad?

---

### Post by Jonathan L on 2011-11-11
> **ikt said:**
> Besides launchpad?

Thanks!  At the risk of sounding idiotic, I've looked there (at some length) and all I find are bug reports and branches with exotic names.  What I'm looking for is the source that matches say, 10.04.3 server CD-ROM image.

Kind regards,
Jonathan.

---

### Post by ikt on 2011-11-12
Don't believe you can do that since there isn't one big source that is the final result, the final release of an ubuntu version is basically just 10's of thousands of packages all frozen in time, this should be shown in launchpad depending on the package.

For example:

[https://launchpad.net/virtualbox/+packages](https://launchpad.net/virtualbox/+packages)

Lucid (10.04)	virtualbox-ose	 Version: **3.2.8**-dfsg-2ubuntu1~lucid1

back in 9.10 it was:

Karmic (9.10)	virtualbox-ose	 **3.0.8**-dfsg-1ubuntu1.1

Getting the source for the packages your looking for depends on which package it was and how they get merged into ubuntu, some projects host their code on launchpad, some on github, some elsewhere.

If you haven't seen this it would be good:

[https://wiki.ubuntu.com/UbuntuDevelopment](https://wiki.ubuntu.com/UbuntuDevelopment)
and loads of info here:
[https://wiki.ubuntu.com/UbuntuDeveloperWeek](https://wiki.ubuntu.com/UbuntuDeveloperWeek)

---

