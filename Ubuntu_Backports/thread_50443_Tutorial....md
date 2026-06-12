---
title: "Tutorial..."
date: 2005-07-20
forum: Ubuntu Backports
---

### Post by Kyral on 2005-07-20
Yanno, there should be a HOWTO on how to Backport stuff, it would take some of the load off of the "official" Backporters.

ie, someone requests a package backported. Instead of the Backporters going through the work to see if its possible, the person could build thier own package then send it into Staging.

Just an idea :D I know there have been times where I have wanted to backport something but just didn't know how to

---

### Post by redlabour on 2005-07-20
[QUOTE=Kyral]Yanno, there should be a HOWTO on how to Backport stuff, it would take some of the load off of the "official" Backporters.

ie, someone requests a package backported. Instead of the Backporters going through the work to see if its possible, the person could build thier own package then send it into Staging.

Just an idea :D I know there have been times where I have wanted to backport something but just didn't know how to[/QUOTE]
 And i love this Idea ! :D 

BTW - it was nice if the Backports rulez where enlarged by the Point "Show your Support for a Request by klicking on Rating Thread or a thing like this". 

[http://www.mandrivaclub.com/modules.php?name=RPM](http://www.mandrivaclub.com/modules.php?name=RPM)

---

### Post by ubuntp on 2005-07-20
A quick guide to get you started.

First of all if the package is in breezy it's fairly simple. Just adjust your /etc/apt/sources.list so that all deb-src entries reference breezy and not hoary. You can have deb as hoary and deb-src as breezy mixed, no problem.

Then grab the package from breezy via **sudo apt-get source package**, if you don't know the exact package name you can likely find it out by using *apt-cache search name_of_the_program*.

apt-get will download the package, and unpack it into a directory. Now go into that directory, if you want to you can adjust some stuff in debian/rules, but you can just leave it at default.

Now run **sudo dpkg-buildpackage** while being in the directory of the extracted package. Now dpkg will tell you if any dependencies are unmet, and if yes, will abort. Most of the time you'll need to install some -dev packages. Once all packages are installed dpkg-buildpackage will build the .deb and that's it (if all goes as planned). You'll have to adjust the version string before if you want to upload as an official backport.

If the package is not in breezy and you have to build it from source it becomes more complicated (especially if you want to make an official package). I'll leave that for another day or someone else :D

---

### Post by sjmorgan on 2005-07-20
```
sudo apt-get build-dep package
``` should sort out any build dependencies. Also ```
fakeroot apt-get -b source package
``` will automagically download and build the package for you in one go.

---

### Post by Kyral on 2005-07-20
How would I edit the version string and upload it to Backport Mirrors?

---

### Post by Kyral on 2005-07-20
Just a status update: I successfully backported FF 1.0.5 from Breezy Source. Now what do I have to do to become an official Backporter? :P

This may just be my drive to give back to Ubuntu coming out...

---

### Post by Velvet Elvis on 2005-07-20
A package built for others to use on their own systems still needs to be built according to the canonical debian maintainers guide doesn't it?

[http://www.debian.org/doc/maint-guide/index.en.html#contents](http://www.debian.org/doc/maint-guide/index.en.html#contents)

If people are going to be posting links to packages they have built themselves, I'd really like to know what method they used to build them and what libraries they compiled against if not vanilla hoary,

I personally don't want to install any packages on my system that are not built 100% to spec, which I assume are still the debian standards in all their anal glory.

I didn't even like using checkinstall when I was running slackware.

---

### Post by Kyral on 2005-07-20
I'm using a stock hoary install, as far as libs go

Only non-Ubuntu stuff I've installed has been Cedega + Point2Play and UT2k4

---

### Post by jdong on 2005-07-20
Google **ubp-build.py**; it's a Python script that I made that creates backported packages. Search the board, too.. it's been mentioned a few times.

---

### Post by Kyral on 2005-07-20
Cool. The only other package I've gotten to work is XChat 2.4.4 (flawlessly)

How would I/Can I get this into the repos?

(Why do I feel like I'm about to be scolded?)

---

