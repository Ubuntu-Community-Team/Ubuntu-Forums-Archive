---
title: "Noob advice: Hardy up to date but need newer package?"
date: 2009-11-01
forum: Server Platforms
---

### Post by photoman355 on 2009-11-01
Hi 

I wan't to update my openssh version to version 4.8p1 or later (I need to use the chrootdirectory function which is only available after this release).  Currently the latest version of openssh available under 8.04LTS is 4.7p1.

What is the best way to update to a package outside an ubuntu release?

The Jaunty openssh package (5.1) is available here [http://packages.ubuntu.com/jaunty/openssh-server](http://packages.ubuntu.com/jaunty/openssh-server).  Is it possible to use these packages in hardy to update or will that cause my system to be unstable as they are designed for jaunty?

Thanks for your help.

---

### Post by Thirtysixway on 2009-11-01
You could either upgrade ubuntu or compile from source.  You may also be able to install it from .deb (I just don't know off the top of my head the commands to do that.)

I'd recommend probably figuring out how to do the .deb option, or upgrade the system.  Source is messy :p

---

### Post by mrsteveman1 on 2009-11-02
Here's a ppa with an updated openssh package for hardy. Whether or not you trust this person is up to you.

[https://launchpad.net/~rainct/+archive/ppa/+packages](https://launchpad.net/~rainct/+archive/ppa/+packages)

That would be the easy route, or search for another PPA with a backported openssh package for hardy, however you might want to simply compile it yourself using the debian method (so it integrates with the package manager). Directions for doing this should be around somewhere in the forum.

---

### Post by Lars Noodén on 2009-11-02
@ photoman355 : I would have expected a newer version of openssh-sever in the [Hardy Backports](http://packages.ubuntu.com/search?keywords=openssh-server&searchon=names&suite=hardy-backports&section=all) repository, but it's not there.  So that leaves apt-pinning.

apt-pinning allows you to select specific versions of specific packages or specific repositories.  

[http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)
[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)
[http://www.howtoforge.com/a-short-introduction-to-apt-pinning](http://www.howtoforge.com/a-short-introduction-to-apt-pinning)
[http://www.argon.org/~roderick/apt-pinning.html](http://www.argon.org/~roderick/apt-pinning.html)

I would not recommend compiling from source, but if you do go that route, I would strongly recommend making your own package.

---

### Post by Lars Noodén on 2009-11-02
You can also file a request that openssh-server be updated for 8.04 (LTS) via backports
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

If you do file a request, please post a link to it here so we can add our 'me, too' to it.

---

### Post by photoman355 on 2009-11-02
Thanks for all your replies.  

Just one more thing I need to know:  The jaunty packages I mentioned that are available from [http://packages.ubuntu.com/jaunty/openssh-server](http://packages.ubuntu.com/jaunty/openssh-server) are these backwards compatible to hardy?

I was thinking I'd do a manual install of the .deb if they are.

---

### Post by Lars Noodén on 2009-11-02
> **photoman355 said:**
> Thanks for all your replies.  

Just one more thing I need to know:  The jaunty packages I mentioned that are available from [http://packages.ubuntu.com/jaunty/openssh-server](http://packages.ubuntu.com/jaunty/openssh-server) are these backwards compatible to hardy?

I was thinking I'd do a manual install of the .deb if they are.

It could be.  An advantage of using the package manager is that it will complain if versions are wrong.  So using the .deb is the way to go, but it could be recommended to use the apt-pinning if the jaunty package turns out to work.  

Were you successful in posting a bug report / request to backports?

---

### Post by photoman355 on 2009-11-16
Hi Lars,

Here's the link to the backport request [https://bugs.launchpad.net/hardy-backports/+bug/286337](https://bugs.launchpad.net/hardy-backports/+bug/286337).  Quite a few request in there already but it looks like it may take a while before something is done.

I've been investigating further and there is a patched version of openssh 4.7p1 that allows chrooting of users [http://sourceforge.net/projects/chrootssh/](http://sourceforge.net/projects/chrootssh/) so that's one possibility.  Am still looking to see if there are any better solutions out there.

---

