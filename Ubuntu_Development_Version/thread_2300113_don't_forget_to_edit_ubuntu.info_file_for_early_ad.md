---
title: "don't forget to edit ubuntu.info file for early adopters"
date: 2015-10-23
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-10-23
Check out this link here - [https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work](https://wiki.ubuntu.com/U%2B1/common-problems#Software-Properties-Gtk_doesn.27t_work)

and manually edit out all instances of 'devel' or 'wily' and insert 'xenial' you will get rid of software-properties-gtk error or wait until Cariboo puts up his edit as he has been doing this for quite some time through many distribution cycles.

btw  ... here is my share..

> 
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)

Suite: xenial
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 16.04 'xenial xerus'
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

Suite: xenial
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 16.04 'xenial xerus'

Suite: xenial
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: xenial
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: xenial-security
ParentSuite: xenial
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: xenial-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: xenial-updates
ParentSuite: xenial
RepositoryType: deb
Description: Recommended updates

Suite: xenial-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: xenial-proposed
ParentSuite: xenial
RepositoryType: deb
Description: Pre-released updates

Suite: xenial-proposed
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: xenial-backports
ParentSuite: xenial
RepositoryType: deb
Description: Unsupported updates

Suite: xenial-backports
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates



Regards..

---

### Post by VinDSL on 2015-10-23
Indubitably !!!

But, often overlooked...  ;)

---

### Post by cariboo on 2015-10-23
I didn't need it last cycle, and so far it looks like it won't be needed this cycle either.

---

### Post by zika on 2015-10-24
> **cariboo said:**
> I didn't need it last cycle, and so far it looks like it won't be needed this cycle either.The only thing that I know of that uses that file is GUI way of keeping sources up-to date and changing them. If You (like many of us) do not use GUI for that You will not get any kind of error and later in the cycle that file gets upgraded... ;)

---

### Post by zika on 2015-10-24
> **cariboo said:**
> I didn't need it last cycle, and so far it looks like it won't be needed this cycle either.The only thing that I know of that uses that file is GUI way of keeping sources up-to date and changing them. If You (like many of us) do not use GUI for that You will not get any kind of error and later in the cycle that file gets upgraded... ;) There is no need, of course, to change anything (including &#8222;devel&#8220; as proposed in the first post in this thread), just add proper section (let's say at proper place but place is irrelevant). I know that You know that, just making observation for possible newcomers. ;)
(I did check necessity of changing that file in order not to get error, yesterday, and it is still present, at least at my install)

---

### Post by ventrical on 2015-10-24
> **VinDSL said:**
> Indubitably !!!

But, often overlooked...  ;)

I use unity7 and xubuntu-desktop so if I do not have the file changed over after sources.list update I will get software-propeties-gtk error when trying to access software&updates. As mentioned by zika, yes .. it gets updated eventually but it is less aggravation to have that error on bootup , especially when I am using xubuntu-desktop which I consider as a super-cli with bells :) lol

---

### Post by cariboo on 2015-10-24
I'm using synaptic to do updates, I downloaded approximately 45 packages without any problems so far.

---

### Post by VinDSL on 2015-10-24
Different strokes...

I go the opposite direct of both of you guys.  I just keep adding to the list.  LoL :D

No harm, no foul:

