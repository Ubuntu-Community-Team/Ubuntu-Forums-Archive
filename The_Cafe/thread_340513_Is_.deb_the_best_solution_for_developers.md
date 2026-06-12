---
title: "Is .deb the best solution for developers"
date: 2007-01-17
forum: The Cafe
---

### Post by Johnsie on 2007-01-17
Ok, I've written a program and have to decide how to distribute it. I had a look into how debs are made and it seemed quite tedious compared to creating a setup.exe. I know that for users (downloaders) the deb system is really easy to user but what about devlopers? Is it the best option? What are the pros and cons of releasing deb files?

Othere alternatives I'm considering are:
-Using tar.gz andhaving the program automatically update itself independently of the repositories. 
-Autopackage
-Binary installer

---

### Post by ComplexNumber on 2007-01-17
> What are the pros and cons of releasing deb files?pros - ubuntu has a large user base at the moment.
cons - other than ubuntu, debian, and derivatives, nobody else uses it. all the big boys distribute their files on rpm.

---

### Post by ssam on 2007-01-17
its not too bad making a deb once you have worked out what the dependencies are and things like that. there ares docs in the wiki and on the debian website. also see [https://wiki.ubuntu.com/MeetingLogs/OpenWeek](https://wiki.ubuntu.com/MeetingLogs/OpenWeek) . i am sure if you ask questions in #ubuntu-motu or the packaging forum here then you will get help.

the alternative is to just provide a .tar.gz and wait for debian or ubuntu to pick it up them self.

---

### Post by ComplexNumber on 2007-01-17
>  the alternative is to just provide a .tar.gz and wait for debian or ubuntu to pick it up them self.i think thats probably the best option too. autopackage is a great idea, but for some unconsciousreason,i still prefer to install an application via synaptic than to go to the autopackage website, download the autopackage package, fire up the terminal, set the permissions of the package to execute, then double click on the package.

---

### Post by Johnsie on 2007-01-17
For something that is updated regularly would I be better having my own repository be a solution? My program is dependent on win32codecs, which I will not be distributing. What are the repo maintainers policies with regard to codec dependent software?

---

### Post by lukew on 2007-01-17
> **Johnsie said:**
> For something that is updated regularly would I be better having my own repository be a solution? My program is dependent on win32codecs, which I will not be distributing. What are the repo maintainers policies with regard to codec dependent software?

Some software in the installation instructions says it is recommends the following... if you want full functionality.

By the sound of things you are writing a media player? I would recommend xyz packages for xyz functionality and only depend upon the things you need for basic functionality.

RPMS have dependancies as well!!

DEB files and RPMS etc are good as they keep the system cleaner when removing things! I always use check install when installing from source!!

Luke

---

### Post by Johnsie on 2007-01-17
The program I'm releasing is at [http://steeky.com/stvlinux](http://steeky.com/stvlinux)

It's a TV watching app, based on mplayer that lets you watch online TV channels.

At the moment it's still in development but there is a tar.gz there that works. I just need to weigh in my options so that I can decide how to distribute it when it's ready.

---

### Post by sassur on 2007-01-18
I think you should consider distribute it in multiple ways. tar.[gz|bz2], deb, rpm, binary package, autopackage, any-other-package-system-you-want-to-support, etc. 
That will lead to a broader user base.

---

### Post by az on 2007-01-18
> **Johnsie said:**
> The program I'm releasing is at [http://steeky.com/stvlinux](http://steeky.com/stvlinux)

It's a TV watching app, based on mplayer that lets you watch online TV channels.

At the moment it's still in development but there is a tar.gz there that works. I just need to weigh in my options so that I can decide how to distribute it when it's ready.

Distribute it at least as source (if you want to be GPL-compliant) and let the distributions worry about packaging it.

Free-libre software is great because of the source.  Everything should come together at the source level.  Binary-compatibility is not important -  especially when it will slow down development.  For example, if you start off aiming for binary-compatibility with even just one distribution, that will end up slowing down progress, since others who would want to contribute to your project and are not running the same OS as you will end up on a different page.

---

