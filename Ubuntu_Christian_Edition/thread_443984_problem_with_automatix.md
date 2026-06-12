---
title: "problem with automatix"
date: 2007-05-14
forum: Ubuntu Christian Edition
---

### Post by framinglory on 2007-05-14
first off i must say i like the ce version of ubuntu, and have no problems with it at all, however i found a potentially problematic..problem

everytime i load the ubuntu ce installer (the one in system>adminitstration>ubuntu ce installer) and then close it later, instead of adding back the feisty automatix repository, it adds edgy, and i'm not sure why. fortunately it is of little consequence, for many reasons, a. i usually only click on the installer by accident, as i've installed everything i need from it. and b. i can just comment out the repository it adds.
However, it could be a potentially serious problem, as it tries to "update" automatix to the edgy version, which subsequently seems to have an affect on package managers after running automatix. unless i force automatix back to it's "old" version, i can't use apt-get or aptitude (i get the "cannot get a lock on sources" problem.)

**to sum it up**, ubuntu ce installer in system>administration is replacing my repositories incorrectly, which is obviously a problem.
if you need more information, just let me know.

this is my sources list as of now
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
#Automatix
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main
#Ichthux
deb [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main
deb-src [http://archive.ichthux.com/ichthux](http://archive.ichthux.com/ichthux) grace main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse
#Wine
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main   > these are all the times it adds edgy repo that i comment out.
#deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by mhancoc7 on 2007-05-14
Thanks for catching this. I am going to be working on an updated release of Ubuntu CE and this will be fixed in it.

God Bless, Jereme

---

### Post by Tru on 2007-05-14
Yes, I have had this same problem with Ubuntu CE 3.0, but I quit using that installer as it doesn't have anything I want in it.  I did it once to see what was in it then it messed up my repos, so I haven't opened it since and actually it would also hang when trying to restore my repos to which messed things up even more.

---

### Post by framinglory on 2007-05-14
glad i could help.
out of curiosity, do you know why it's doing this?

---

### Post by mhancoc7 on 2007-05-15
Yes, one of the scripts used by the UCE Installer is appending the wrong sources to your sources.list file. I would advise not using it until the fix is released.

Thanks, Jereme

---