```
ChangelogURI: http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog

Suite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu development series
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

Suite: devel
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: xenial
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 15.10 'xenial werewolf'
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

Suite: xenial
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 15.10 'xenial werewolf'

Suite: xenial
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*15.
MatchURI: cdrom:\[Ubuntu.*15.10
Description: Cdrom with Ubuntu 15.10 'xenial werewolf'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: xenial
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: xenial
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: xenial-security
ParentSuite: xenial
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: xenial-security
ParentSuite:xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: xenial-updates
ParentSuite: xenial
RepositoryType: deb
Description: Recommended updates

Suite:xenial-updates
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: xenial-proposed
ParentSuite: xenial
RepositoryType: deb
Description: Pre-released updates

Suite: xenial-proposed
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: xenial-backports
ParentSuite: xenial
RepositoryType: deb
Description: Unsupported updates

Suite: xenial-backports
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 15.10 'Wily Werewolf'
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

Suite: wily
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 15.10 'Wily Werewolf'

Suite: wily
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*15.10
MatchURI: cdrom:\[Ubuntu.*15.10
Description: Cdrom with Ubuntu 15.10 'Wily Werewolf'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: wily
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: wily-security
ParentSuite: wily
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: wily-security
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb
Description: Recommended updates

Suite: wily-updates
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb
Description: Pre-released updates

Suite: wily-proposed
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb
Description: Unsupported updates

Suite: wily-backports
ParentSuite: wily
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: vivid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 15.04 'Vivid Vervet'
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

Suite: vivid
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 15.04 'Vivid Vervet'

Suite: vivid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*15.04
MatchURI: cdrom:\[Ubuntu.*15.04
Description: Cdrom with Ubuntu 15.04 'Vivid Vervet'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: vivid
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: vivid
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: vivid-security
ParentSuite: vivid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: vivid-security
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: vivid-updates
ParentSuite: vivid
RepositoryType: deb
Description: Recommended updates

Suite: vivid-updates
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: vivid-proposed
ParentSuite: vivid
RepositoryType: deb
Description: Pre-released updates

Suite: vivid-proposed
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: vivid-backports
ParentSuite: vivid
RepositoryType: deb
Description: Unsupported updates

Suite: vivid-backports
ParentSuite: vivid
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: utopic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.10 'Utopic Unicorn'
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

Suite: utopic
ParentSuite: utopic
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.10 'Utopic Unicorn'

Suite: utopic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.10
MatchURI: cdrom:\[Ubuntu.*14.10
Description: Cdrom with Ubuntu 14.10 'Utopic Unicorn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: utopic
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: utopic
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: utopic-security
ParentSuite: utopic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: utopic-security
ParentSuite: utopic
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: utopic-updates
ParentSuite: utopic
RepositoryType: deb
Description: Recommended updates

Suite: utopic-updates
ParentSuite: utopic
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: utopic-proposed
ParentSuite: utopic
RepositoryType: deb
Description: Pre-released updates

Suite: utopic-proposed
ParentSuite: utopic
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: utopic-backports
ParentSuite: utopic
RepositoryType: deb
Description: Unsupported updates

Suite: utopic-backports
ParentSuite: utopic
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 14.04 'Trusty Tahr'
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

Suite: trusty
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 14.04 'Trusty Tahr'

Suite: trusty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*14.04
MatchURI: cdrom:\[Ubuntu.*14.04
Description: Cdrom with Ubuntu 14.04 'Trusty Tahr'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: trusty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: trusty-security
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb
Description: Recommended updates

Suite: trusty-updates
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb
Description: Pre-released updates

Suite: trusty-proposed
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb
Description: Unsupported updates

Suite: trusty-backports
ParentSuite: trusty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: saucy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.10 'Saucy Salamander'
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

Suite: saucy
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.10 'Saucy Salamander'

Suite: saucy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.10
MatchURI: cdrom:\[Ubuntu.*13.10
Description: Cdrom with Ubuntu 13.10 'Saucy Salamander'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: saucy
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: saucy-security
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb
Description: Recommended updates

Suite: saucy-updates
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb
Description: Pre-released updates

Suite: saucy-proposed
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb
Description: Unsupported updates

Suite: saucy-backports
ParentSuite: saucy
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 13.04 'Raring Ringtail'
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

Suite: raring
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 13.04 'Raring Ringtail'

Suite: raring
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*13.04
MatchURI: cdrom:\[Ubuntu.*13.04
Description: Cdrom with Ubuntu 13.04 'Raring Ringtail'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: raring
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: raring-security
ParentSuite: raring
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: raring-security
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb
Description: Recommended updates

Suite: raring-updates
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb
Description: Pre-released updates

Suite: raring-proposed
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb
Description: Unsupported updates

Suite: raring-backports
ParentSuite: raring
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: quantal
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.10 'Quantal Quetzal'
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

Suite: quantal
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.10 'Quantal Quetzal'

Suite: quantal
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.10
MatchURI: cdrom:\[Ubuntu.*12.10
Description: Cdrom with Ubuntu 12.10 'Quantal Quetzal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: quantal
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: quantal
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: quantal-security
ParentSuite: quantal
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: quantal-security
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: quantal-updates
ParentSuite: quantal
RepositoryType: deb
Description: Recommended updates

Suite: quantal-updates
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: quantal-proposed
ParentSuite: quantal
RepositoryType: deb
Description: Pre-released updates

Suite: quantal-proposed
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: quantal-backports
ParentSuite: quantal
RepositoryType: deb
Description: Unsupported updates

Suite: quantal-backports
ParentSuite: quantal
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 12.04 'Precise Pangolin'
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

Suite: precise
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 12.04 'Precise Pangolin'

Suite: precise
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*12.04
MatchURI: cdrom:\[Ubuntu.*12.04
Description: Cdrom with Ubuntu 12.04 'Precise Pangolin'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: precise
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: precise-security
ParentSuite: precise
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: precise-security
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb
Description: Recommended updates

Suite: precise-updates
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb
Description: Pre-released updates

Suite: precise-proposed
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb
Description: Unsupported updates

Suite: precise-backports
ParentSuite: precise
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.10 'Oneiric Ocelot'
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

Suite: oneiric
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.10 'Oneiric Ocelot'

Suite: oneiric
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.10
MatchURI: cdrom:\[Ubuntu.*11.10
Description: Cdrom with Ubuntu 11.10 'Oneiric Ocelot'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: oneiric
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: oneiric-security
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb
Description: Recommended updates

Suite: oneiric-updates
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb
Description: Pre-released updates

Suite: oneiric-proposed
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb
Description: Unsupported updates

Suite: oneiric-backports
ParentSuite: oneiric
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


Suite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 11.04 'Natty Narwhal'
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

Suite: natty
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 11.04 'Natty Narwhal'

Suite: natty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*11.04
MatchURI: cdrom:\[Ubuntu.*11.04
Description: Cdrom with Ubuntu 11.04 'Natty Narwhal'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: natty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: natty-security
ParentSuite: natty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: natty-security
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb
Description: Recommended updates

Suite: natty-updates
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb
Description: Pre-released updates

Suite: natty-proposed
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb
Description: Unsupported updates

Suite: natty-backports
ParentSuite: natty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

Suite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.10 'Maverick Meerkat'
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

Suite: maverick
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.10
MatchURI: cdrom:\[Ubuntu.*10.10
Description: Cdrom with Ubuntu 10.10 'Maverick Meerkat'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: maverick
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: maverick-security
ParentSuite: maverick
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: maverick-updates
ParentSuite: maverick
RepositoryType: deb
Description: Recommended updates

Suite: maverick-proposed
ParentSuite: maverick
RepositoryType: deb
Description: Pre-released updates

Suite: maverick-backports
ParentSuite: maverick
RepositoryType: deb
Description: Unsupported updates

Suite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 10.04 'Lucid Lynx'
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

Suite: lucid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*10.04
MatchURI: cdrom:\[Ubuntu.*10.04
Description: Cdrom with Ubuntu 10.04 'Lucid Lynx'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: lucid-security
ParentSuite: lucid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: lucid-updates
ParentSuite: lucid
RepositoryType: deb
Description: Recommended updates

Suite: lucid-proposed
ParentSuite: lucid
RepositoryType: deb
Description: Pre-released updates

Suite: lucid-backports
ParentSuite: lucid
RepositoryType: deb
Description: Unsupported updates

Suite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.10 'Karmic Koala'
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

Suite: karmic
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.10
MatchURI: cdrom:\[Ubuntu.*9.10
Description: Cdrom with Ubuntu 9.10 'Karmic Koala'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: karmic-security
ParentSuite: karmic
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: karmic-updates
ParentSuite: karmic
RepositoryType: deb
Description: Recommended updates

Suite: karmic-proposed
ParentSuite: karmic
RepositoryType: deb
Description: Pre-released updates

Suite: karmic-backports
ParentSuite: karmic
RepositoryType: deb
Description: Unsupported updates

Suite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 9.04 'Jaunty Jackalope'
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
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: jaunty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*9.04
MatchURI: cdrom:\[Ubuntu.*9.04
Description: Cdrom with Ubuntu 9.04 'Jaunty Jackalope'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: jaunty-security
ParentSuite: jaunty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: jaunty-updates
ParentSuite: jaunty
RepositoryType: deb
Description: Recommended updates

Suite: jaunty-proposed
ParentSuite: jaunty
RepositoryType: deb
Description: Pre-released updates

Suite: jaunty-backports
ParentSuite: jaunty
RepositoryType: deb
Description: Unsupported updates

Suite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.10 'Intrepid Ibex'
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

Suite: intrepid
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.10
MatchURI: cdrom:\[Ubuntu.*8.10
Description: Cdrom with Ubuntu 8.10 'Intrepid Ibex'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: intrepid-security
ParentSuite: intrepid
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: intrepid-updates
ParentSuite: intrepid
RepositoryType: deb
Description: Recommended updates

Suite: intrepid-proposed
ParentSuite: intrepid
RepositoryType: deb
Description: Pre-released updates

Suite: intrepid-backports
ParentSuite: intrepid
RepositoryType: deb
Description: Unsupported updates


Suite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 8.04 'Hardy Heron'
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

Suite: hardy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*8.04
MatchURI: cdrom:\[Ubuntu.*8.04
Description: Cdrom with Ubuntu 8.04 'Hardy Heron'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hardy-security
ParentSuite: hardy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: hardy-updates
ParentSuite: hardy
RepositoryType: deb
Description: Recommended updates

Suite: hardy-proposed
ParentSuite: hardy
RepositoryType: deb
Description: Pre-released updates

Suite: hardy-backports
ParentSuite: hardy
RepositoryType: deb
Description: Unsupported updates


Suite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu
BaseURI-sparc: http://archive.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.10 'Gutsy Gibbon'
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
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: gutsy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.10
MatchURI: cdrom:\[Ubuntu.*7.10
Description: Cdrom with Ubuntu 7.10 'Gutsy Gibbon'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: gutsy-security
ParentSuite: gutsy
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-sparc: http://security.ubuntu.com/ubuntu/
MatchURI-sparc: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: gutsy-updates
ParentSuite: gutsy
RepositoryType: deb
Description: Recommended updates

Suite: gutsy-proposed
ParentSuite: gutsy
RepositoryType: deb
Description: Pre-released updates

Suite: gutsy-backports
ParentSuite: gutsy
RepositoryType: deb
Description: Unsupported updates


Suite: feisty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 7.04 'Feisty Fawn'
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
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: feisty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*7.04
MatchURI: cdrom:\[Ubuntu.*7.04
Description: Cdrom with Ubuntu 7.04 'Feisty Fawn'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: feisty-security
ParentSuite: feisty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: feisty-updates
ParentSuite: feisty
RepositoryType: deb
Description: Recommended updates

Suite: feisty-proposed
ParentSuite: feisty
RepositoryType: deb
Description: Pre-released updates

Suite: feisty-backports
ParentSuite: feisty
RepositoryType: deb
Description: Unsupported updates

Suite: edgy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.10 'Edgy Eft'
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
CompDescription: Restricted software
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: edgy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.10
MatchURI: cdrom:\[Ubuntu.*6.10
Description: Cdrom with Ubuntu 6.10 'Edgy Eft'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: edgy-security
ParentSuite: edgy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: edgy-updates
ParentSuite: edgy
RepositoryType: deb
Description: Recommended updates

Suite: edgy-proposed
ParentSuite: edgy
RepositoryType: deb
Description: Pre-released updates

Suite: edgy-backports
ParentSuite: edgy
RepositoryType: deb
Description: Unsupported updates

Suite: dapper
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 6.06 LTS 'Dapper Drake'
Component: main
CompDescription: Officially supported
CompDescriptionLong: Canonical-supported free and open-source software
Component: universe
CompDescription: Community-maintained (universe)
CompDescriptionLong: Community-maintained free and open-source software
Component: restricted
CompDescription: Non-free drivers
CompDescriptionLong: Proprietary drivers for devices
Component: multiverse
CompDescription: Restricted software (Multiverse)
CompDescriptionLong: Software restricted by copyright or legal issues

Suite: dapper
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*6.06
MatchURI: cdrom:\[Ubuntu.*6.06
Description: Cdrom with Ubuntu 6.06 LTS 'Dapper Drake'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: dapper-security
ParentSuite: dapper
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Important security updates

Suite: dapper-updates
ParentSuite: dapper
RepositoryType: deb
Description: Recommended updates

Suite: dapper-proposed
ParentSuite: dapper
RepositoryType: deb
Description: Pre-released updates

Suite: dapper-backports
ParentSuite: dapper
RepositoryType: deb
Description: Unsupported updates

Suite: breezy
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
MirrorsFile: Ubuntu.mirrors
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 'Breezy Badger'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: breezy
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.10
MatchURI: cdrom:\[Ubuntu.*5.10
Description: Cdrom with Ubuntu 5.10 'Breezy Badger'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: breezy-security
ParentSuite: breezy
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.10 Security Updates

Suite: breezy-updates
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Updates

Suite: breezy-backports
ParentSuite: breezy
RepositoryType: deb
Description: Ubuntu 5.10 Backports

Suite: hoary
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
MirrorsFile: Ubuntu.mirrors
Description: Ubuntu 5.04 'Hoary Hedgehog'
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: hoary
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*5.04
MatchURI: cdrom:\[Ubuntu.*5.04
Description: Cdrom with Ubuntu 5.04 'Hoary Hedgehog'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: hoary-security
ParentSuite: hoary
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-ia64: http://ports.ubuntu.com/
MatchURI-ia64: ports.ubuntu.com/ubuntu-ports
BaseURI-hppa: http://ports.ubuntu.com/
MatchURI-hppa: ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 5.04 Security Updates

Suite: hoary-updates
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Updates

Suite: hoary-backports
ParentSuite: hoary
RepositoryType: deb
Description: Ubuntu 5.04 Backports

Suite: warty
RepositoryType: deb
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu
Description: Ubuntu 4.10 'Warty Warthog'
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright
Component: universe
CompDescription: Community-maintained (Universe)
Component: multiverse
CompDescription: Non-free (Multiverse)

Suite: warty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*4.10
MatchURI: cdrom:\[Ubuntu.*4.10
Description: Cdrom with Ubuntu 4.10 'Warty Warthog'
Available: False
Component: main
CompDescription: No longer officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: warty-security
ParentSuite: warty
RepositoryType: deb
BaseURI: http://security.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Ubuntu 4.10 Security Updates

Suite: warty-updates
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Updates

Suite: warty-backports
ParentSuite: warty
RepositoryType: deb
Description: Ubuntu 4.10 Backports

```

