---
title: "changing sources list to /vivid/ adds /devel/ by default to Ubuntu.info"
date: 2014-10-25
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-10-25
Changing sources list to /vivid/ will add /devel/ in Ubuntu.info by default  after fresh install of utopic. Nothing I did.

> 
ChangelogURI: [http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog](http://changelogs.ubuntu.com/changelogs/pool/%s/%s/%s/%s_%s/changelog)

Suite: devel
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)
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
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu development series

Suite: devel
Official: false
RepositoryType: deb
BaseURI: [http://archive.canonical.com](http://archive.canonical.com)
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: devel
Official: false
RepositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: devel-security
ParentSuite: devel
RepositoryType: deb
BaseURI: [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/)
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/)
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: devel-security
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb
Description: Recommended updates

Suite: devel-updates
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb
Description: Pre-released updates

Suite: devel-proposed
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb
Description: Unsupported updates

Suite: devel-backports
ParentSuite: devel
RepositoryType: deb-src
BaseURI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates


---

### Post by zika on 2014-10-25
> **ventrical said:**
> Changing sources list to /vivid/ **will add /devel/ in sources.list** by default  after fresh install of utopic. Nothing I did.Will add devel to /etc/apt/sources.list as You propose or to /usr/share/python-apt/templates/Ubuntu.info as You have shown in code-tags? I do think it is latter.

---

### Post by ventrical on 2014-10-25
> **zika said:**
> Will add devel to /etc/apt/sources.list as You propose or to /usr/share/python-apt/templates/Ubuntu.info as You have shown in code-tags? I do think it is latter.

Nope . I never touched this install in that latter  manner as your inferred above. It's default.

Regards..

---

### Post by zika on 2014-10-25
> **ventrical said:**
> Nope . I never touched this install in that latter  manner as your inferred above. It's default.

Regards..You did not read my post, either. Just check about which file ou're writing about and contents of which file You've put into code-tags. I did not infer anything. To the contrary.

---

### Post by Elfy on 2014-10-25
my sources list - sed utopic to vivid - added vbox myself - did nothing else to it.

```

# deb cdrom:[Xubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022)]/ vivid main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
deb http://security.ubuntu.com/ubuntu vivid-security universe
deb-src http://security.ubuntu.com/ubuntu vivid-security universe
deb http://security.ubuntu.com/ubuntu vivid-security multiverse
deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb-src http://archive.canonical.com/ubuntu vivid partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu vivid main
# deb-src http://extras.ubuntu.com/ubuntu vivid main

deb http://download.virtualbox.org/virtualbox/debian trusty contrib

```

I DID though have devel added to the /usr/share/python-apt/templates/Ubuntu.info file when I went to deal with that yesterday

---

### Post by ventrical on 2014-10-25
> **zika said:**
> You did not read my post, either. Just check about which file ou're writing about and contents of which file You've put into code-tags. I did not infer anything. To the contrary.

[s]I did read your post and as the title says  'sources list'. Or shall I be more accurate and write 'sources.list' .

Content put into code tags is the content of "sources.list' after update/upgrade to /vivid/.

So my point is that after:

```



[B]sudo sed -i 's/utopic/vivid/g' /etc/apt/sources.list

[/B]
[B]sudo apt-get update && sudo apt-get dist-upgrade

[/B][B][B]sudo apt-get update

[/B][/B][B]sudo apt-get dist-upgrade

[/B]
```[B]

The sources.list text contains /devel repos and not /vivid.[/B][/s][B]

Regards.

After reading elfys message I realized  the file was Ubuntu.info and not sources.list!:)


[/B]

---

### Post by ventrical on 2014-10-25
> **Elfy said:**
> my sources list - sed utopic to vivid - added vbox myself - did nothing else to it.

```

# deb cdrom:[Xubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022)]/ vivid main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid universe
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu vivid-security main restricted
deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
deb http://security.ubuntu.com/ubuntu vivid-security universe
deb-src http://security.ubuntu.com/ubuntu vivid-security universe
deb http://security.ubuntu.com/ubuntu vivid-security multiverse
deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu vivid partner
# deb-src http://archive.canonical.com/ubuntu vivid partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu vivid main
# deb-src http://extras.ubuntu.com/ubuntu vivid main

deb http://download.virtualbox.org/virtualbox/debian trusty contrib

```

I DID though have devel added to the /usr/share/python-apt/templates/Ubuntu.info file when I went to deal with that yesterday



 I need a break :)

---

### Post by Elfy on 2014-10-25
:)

there is that - of course the other thing is that if your sources.list DID look like post#1 you'd have all manner of problems using apt :D

---

### Post by ventrical on 2014-10-25
> **zika said:**
> Will add devel to /etc/apt/sources.list as You propose or to /usr/share/python-apt/templates/Ubuntu.info as You have shown in code-tags? I do think it is latter.

Yes .. correct.

Thanks again..

---

### Post by ventrical on 2014-10-25
> **Elfy said:**
> :)

there is that - of course the other thing is that if your sources.list DID look like post#1 you'd have all manner of problems using apt :D


:) .. I have so many installs going .. I just get a little overwhlemed.No excuse for me to put up wrong assumptions :)

Regards..

---

