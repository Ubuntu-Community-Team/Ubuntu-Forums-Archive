---
title: "[SOLVED] vmware won't install"
date: 2008-01-18
forum: Virtualisation
---

### Post by Sinkingships7 on 2008-01-18
i get that "vmware cannot be installed on your computer type (i386)" error.
quite aggravating. 

anyone know how to get around this?

any help would be greatly appreciated.

---

### Post by iansane on 2008-01-18
is it the server 1.03  tar.gz package from vmware? That's the one I installed and I don't recall having that error.

---

### Post by Sinkingships7 on 2008-01-18
it was just from the add/remove programs under applications. should i download the tar.gz, and if so, where from?

---

### Post by iansane on 2008-01-18
I looked in add/remove and in the description it says cannot be installed on my computer type (i386) the vendor decided not to support my computer type.

It's just as well.  The vmware server actually allows you to create a virtual machine. I don't think the player does.

Go to [http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) and choose the 1.0.3 release at the top of the list. When you click download, you'll have to scroll down and accept the license agreement. then it will take you to the downloads. Its the tar.gz package. look for install instructions and be sure to get your free activation serials (you can get a bunch if you want). If I remember right there are some install instructions inside the folder after you extract the tar.gz but read the info on the website just in case.

---

### Post by bodycoach2 on 2008-01-18
BUMP
I'd like to know how to get VMWare working on Ubuntu again too. Worked fine in Fiesty, gone in Gutsy.
Please, if possible, provide instructions.

(edited) Opps...that was fast.

---

### Post by PmDematagoda on 2008-01-18
Could you please post the results of:-
```
cat /etc/apt/sources.list
```

---

### Post by iansane on 2008-01-18
yeah its the first linux download right under the two windows ones and there is a register link at the top left of the page right above the downloads to get your serial

Once you've extracted it cd to the folder it's in and then go to the following url and start with the "sudo vmware-installer.pl" command. As far as I remember that's how I installed it. It was a couple months ago and I need a memory upgrade

[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)

---

### Post by Sinkingships7 on 2008-01-18
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by iansane on 2008-01-18
> **PmDematagoda said:**
> Could you please post the results of:-
```
cat /etc/apt/sources.list
```

I guess you weren't talking to me but I had the same issue so I installed from vmware website. Here's my sources list

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
 deb http://archive.canonical.com/ubuntu gutsy partner
 deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

Is there something missing?

---

### Post by iansane on 2008-01-18
I noticed I have the gutsy backports and gutsy partner sources uncommented and sinkingships7 doesn't. I still can't get vmware from add/remove though. I guess they don't have anything to do with it.

---

### Post by Sinkingships7 on 2008-01-18
bump

---

### Post by fjgaude on 2008-01-19
Use Synaptic and Search for vmware. Click it. Install.

But first make sure that in Settings/Repositories/Third-Party Software that the partner line is clicked.

---

### Post by Sinkingships7 on 2008-01-19
> **fjgaude said:**
> Use Synaptic and Search for vmware. Click it. Install.

But first make sure that in Settings/Repositories/Third-Party Software that the partner line is clicked.

that worked like a charm! thank you!

---

### Post by iansane on 2008-01-19
I think I must have had the issue and just went to vmware site to solve it. I'm still new and finding out everyday just how powerful synaptic is.

Does anyone know why the player in add/remove doesn't install? I thought add/remove, apt-get, and synaptic all used the same repos but synaptic just allowed you to see them all or something like that. I guess my noobness is really showing now. :-)

---

