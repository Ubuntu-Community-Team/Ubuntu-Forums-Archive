---
title: "Any plans on Apache 2.4.1?"
date: 2012-12-11
forum: Server Platforms
---

### Post by OneSeventeen on 2012-12-11
I'm just curious if Apache 2.4 is on the roadmap.  I realize apache is a HUGE undertaking to support and change, but was just curious since I'm using ubuntu-server to power my development servers (and production webservers) and just recently discovered that when you use the apache module vhost_alias it doesn't update the apache DocumentRoot variable properly. (therefore breaking many frameworks, wordpress, and other web applications)

This was fixed in 2.4.1 but I'm not one to go against the vanilla Ubuntu packages.

Just curious since I don't really know what goes into changing something as fundamental as Apache.

---

### Post by Cheesemill on 2012-12-11
There are quite a few things that need to happen before Apache 2.4 reaches the official Ubuntu repositories.

Packages for the next version of Ubuntu are taken from Debian Testing.

Currently Apache 2.4.2 is only availible in Debian Experimental, this package will be tested until it has no critical bugs before being moved to Debian Unstable. It then undergoes more rounds of bug testing and QA before being moved again to Debian Testing, at which point it will be available for incorporation into whatever version of Ubuntu is being developed at the time.

To be included in a specific Ubuntu release, all of this has to happen before the 'Debian Import  Freeze' date in the release cycle. For 13.04 this is 14th Feb 2013, I think that it's highly unlikely that this will happen in time so my best guesstimation is that we won't see Apache 2.4 in the Ubuntu repositories until 13.10 at the earliest, it will definately be ready for the next LTS release (14.04).

Also bear in mind that Apache 2.4 will ***never*** be available in the official repositories for versions of Ubuntu that have already been released. If you want to stay with the vanilla repositories you will have to upgrade your machines to whichever version of Ubuntu is released with Apache 2.4 already included.

Some links and reading for you:
[Current state of apache2 in Debian.]("http://packages.debian.org/search?keywords=apache2&searchon=names&suite=all&section=all")
[Debian release information.]("http://wiki.debian.org/DebianReleases")
[Ubuntu 13.04 release schedule.]("https://wiki.ubuntu.com/RaringRingtail/ReleaseSchedule")
[Why current releases will never get Apache 2.4.]("http://askubuntu.com/questions/151283/why-dont-the-ubuntu-repositories-have-the-latest-versions-of-software")

---

