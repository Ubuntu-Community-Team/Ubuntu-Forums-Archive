---
title: "How to upgrade from 7.04 to 7.10 Beta (Gutsy Gibbon)"
date: 2007-09-27
forum: Sudan Team
---

### Post by Y2J on 2007-09-27
**Before you start:**

As always make sure to:

sudo apt-get update
sudo apt-get upgrade

Then you’ll need to type (use a terminal so you can watch for errors!)

gksudo “update-manager -c -d”

if the terminal spits out the following error:
```

warning: could not initiate dbus
current dist not found in meta-release file
```

You’ll need to do the following which should fix the problem.

```
sudo gedit /var/lib/update-manager/meta-release
```

if after typing this your editor does not show any text you’ll need to paste this into your text editor and save the file.

```

Dist: warty
Name: Warty Warthog
Version: 04.10
Date: Wed, 20 Oct 2004 07:28:17 UTC
Supported: 0
Description: This is the warty warthog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/warty/Release

Dist: hoary
Name: Hoary Hedgehog
Version: 05.04
Date: Fri, 08 Apr 2005 08:18:19 UTC
Supported: 0
Description: This is the Hoary Hedgehog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hoary/Release

Dist: breezy
Name: Breezy Badger
Version: 05.10
Date: Thu, 13 Oct 2005 19:34:42 UTC
Supported: 0
Description: This is the Breezy Badger release
Release-File: http://archive.ubuntu.com/ubuntu/dists/breezy/Release

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 1
Description: This is the Dapper Drake release
Release-File: http://archive.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/DapperReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg

Dist: edgy
Name: Edgy Eft
Version: 6.10
Date: Thu, 26 Oct 2006 12:00:00 UTC
Supported: 1
Description: This is the Edgy Eft release
Release-File: http://archive.ubuntu.com/ubuntu/dists/edgy/Release
ReleaseNotes: http://changelogs.ubuntu.com/EdgyReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/edgy-updates/main/dist-upgrader-all/current/edgy.tar.gz.gpg

Dist: feisty
Name: Feisty Fawn
Version: 7.04
Date: Thu, 19 Apr 2007 13:00:00 +0200
Supported: 1
Description: This is the 7.04 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/feisty/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/feisty-proposed/main/dist-upgrader-all/current/feisty.tar.gz.gpg

Dist: gutsy
Name: Gutsy Gibbon
Version: 7.10
Date: Thu, 18 Oct 2007 12:00:00 UTC
Supported: 0
Description: This is the 7.10 release
Release-File: http://archive.ubuntu.com/ubuntu/dists/gutsy/Release
ReleaseNotes: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg
```

and then, again, type the following command:

```
gksudo "update-manager -c -d"
```

Can you see the magical Upgrade button now ?! :)

---

### Post by Skerit on 2007-09-27
Hah, I never actually looked at the meta-release file, lol :P

However, I still prefer to replace every "feisty" indication with "gutsy" in my sources.list and then just dist-upgrade :P

---

### Post by thiebaude on 2007-10-03
This worked just great.I've upgraded from 7.04 to 7.10 Gutsy.


Thanks

---

### Post by brianmrowe on 2009-04-22
While nothing else would work to get me from 7.04 to 7.10 this did work.  The gusty.tar.gz in the meta file isn't in that location, so it can't download it.  but changing the sources to gutsy worked. Thanks

---

