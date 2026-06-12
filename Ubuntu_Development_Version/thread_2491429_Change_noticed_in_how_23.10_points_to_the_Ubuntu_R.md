---
title: "Change noticed in how 23.10 points to the Ubuntu Repo's for Mantic"
date: 2023-10-08
forum: Ubuntu Development Version
---

### Post by MAFoElffen on 2023-10-08
I have been testing the daily's for Mantic and keeping some instances persistent to test them on the updates.

I am a part of some Bug reports on the new Flutter Installer for 23.04 on, as well as a question on launchpad and an issue at the ubuntu-desktop-installer GitHub. Things that I think need to be corrected before 24.04 LTS.

*** What many do not realize here yet... In the system layout, not the installer itself. 

On updates of the persistent images I would get errors that the release key for using the cdrom repo was no longer valid. The key was dated as 2012, and /etc/apt/sources.list only had one line, pointing to the ISO. I added a sources.list in the format of the previous releases.

On update, I then got an error of duplicate entries in the sources. That is when I noticed the layout change... I commented out all the lines of /etc/apt/sources.list and it was fine.

They changed how /etc/apt/sources.list and /etc/apt/sources.list.d/ is laid out, and how it now points to the Ubuntu Repo's. They moved the contents of the sources.list to sources.list.d. Software & Updates, when you check the checkboxes now points to /etc/apt/sources.list.d/ubuntu.sources
```

mafoelffen@minatuar-009:~$ grep . /etc/apt/sources.list.d/ubuntu.sources
Types: deb
URIs: http://us.archive.ubuntu.com/ubuntu
Suites: mantic mantic-updates mantic-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Types: deb
URIs: http://us.archive.ubuntu.com/ubuntu
Suites: mantic-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

```
I think we should share that change with members that will be supporting 23.10 on in the General and Installation & Updates Sections so they are aware of it.

---

### Post by MAFoElffen on 2023-10-08
To show you a comparison, 23.04 used the old format and layout:
```

mafoelffen@lunar-lander-01:~$ ls -lah /etc/apt/sources.list
-rw-rw-r-- 1 root root 2.8K Mar 17  2023 /etc/apt/sources.list
mafoelffen@lunar-lander-01:~$ ls -lah /etc/apt/sources.list.d/
total 23K
drwxr-xr-x 2 root root   3 Mar 17  2023 .
drwxr-xr-x 8 root root   9 Dec 31  2022 ..
-rw-r--r-- 1 root root 164 Mar 17  2023 mafoelffen-ubuntu-system-info-lunar.list
mafoelffen@lunar-lander-01:~$ grep . /etc/apt/sources.list
# deb cdrom:[Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1)]/ jammy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lunar main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lunar-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar-updates main restricted
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lunar universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar universe
deb http://us.archive.ubuntu.com/ubuntu/ lunar-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar-updates universe
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lunar multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lunar-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar-updates multiverse
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lunar-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lunar-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu lunar-security main restricted
# deb-src http://security.ubuntu.com/ubuntu lunar-security main restricted
deb http://security.ubuntu.com/ubuntu lunar-security universe
# deb-src http://security.ubuntu.com/ubuntu lunar-security universe
deb http://security.ubuntu.com/ubuntu lunar-security multiverse
# deb-src http://security.ubuntu.com/ubuntu lunar-security multiverse
# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
mafoelffen@lunar-lander-01:~$ grep . /etc/apt/sources.list.d/mafoelffen-ubuntu-system-info-lunar.list
deb https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/ lunar main
# deb-src https://ppa.launchpadcontent.net/mafoelffen/system-info/ubuntu/ lunar main

```

---

### Post by corradoventu on 2023-10-09
In the last Mantic ISOs sources.list is no longer in deb822 format but again in the old format.
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2033949](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2033949)

---

### Post by MAFoElffen on 2023-10-09
I joined that Bug Report as affected.

---

### Post by #&amp;thj^% on 2023-10-09
It really hasn't been fixed.
> Julian Andres Klode (juliank) wrote on 2023-10-04: 			#8

Well the bug remains nonetheless, just the importance gets lower
Changed in software-properties (Ubuntu Mantic):
importance: 	High &#8594; Low 

---

### Post by MAFoElffen on 2023-10-09
Yes. It still happens on today's daily.

Sidenote:
Today's 'Daily' add's another challenge concerning in my test cases for ZFS. The current daily is image for current 20231005. During the install, if I update ubuntu-desktop-installer to "0+git.bb3cfa22" and let the installer restart with that version, then it crashes big-time for the ZFS: "PartitionMethod":"use_zfs", which is my concerned test cases. If I skip the installer update, it does work. [https://bugs.launchpad.net/subiquity/+bug/2038856](https://bugs.launchpad.net/subiquity/+bug/2038856)

I do not know if that new (current online) updated git has problems with other test cases (different installer option scenarios).

---

