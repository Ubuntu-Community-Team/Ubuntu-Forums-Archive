---
title: "Should the Ubuntu package suffix be changed?"
date: 2007-11-12
forum: The Cafe
---

### Post by Interestedinthepenguin on 2007-11-12
Does anyone think the package suffix, *.deb*, should be changed to *.ubu*, or something?

This has been on my mind since I first installed Ubuntu...

I was downloading packages for my Ubuntu PC that didn't have an internet connection, and ended up downloading Debian's deb packages, which don't work in Ubuntu.  

That may have an been extremely stupid thing to do, but as a person new to GNU/Linux, I was a bit confused about the packages.  (I'd read a little about Debian, since Ubuntu's one of its forks).

Just my two cents.:)

---

### Post by -grubby on 2007-11-12
it would render all current packages incompatible. And I still don't get why some debian packages don't work with ubuntu or vice versa

---

### Post by Nano Geek on 2007-11-12
I don't think we should. It would just cause extra confusion for users and developers. Plus it would add an yet another packaging format.

---

### Post by Kingsley on 2007-11-12
Debian developers would cry a ****storm if that happened.

---

### Post by jviscosi on 2007-11-12
[Sit, Ubu, sit.  Good dog.]("http://en.wikipedia.org/wiki/Ubu_Productions")

I've actually had fairly good luck installing DEB packages, although I've only done it a couple of times.  I would vote leave them as DEBs if only to acknowledge Ubuntu's heritage.

---

### Post by FG123 on 2007-11-12
Hell no. The .deb represents its compatability with the Debian Package Manager, no need to be special.

---

### Post by Interestedinthepenguin on 2007-11-12
@**jviscosi**: Interesting.:)

I understand you guys. 

I just wanted some opinions.:redface:

---

### Post by boast on 2007-11-12
.deb and .rpm is all that should exist.  and thats too many

---

### Post by Interestedinthepenguin on 2007-11-12
> **boast said:**
> .deb and .rpm is all that should exist.  and thats too many

Really?  Why? ...Am I missing something?

---

### Post by Nano Geek on 2007-11-12
> **Interestedinthepenguin said:**
> Really?  Why? ...Am I missing something?It would be *so* much easier if there weren't two different packages. There really is no use in having two different system for installing software.

---

### Post by yabbadabbadont on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> It would be *so* much easier if there weren't two different packages. There really is no use in having two different system for installing software.

Exactly, they should all be tgz files, Slackware style...  ;)

Actually, no need for prebuilt packages at all.  Use a package management system that can build from source.  BSD ports, Gentoo portage, Arch ABS (?), SourceMage spells, and so forth.  :D

---

### Post by reacocard on 2007-11-12
> **yabbadabbadont said:**
> Exactly, they should all be tgz files, Slackware style...  ;)

Actually, no need for prebuilt packages at all.  Use a package management system that can build from source.  BSD ports, Gentoo portage, Arch ABS (?), SourceMage spells, and so forth.  :D

the problem with building from source is it takes more disk space and time to install anything. packages + repositories let software be built once, then used by many different people, ultimately saving large amounts of time. also, can you imagine how much worse that would be on say a 500mhz processor w/ 4gb disk space? ubuntu can run fine on such a system, and apt is only marginally slowed down, but compiling from source would take much longer.

I admit it'd be nice to have a universal package format, but it's not likely to happen due to binary (and other) incompatibilities among distros.

---

### Post by yabbadabbadont on 2007-11-12
> **reacocard said:**
> can you imagine how much worse that would be on say a 500mhz processor w/ 4gb disk space?
**I** don't have to imagine it...  although, technically, I had 6GB of disk space.  :)
> **reacocard said:**
> I admit it'd be nice to have a universal package format...
A source based package manager *is* a universal package format.  It is the most universal one there is.  ;)

---

### Post by Adrenal on 2007-11-12
> **asjdfwejqrfjcvm msz34rq33 said:**
> It would be *so* much easier if there weren't two different packages. There really is no use in having two different system for installing software.
Yeh, who needs competition? Load of tosh if you ask me

---

### Post by reacocard on 2007-11-12
> **yabbadabbadont said:**
> **I** don't have to imagine it...  although, technically, I had 6GB of disk space.  :)

my point still stands. it's certainly possible, just a lot less convenient, especially with more-complex software such as firefox, openoffice and the linux kernel.

> A source based package manager *is* a universal package format.  It is the most universal one there is.  ;)

true enough. perhaps the best method would be a combination of the two: allow repositories containing binary packages built again different distros, and also providing source packages. If a suitable binary package cannot be found, install from the source package instead. However this still has the not-insignificant overhead of requiring the user to install a compiler and development headers the first time this happens.

personally, I'm quite happy with apt. there are very few things I use that I don't get from the repos, and that's usually because it's either software that's still early in development and simply hasn't made it in yet (eg. AWN), upstream updates much more frequently than the repos (eg Exaile), or its simply a niche app that hasn't seen enough use to be put into universe yet (eg. falcon). For such apps, I either use a provided third-party repo, or build my own packages and host them in [my repo]("http://syzygy42.tuxfamily.org/"), allowing other people to use this software without the overhead of source.

---

### Post by Scruffynerf on 2007-11-13
Well, we already have:
.deb
.rpm
.tar
.gz
.autopackage
.run
.sh

... and I'm sure that there are plenty others available, such as things through CVS and SVN. Why do you want to add another?

---