---

### Post by ventrical on 2015-10-24
But Vin .. whats this-

```

BaseURI: cdrom:\[Ubuntu.*15.
MatchURI: cdrom:\[Ubuntu.*15.10
Description: Cdrom with Ubuntu 15.10 'xenial werewolf'
Available: False

```

and .. do you get software-properties -gtk error ?

cause if I am wrong then I gave Cariboo some wrong information and assumption and
I have to go back and fix it.

Regards..

---

### Post by zika on 2015-10-25
> **VinDSL said:**
> Different strokes...I go the opposite direct of both of you guys.  **I just keep adding to the list.**  LoL :DThe only proper and the way it will be done also when proper file from source comes.

---

### Post by VinDSL on 2015-10-25
> **ventrical said:**
> But Vin .. whats this-

```

BaseURI: cdrom:\[Ubuntu.*15.
MatchURI: cdrom:\[Ubuntu.*15.10
Description: Cdrom with Ubuntu 15.10 'xenial werewolf'
Available: False

```

and .. do you get software-properties -gtk error ?

cause if I am wrong then I gave Cariboo some wrong information and assumption and
I have to go back and fix it.

Regards..

Yes n' no.  I guess I missed that one, and more, and spent the last 3 hours correcting the oversight :)

Yes, last night everything was fine, but I surmise after starting my machine, this morning, things went awry.

