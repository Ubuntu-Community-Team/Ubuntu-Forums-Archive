---
title: "System error caused by sources.list"
date: 2014-01-12
forum: Ubuntuzilla
---

### Post by Sleepy-zz-John on 2014-01-12
Hi.    I'm finding what appears to be a very similar problem to the one in thread  "Error in apt-get for SourceForge" 
Started by DPMR, 3 Weeks Ago.

First, a bit of background to my case:

I've got a new laptop on which I've installed precise 12.04.3 and I'm trying to add Seamonkey 2.23 on it,  which is not available in Software Center.   Consequently I've been following the Installation section on [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page).   Everything seemed to go OK up to the line "Update your package database"  and the entry "sudo apt-get update",  but then:

:~$ sudo apt-get update
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.,    

Not good,  so here's a copy of my sources.list:

```
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.3 LTS _Precise Pangolin_ - Release amd64 (20130820.1)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://th.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://th.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://th.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://th.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://th.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://th.archive.ubuntu.com/ubuntu/ precise universe
deb http://th.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://th.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://th.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://th.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://th.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://th.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://th.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://th.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb https://launchpad.net/~exalm/+archive/seamonkey 2.23
deb-src https://launchpad.net/~exalm/+archive/seamonkey 2.23
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Of course that errored line 59 contains exactly the source that I want to use,  but I can't see what's wrong or how I could correct it.

The situation then becomes more serious because I subsequently find sources.list is giving me a system error that's preventing me from opening Software Center.   The only way I've found to overcome this is to restore my sources.list back to it's original version without the additions I need. 

Would appreciate some explanation if possible why line 59 there is causing this trouble,  and how I might add  deb [https://launchpad.net/~exalm/+archive/seamonkey](https://launchpad.net/~exalm/+archive/seamonkey) 2.23 to my available sources so I can proceed to the next step of 

sudo apt-get install seamonkey-mozilla-build

---

### Post by steeldriver on 2014-01-12
The ppa appears to be only available for quantal - the exact syntax to add it is given if you click the 'Technical details about this PPA' link on the launchpad page

```

deb [http://ppa.launchpad.net/exalm/seamonkey/ubuntu](http://ppa.launchpad.net/exalm/seamonkey/ubuntu) quantal main 
deb-src [http://ppa.launchpad.net/exalm/seamonkey/ubuntu](http://ppa.launchpad.net/exalm/seamonkey/ubuntu) quantal main 

```

---

### Post by nanotube on 2014-01-14
> **Sleepy-zz-John said:**
> 
E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.,    

```
...
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```


I am using precise, and have exactly the same line for ubuntuzilla in my sources, with no problems... 
could it be one of the lines you have above it that's confusing the package manager? Try deleting the ppas above it and giving it another shot?

> 
The situation then becomes more serious because I subsequently find sources.list is giving me a system error that's preventing me from opening Software Center.   The only way I've found to overcome this is to restore my sources.list back to it's original version without the additions I need. 


Well, that's not a bad idea - restore to original, then add things one by one, and run 'sudo apt-get update', after every one, to see where exactly the problem crops up.

> 
Would appreciate some explanation if possible why line 59 there is causing this trouble,  and how I might add  deb [https://launchpad.net/~exalm/+archive/seamonkey](https://launchpad.net/~exalm/+archive/seamonkey) 2.23 to my available sources so I can proceed to the next step of 

sudo apt-get install seamonkey-mozilla-build

the launcpad ppa doesn't use mozilla builds. and also as previous post mentioned, doesn't seem to exist for precise.

please let know how the troubleshooting goes.

---

### Post by Sleepy-zz-John on 2014-01-17
Thanks steeldriver and thanks nanotube for your responses.   I finally took a different approach to this problem and worked with Exalm, the PPA originator, to have a Precise version of Seamonkey 2.23 made available instead of trying to use his Quantal version,  and after a few false starts I've now successfully installed from that.   I never did discover the exact cause of that sources.list line 59 error,  but I may have made some procedural mistakes in my earlier PPA attempts with the Quantal version..  A dependency not satisfiable issue arose and I know I made the mistake of downloading the ppa quantal .deb file and trying to install it in Software Center instead of starting with a Terminal add-apt-repository ppa: command,  so maybe my line 59 error was somehow caused by that.   

Anyway,  appreciate that you both tried to come to my rescue on this one.

---

