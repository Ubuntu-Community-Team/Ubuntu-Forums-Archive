---
title: "Artful Aardvark Release Schedule, Partial Upgrades, and Common Questions"
date: 2017-04-20
forum: Ubuntu Development Version
---

### Post by cariboo on 2017-04-20
This is where you will find the Artful Aardvark release schedule, as well as the answers to frequently asked questions.

[Release Schedule ]("https://wiki.ubuntu.com/ArtfulAardvark/ReleaseSchedule")

If you are asked to do a partial upgrade, please read this first:

[Partial upgrade]("https://wiki.ubuntu.com/U%2B1/partial_upgrade")

There always are many questions about what to do and how to do things during a release cycle:

[Common Questions]("https://wiki.ubuntu.com/U%2B1/common-problems")

If you are looking for the Daily iso's, have a look here:

Ubuntu - coming soon
Kubuntu - coming soon
Xubuntu - coming soon
Lubuntu - coming soon
Ubuntu Mate - coming soon
Ubuntu Budgie - coming soon

As many of you may know we have created a U+1 testing team to do a better job of reporting bugs, and generally to make things better for all during the testing cycle. To that end, we have created a wiki where a lot of information regarding testing is available. You don't have to be a team member to be able to test , testing is open to everyone regardless of your experience level. That being said, to get the most possible feedback from your bug reports, check this out, before creating a bug report:

[Create a good bug report]("https://help.ubuntu.com/community/ReportingBugs") 

Here are some more useful links:

[Artful changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/Artful-changes")

[Ubuntu Developers ]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel")

Note: This post will be updated as more information becomes available

---

### Post by ventrical on 2017-04-22
Ubuntu.info file:

```
Suite: bionic
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 17.10 'bionic beaver'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
ParentComponent: universe
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: bionic
ParentSuite: bionic
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 17.10 'bionic beaver'

Suite: bionic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*17.10
MatchURI: cdrom:\[Ubuntu.*17.10
Description: Cdrom with Ubuntu 17.10 'bionic beaver'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: bionic
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: bionic
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: bionic-security
ParentSuite: bionic
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: bionic-security
ParentSuite:bionic
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: bionic-updates
ParentSuite: bionic
RepositoryType: deb
Description: Recommended updates

Suite:bionic-updates
ParentSuite: bionic
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: bionic-proposed
ParentSuite: bionic
RepositoryType: deb
Description: Pre-released updates

Suite: bionic-proposed
ParentSuite: bionic
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: bionic-backports
ParentSuite: bionic
RepositoryType: deb
Description: Unsupported updates

Suite: bionic-backports
ParentSuite: bionic
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates
```

---

### Post by ventrical on 2017-10-25
@cariboo

I edited the Ubuntu.info file and properties-software-gtk still pops up. any ideas ?

Regards..

---

### Post by cariboo on 2017-10-25
I plan on updating the thread when I get a little more time on my weekend (Monday - Tuesday next week). Things are pretty busy in the cariboo household at the moment. :)

---

### Post by flocculant on 2017-10-26
> **ventrical said:**
> @cariboo

I edited the Ubuntu.info file and properties-software-gtk still pops up. any ideas ?

Regards..

works here - grabbed needed update from -proposed

---

### Post by wildmanne39 on 2017-10-26
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by ventrical on 2017-10-26
> **flocculant said:**
> works here - grabbed needed update from -proposed

On this one install I did everything ... but can't get software&updates to work.  How did you do it from the terminal?

---

### Post by cariboo on 2017-10-26
Try adding:

```
deb http://ca.archive.ubuntu.com/ubuntu/ bionic-proposed restricted universe main multiverse

```

to /etc/apt/sources.list

---

### Post by flocculant on 2017-10-26
> **cariboo said:**
> Try adding:

```
deb http://ca.archive.ubuntu.com/ubuntu/ bionic-proposed restricted universe main multiverse

```

to /etc/apt/sources.list

This. Except I always use Main Server.

---

### Post by ventrical on 2017-10-26
> **cariboo said:**
> Try adding:

```
deb http://ca.archive.ubuntu.com/ubuntu/ bionic-proposed restricted universe main multiverse

```

to /etc/apt/sources.list

That got it back online :)
Thanks .. Regards..

---

