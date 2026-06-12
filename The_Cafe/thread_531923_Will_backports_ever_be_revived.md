---
title: "Will backports ever be revived"
date: 2007-08-22
forum: The Cafe
---

### Post by siimo on 2007-08-22
Well since Breezy days or so when backport became official.. nothing significant  that is actually useful has actually been backported.   I'm talkin stuff like Pidgin or Deluge torrent or GIMP etc.    Kinda sucks if you ask me.  Pigin 2.1.1 came out today and since Gibbon is already in version freeze it wont have it.   ](*,)

Don't tell me to compile it myself or use some stupid site like getdeb.  How about a proper backport repo where we can grab updates.. with a big fat warning that they are not supported of course.

1. Fedora provides updates.
2. Mandriva has backports too.
3. As does SUSE
4. Ubuntu ??? 

Not flaming these are serious questions.   This is 2007 for gods sake, even in windows 95 people could update softwares easily without upgrading to new version of OS.   If other distros support it then why not ubuntu who actually did use to do it thanks to the community backports when they first came out.. but making them official sorta killed it.  :frown:

---

### Post by mostwanted on 2007-08-22
+1

I have been wondering about this myself.

---

### Post by curuxz on 2007-08-22
Don't mean this in a nasty way, but why don't YOU join the backporting team and help them out.

I know its a pain but if we all try and fix the problems we see instead of reporting them and waiting for someone else to do it we will move much faster. Its what the japanese call TQM or near enough to that principal. 

It should also be noted that the other distro's you have mentioned are much more commercially run that ubuntu and far more established IMHO.

Maybe you could make a list of the stuff you want back-ported to LTS? Then ask someone to show you how to start doing it, as far as I know its not that hard :)

---

### Post by wildkarde on 2007-08-22
What's wrong with getdeb?

---

### Post by tdrusk on 2007-08-22
> **wildkarde said:**
> What's wrong with getdeb?

The only problem I see with it is it doesn't give you a system update when a new program is released.

---

### Post by eentonig on 2007-08-22
> user@host:$ apt-cache search webmin
webmin - A web-based administration interface for Unix systems.
user@host:$ sudo apt-get install webmin

and 
> user@host:$ tasksel

Does two should do the trick

---

### Post by phrostbyte on 2007-08-22
More backports please!

---

### Post by kostkon on 2007-08-22
I suppose, that now with the [availability  of *PPAs (Personal Package Archives)* from today]("http://www.ubuntu.com/news/launchpad-personal-package-archive"), *Backports* would be one of the many repositories. Now, easily anyone can make their own, so I think the problem of getting fresh versions of applications from repositories will be solved.

PPAs is a briliant idea I believe. What do you think?

---

### Post by mostwanted on 2007-08-24
> **kostkon said:**
> I suppose, that now with the [availability  of *PPAs (Personal Package Archives)* from today]("http://www.ubuntu.com/news/launchpad-personal-package-archive"), *Backports* would be one of the many repositories. Now, easily anyone can make their own, so I think the problem of getting fresh versions of applications from repositories will be solved.

PPAs is a briliant idea I believe. What do you think?

WOW! That is actually amazing. Canonical are centering the "unofficial" developer community around Ubuntu. This is a great way of keeping track of the core Ubuntu packages as well the unoffical packages and with time it could probably be integrated somewhat into the package manager (like a* search PPAs *function in Synaptic).

Very exciting. I'm hoping they will make a big deal out of promoting this.

---

### Post by jethro10 on 2007-08-24
> **siimo said:**
> Well since Breezy days or so when backport became official.. nothing significant  that is actually useful has actually been backported.   I'm talkin stuff like Pidgin or Deluge torrent or GIMP etc.    Kinda sucks if you ask me.  Pigin 2.1.1 came out today and since Gibbon is already in version freeze it wont have it.   ](*,)

Don't tell me to compile it myself or use some stupid site like getdeb.  How about a proper backport repo where we can grab updates.. with a big fat warning that they are not supported of course.

1. Fedora provides updates.
2. Mandriva has backports too.
3. As does SUSE
4. Ubuntu ??? 

Not flaming these are serious questions.   This is 2007 for gods sake, even in windows 95 people could update softwares easily without upgrading to new version of OS.   If other distros support it then why not ubuntu who actually did use to do it thanks to the community backports when they first came out.. but making them official sorta killed it.  :frown:
I totally agree.
However calling getdeb stupid is childish and immature. It provides a very useful service to me and many others. This comment did not help anything.
Jeff

---

### Post by kanem on 2007-08-24
> **jethro10 said:**
> I totally agree.
However calling getdeb stupid is childish and immature. It provides a very useful service to me and many others. This comment did not help anything.
Jeff
Wow, I had never heard about getdeb before. That site is great. So why doesn't this satisfy people's need for more backports? Because it's not from Canonical?

Edit:
Oh wait, fuzzyhair already answered that question. Doesn't seem like a big deal to me having to go to the getdeb site instead of having synaptic do it. Besides, if getdeb packages were in a repository that we could use, update-manager would want to upgrade *all* the packages that getdeb has, not just the one I want. So I'd have to not have the getdeb repository enabled most of the time. Then when I want something from them, enable their repository, see if they have the package, install it, then disable the repository again. It'd be just as easy to just go to the site and download it.

---

### Post by phrostbyte on 2007-08-24
> **kostkon said:**
> I suppose, that now with the [availability  of *PPAs (Personal Package Archives)* from today]("http://www.ubuntu.com/news/launchpad-personal-package-archive"), *Backports* would be one of the many repositories. Now, easily anyone can make their own, so I think the problem of getting fresh versions of applications from repositories will be solved.

PPAs is a briliant idea I believe. What do you think?

It'll be nice if there was a"hobbyist" guide to packing Debian software somewhere. I'm sure a lot of people would be intimidated to use a service like that.

---

### Post by Hobbsee on 2007-08-24
> **phrostbyte said:**
> It'll be nice if there was a"hobbyist" guide to packing Debian software somewhere. I'm sure a lot of people would be intimidated to use a service like that.

The packaging guide is at [http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html](http://doc.ubuntu.com/ubuntu/packagingguide/C/index.html) - See [https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New) for information on getting a package integrated into Ubuntu - Other developer resources are at [https://wiki.ubuntu.com/DeveloperResources](https://wiki.ubuntu.com/DeveloperResources) - See also !backports

Unfortunately, there is no "easy" way to do packaging - it actually requires knowing what you're doing, so you don't break things.

---

### Post by kostkon on 2007-08-24
> **phrostbyte said:**
> It'll be nice if there was a"hobbyist" guide to packing Debian software somewhere. I'm sure a lot of people would be intimidated to use a service like that.

The main advantage of PPAs is that all the projects hosted at Launchpad will be able to offer an repository. 

Take for example projects like *AWN*, which is very successful, or *Deluge*, will be able easily to offer you a safe and secure repository to add to your software sources list.

Also for projects outside Launchpad, think of someone that knows about packaging and/or he/she is an developer and likes very much *Pidgin*, for example, will setup a repository for it, and so on, so on.

Thus, the need for *Backports* or even *getdeb.net* will lessen over time I believe.

---

