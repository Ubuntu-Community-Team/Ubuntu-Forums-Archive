---
title: "Debian Based?   What's the difference?"
date: 2006-02-22
forum: The Cafe
---

### Post by hizaguchi on 2006-02-22
I'm kinda new to Linux, and up until now I've just been using Ubuntu because it was the first distro I tried and it was easy to install.  But I've been checking out some different live CDs lateley and I've been thinking of installing Elive.

My question is, once you get a Debian based OS installed, what is the difference between them?  I mean, if I just changed my repositories from Ubuntu Breezy to Debian Sid, and upgraded everything, would I basically have a Debian system then?  Or is the difference deeper than just the packages you have loaded?

I ask because I recently did a Ubuntu server install on my old computer and just followed one of the guides to getting E17 (partially for fun and partially because I don't use half of what's included in the full Ubuntu install).  Other than the package repositories that are selected by default, is this any different from just installing Elive?

Thanks, and sorry if I'm in the wrong area.  I wasn't exactly sure where this belonged.

---

### Post by heimo on 2006-02-22
How Ubuntu and Debian are related:
[http://www.ubuntu.com/ubuntu/relationship/](http://www.ubuntu.com/ubuntu/relationship/)

---

### Post by hizaguchi on 2006-02-22
Ok, that was a great read, but it mostly talks about philosophy, update policies, and release timelines.  I'm still a little confused.  Is a package from the Ubuntu repositories identical to the same package from Debian?  Or from anywhere else?  Or is there a difference?  And if I wanted to know how to install something that I can't find a package for, and there isn't a howto in these forums, could I follow a guide from any other Debian based OS's forums?  I guess what I'm saying is, how compatable are the distros with each other?

---

### Post by weasel fierce on 2006-02-22
I've generally had no problem using debian packages in ubuntu, but every now and again, you may run into things not working properly

---

### Post by heimo on 2006-02-22
Ubuntu is very close to sid, but with additions. I would not mix any important packages, only in some special case would I install some small piece of software from Debian repository that I knew had very little dependencies. I believe all of the Ubuntu packages are recompiled and may have different dependencies, some of them are (AFAIK) identical in source code, but many have changes. (see the way Ubuntu packages are named '*ubuntu?' where ? is revision in Ubuntu).

Many guides are interchangable between Debian and Ubuntu. You can always use generic binary packages (if available) or compile from source. It's a better idea than mixing packages from different distributions. Ubuntu has... lots of packages and at least for me it's rare that I need something which is not already available (I think I've installed 4-5 applications from source / .tar.gz-"packages").

Hopefully this answered your question a bit better. :)

---

### Post by jasay on 2006-02-22
[QUOTE=hizaguchi]Ok, that was a great read, but it mostly talks about philosophy, update policies, and release timelines.  I'm still a little confused.  Is a package from the Ubuntu repositories identical to the same package from Debian?  Or from anywhere else?  Or is there a difference?  And if I wanted to know how to install something that I can't find a package for, and there isn't a howto in these forums, could I follow a guide from any other Debian based OS's forums?  I guess what I'm saying is, how compatable are the distros with each other?[/QUOTE]Mark Shuttleworth talks a little about compatibility with Debian [here]("https://wiki.ubuntu.com/MarkShuttleworth?highlight=%28shuttleworth%29") (about a third of the way down the page).

---

### Post by xequence on 2006-02-22
Ubuntu works on my computer, debian doesent. (It doesent support my monitor or video or something).

Oh, and with the exception of w32codecs, I dont think you can use the debian repos in ubuntu. They mess it up I heard.

---

### Post by super on 2006-02-22
i found out the hard way that many debian packagess and ubuntu packages are not always compatible. in particular, installing the libc6 and glibc packages in debian repos (which btw provide the base for the entire ubuntu system) will almost assuredly hose your system.

if at all possible **do not use** debian repos with your ubuntu

if you absolutely need a package and you don't want to compile from source (which is probably the better way) download the individual package and dpkg -i it manually.

---

