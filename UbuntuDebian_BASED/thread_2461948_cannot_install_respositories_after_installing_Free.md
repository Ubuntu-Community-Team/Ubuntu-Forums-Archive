---
title: "cannot install respositories after installing Freespire with ubuntu 20.04"
date: 2021-05-10
forum: Ubuntu/Debian BASED
---

### Post by jwmullins2 on 2021-05-10
I have installed other flavors of ubuntu and think I have found the one I want to use. I have installed Freespire based on ubuntu 20.04. I am trying to install an app that needs anbox or wine to run it. I have had no success in installing either one. It appears I cannot install a respository that is needed. One error message says "Malformed entry 70 in list file   /etc/apt/sources.list   (Component).
  I am new to ubuntu even though I have tried different OSs based on ubuntu. This is the first one I have really liked. I can use the terminal fairly well. Any help will be greatly appreciated.
I have an HP mini 5103

I thank you in advance.

---

### Post by deadflowr on 2021-05-10
*Thread moved to **Ubuntu/Debian BASED***

What are the entries you tried to add?

---

### Post by jwmullins2 on 2021-05-27
> **deadflowr said:**
> *Thread moved to **Ubuntu/Debian BASED***

What are the entries you tried to add?

Sorry. I am not sure. If you mean which repository, I was trying to install Anbox so that I could install Playstore. I have tried different people's
procedures. If you could tell me where to find one. I can tell you exactly what it says. Sorry to be a bother.

---

### Post by deadflowr on 2021-05-27
>  I am not sure. If you mean which repository, I was trying to install Anbox so that I could install Playstore.
I mean what are the entries for what you added.
Post the sources.list file
```
cat /etc/apt/sources.list
```

---

### Post by scorp123 on 2021-05-27
> **jwmullins2 said:**
> One error message says "Malformed entry 70 in list file   /etc/apt/sources.list   (Component).

So .. why are you not posting that file then so we can take a look? "Malformed entry" sounds like you got a typo in there. Post the file. Show us.

---

### Post by jwmullins2 on 2021-05-28
When I enter that code, I get this
```
# deb cdrom:[Xubuntu 20.04 LTS _Focal Fossa_ - Release amd64 (20200423)]/ focal main multiverse restricted universe


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal partner


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse


# This system was installed using small removable media
# (e.g. netinst, live or single CD). The matching "deb cdrom"
# entries were disabled at the end of the installation process.
# For information about how to configure apt package sources,
# see the sources.list(5) manual.
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) bionic main
deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main
# deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main

```
 I hope this is what you meant.

---

### Post by deadflowr on 2021-05-28
There's a line missing at the end.

---

### Post by ajgreeny on 2021-05-28
I am not a wine user but I think you should delete or comment out line 66 in the sources.list file that points to a bionic repository; you already have the focal repository enabled so I suspect having the two may be causing problems as well as having no possible use that I'm aware of in a focal installation.

---

### Post by jwmullins2 on 2021-05-29
To deadflower. Tried it again. That is all that comes up. How can I get the missing line inserted?

---

### Post by jwmullins2 on 2021-05-29
To ajgreeny. I am not sure what you mean here. I alredy have wine installed and it works. I am trying to install Anbox.

---

### Post by TheFu on 2021-05-29
> **jwmullins2 said:**
> To deadflower. Tried it again. That is all that comes up. How can I get the missing line inserted?

Always add 1 extra blank line at the end of every config file.  ALWAYS!!!  It is an old Unix thing.  Some programs just don't understand that the EOF and EOL markers are equivalent, so they don't handle EOL.  Which can make the last line with an EOF, no EOL, not seen.

>  To ajgreeny. I am not sure what you mean here. I alredy have wine installed and it works. I am trying to install Anbox. 
Mixing repos from different distros is a failure. Asking for trouble. It is bad.  Remove the lines that have bionic in them of you are running focal.  This is a "truth" in the world, not up for debate.

---

### Post by deadflowr on 2021-05-29
> **jwmullins2 said:**
> To deadflower. Tried it again. That is all that comes up. How can I get the missing line inserted?

Let's forgo the sources.list file and see what
```
sudo apt update
```
outputs.
Post those results.

The issue with a missing line is the fact that the error relates to line 70 missing or having a broken component field,
but all entries shown have correct components. And the last entry doesn't even matter.
So looking at the output from apt should narrow things down or explain more on where the issue might be.

---

