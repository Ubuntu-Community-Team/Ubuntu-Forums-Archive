---
title: "legally unencumbered stepmania 3.9 theme"
date: 2006-12-10
forum: The Cafe
---

### Post by Simon80 on 2006-12-10
Hey everybody, I've been working on packaging StepMania 3.9 so that I can get it into universe for feisty.  Currently StepMania from cvs is too rough to package for a release, I have packages of that as well.  Anyway, the thing that's keeping StepMania out right now is the fact that 3.9's default theme is in dubious legal status.  If anybody can find a theme that isn't a derivative work, and is also licensed in compliance with the [DFSG]("http://www.debian.org/social_contract"), then I can use that instead, and hopefully get stepmania into Ubuntu.  Alternatively, if any enterprising artists want to design their own Ubuntu-themed stepmania theme, that would be even cooler, but probably too much effort.  See [Creating a Theme]("http://www.stepmania.com/wiki/Creating_a_Theme") on the stepmania wiki if you're interested in doing this.

My packages for stepmania 3.9 are published at [http://www.eng.uwaterloo.ca/~sruggier/files/apt/](http://www.eng.uwaterloo.ca/~sruggier/files/apt/), if anyone wants to use them now.  If you're on edgy i386, you can just grab the binary packages [stepmania]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania_3.9-0ubuntu1_i386.deb") and [stepmania-data]("http://www.eng.uwaterloo.ca/~sruggier/files/apt/stepmania-data_3.9-0ubuntu1_all.deb").  Otherwise, you can get the *.dsc, *.orig.tar.gz, and *.diff.gz files, and then build them with dpkg-source and debuild.  The stepmania-data package basically contains a little bit of fluff, and the default theme, which needs replacing.

Update: I've decided it makes more sense to try to clarify the license of the latest version instead of 3.9, since it's only a matter of time before 3.9 becomes obsoleted by a new release, and the themes are incompatible.

---