No, I wasn't getting errors last night, and debug looked okay, but yes, tonight I starting getting “hash sum mismatch” errors on a couple of repos.  I switched sources even, thinking it was a fluke.  Some of the mismatches went away, depending on the source, but I was concerned enough about it that I was afraid to do an update.  I just chalked it up to startup probs, and assumed it would go away with time -- then, I saw your post. 0.o

Anyway, I emptied the jar, so to speak, and started afresh.

This is what I used this time...

```
Suite: xenial
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 16.04 'xenial xerus'
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

Suite: xenial
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 16.04 'xenial xerus'

Suite: xenial
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*16.04
MatchURI: cdrom:\[Ubuntu.*16.04
Description: Cdrom with Ubuntu 16.04 'xenial xerus'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: xenial
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: xenial
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: xenial-security
ParentSuite: xenial
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: xenial-security
ParentSuite:xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: xenial-updates
ParentSuite: xenial
RepositoryType: deb
Description: Recommended updates

Suite:xenial-updates
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: xenial-proposed
ParentSuite: xenial
RepositoryType: deb
Description: Pre-released updates

Suite: xenial-proposed
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: xenial-backports
ParentSuite: xenial
RepositoryType: deb
Description: Unsupported updates

Suite: xenial-backports
ParentSuite: xenial
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

```

