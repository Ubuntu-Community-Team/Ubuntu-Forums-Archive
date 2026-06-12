---
title: "Some how got Kubuntu 17.04 but repositories have no &quot;release files&quot;"
date: 2016-12-01
forum: Ubuntu Development Version
---

### Post by reb682 on 2016-12-01
I dont't know how I ended up with Kubuntu 17.04 but not complaining. Only when I go to Repositories  the ppa's listed shows they have no release files.
---------------------------------------------
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.
The repository 'http://ppa.launchpad.net/ondrej/php/ubuntu zesty Release' does not have a Release file.Updating from such a repository can't be done securely, and is therefore disabled by default.See apt-secure(8) manpage for repository creation and user configuration details.The repository 'http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu zesty Release' does not have a Release file.
_____________________________
I do not know how to check the repository address or See apt-secure(8) manpage for repository creation.The info shows I have Kubuntu 17.04
I also have Windows8 and Ubuntu 16.10.
When I boot up in the morning I have NO internet. The internet works in Windows8 and Ubuntu 16.10. After opening one of them I can go back to Kubuntu 17.04 and I will have Internet. Strange.Everything else seems to be working and I am getting some updates 17.04 in software updates. Should I just try to do Daily Updates in 17.04. I will have to get release files for that I think. Is there any other information I could send you to help? If so please give me instructions how to do it. Thanks for any help.

---

### Post by howefield on 2016-12-01
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by ventrical on 2016-12-01
Can you check your ubuntu.info file and match it against this-  [https://wiki.ubuntu.com/U%2B1/common-problems](https://wiki.ubuntu.com/U%2B1/common-problems)

thnxs

---

### Post by reb682 on 2016-12-01
When I do INFO I get the gear looking emblem and the Info of my system such as KDE PLasma Version 5.7.5/KDE Frameworks Version 5.26.0/ QT Version 5.6.1/
I do no think this is what you had in mind.

---

### Post by ventrical on 2016-12-01
> **reb682 said:**
> When I do INFO I get the gear looking emblem and the Info of my system such as KDE PLasma Version 5.7.5/KDE Frameworks Version 5.26.0/ QT Version 5.6.1/
I do no think this is what you had in mind.

Check this file here at- 

/usr/share/python-apt/templates/Ubuntu.info

Should look like this - 

```

Suite: zesty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://archive.ubuntu.com/ubuntu
MatchURI-amd64: archive.ubuntu.com/ubuntu
BaseURI-i386: http://archive.ubuntu.com/ubuntu
MatchURI-i386: archive.ubuntu.com/ubuntu
MirrorsFile-amd64: Ubuntu.mirrors
MirrorsFile-i386: Ubuntu.mirrors
Description: Ubuntu 17.04 'zesty zapus'
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

Suite: zesty
ParentSuite: zesty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Ubuntu 17.04 'zesty zapus'

Suite: zesty
RepositoryType: deb
MatchName: .*
BaseURI: cdrom:\[Ubuntu.*16.
MatchURI: cdrom:\[Ubuntu.*16.10
Description: Cdrom with Ubuntu 17.04 'zesty zapus'
Available: False
Component: main
CompDescription: Officially supported
Component: restricted
CompDescription: Restricted copyright

Suite: zesty
Official: false
RepositoryType: deb
BaseURI: http://archive.canonical.com
MatchURI: archive.canonical.com
Description: Canonical Partners
Component: partner
CompDescription: Software packaged by Canonical for their partners
CompDescriptionLong: This software is not part of Ubuntu.

Suite: zesty
Official: false
RepositoryType: deb
BaseURI: http://extras.ubuntu.com
MatchURI: extras.ubuntu.com
Description: Independent
Component: main
CompDescription: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.

Suite: zesty-security
ParentSuite: zesty
RepositoryType: deb
BaseURI: http://ports.ubuntu.com/ubuntu-ports/
MatchURI: ports.ubuntu.com/ubuntu-ports
BaseURI-amd64: http://security.ubuntu.com/ubuntu/
MatchURI-amd64: archive.ubuntu.com/ubuntu|security.ubuntu.com
BaseURI-i386: http://security.ubuntu.com/ubuntu/
MatchURI-i386: archive.ubuntu.com/ubuntu|security.ubuntu.com
Description: Important security updates

Suite: zesty-security
ParentSuite:zesty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports|security.ubuntu.com
Description: Important security updates

Suite: zesty-updates
ParentSuite: zesty
RepositoryType: deb
Description: Recommended updates

Suite:zesty-updates
ParentSuite: zesty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Recommended updates

Suite: zesty-proposed
ParentSuite: zesty
RepositoryType: deb
Description: Pre-released updates

Suite: zesty-proposed
ParentSuite: zesty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Pre-released updates

Suite: zesty-backports
ParentSuite: zesty
RepositoryType: deb
Description: Unsupported updates

Suite: zesty-backports
ParentSuite: zesty
RepositoryType: deb-src
BaseURI: http://archive.ubuntu.com/ubuntu/
MatchURI: archive.ubuntu.com/ubuntu|ports.ubuntu.com/ubuntu-ports
Description: Unsupported updates

```

---

### Post by reb682 on 2016-12-03
At one point my info says *17.04 on two lines when the sample says *16. and *16.10
Two paragraphs later the following is missing completly
______________________________
Suite: zesty
Official: false
repositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: Main
CompDescrition: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.
______________________________________
Should I add this paragraph and change the *17.04 to what is shown in yours

---

### Post by ventrical on 2016-12-04
> **reb682 said:**
> At one point my info says *17.04 on two lines when the sample says *16. and *16.10
Two paragraphs later the following is missing completly
______________________________
Suite: zesty
Official: false
repositoryType: deb
BaseURI: [http://extras.ubuntu.com](http://extras.ubuntu.com)
MatchURI: extras.ubuntu.com
Description: Independent
Component: Main
CompDescrition: Provided by third-party software developers
CompDescriptionLong: Software offered by third party developers.
______________________________________
Should I add this paragraph and change the *17.04 to what is shown in yours

As I understand it .. if you use a current 17.04 ISO you will not have to change ubuntu.info file. It will be done automatically. However.. seeing that you are having repo  problems it is advised that you can put the file I posted and insert it on top of your ubuntu.info file. Since you are using Kubuntu it may not work. You may have to start with a new ISO or wait for somebody who is running Kubuntu to reply. 

regards..

---

