---
title: "Experimental Packages?"
date: 2007-01-19
forum: Repositories &amp; Backports
---

### Post by randomperson83 on 2007-01-19
Hey, I've been using Gentoo as a server linux for many years, but always used a Windows desktop until now. :) My roommate had good success with Ubuntu, so I figured I'd give it a try. Unfortunately my install experience (Edgy Eft) really sucked due to having too many hard drives and video cards in my machine... but it works now after some work! :D

The thing is, how does one install bleeding-edge packages, or is there even such a functionality? Take for example, ntfs-3g... the last version that synaptic lists there is 9/2006, and theres already been a few releases since then. 

Of course, the ntfs-3g project releases a tgz package, but if theres a pre-packaged version then I'd rather install that. I just don't quite know how to find it. 

If someone could point me to some decent documentation about how the package manager works and how one can obtain dangerous/experimental packages, that would be awesome. Thanks. :)

---

### Post by deadlydeathcone on 2007-01-20
> **randomperson83 said:**
> The thing is, how does one install bleeding-edge packages, or is there even such a functionality? Take for example, ntfs-3g... the last version that synaptic lists there is 9/2006, and theres already been a few releases since then.

There isn't a dedicated repository for bleeding edge packages, but you can find tons of things by either searching the forum for Google. I've found everything I've needed, at least.

As far as ntfs-3g goes, see these two threads:
[URL="http://www.ubuntuforums.org/showthread.php?t=217009"]
 HOWTO: NTFS with read/write support using ntfs-3g[/URL]
[ ntfs-config : NTFS write support made easy]("http://ubuntuforums.org/showthread.php?t=337970")

I just enabled it myself and it's working flawlessly: just enable the repos in the first thread, upgrade and install the correct packages and use the tool in the second thread to enable everything.

As far as sources and repositories go, you can either edit /etc/apt/sources.list or under Gnome use "Software Sources", the gui tool. I've attached my sources.list to get you up to speed, although there are some things on there you may want to comment out (like the suspend2 and nvidia repositories). If you enable trevino's repository you can download his sources.list via apt-get with contains most of the experimental repositories out there.

Anyways good luck, and welcome to the forums!

---

### Post by randomperson83 on 2007-01-20
Awesome. Thanks. :)

---

