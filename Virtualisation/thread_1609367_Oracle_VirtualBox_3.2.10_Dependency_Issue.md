---
title: "Oracle VirtualBox 3.2.10 Dependency Issue"
date: 2010-10-30
forum: Virtualisation
---

### Post by hantms on 2010-10-30
I have VirtualBox 3.2.8 already installed, but I cannot upgrade to 3.2.10 due to a dependency issue.

This applies both when downloading the .deb file AND when using VirtualBox repository.

Errors:

virtualbox-3.2:
  Depends: libqtcore4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libqtgui4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libssl0.9.8 (>=0.9.8m-1) but 0.9.8k-7ubuntu8.2 is to be installed
 Recommends: libsdl-ttf2.0-0 but it is not going to be installed

---

### Post by JustinR on 2010-10-30
> **hantms said:**
> I have VirtualBox 3.2.8 already installed, but I cannot upgrade to 3.2.10 due to a dependency issue.

This applies both when downloading the .deb file AND when using VirtualBox repository.

Errors:

virtualbox-3.2:
  Depends: libqtcore4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libqtgui4 (>=4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
  Depends: libssl0.9.8 (>=0.9.8m-1) but 0.9.8k-7ubuntu8.2 is to be installed
 Recommends: libsdl-ttf2.0-0 but it is not going to be installed

Are there any updates in Update Manager?

---

### Post by gregaryh on 2010-11-02
I am seeing the same issue. I am running on AMD64. I tried modifying the .deb to remove the dependency but must have messed something up. I tried installing the 3.2.8 package for debian but it has a missing python dependency. I am thinking the folks at VB just need to rebuild the package with the older Qt libs.

---

### Post by DuncanWatson on 2010-11-05
I have the same problem.  Unfortunately this blocks some tasks I have active right now.  Are there any other solutions besides VMWare Server than I can run?  I need a VM to run under my Ubuntu 10.10 and run the corporate image of windows within it.

Ah well.

---

### Post by JustinR on 2010-11-05
> **gregaryh said:**
> I am seeing the same issue. I am running on AMD64. I tried modifying the .deb to remove the dependency but must have messed something up. I tried installing the 3.2.8 package for debian but it has a missing python dependency. I am thinking the folks at VB just need to rebuild the package with the older Qt libs.

Hi sorry for the delay,

Can you go to your home folder and press 'CTRL + H' to view hidden files, copy the '.virtualbox' folder to your desktop (you can remove the period on the folder to make it visible after you move it)

Then go to Applications > Accessories > Terminal:
```

sudo apt-get purge virtualbox

```

After that, try installing the latest version of VirtualBox. If it is successful then copy back the '.virtualbox' folder on your desktop and back into your home folder.

---

### Post by gregaryh on 2010-11-05
No cigar. This is what I did...
```

ghendricks@mewtwo:~$ mv .VirtualBox/ VirtualBox/
ghendricks@mewtwo:~$ sudo apt-get purge virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox-ose* virtualbox-ose-qt*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 45.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 186793 files and directories currently installed.)
Removing virtualbox-ose-qt ...
Purging configuration files for virtualbox-ose-qt ...
Removing virtualbox-ose ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Purging configuration files for virtualbox-ose ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
ghendricks@mewtwo:~$ sudo apt-get install virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting virtualbox-3.2 instead of virtualbox
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  virtualbox-3.2: Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.6.2-0ubuntu5.1 is to be installed
                  Depends: libssl0.9.8 (>= 0.9.8m-1) but 0.9.8k-7ubuntu8.3 is to be installed
E: Broken packages

```Here is my /etc/apt/sources.list file:

```

ghendricks@mewtwo:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://archive.canonical.com/ lucid partner
deb http://download.virtualbox.org/virtualbox/debian maverick non-free

```

---

### Post by JustinR on 2010-11-05
Hi,

Have you tried this code:
```

sudo apt-get install virtualbox-ose -f

```
?

---

### Post by gregaryh on 2010-11-06
Oh yes, I had OSE installed already, but it doesn't support USB to guests which is why I wanted to switch to the PUEL version.

---

### Post by kloplop321 on 2010-11-12
I too have this problem, I wish to install this because of USB support. I tried to use the deb and ignore these dependencies, and the virtualbox command doesn't work afterward..
It acts like the binary was never actually installed.. :(

---