### Post by reacocard on 2007-11-13
> **Scruffynerf said:**
> Well, we already have:
.deb
.rpm
.tar
.gz
.autopackage
.run
.sh

... and I'm sure that there are plenty others available, such as things through CVS and SVN. Why do you want to add another?

I don't. I'm just saying I like the idea of a universal format that would *replace* all of these, but also that the technical difficulties of doing so make such an endeavor unlikely to succeed.

---

### Post by Joedude on 2007-11-13
I don't think it should change at all. Nor do I care about universal packaging, source pm, or even coming up with a "linux standard" package.

Diversity is what makes linux, liniux. You may have a distro which uses red hat package management, debian package management and all linuces can compile from source. Adding a new one as an all encompasing would be redundant and a waste of time. Choosing either RPM or DEB as a base  won't work either. It's like putting diesel in an unleaded engine. Ubuntu is based on debian, because at the end of the day, it is the best distro out there.

---

### Post by yabbadabbadont on 2007-11-13
> **reacocard said:**
> my point still stands. it's certainly possible, just a lot less convenient, especially with more-complex software such as firefox, openoffice and the linux kernel.
What point?  Unless you have done it yourself, you have no basis for your conclusion.  It was quite usable as I only had those features that I actually needed included in each package.  This meant lower memory and disk space requirements.  Yes, some packages would take a while to build.  You just have to decide if the time spent on them is worth it (or use binaries just for those few packages).  Even then it wasn't a big deal as I just kicked off the build before leaving for work or going to bed.

> **reacocard said:**
> true enough. perhaps the best method would be a combination of the two: allow repositories containing binary packages built again different distros, and also providing source packages. If a suitable binary package cannot be found, install from the source package instead. However this still has the not-insignificant overhead of requiring the user to install a compiler and development headers the first time this happens.

That pretty much describes two of the systems I mentioned previously.  BSD and Arch.  :)

---

### Post by thx11381974 on 2007-11-13
> **reacocard said:**
> I don't. I'm just saying I like the idea of a universal format that would *replace* all of these, but also that the technical difficulties of doing so make such an endeavor unlikely to succeed.

I think a universal format is a great idea not having one is holding Linux back. I don't think it would be a matter of technology, but getting the various distros to agree. That may be imposable

---

### Post by conehead77 on 2007-11-13
> **thx11381974 said:**
> I think a universal format is a great idea not having one is holding Linux back. I don't think it would be a matter of technology, but getting the various distros to agree. That may be imposable

Why is this holding Linux back?

---

### Post by thx11381974 on 2007-11-13
> **conehead77 said:**
> Why is this holding Linux back?

Having half a dozen formats confuses users & makes it difficult for hardware manufacturers to put out drivers and software for their hardware. Presently it's not economically worth while to develop hardware drivers for linux who's users are less than 5% of the market. Distro's agreeing to a single package system would help just about every aspect of Linux. 
Uniformity is why Microsoft controls the computer market.

---

### Post by adam.tropics on 2007-11-13
> **thx11381974 said:**
> Having half a dozen formats confuses users & makes it difficult for hardware manufacturers to put out drivers and software for their hardware. Presently it's not economically worth while to develop hardware drivers for linux who's users are less than 5% of the market. Distro's agreeing to a single package system would help just about every aspect of Linux. 

Not sure you know. I can see that the differing packaging systems might mean they (hardware manufacturers) are reluctant to package drivers, but I don't think it is in their reasons for not developing them.
> **thx11381974 said:**
> 
Uniformity is why Microsoft controls the computer market.

Microsoft doesn't control the market. Their customers' do, and generally I think they have more power in controlling it than they give themselves credit for.

Back on topic though...unless Ubuntu come up with a new package manager that doesn't for some odd reason handle any current format, then no, it's just unnecessary. People should just be a bit wary what they install, as with any other OS.

---

### Post by thx11381974 on 2007-11-13
> **adam.tropics said:**
> Microsoft doesn't control the market. Their customers' do, and generally I think they have more power in controlling it than they give themselves credit for.

I agree, my point was uniformity is the #1 thing M$ gives them.

---

### Post by Joedude on 2007-11-13
Uniformity is also one of the many reasons MS products are easily succeptable to viruses, malware and spyware.

---

### Post by K.Mandla on 2007-11-13
> **Interestedinthepenguin said:**
> Does anyone think the package suffix, *.deb*, should be changed to *.ubu*, or something?
Nah.

---

### Post by Scruffynerf on 2007-11-13
> **Joedude said:**
> Uniformity is also one of the many reasons MS products are easily succeptable to viruses, malware and spyware.

No, that would be bad coding practices. Only MS developers ever see MS code. Some third party groups spend a fortune to buy aspects of the code (API's) to develop their products on.

Also, there's a bunch of viruses for windows simply owing to the install base.

---

### Post by Frak on 2007-11-13
.ubu wouldn't be difficult, just some changes to the dh_make software is needed, along with dpkg. But most of the changes would be trivial.

Also, the utnubu team would only have to go through the only change of changing extensions. The repos could just use a VERY simple script to change all instances of .deb into .ubu

---

### Post by Interestedinthepenguin on 2007-11-13
> **Frak said:**
> .ubu wouldn't be difficult, just some changes to the dh_make software is needed, along with dpkg. But most of the changes would be trivial.

Also, the utnubu team would only have to go through the only change of changing extensions. The repos could just use a VERY simple script to change all instances of .deb into .ubu


That's what I was thinking (minus the part about dh_make as I've never heard of it.)!:)

---