Everything went smoothly after using the above, and more upgrades immediately flowed in - so many, in fact, that I was down to 0% space on my root drive, at one point.  'Extras' is AWOL, but that's to be expected.

Anyway, all's well that ends well, eh what ?!?!?  ;)

---

### Post by VinDSL on 2015-10-25
I'm getting a couple of *warnings*, but no errors... ;)


&#9581;&#9472;vindsl@Zuul ~  
&#9584;&#9472;&#10148;  sudo software-properties-gtk --debug
[sudo] password for vindsl: 
sys:1: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
sys:1: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
ENABLED COMPS: {'multiverse', 'main', 'restricted', 'universe'}
INTERNET COMPS: {'multiverse', 'main', 'restricted', 'universe'}
MAIN SOURCES
 URI: [http://mirror.os6.org/ubuntu/](http://mirror.os6.org/ubuntu/)
 Comps: ['main', 'restricted', 'universe', 'multiverse']
 Enabled: True
 Valid: True
 MatchURI: archive.ubuntu.com/ubuntu
 BaseURI: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)


CHILD SOURCES
 URI: [http://mirror.os6.org/ubuntu/](http://mirror.os6.org/ubuntu/)
 Comps: ['restricted', 'main', 'universe', 'multiverse']
 Enabled: True
 Valid: True
 MatchURI: archive.ubuntu.com/ubuntu
 BaseURI: None


 URI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
 Comps: ['restricted', 'main', 'universe', 'multiverse']
 Enabled: True
 Valid: True
 MatchURI: archive.ubuntu.com/ubuntu|security.ubuntu.com
 BaseURI: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)


 URI: [http://mirror.os6.org/ubuntu/](http://mirror.os6.org/ubuntu/)
 Comps: ['restricted', 'main', 'universe', 'multiverse']
 Enabled: True
 Valid: True
 MatchURI: archive.ubuntu.com/ubuntu
 BaseURI: None


 URI: [http://mirror.os6.org/ubuntu/](http://mirror.os6.org/ubuntu/)
 Comps: ['restricted', 'main', 'universe', 'multiverse']
 Enabled: True
 Valid: True
 MatchURI: archive.ubuntu.com/ubuntu
 BaseURI: None


CDROM SOURCES
SOURCE CODE SOURCES
DISABLED SOURCES
ISV
&#9581;&#9472;vindsl@Zuul ~  
&#9584;&#9472;&#10148;

---

### Post by zika on 2015-10-25
```
:~$ [SIZE=6]**gksu**[/SIZE] software-properties-gtk --debug
No ask_pass set, using default!
xauth: /tmp/libgksu-zeHeRb/.Xauthority
STARTUP_ID: gksu/software-properties-gtk/3834-0-****************_TIME7675106
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: software-properties-gtk
buffer: -GNOME_SUDO_PASS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
GIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/aptdaemon/client.py:474: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  "locale-changed": (GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/aptdaemon/client.py:477: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  "terminal-changed": (GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/aptdaemon/client.py:480: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  "debconf-socket-changed": (GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/aptdaemon/client.py:483: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  "http-proxy-changed": (GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/aptdaemon/client.py:486: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  "medium-required": (GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/aptdaemon/client.py:490: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  "config-file-conflict": (GObject.SIGNAL_RUN_FIRST,
sys:1: PyGIWarning: Gdk was imported without specifying a version first. Use gi.require_version('Gdk', '3.0') before import to ensure that the right version gets loaded.
sys:1: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
/usr/lib/python3/dist-packages/aptdaemon/gtk3widgets.py:565: PyGIDeprecationWarning: GObject.SIGNAL_RUN_FIRST is deprecated; use GObject.SignalFlags.RUN_FIRST instead
  __gsignals__ = {"finished": (GObject.SIGNAL_RUN_FIRST,
/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py:56: PyGIDeprecationWarning: GLib.pyglib_version is deprecated; use gi.version_info instead
  if GLib.pyglib_version < (3, 9, 1):
xauth: /tmp/libgksu-zeHeRb/.Xauthority
xauth_env: /run/user/1000/gdm/Xauthority
dir: /tmp/libgksu-zeHeRb
```

---

### Post by VinDSL on 2015-10-25
Oh, OK, zika !  LoL :)

&#9581;&#9472;vindsl@Zuul ~  
&#9584;&#9472;&#10148;  gksu software-properties-gtk --debug
No ask_pass set, using default!
xauth: /tmp/libgksu-BXtpaz/.Xauthority
STARTUP_ID: gksu/software-properties-gtk/3686-0-Zuul_TIME8463172
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: software-properties-gtk
buffer: -GNOME_SUDO_PASS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
xauth: /tmp/libgksu-BXtpaz/.Xauthority
xauth_env: /home/vindsl/.Xauthority
dir: /tmp/libgksu-BXtpaz
&#9581;&#9472;vindsl@Zuul ~  
&#9584;&#9472;&#10148;

---

### Post by slickymaster on 2015-10-25
> **cariboo said:**
> I didn't need it last cycle, and so far it looks like it won't be needed this cycle either.

Same here.

---

### Post by ventrical on 2015-10-25
> **slickymaster said:**
> Same here.

So you didn't  get software-properties-gtk warning on reboot and when you click software&updates it comes up working in gui?

Regards..

---

### Post by slickymaster on 2015-10-25
> **ventrical said:**
> So you didn't  get software-properties-gtk warning on reboot and when you click software&updates it comes up working in gui?

Regards..

Exactly ventrical. All went smoothly, as last cycle.

---

### Post by zika on 2015-10-25
> **cariboo said:**
> I didn't need it last cycle, and so far it looks like it won't be needed this cycle either.
> **slickymaster said:**
> Same here.
> **slickymaster said:**
> Exactly ventrical. All went smoothly, as last cycle.
Did the two of You, by any chance, use &#8222;devel&#8220; branch in sources.list? That would be one way of explaining that. I did try without adding xenial stuff in aforementioned file with no luck. Yes, I do use CLI only approach but I did want to make sure before I write anything about it...

---

### Post by ventrical on 2015-10-25
> **zika said:**
> Did the two of You, by any chance, use „devel“ branch in sources.list? That would be one way of explaining that. I did try without adding xenial stuff in aforementioned file with no luck. Yes, I do use CLI only approach but I did want to make sure before I write anything about it...

CLI here too on one install. The ubuntu.info file came up with /devel/ repos after switiching the cycle in the sources.list with the standard method we use here and so when back in GUI I got software-properties-gtk  report. When I manualy edited in /xenial/ for /devel/ that apport problem pop up went away and I was able to use software&updates in GUI.

  I think perhaps the gtk report was for super-early adopters. Pehaps if one waited for a few days then the file may have been appended by then. My 2 cents only. It used to work on /devel/ no problem. I remember a debate we had on that  a few cycles back. My 2 cents again .. jumping in early may produce that problem.

Regards..

---

### Post by ventrical on 2015-10-25
> **slickymaster said:**
> Exactly ventrical. All went smoothly, as last cycle.

Question of curiosity.

Did you jump right in  . ie; Thursday night/Friday morning or did you wait an extra day or so?

Thanks

regards..

---

### Post by slickymaster on 2015-10-26
> **ventrical said:**
> Question of curiosity.

Did you jump right in  . ie; Thursday night/Friday morning or did you wait an extra day or so?

Thanks

regards..

Last Friday, 2015-10-23.

---

### Post by slickymaster on 2015-10-26
> **zika said:**
> Did the two of You, by any chance, use „devel“ branch in sources.list? <---snip--->

Yes, I did.

---

### Post by ventrical on 2015-10-26
> **slickymaster said:**
> Yes, I did.

As I posted elsewhere .. that option used to work for me .. but not any more. Must be a caveat I am missing..

thnks

---

### Post by dino99 on 2015-10-26
a newer python-apt (& the likes) has been published; so the handmade change is no more needed

---

### Post by ventrical on 2015-10-26
> **dino99 said:**
> a newer python-apt (& the likes) has been published; so the handmade change is no more needed

Yeah .. thats it.   When I migrated that change was not rolled over yet ..hence the topic title .. early adopters :) but that was pretty fast .. so the rolling release model barely had a hiccup. 

thanks 

Regards..

---

